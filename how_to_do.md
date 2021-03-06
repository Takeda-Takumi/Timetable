# 基本的な開発手順
### このリモートリポジトリを4人で共有します
このリモートリポジトリを直接各々のローカル環境に落としてもらって、featureブランチが完成したらpushしてプルリク出して、github上でdevelopにmergeするスタンスでやります。

### forkは使わなくていいと思う 
そもそもgitに慣れてないし、fork使うと若干手間がかかる。OSSみたいに知らない人とやるわけでもないし、1つのリモートリポジトリを共有して開発するほうが楽だし、gitに慣れるにはいいと思う

## 命名規則
### 使用する規則
- PascalCase(UpperCamelCase)
	- 先頭を大文字にし、単語の区切りを大文字にする<br>
	myfirstproject -> MyFirstProject
- snake_case
 	- 単語はすべて小文字で、単語の区切りを_(アンダースコア)で仕切る<br>
	myfirstproject -> my_first_project	

|場所|命名方法|
|--------|--------|
|クラス|PascalCase|
|クラスメソッド|snake_case|
|クラス変数|snake_case|
|privateなクラスメソッド|snake_case|
|privateなクラスメソッド|snake_case|
|変数|snake_case|
|ファイル名|snake_case|

## コミットメッセージの書き方
参考: https://qiita.com/itosho/items/9565c6ad2ffc24c09364
* フォーマット<br>
1行目：\[コミット種別\]変更内容の要約（タイトル、概要）<br>
2行目 ：空行<br>
3行目以降：変更した理由（内容、詳細）<br>
* コミット種別<br>
fix：バグ修正<br>
add：新規（ファイル）機能追加<br>
update：機能修正（バグではない）<br>
remove：削除（ファイル）<br>
* 例<br>
>\[fix\]削除フラグが更新されない不具合の修正<br>
>(空行)<br>
>refs #110 更新SQLの対象カラムに削除フラグが含まれていなかったため追加しました。<br>



## 初期設定

### 1. **ローカル環境にcloneする**<br>
git clone https://github.com/Takeda-Takumi/TimeTable<br>
<br>
### 2. **リモートリポジトリのURLを設定**<br>
git remote set-url origin https://Takeda-Takumi@github.com/Takeda-Takumi/TimeTable<br>
<br>
### 3. **リモートのmasterの内容をローカルのmasterに反映させる**<br>
* origin/masterを追跡対象にする<br>
(masterにいる状態で) git branch -u origin/master<br>

* リモートの情報をローカルのmasterに反映<br>
git pull<br>
### 4. **developブランチを切る**<br>
* developブランチを作成する<br>
(masterにいる状態で) git branch develop<br>
* developブランチに移動<br>
git checkout develop<br>
### 5. **リモートのdevelopの内容をローカルのdevelopに反映させる**<br>
* origin/developを追跡対象にする<br>
(developにいる状態で) git branch -u origin/develop<br>

* リモートの情報をローカルのdevelopに反映<br>
git pull<br>
<br>

## 開発の進め方
### 1. developを最新の状態にする<br>
* ***!!!!!!!!!!!!必ず実行してください!!!!!!!!!!!!!!!!!!!!!***
* (developにいる状態で) git pull
* **!!!!!!どんなときでも新しくブランチを切るときは、必ず最新の状態にしてから切ってください!!!!!!!**
### 2. developからfeatureブランチを切る<br>
* featureを作成<br>
(developにいる状態で) git branch feature/<このブランチでやることを端的に表した名前><br>
> 例: カレンダーを作る => feature/createCalendar
* featureに移動<br>
git checkout feature/<付けた名前><br>
* あまり大きな単位でブランチを切らないほうがいい<br>
> × カレンダーを作り、日付を表示して、通知機能を付ける<br>
> ○ カレンダーの枠組みを作る

### 3. **featureブランチで機能を実装する**<br>
### 4. commitする<br>
* commitしたいファイルをステージングする<br>
 git add <コミットの対象とするファイル><br>
> [例]<br>
> git add README.md<br>
> git add text.txt<br>
> git add . (ピリオド)で全てのファイルを選択できる<br>
* ステージングしたファイルをcommitする<br>
		git commit -m "<コミットメッセージ>"<br> 
