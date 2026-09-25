# learning_pytorch
PyTorch学習用リポジトリ

## GoogleColabと連携
GitHubに置いたファイルから関数を読み取る
```bash
!wget https://raw.githubusercontent.com/ozktkj/learning_pytorch/refs/heads/main/functions.py
```
```python
import functions

functions.show_graph(plt,history,"グラフタイトル")
``

## データセットを自分で作る

### 課題
1.題材を決める。3〜5クラス、1クラス100〜300枚が現実的。自社の製品写真、書類の種別、部屋の写真など、自分が正解を判定できるものにする。
1.ImageFolder 形式のディレクトリに並べる。
1.train / val / test に分割する。先に test を切り離して、最後まで一切見ない。
1.重複画像・ラベル間違いを目視で潰す。モデルを変えるより効く。

```
data/
├── train/
│   ├── classA/  img001.jpg ...
│   ├── classB/
│   └── classC/
├── val/
└── test/          # 最後の1回だけ使う。チューニング中は絶対に見ない
```

### 1クラスの定義

1クラスをどう定義するか...

`写真から一貫して読み取れる、１つの見た目のパターン`

- 見た目で区別できるか
- クラス内で一貫しているか
- クラス間である程度離れているか
- 1枚の画像が1クラスで確実に決まるか
- 枚数を均等に集められるか
- 背景を頼らせない工夫ができるか

