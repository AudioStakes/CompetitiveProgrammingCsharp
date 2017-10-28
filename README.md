# Tips of CompetitiveProgramming for Csharp

# 頻出コード
### 基本
```csharp
int a,b,c;
  a = int.Parse(Console.ReadLine()); //標準入力
  string[] str = Console.ReadLine().Split(' ');//2つ以上のスペース区切り入力の取得
  b = int.Parse(str[0]);  //数値で受け取りたい場合は変換する
  c = int.Parse(str[1]);
  Console.Write("改行なし a = {0} b = {1} c = {2}", a, b, c)//改行なし出力"
  Console.WriteLine("改行あり a = {0} b = {1} c = {2}", a, b, c);//改行付き出力"
```

### 標準入力された値が数値か判別
```csharp
line = Console.ReadLine();
int j;
if (Int32.TryParse(line, out j))
    Console.WriteLine(j);
else
    Console.WriteLine(line);
```

### 二次元配列を動的に生成
```csharp
int[,] sName1 = new int[3, 2];
sName1[0, 0] = 1;
sName1[0, 1] = 2;
sName1[1, 0] = 3;
sName1[1, 1] = 4;
sName1[2, 0] = 5;
sName1[2, 1] = 6;
Console.WriteLine(sName1[0,0]);
Console.Out.Flush();
Console.ReadKey();
```

# LINQ
### しておくこと
```csharp
using System.Linq;
var empty = new int[] {};
var a1533 = new int[] { 1, 5, 3, 3 };
```

### 最大値
```csharp
a1533.Max(); // → 5
empty.Max(); // → InvalidOperationException
empty.DefaultIfEmpty(-1).Max(); // → -1 (空の場合は -1 を返す)
```

### 最小値
```csharp
a1533.Min(); // → 1
empty.Min(); // → InvalidOperationException
empty.DefaultIfEmpty(-1).Min(); // → -1 (空の場合は -1 を返す)
```

### 合計値  
```csharp
a1533.Sum(); // → 12
empty.Sum(); // → 0
```

### 平均
```csharp
a1533.Average(); // → 3.0
empty.Average(); // → InvalidOperationException
empty.DefaultIfEmpty(-1).Average(); // → -1 (空の場合は -1 を返す)
```

### 逆順    
```csharp
a1533.Reverse().ToArray(); // → { 3, 3, 5, 1 }
```

### フィルタ
```csharp
a1533.Where(s => s < 4).ToArray(); → // { 1, 3, 3 }
```

### 写像(map)
```csharp
a1533.Select(s => s * 2).ToArray(); // → { 2, 10, 6, 6 }
```

### 写像&平坦化 (concatMap)
```csharp
a1533.SelectMany(s => new[] { s, s }).ToArray(); // → { 1, 1, 5, 5, 3, 3, 3, 3 }
```

### マージ
```csharp
a1533.Zip(new int[] { 1, 2, 1, 2 }, (a, b) => a + b).ToArray(); // { 2, 7, 4, 5}
```

### 重複削除
```csharp
a1533.Distinct().ToArray(); // → { 1, 5, 3 }
```

### 最初の要素
```csharp
a1533.First(); // → 1
empty.First(); // → InvalidOperationException
empty.FirstOrDefault(); // → 0 （空の場合は例外を投げるのではなくその型の初期値を返す）
```

### 最後の要素
```csharp
a1533.Last(); // → 3
empty.Last(); // → InvalidOperationException
empty.LastOrDefault(); // → 0 （空の場合は例外を投げるのではなくその型の初期値を返す）
```

### 最初の要素（長さが１でない場合は例外を投げる）
```csharp
a1533.Single(); // → InvalidOperationException
empty.Single(); // → InvalidOperationException
a1533.SingleOrDefault(); // → InvalidOperationException
empty.SingleOrDefault(); // → 0 （空の場合は例外を投げるのではなくその型の初期値を返す）
```

### X 番目の要素
```csharp
a1533.ElementAt(1);           // 5
a1533.ElementAt(99);          // → ArgumentOutOfRangeException
a1533.ElementAtOrDefault(99); // → 0（範囲外の場合は例外を投げるのではなくその型の初期値を返す）
```

