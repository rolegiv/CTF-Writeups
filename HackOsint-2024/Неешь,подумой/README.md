# Не ешь, подумой (RE, Medium+) by [w33d](https://github.com/w3irdd)

# Задание

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/6eaefd10-c2fc-47c9-a29d-936f191368db)


# Решение

Вот, что мы видим при запуске.

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/59cdc002-87ff-4083-92b1-fa32b361721f)

Сразу скажу, что в загловке окна рикрол в Base64 :) Запускаем IDA.

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/1a82917f-33da-4234-a9e5-83c989dc8fc9)

Находим, где у нас подгружается картинка. Переходим по адресу и копируем байты по этому адресу. Здесь вся начинка картинки, но без хедера, поэтому она у нас не откроется. Добавляем самый обычный JPG-хедер с RGB и получаем оригинал.
Пробуем брутить его через stegseek.

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/b4dbe550-4a95-4426-a3aa-4d49995be174)

# Флаг
**B0NU${B1RD_G0T_0WNED_BY_SH4URM4}**

