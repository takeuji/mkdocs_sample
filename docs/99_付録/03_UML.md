---
title: シーケンス図の記載例
---

<div class="mermaid">
sequenceDiagram
  # エイリアス
  participant cl as クライアント
  participant top as index.html
  participant bt as &lt;content-button&gt;
  participant ah as &lt;auth-dialog&gt;
  participant sw as &lt;swiper&gt;
　cl->>+top : リクエスト
  top-->>top : リファラー判別、qrcode=のパラメータがあるか？
  top-->>top : 初期処理(jsonロード)
  top->>-cl : レスポンス
  cl->>top : ロックボタンクリック
  activate top
  top->>bt : ボタンクリック
  bt-->>bt : クリックされたボタンインスタンス自身をauth-dialogに渡す
  bt-->>top : クリックイベント発火
  top->>+ah : ダイアログを表示
  ah-->>ah : 位置情報/カメラ情報取得
  ah-->>top : 検出イベント発火
  top-->>bt : 認証の移譲
  bt-->>top : 認証結果の返却
  top-->>ah : 結果表示
  Note right of top: ↑認証がOKなら
  ah-->>sw : swiper表示
  sw-->>sw : index.htmlのslot表示
  top->>cl : ダイアログを表示
  top-->>top : ロック解除されたボタンをLocalStrageに保存
  top-->>top : コンプリートしたか判別
　 deactivate top 
</div>