##  以下の変更をし、実行

- ボードのサイズを4から、boardSizeに変更
- tiles配列でタイルを管理する
- アニメーション状態かどうかのチェック
- 2を生成し、タイルにセットする

```swift
// GameViewController.swift

class GameViewController: UIViewController {
  @IBOutlet var boardView: UIView
  let board = Board()
  var tiles = [TileLabel]()
  var animating = false

  override func viewDidLoad() {
      super.viewDidLoad()
  }

  override func viewDidLayoutSubviews(){
      for y in 0..<board.boardSize {
          for x in 0..<board.boardSize {
              let tileSize:CGFloat = boardView.frame.size.width / CGFloat(board.boardSize)
              let tile = TileLabel(frame:CGRectMake(tileSize * CGFloat(x), tileSize * CGFloat(y), tileSize, tileSize))
              boardView.addSubview(tile)
              tiles += tile
          }
      }
      let generatedPos = board.generateNumber()
      tiles[generatedPos].setNumber(2)
  }
}
```