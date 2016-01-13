import requests
from bs4 import BeautifulSoup
import time

def all_spider(max_pages):
    page = 0
    count = 1
    nap = 5
    dest_url = r'Ljoy_links.txt'
    fw = open(dest_url, 'w')
    while page <= max_pages:
        url = 'http://old.reactor.cc/all/' + str(page)
        var_page = requests.get(url)
        plain_text = var_page.text
        soup = BeautifulSoup(plain_text, "html.parser")
        tags = soup.findAll('img')
        fw.write('Joy page is ' + url + '\n')
        for tag in tags:
            src = tag.get('src')
            post_cheker = src.split('/')
            for word in post_cheker:
                if word == 'post':
                    fw.write(str(src) + ' ' + '\n')
        page_counter = page % 10
        if page > 0:
            if page_counter == 0:
                print(count, ' pages completed. Last page is ', page, '\n')
                print('take a nap for ', nap, ' seconds')
                time.sleep(nap)
        page += 1
        count += 1
    fw.close()
    print('Parsing complete')