### 先頭から要素を取得
```csharp
a1533.Take(1).ToArray(); // → { 1 }
```

### 先頭から要素をスキップ
```csharp
a1533.Skip(1).ToArray(); // → { 5, 3, 3 }
```

### 先頭から条件を満たす要素を取得
```csharp
a1533.TakeWhile(s => s == 1).ToArray(); // → { 1 }
```

### 先頭から条件を満たす要素をスキップ
```csharp
a1533.SkipWhile(s => s == 1).ToArray(); // → { 5, 3, 3 }
```

### 安定ソート
```csharp
a1533.OrderBy(s => s).ToArray();           // → { 1, 3, 3, 5}
a1533.OrderByDescending(s => s).ToArray(); // → { 5, 3, 3, 1}
```

### 要素が全て条件を満たしているかを判定
```csharp
a1533.All(s => s % 2 == 1); // → true
```

### 条件を満たす要素が存在するかを判定
```csharp
a1533.Any(s => s % 2 == 0); // → false
```

### 条件を満たす要素の個数
```csharp
a1533.Where(s => s == 3).Count(); // → 2
a1533.Count(s => s == 3);         // → 2
```

### 配列が空ではないかを判定
```csharp
a1533.Any(); // → true
empty.Any(); // → false
```
### 配列の重複&重複じゃない数を出力
```csharp
var sample_list = new string[] { sample[0], sample[1], sample[2], sample[3] };
            List<string> duplicates =
               sample_list.GroupBy(x => x)
               .Where(g => g.Count() > 1)
               .Select(g => g.FirstOrDefault()).ToList();
            List<string> notDuplicates =
                sample_list.Distinct().ToList();

            foreach (var duplicate in duplicates)
            {
                Console.WriteLine(duplicate);
            }
            foreach (var notDuplicate in notDuplicates)
            {
                Console.WriteLine(notDuplicate);
            }
```

# ショートカット　（Mac?)
### 参考
- https://qiita.com/kengop/items/ac9b57404d30e0cfdd20
- http://useless.hatenablog.com/entry/2016/07/25/190000
- http://beachside.hatenablog.com/entry/2015/12/09/000000
- https://msdn.microsoft.com/ja-jp/library/da5kh0wa.aspx

### コードスニペット
- スニペットの挿入
  - Ctrl + K , Ctrl + X
- ブロックの挿入
  - Ctrl + K , Ctrl + S

### 対象のソースコードをメソッドとして切り出す
- Crtl+R → Ctrl+M

### ドキュメント全体をフォーマット（整形）
- Ctrl + K, Ctrl + D
- インデントがモコモコになったときに

### 選択範囲をフォーマット（整形）
- Ctrl + K, Ctrl + F

### コメントアウト
- Ctrl + K, Ctrl + C
- コメントアウトの「C」

### コメントアウトを解除
- Ctrl + K, Ctrl + U
- アンコメントの「U」

### NavigateBackward
- Ctrl + -（マイナス）
- カーソルを当てたところを記憶していて、戻る機能
- ファイルをまたがっても戻れる

### ファイルのタブを切り替え
- Ctrl + Tab

### 全ファイルにまたがってキーワード検索
- Ctrl+Shift+F

### 開いているファイル内をキーワード検索
- Ctrl+F

### 次の単語へ移動
- Ctrl + →

### 選択範囲の特定の単語を置換
- Ctrl+F
- 検索画面に単語を入力
- "∨"をクリックし、置換画面を表示
- 置換後の単語を入力し、Enter

# VisualStudio操作方法
### クラスのアセンブリの追加方法
1. 「追加したいクラス名　+ MSDN」で検索
2. どのアセンブリに属しているか調べる
3. visualstudioのソリューションエクスプローラーの参照フォルダを右クリック
4. 参照の追加を選択
5. 参照マネージャーダイアログの左側ペイで、アセンブリ-フレームワークを選択
6. 一覧から調べたアセンブリ名を選択し、OKをクリック

### 値型にnullを設定する方法
```csharp
int? num = null;
if (num.HasValue){
Console.WrireLine("num = {0}", num.Value);
} else {
  Console.WriteLine("num = null");
}
```
