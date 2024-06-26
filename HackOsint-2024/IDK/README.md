# IDK (Криптография, Hard) by [rolegiv](https://github.com/rolegiv)  [w33d](https://github.com/w3irdd)

# Задание

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/68290b11-e583-42e2-a600-7c8b6a410062)

# Решение

Открываем файл, видим сигнатуру JPEG. Меняем расширение файла.

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/43a41b30-ec54-4b1d-baf9-21c541ad0da0)

Внутри обнаруживаем зашитый с помощью Steghide текстовый файл.

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/6d033c99-0937-464f-842f-eb49d3e60750)

Шифротекст:
ThereIsNoKey
Ils7CnNDN0gaZxkFVjEFVjZZJ1hyVgcrHFYTKhVBKwknUjYQAyIDBRcjExMwFjdOfDonIVAPGTFWWDwWJBcmWAtnBxcPZAJcch02VCBJHjNQAh4tBRM/HCBEM1cLZwcfAiwZRiZZMhc5VRdnBB4TKlZKPQxzQDtcAmcTGhctGxMmETpEclIBKQUFWE58cWI3BhMpSF4VLxUkPSYEYjk9Ax4BHT5UKT0UQk5YcwBYclcBKBRWGjEVWHNZGhclWR0vUA8ZMVZBNxg/WysQBSkfAVYsGURyIRxlclUAJAIPBjAfXDxZMls1XxwuBB4bZAFcIBIgGVhgQBReVj9kHlIkHHNAIFkaMxUYViVWRz0WPxc0XxxnKDkkZBVBKwknWDNeDysJBR83VlEzCjZTcl8AZzsYGTMYEwIVMl48RAs/BFY3MAJSMRJ9PQFfAyJQAhMnHl07GjJbclkAIR8EGyUCWj0XaT0GWAtnKDkkZBlDNwsyQztfAGcTFxhkFFZyDD1TPV4La1AXGigZRDsXNBc9XgtnBBlWIBNXJxo2FyZYC2cVGBU2D0MmEDxZclsLPlAQBCsbEyYRNhciXA8uHgITPAITMxc3FzFZHi8VBAIhDkd8WQdfO0NOJBgXBCUVRzcLOkQmWQ1nFQ4GKwVWIVkLeAAQGihQAAMoGFYgGDFePlkaLhUFVjcDUDpZMkRyewAoBxhWFBpSOxcnUipETgYEAhcnHUB+WSNWIEQHJAUaFzYaSnIOO1I8EBovFVYdIQ8TOwpzUjtEBiICVgQhBlYzDTZTcl8cZwMeGTYCViBZJ18zXk4zGBNWKRNAIRg0UnwQOi8VVgQrGUdyFjUXJlgHNFAAAygYViAYMV4+WRo+UBofIQUTOxdzQzpVTjUVBhMwH0c7DzYXIlEaMxUEGGQCWzMNc1I/VRwgFQVWMx5WPFkyFyFYATUEVh0hDxM7CnNWIkACLhUSVikDXyYQI1s3EBouHRMFZBJGIBA9UHJEBiJQLjkWVlY8GiFOIkQHKB5WBjYZUDcKIBk=
Подсказка в самом названии текстового файла и на первой строке. Это XOR с Base64. 

Брутфорсим шифротекст:

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/03172f90-5260-426d-a1bf-5c40769eb512)

Так же один из инструментов решения после окончания CTF был предложен одним из организаторов [FazaN](https://github.com/CyberFazaN) там в полуавтоматическом режиме можно подбирать ключ - [XOR_KPA](https://github.com/CyberFazaN/XOR_KPA)

# Флаг
**B0NU${x0R_cRyP70@n4L1sy$_KP4}**
