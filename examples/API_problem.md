## Example API problem

### Problem name
Luke and languages

### Problem Statement
Luke is learning many languages so that he can communicate easily during his journey. He came across a difficult paragraph in Dutch language. He didn't understand the meaning of certain words. Translate those words to english for him. The difficult words are highlighted in paragraph as follows.
```
>>difficult_word<<
```

Use the below API
https://tech.yandex.com/dictionary/

Note:
The script will run in linux environment with root access and internet connectivity.

### Input format
A single line containing a paragraph **S** in dutch language.

### Output format
n lines, each containing the english translation of each highlighted word in the order in which they appear in the paragraph. In case if there are multiple translations for a word, output the first translation.

### Limits
1 <= |S| <= 10000

### Sample test cases

### Input
```
Na weken van hard werken is het dan eindelijk zover. >>Morgen<< gaan de deuren open voor de officiele opening van Pan&Cook het nieuwe restaurant in het centrum van Rooi. Het pand op de hoek Heuvel-Kerkstraat vroeger >>bekend<< als "Pand Gloudemans" en de laatste jaren in gebruik geweest bij Van de Ven Accountants herbergt voortaan een restaurant waar de hongerige consument, jong en oud, terecht kan voor een op traditionele wijze gebakken pannenkoek. Maar ook voor een lunch of een feestje of partijtje kan men er terecht.
```
### Output
```
tomorrow
known
```

### Tags
API, Easy, regex, Yandex, Dictionary

### Editorial
https://tech.yandex.com/dictionary/doc/dg/reference/lookup-docpage/

### Solution

``` python
import requests
import json
import re

def main():
    p = raw_input()
    urlt = 'https://dictionary.yandex.net/api/v1/dicservice.json/lookup?key=APIkey&lang=nl-en&text={word}'
    pattern = re.compile(r'>>(.*?)<<')
    words = pattern.findall(p)
    for word in words:
        #print word
        url = urlt.replace('{word}',word)
        res = requests.get(url)
        json_res = json.loads(res.text)
        #print(json.dumps(json_res, indent=2))
        print(json_res['def'][0]['tr'][0]['text'])

if __name__ == '__main__':
    main()
```
