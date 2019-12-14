### QuerySetAPIについてのメモ書き
___
##### 12/15/2019  
1. クエリセットとは：モデルのオブジェクトのリストのこと。
* データベースからデータを読み込んだり、抽出したり、並べ替えたりできる。
2. pyton manage.py shell で実際にクエリセットを操ることができる。
* モデルの読み込みが必要。
3. ORMの構文  
```>>> Post.objects.filter(title__contains='title')```
* アンダーバーが１つの場合：title_containsというフィールド名だと判断される
* アンダーバーが２つの場合：フィールドとフィルター（"contains"）をセパレイトすることで照合される。  
4. Method-chaining(非常に強力なクエリセットの武器)  
```>>> Post.objects.filter(published_date__lte=timezone.now()).order_by('published_date')```  
```>>> <QuerySet [<Post: Post number 2>, <Post: My 3rd post!>, <Post: 4th title of post>, <Post: Sample title>]>```  

5. https://docs.djangoproject.com/ja/2.2/ref/models/querysets/ (クエリセットのドキュメント（英語))  
6. いくつか紹介  
* filter(**kwargs)/exclude(**kwargs):与えられたパラメーターにマッチした/しなかったオブジェクトを返す。
* order_by(*fields):呼び出すデータの順番を変える。
* values(*fields, **expressions):辞書型のクエリセットを返す。values_listの場合はタプルで返す。
* union(*other_qs, all=False):クエリセットを合体する。
* select_related(*fields):外部キーのオブジェクトを参照することができる。
