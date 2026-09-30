
Учебный проект: GUI-приложение на **Go** с библиотекой **Fyne**, автоматически собирается под **Linux, macOS, Windows** через **GitHub Actions** и публикуется в **GitHub Releases** при push тега `v*`.

---

## 📸 Скриншоты

### 1. Работающее приложение

<img width="1914" height="909" alt="Снимок экрана 2026-09-30 132002" src="https://github.com/user-attachments/assets/db34971a-95fc-4f16-922f-e8b1805ef3ca" />



*Окно Hello GUI v0.1.0 — кнопки «Поздороваться» и «Выход», версия подтянулась из git-тега, сумма 1..10 = 55*

### 2. GitHub Actions — CI/CD успешно прошёл

<img width="1772" height="744" alt="Снимок экрана 2026-09-30 131820" src="https://github.com/user-attachments/assets/28def913-5608-4dab-96f9-703646400bd0" />


### 3. GitHub Release v0.1.0 — 3 бинарника

<img width="1482" height="939" alt="Снимок экрана 2026-09-30 131828" src="https://github.com/user-attachments/assets/b84f5062-b8a1-4e61-83e6-470f648f5e32" />


*Автоматически создан релиз с артефактами под Linux, macOS и Windows*

---

## ⬇️ Скачать

Бинарники в [Releases](https://github.com/Evgeny65ok/hello-gui/releases):

- 🐧 **Linux x64** — `hello-gui-linux-x64`
- 🍎 **macOS ARM** — `hello-gui-macos-arm64`
- 🪟 **Windows x64** — `hello-gui-windows-x64.exe`

---

## 🛠 Сборка

Нужен **Go 1.23+** и **GCC** (для CGO — Fyne использует GLFW на C).

```bash
git clone https://github.com/Evgeny65ok/hello-gui.git
cd hello-gui
go mod tidy
go test ./... -v
go build -o hello-gui .
./hello-gui
```

---

## 🔁 CI/CD

Файл: [`.github/workflows/ci.yml`](.github/workflows/ci.yml)

- **Push в `main`** → job `test` (gofmt, vet, тесты, сборка)
- **Push тега `v*`** → job `test` + job `release` (3 бинарника параллельно)
- **Pull request** → job `test`

Почему **3 runner'а**, а не cross-compilation: Fyne использует **CGO**, нужен **нативный GCC** под каждую ОС.

---

## 📂 Структура

```
hello-gui/
├── .github/workflows/ci.yml
├── Dockerfile.test
├── logic.go
├── logic_test.go
├── main.go
├── go.mod
├── go.sum
└── README.md
```

---

## 👤 Автор

**Evgeny65ok** — [@Evgeny65ok](https://github.com/Evgeny65ok)

🔗 [Репозиторий](https://github.com/Evgeny65ok/hello-gui) · 🚀 [Релизы](https://github.com/Evgeny65ok/hello-gui/releases) · ⚙️ [Actions](https://github.com/Evgeny65ok/hello-gui/actions)