* <コミットメッセージ>はそのコミットで追加した内容を端的に記載する<br>
> [例]<br>
> 時間割の枠組みを作成しました。<br>
> コマをクリックしたときにウインドウが出るようにしました。<br>
### 5. **pushする**
* 始めてpushする時<br>
		git push -u origin <そのブランチの名前>
* 2回目以降<br>
		git push<br>
### 6. **pull requestを出す** <br>
* https://github.com/Takeda-Takumi/TimeTable にアクセスして、赤枠をクリック<br>
	![image](https://user-images.githubusercontent.com/91676218/152789679-f823601b-6c6d-4bf6-9cc9-202654096c48.png)<br>
	<br><br>
* 赤枠をクリック<br>
	![image](https://user-images.githubusercontent.com/91676218/152791199-a8eaf696-d615-4625-9d54-7b930fa83308.png)<br>
	<br><br>
* ***まじで重要！！！！！！***<br>
	![image](https://user-images.githubusercontent.com/91676218/152791911-0b1f0cb3-4b43-4148-a982-05a31bd8ed9c.png)
	* ① base: developになってることを確認
	* ② compare: feature/<今からの追加する機能>になっていることを確認<br>
	<br><br>
* 大丈夫だったらクリック<br>
	![image](https://user-images.githubusercontent.com/91676218/152792857-9fe2f9ff-b35e-4893-b2c1-0493e5db72bc.png)<br>
	<br><br>
* コメントを書いて, Create pull requestを押す<br>
	![image](https://user-images.githubusercontent.com/91676218/152793861-e8e633fa-154e-4c09-83ab-23bf264ea457.png)<br>
<br><br><br><br><br>
### 7. **developにmergeする**
* pull requestができると、ホーム画面のPull requestの所に通知が出ます<br>
	![image](https://user-images.githubusercontent.com/91676218/152794653-3e15ee1d-aa28-4576-8a30-bd0e9d7f28c5.png)<br>
	![image](https://user-images.githubusercontent.com/91676218/152794907-afd79574-4188-4f85-9a9f-1d7f544e9773.png)<br>
	<br><br>
* ソースコードを読みます<br>
	![image](https://user-images.githubusercontent.com/91676218/152795439-1063747a-f07d-43be-afed-0595af102e18.png)<br>
	<br><br>
* file changedはこのように表示されます
	![image](https://user-images.githubusercontent.com/91676218/152795639-cc56f240-c3ec-4e7d-9cc9-d13c7ecaa562.png)<br>
	<br><br>
* 問題なさそうであれば、mergeします
	![image](https://user-images.githubusercontent.com/91676218/152795908-056d0859-016f-4729-994c-cc8fcb91e711.png)<br>
	![image](https://user-images.githubusercontent.com/91676218/152796110-0dbaecc2-cf8a-45a5-bd34-a7519d135f1f.png)<br>
	<br><br>
* **今回のプロジェクトでは自分でmergeしてしまって構いません**<br>
	* 各個人で自由に作業してもらっているため、他の人にマージしてもらう方法だとマージしてもらうまでの待機時間が長くなってしまうので、今回は自分でmergeしていいことにします。<br>
	* 誰かと作業時間が揃っていたら、練習がてらコードレビューをしてマージしてみてください。
	* 実際の開発では、自分でマージせず上司の方や他の人にコードレビューをしてもらってからマージします。


<br><br><br><br><br>
### 8. **featureブランチの削除**<br>
* mergeを行ったら、mergeしたfeatureブランチは削除してください<br>
* ①と②を順番にクリック<br>
	![image](https://user-images.githubusercontent.com/91676218/152797504-dccd44ae-b693-4ece-aed3-57bd8955db11.png)<br>
	<br><br>
* Active branchesから削除したいブランチのゴミ箱ボタンをクリック
	![image](https://user-images.githubusercontent.com/91676218/152797875-2d5eae77-d077-4bc1-a8a2-59d59581aa01.png)<br>
<br><br>
これを繰り返して開発を行う予定です<br>
分かりにくいと思うので、遠慮なく聞いてください<br>
