# SomDef (Криптография, Easy) by [w33d](https://github.com/w3irdd) (First blood - Gold)

# Задание

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/921e9017-93e1-4271-a2d0-3c54584cc334)

# Решение

Шифротекст:

THECAPTUREFLAGTHECAPTURETHETHEFLAGTHECAPTURETHETHE
CAPTURETHECAPTURETHEFLAGTHECAPTUREFLAGTHECAPTURECAPTURETHEFLAGTHETHETHEFLAGTHECAPTURETHECAPTURETHECAPTURE
CAPTURETHECAPTURECAPTUREFLAGCAPTURECAPTURECAPTUREFLAGTHETHECAPTURE
CAPTURETHECAPTUREFLAGCAPTURETHEFLAGCAPTURECAPTURECAPTUREFLAGTHECAPTURECAPTURE
THETHECAPTURETHEFLAGTHECAPTURETHETHEFLAGTHECAPTUREFLAGCAPTURECAPTURETHE
THETHECAPTURETHEFLAGCAPTURECAPTURECAPTUREFLAGTHECAPTURETHEFLAGCAPTURECAPTUREFLAGTHECAPTUREFLAGCAPTUREFLAGTHECAPTURETHECAPTURETHECAPTURE
CAPTURECAPTUREFLAGCAPTURECAPTURECAPTURECAPTURECAPTUREFLAGTHECAPTURETHEFLAGCAPTURECAPTURETHETHEFLAGCAPTURECAPTURECAPTURECAPTURETHEFLAGCAPTURETHEFLAGCAPTURETHECAPTUREFLAGTHECAPTUREFLAGTHECAPTURETHECAPTURETHECAPTURE

Сразу видно, что это дискретный шифр и, скорее всего, морзянка. Слово FLAG – разделитель, THE – точка, CAPTURE – тире. Расшифровываем. ALL CAPS! YOU KNOW FLAG FORMAT! M0RZ9NKA!

# Получаем флаг

**B0NU${M0RZ9NKA}**
