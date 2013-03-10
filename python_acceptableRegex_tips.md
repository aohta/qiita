acceptableRegex.py というライブラリを利用すると、正規表現にマッチする文字列を返してもらえます。
結果を利用するとファジングぽいことができます。

### インストール

ファイルは、githubから取得します。

```sh
$ git clone https://github.com/tokoroten/acceptableRegex.git
```

### 利用方法

取得した acceptableRegex.py を PYTHONPATH が通っている箇所におくか、
作成するスクリプトと同一ディレクトリに置きます。

使い方は、 acceptableRegex.py の main() にありますが、
getAcceptableRegex に正規表現を渡すと、マッチする結果を返されます。

```python
from acceptableRegex import getAcceptableRegex

if __name__ == '__main__':
    print getAcceptableRegex('[0-9]{9}')
```

このサンプルだと、 9桁の0から9の数値が返されます。

### てきとうなCSVを作る

acceptableRegex.py の結果を利用すると、
CSV を読み込んでなにかをするプログラムなどのテストで利用するなどできそうです。

```python:sample.py
# -*- coding: utf-8 -*-

import csv

from acceptableRegex import getAcceptableRegex

if __name__ == '__main__':
    with open('eggs.csv', 'wb') as f:
        csvfile = csv.writer(f)
        for x in range(1, 100):
            syouhin = getAcceptableRegex('[a-zA-Z]{10}')
            price = getAcceptableRegex('[01]{1}[0-9]{3}')
            category = getAcceptableRegex('(aaa|bbb|ccc|fff)')
            csvfile.writerow([syouhin, price, category])
```

