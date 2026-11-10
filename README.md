# Issue 駆動開発 体験用リポジトリ（カフェ編）

3人チームで「カフェのメニューサイト」を完成させながら、**Issue 駆動開発**の流れを体験します。

使う技術: **HTML + Tailwind CSS（CDN）** だけ。インストールは不要です。
`index.html` をブラウザで開けば表示できます。

---

## Issue 駆動開発とは？

「**やることを先に Issue に書いてから、その Issue のために作業する**」進め方です。

```
① Issue を立てる → ② ブランチを切る → ③ 作業・コミット → ④ プルリクエスト → ⑤ レビュー → ⑥ マージ（Issue が閉じる）
```

- 何をやるかが Issue に残るので、チームで作業が重ならない
- 「なぜこの変更をしたのか」を、後から Issue を見れば追える

---

## 担当分け

| Issue | 内容 | 変更する場所 | 担当 |
| --- | --- | --- | --- |
| #1 | トップをお店仕様にする | `index.html` の【Issue #1 担当】 | Aさん |
| #2 | メニューを3品にする | `index.html` の【Issue #2 担当】 | Bさん |
| #3 | 店舗情報（営業時間・住所）を追加する | `index.html` の【Issue #3 担当】 | Cさん |

Issue に書く内容は `docs/issues/` にあります。

> 3人とも同じ `index.html` を編集しますが、**担当範囲が離れているので、範囲の外を触らなければコンフリクトしません**。

---

## 進め方

### 0. 準備（代表者1人がやる）
1. このリポジトリを GitHub に push する
2. Settings → Collaborators から、他の2人を招待する
3. `docs/issues/` の3つのファイルの内容をコピーして、**Issue を3つ立てる**
   （New issue → 「タスク」テンプレートを使うと楽です）
4. 各 Issue の右側の **Assignees** に担当者を設定する

### 1. 自分の環境にコピーする（全員）
```bash
git clone <リポジトリのURL>
cd <リポジトリ名>
```

### 2. Issue 用のブランチを作る
ブランチ名に **Issue 番号** を入れるのがポイントです。

```bash
git switch main
git pull origin main
git switch -c feature/1-hero        # Issue #1 の人
# git switch -c feature/2-menu   # Issue #2 の人
# git switch -c feature/3-info    # Issue #3 の人
```

### 3. 作業してコミットする
`index.html` の**自分の担当範囲だけ**を編集し、ブラウザで確認します。

```bash
git add index.html
git commit -m "お店の名前を変更 #1"
```

コミットメッセージに `#1` のように Issue 番号を入れると、
GitHub の Issue 画面にそのコミットが表示されます。

### 4. push してプルリクエスト（PR）を作る
```bash
git push -u origin feature/1-hero
```

GitHub で「Compare & pull request」を押し、本文に **`closes #1`** と書きます。
→ PR がマージされると、**Issue #1 が自動で閉じます**。

### 5. レビューしてもらう
- 他のメンバーに **Reviewers** を設定する
- レビューする人は「Files changed」で変更を見て、コメント or Approve する

### 6. マージする
Approve をもらったら「Merge pull request」を押します。
Issue が自動で Closed になったことを確認しましょう 🎉

### 7. 最新の main を取り込む
他の人のマージ後は、手元の main を最新にしておきます。

```bash
git switch main
git pull origin main
```

---

## 全部終わったら（発展）
- 自分たちで **新しい Issue を考えて立てて**、同じ流れでもう一度やってみましょう
  - 例: 「メニューにケーキセットを追加する」「店舗情報に地図へのリンクを追加する」
- わざと2人で同じ行を変えて、**コンフリクトの解消** を体験してみましょう
