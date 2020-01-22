# Gitの操作【初級編】の練習リポジトリ

@version 0.0.1

### テキストの編集完了
git コマンド集 
  

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

# ブランチの削除 
ローカルブランチの削除  
```
$ git branch -D <ブランチ名>
```

リモートブランチの削除  
```
$ git push origin <ブランチ名>
```

# コミットコメントの修正

```
$ git add .
$ git commit -m "issue 365日の修正対応"

$ git log
$ git commit --amend -m "issue 365の修正対応"
```

```
$ git add .
$ git commit -m "issue 365の修正対応"
:

$ git add .
$ git commit -m "issue 366の修正対応" 
:

$ git add .
$ git commit -m "issue 366の修正対応" 
$ git log
```

```
$ git rebase -i HEAD~3
pick d6d9ec4 issue 365日の修正対応 <- こいつのコミットメッセージを修正する。
pick e1cb3cb issue 366の修正対応
pick a202fbd issue 367の修正対応 

↓

edit d6d9ec4 issue 365日の修正対応

```
これで、コミット履歴の３つ前に戻っている状態になる。
修正したいコミット先頭の「pick」を「edit」に書き換える。
***※もしも該当コミットの作業自体も修正・変更したい場合は、  この時点で作業ファイルを修正することも可能です。***  

```
$ git commit --amend -m "issue 365の修正対応"
$ git rebase --continue
$ git log
```
対応完了です。

ここから下の内容はコンフリクトぼ原因になりうる変更です。
＊
＊
＊
＊
＊
＊
ここ以上でコンフリクトが発生する可能せいある。
