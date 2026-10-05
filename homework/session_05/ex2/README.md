# Bài 2 — Interactive Rebase (squash / reword / drop)

## Mục tiêu đã làm

- Gộp 3 commit nhỏ cuối thành **1 commit**
- Message cuối: `feat: hoan thien module authentication`
- **Drop** commit tạo `temp.txt`

## Chuẩn bị 4 commit

```bash
echo "// auth module" > auth.js
git add auth.js && git commit -m "feat: khoi tao module auth"

echo "// auth module fixed" > auth.js
git add auth.js && git commit -m "fix typo"

echo "// auth + utils" > auth.js
git add auth.js && git commit -m "adds utility functions"

echo "debug" > temp.txt
git add temp.txt && git commit -m "add temp file for debug"
```

## Interactive Rebase

```bash
git rebase -i HEAD~4
```

### Cấu hình trong editor

```text
pick  aaaaaaa feat: khoi tao module auth
squash bbbbbbb fix typo
squash ccccccc adds utility functions
drop   ddddddd add temp file for debug
```

| Commit | Lệnh |
|--------|------|
| 1 – khởi tạo auth | `pick` |
| 2 – fix typo | `squash` |
| 3 – utility | `squash` |
| 4 – temp.txt | `drop` |

Lưu file → Git mở editor message gộp → sửa thành:

```text
feat: hoan thien module authentication
```

Lưu và đóng.

## Kết quả kiểm tra

```bash
git log --oneline
```

Kỳ vọng (gần đúng):

```text
<hash> feat: hoan thien module authentication
```

Không còn `fix typo`, `adds utility functions`, `add temp file for debug`. Không còn `temp.txt` trong tree của commit đó.

## Ảnh minh chứng (dán khi nộp)

1. Màn hình `git rebase -i` (pick / squash / drop)
2. Output `git log --oneline` sau rebase

```text
# dán log sau rebase

```
