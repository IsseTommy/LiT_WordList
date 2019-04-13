# 単語帳アプリ
***
## １、押さえておくポイント、Swift言語特性
### ナビゲーションバーを設置したい場合
ナビゲーションバーとは画面上部にあるタイトルや戻るボタンなどがある、タブのこと  
#### 方法
1. ナビゲーションバーを設置したい、画面を選択する  
1. 画面上側のEditorからEmbit in、Navigation Barを選ぶ  
#### 方法
ナビゲーションバーにボタンを追加したい場合はBar button Itemを設置する。  

---

### ユーザーが入力できるテキストフィールドを作りたいとき
ボタンを配置するときの要領でText Fieldを設置する  

---

### Table Viewを使う方法
Table Viewとは、iPhoneの設定画面のような画面のこと  

1. MainStoryBoardでTable ViewをView Controllerの代わりに設置する。
1. コードを書くファイル（Cococa touch）を作るときはSub classがTable Viewになっていることを確認する

#### コードを書いていく。
テーブルビューを使うには主に３つのメゾットを書く必要がある
```
override func numberOfSections(in tableView: UITableView) -> Int {
        // #warning Incomplete implementation, return the number of sections
        return テーブルビューで表示したいセクションの数
    }

    override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        // #warning Incomplete implementation, return the number of rows
        return 全体で表示するセルの数（列の数）
    }

    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath) as! ListTableViewCell
        
        let nowIndexPathDictionary = wordArray[indexPath.row]
        
        cell.englishLabel.text = 表示したい文字列
        cell.japaneseLabel.text = 表示したい文字列

        return cell
    }
```

---

### データの保存の仕方
データを保存するにはUserDeffaultsを使う。
#### 方法
1. UserDeffaultsを初期化する。
```
let saveData = UserDefaults.standard
```
1. 保存の方法
```
saveData.set(保存する変数, forKey: "鍵となるキーワード")
```
2. 呼び出しの仕方
```
wordArray = saveData.呼び出す変数の型(forKey: "鍵となるキーワード")
```

---

### アラートを出す方法
以下のコードをでアラートを出すことができる。
```
let alert = UIAlertController(title: "タイトル", message: "メッセージ", preferredStyle: .alert)
        alert.addAction(UIAlertAction(title: "アクションボタンの文字", style: .default, handler: nil))
        self.present(alert, animated: true, completion: nil)
```

___

## ２、エラー

### ビルドできずに長いエラーがでる。（単語を足すとテーブルビューが表示できなくなる）
#### 原因
カスタムセルにいらないラベルが入っている
