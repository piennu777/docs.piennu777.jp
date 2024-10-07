---
icon: webhook
description: togetnoteのAPIについてがここに書かれています。
---

# API Document

## TOKEN

APIを使用するにはユーザーに1つ与えられるTOKEN（token、トークン）を取得、発行する必要があります。\
TOKENの発行方法は機能紹介のところで紹介されているので何かわからないことがあればそこをご参照ください。

{% content-ref url="functions/token.md" %}
[token.md](functions/token.md)
{% endcontent-ref %}

***

## Limitations

togetnoteのAPIには制限があります。

|                    |             |                              |
| ------------------ | ----------- | ---------------------------- |
| Per day（86400 sec） | 50回（リクエスト数） | 同じIPアドレスで1日50回のリクエストを送信できます。 |
| Interval time      | 10秒間        | リクエストを送信してからのインターバルです。       |

この制限が利用者数や環境や状況によって変更される可能性があります。

## Error Code

ここにtogetnoteにリクエストを送信したときに帰ってくるエラーの原因などがまとめてあります。

<table><thead><tr><th width="99"></th><th></th></tr></thead><tbody><tr><td>500</td><td>何らかの理由によって、その目的を果たすことができなかった</td></tr><tr><td>429</td><td>同じIPアドレスから、許可されているリクエスト数以上のものを送信しようとした<br>またはインターバルを無視してリクエストしようとした</td></tr><tr><td>413</td><td>許可されている文字数の制限を超えた</td></tr><tr><td>401</td><td>提供されたものが正常なもの、正しいものではなかった</td></tr><tr><td>400</td><td>提供されなきゃいけないものが提供されていなかった</td></tr></tbody></table>

***

## note/create

このAPIは以下のURLを使用することで使用可能です。\
これを使用すればタイトル、内容をパラメーターから指定し、ノートを追加することができます。

```
https://tn.piennu777.jp/API/note/create/
```

#### 必須パラメーター

```
?token={token}&title={title}&note={note}
```

#### サンプル

```json
https://tn.piennu777.jp/API/note/create/?token=000000000000000000000000000000000000000000000000000000000000000000000000000000000000&title=TITLE&note=NOTE

{
    "success": true,
    "title": "TITLE",
    "note": "NOTE",
    "created_at": "2024-10-07 23:08:20",
    "note_id": "00000000000000000000000000000000"
}
```

## note/delete

このAPIは以下のURLを使用することで使用可能です。\
これを使用すれば自分のノートをIDを入力ことによって削除することができます。

```
https://tn.piennu777.jp/API/note/delete/
```

必須パラメーター

```
?token={token}&note_id={note_id}
```

サンプル

```json
https://tn.piennu777.jp/API/note/create/?token=000000000000000000000000000000000000000000000000000000000000000000000000000000000000&note_id=00000000000000000000000000000000

{
    "success": true,
    "note_id": "00000000000000000000000000000000",
    "message": "Note deleted successfully."
}
```

