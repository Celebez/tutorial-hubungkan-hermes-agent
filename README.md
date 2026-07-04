# Tutorial: Hubungkan Hermes Agent ke Telegram & Discord

Panduan lengkap setup **Hermes Agent** — agent AI dari Nous Research — agar bisa komunikasi lewat **Telegram** dan **Discord**.

---

## 📦 Prasyarat

- VPS/Server Linux (Ubuntu recommended)
- Python 3.10+
- Token bot Telegram dan Discord

---

## 1️⃣ Setup Hermes Agent

```bash
# Clone repo
git clone https://github.com/nousresearch/hermes-agent.git
cd hermes-agent

# Install
pip install -r requirements.txt
```

---

## 2️⃣ Koneksi Telegram

### Buat Bot Telegram

1. Buka [@BotFather](https://t.me/BotFather) di Telegram
2. Kirim `/newbot` → ikuti instruksi
3. Simpan **token bot** (`123456:ABC-DEF1234ghIkl`)

### Tambah ke Hermes

```bash
# edit config.yaml
hermes config set telegram.token "BOT_TOKEN_ANDA"
hermes config set telegram.chat_id "CHAT_ID_ANDA"
```

### Test

```bash
hermes send "Halo! Ini test dari Hermes Agent" --to telegram
```

---

## 3️⃣ Koneksi Discord

### Buat Bot Discord

1. Buka [Discord Developer Portal](https://discord.com/developers/applications)
2. **New Application** → beri nama
3. Tab **Bot** → **Add Bot**
4. Copy token
5. Invite bot ke server via OAuth2 URL (`bot` + `Send Messages`)

### Tambah ke Hermes

```bash
hermes config set discord.token "DISCORD_BOT_TOKEN"
hermes config set discord.channel_id "CHANNEL_ID_ANDA"
```

### Test

```bash
hermes send "Test dari Hermes Agent!" --to discord
```

---

## 4️⃣ Automation dengan Cron Job

```bash
hermes cron create "daily-summary" --schedule "0 9 * * *" --deliver telegram
hermes cron create "market-report" --schedule "*/30 * * * *" --deliver discord
```

---

## 🛠 Troubleshooting

| Masalah | Solusi |
|---------|--------|
| Bot tidak response | Cek token |
| 403 Forbidden | Invite bot ke channel |
| Connection timeout | Firewall: buka port |

---

## 📜 License

MIT — by **@Celebez**

---

## 📬 Kontak

- Telegram: [@0xCelebez](https://t.me/0xCelebez)
- X: [@0xCelebez](https://x.com/0xCelebez)