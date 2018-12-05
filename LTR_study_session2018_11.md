#第三回　LTR勉強会

## **How to use LTR Solr Plugin** プロローグ （Presented by ）

###検索システムで困る時
* want to tune ranking 
	1. score * 100 
	2. Title と本文のブースト値を変える。
	3. このようにチューニングしてもinverted indexが変われば、チューニングのし直しが必要になる。

###LTRとは
* 検索結果に対するユーザーのアクション（クリックetc）を得点化して、ランキングに反映させる。

###SolrのLTR
1. Solrの起動
	* defult で設定されていないので、設定する必要がある。
```sh 
bin/solr start -p 
```	
2. 素性抽出の条件を作成 
	* Solr documentの中でどれをリランクする時に用いるのかを定義する。	
		* ここで定義しておかないと使われない。
	 	* 数値でなければならない。
3. Solrへアップロード	
* check if your 素性 is uploaded to Solr.  
Send the following request. 
```sh 
あとでおしえてもらう
``` 
4. Define the Model 
	* re-rank 時の重みを決定する。

5. Re-rank してみる。

6. 肝心のモデル定義
	* Solrのソースをダウンロードする		
	* Liblinearとダウンロードする。
	* DIR name に注意。
	* python2を使用（３は動かない）
７. Liblinearを使うために・・・
	* Example Folder に必要なものは基本的に含まれている。
		* <font color="red">source code を落とした場合に限る。</font> binaryではだめ。
		* `ExampleFeactures.js ` を編集する
8. Function Query との違い  
リランクは基本的に重みを決定する　ー＞　重み調整を行うFunction Queryと何が違うのだろうか？
	* LTR のメリット
		* Top N 件のみをリランクの対象にするので、計算量を抑えられる。
		* リランクの際はSolrのスコアは考慮されない。
			*選択した素性のみでリランクする
			* Function QueryだとSolrのスコアと合算されるので、Solr自体のスコアの影響を受けてしまう。
	* LTRの大変なところ
		* 渡すJson が複雑になるところ

## **海外カンファレンス報告.** ーランキング学習の現状ー　(Presented by )
1. LTR usecase 1
	* Elsevier 
		* Science Direct のリコメンデーション　
			1. データの前処理　（ユーザーのアクティビティ）
			2. データの前処理　
			3. IBCF モデル　強調フィルタリング（Collaborative Filtering, CF）の一種
			4. 
2. 強調フィルタリング（Collaborative Filtering, CF）
	* Memory-based 
	* User-based 
	* Item-based -- Science Direct で使用
		* メリット
			* Userのパーソナルinformationが必要ない
		* デメリット
			* 極端に人気のある記事がリコメンドされやすい
3. LTR usercase 2
	* HomeDepo 
		* Auto-complete にLTR を使用する　（斬新なアイデア）
		* type ahead service 
			* Suggestion として`よく使われる単語（キーワード` をより上位にあげる。
		* 正解はクリックデータに基づく。
		* 検索語候補のリストが文書リスト
		* 入力された文字、時間がクエリ
4. LTR usercase 3
	* Bloomberg 
		* Solr の LTR を開発しdelpoyした会社。
		* 検索改善にLTRを利用
		* Label はマンパワーでつける
	* deploy までの過程と結果
		* 期待の結果を確認するが、パフォーマンスが悪くなる。
		* 試用：ユーザー１割に試す。
		



