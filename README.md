## リブロワークス，『Docker&仮想サーバ完全入門　 Web クリエイター&エンジニアの作業がはかどる開発環境構築ガイド』，2022

### section11-4 「flask コンテナを構築する」について

- 以下のように修正した
  remove

```
RUN pip install flask==2.1.0
```

add

```
RUN pip install flask===2.2.2
RUN pip install WerkZeug==2.3.7
```

### 原因

- 書籍出版後，WerkZeug のアップデート時に'url_quote'が削除されたっぽい．そのため，flask と Werkzeug のバージョンを適切に合わせないとエラーが出て動かなくなるらしい．
- 修正後，`docker compose build`してから`docker compose up -d`したら治った．
