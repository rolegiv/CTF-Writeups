# Твистер Джуниор (RE, Easy) by [w33d](https://github.com/w3irdd) (First blood - Bronze)

Все исполняемые файлы с CTF после детекта оказались PE-файлами, написанными на C++, так что этот момент опущен в решениях.
После запуска, программа ничего не делает, но ждет чего-то на ввод. Дизассемблируем.

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/41069be2-b7ef-4c1b-a957-ea1df87cefb5)

Видим, что программа ожидает нажатия четырех определенных клавиш, а именно
Ctrl + Shift + Insert + Home
Флаг выводится в терминал:

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/3f81ab50-0c4c-4d20-8935-a2ded5498e6d)

# Флаг
**B0NU${Y0U_KN0W_THE_H0TK3Y}**
