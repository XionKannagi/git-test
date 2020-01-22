# Gitの操作【初級編】の練習リポジトリ

@version 0.0.1

### テキストの編集完了
バージョンを更新  
git tagのテスト  

```
$ git tag -a "v0.0.1" -m "バージョン0.0.1をリリース"
$ git add .
$ git commit -m "コミットコメント"
$ git push origin master
```

tag付けを後からする場合は 

```
$ git add .
$ git commit -m "コミットコメント"
$ git push origin master
$ git log
$ git tag -a "v0.1.1" -m "バージョン0.0.1をリリース" <コミット番号>
$ git push origin v0.1.1:v0.1.1
```
***※基本的にはリリース可能なバージョンにtagをつけるため後からつける。*** 


# tagからのcheckout
```
$ git chechout -b v0.1.0 v0.0.1
```

