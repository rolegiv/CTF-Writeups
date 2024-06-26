# ФигВам (Misc, Easy) by [w33d](https://github.com/w3irdd)

# Задание

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/97473c08-a7c5-4009-9031-6bd0302b7ce8)


# Решение
![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/203ad3fe-1d81-49b0-8ceb-26b333bfd118)

Здесь картинка с фигой. Находим ссылку на проект в Figma:

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/600fbc5c-e49c-4033-94d6-e91bdec72d0a)


https://www.figma.com/file/k7kcbJAL5dRIFi45OnBRLJ/Untitled?type=design&node-id=0%3A1&mode=design&t=b5zN7EGul107LvJ5-1

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/81277c7d-8e6a-445b-a68e-613223f06862)

Находим среди кучи картинок картинку с текстом. Тут зашифрованный флаг.

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/04120fbb-016c-4b80-94a9-ed877da4ec9f)

Так как нам известно, что формат флага - "B0NU${}", можем предположить, что это ROT. После математического сдвига в 5 символов получаем флаг.

# Флаг

**B0NU${$t3r30f1gma}**
