# Discard (Misc, Easy) by Awebo

# Задание

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/daab22c9-7f9a-4ec6-8b01-60ead808e179)

# Решение

Шифротекст:

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/b4497eb8-2fa5-4d06-8fad-25164af28231)

Выписываем строку, пытаемся подобрать шифр. 9EEADi^^5:D4@C5]88^8bE;!+cFtb
Это ROT47.

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/9844e402-755e-4487-9bbc-e3ac18de516f)

Переходим по ссылке на Discord-канал. Тут очень много текстовых и голосовых каналов. Прокликиваем все и находим .img файл. Это на самом деле PNG картинка (определяем по сигнатуре).

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/806890aa-5a82-4bce-93e2-f721f2ad3931)

Подсказка! Архив. Внутри зашит архив с txt файлом.

Вытаскиваем его с помощью утилиты Binwalk и смотрим текст внутри. Сразу можем заметить, что в тексте есть невидимые символы пробела и табуляции. Читаем текст и обнаруживаем подсказку: весь рассказ написан про снежинки, вывод: это 100% утилита stegsnow.

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/5c5c318d-2e02-49b4-8e21-4eb175dc84af)

# Флаг
**B0NU${Sn0WyD1sK09DF14G}**
