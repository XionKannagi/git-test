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


# コンフリクト（競合）
同時に１つのファイルを２人以上が編集し内容をマージすると  
コンフリクト（競合）という状態になる場合があります。  
一度コンフリクトすると自動的なマージができなくなるため、  
手動によるマージによる解決が必要となります。  
この時、内容を把握しない状態でマージを行うと他者の変更履歴を自分の変更で上書きし
バグはインシデントの原因につながるため十分注意しましょう。

