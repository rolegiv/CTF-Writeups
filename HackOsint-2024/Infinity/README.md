# Infinity (Web, Medium) by [rolegiv](https://github.com/rolegiv) (First blood - Gold)

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/9a73d001-ed96-464c-9c4d-7619219404b4)


На сайте ничего кликабельного нет. Смотрим console, находим ссылку для "старта испытания"

![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/3b88900e-9580-4384-8f4d-ae6db7f1214b)

Тут у нас гифки с покемонами, которые можно переключать. Из описания задания про «множественные редиректы» принимаем решение, что нам нужно долистать до последнего покемона. Напишем скрипт, который переберет все страницы.
![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/6ac2033e-cd1b-48c2-9f7d-48f79d6edf28)

Мой скрипт (Единственное приходилось постоянно менять "start_url" так как останавливались редиректы. Почему - хз. Но это буквально 2-3 раза и мы на последней странице)
```
import requests
from bs4 import BeautifulSoup

# Начальный URL
start_url = 'http://demo.hackosint.net:36363/fd579f23625840103536f084f8d0e6f9/pokes/93f38cf7fb307575fda067ab72813098.html'

def fetch_page(url):
    try:
        response = requests.get(url)
        response.raise_for_status()
        return response.text
    except requests.exceptions.HTTPError as err:
        print(f"HTTP error occurred: {err}")
    except Exception as err:
        print(f"Other error occurred: {err}")
    return None

def get_next_page_url(html):
    soup = BeautifulSoup(html, 'html.parser')
    next_btn = soup.find('a', id='nextBtn')
    return next_btn['href'] if next_btn else None

def get_img_alts(html, src_startswith):
    soup = BeautifulSoup(html, 'html.parser')
    img_tags = soup.find_all('img', src=lambda x: x and x.startswith(src_startswith))
    return [img.get('alt') for img in img_tags] if img_tags else []

def switch_pages(start_url, max_tries=1000):
    current_url = start_url
    visited_urls = []

    for _ in range(max_tries):
        html = fetch_page(current_url)
        if not html:
            print(f"Failed to fetch page: {current_url}")
            break

        img_alts = get_img_alts(html, 'http://demo.hackosint.net:36363/fd579f23625840103536f084f8d0e6f9/img/')
        print(f"Fetched page: {current_url}")
        for alt in img_alts:
            print(f"Image alt: {alt}")

        visited_urls.append(current_url)

        next_page_url = get_next_page_url(html)
        if not next_page_url:
            print("No next page found. Stopping.")
            break

        current_url = requests.compat.urljoin(start_url, next_page_url)

    return visited_urls

# Запускаем автоматическое переключение страниц
visited_urls = switch_pages(start_url)
print("Visited URLs:", visited_urls)
```

Последняя страница (редирект) и соответственно флаг
http://demo.hackosint.net:36363/fd579f23625840103536f084f8d0e6f9/pokes/6699c8dd228071cf56afffbe8d74196d.html
![image](https://github.com/rolegiv/CTF-Writeups/assets/147992165/6863a103-22e0-4d96-95b9-fd97fd34f70c)

# Флаг
**B0NU${CR4WL_CRAW1_CR4W1}**
