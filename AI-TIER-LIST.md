# Multi-Agent: Tier List AI Gratis + Pembagian Role

> **Versi:** v1 · **Terakhir diperbarui:** 2026-10-11
> **Tujuan:** menjalankan banyak AI agent gratis secara paralel untuk bekerja, lengkap dengan role masing-masing.
> **File ini diperbarui setiap ada perubahan** (tool baru, limit berubah, role diganti). Lihat [Changelog](#changelog).

## Cara membaca

- **Tier** adalah penilaian subjektif: besar kuota gratis, kestabilan, dan kemudahan dijalankan headless/otomatis. Bukan benchmark.
- Angka limit berasal dari hasil pencarian web per tanggal di atas. **Sumbernya sering saling bertentangan** dan promo gratis sering berakhir. Cek ulang di aplikasinya sebelum bergantung pada satu angka.
- Klaim benchmark yang berasal dari vendor ditandai *(klaim vendor)*.
- Baris bertanda **(belum diverifikasi)** hanya muncul sebagai nama di daftar komparasi, tanpa data limit.

---

## 1. Agent CLI (bisa dijalankan di VPS)

| Tier | Tool | Limit gratis | Role |
|---|---|---|---|
| **S** | Gemini CLI | ~1.000 request/hari, 60/menit (akun Google). Satu prompt bisa jadi banyak request. Mayoritas model kelas Flash. Ada indikasi Antigravity CLI menggantikannya untuk tier gratis Google *(belum diverifikasi)* | Explorer dan penulis dokumentasi (konteks 1M) |
| **S** | Qwen Code | ~1.000-2.000 request/hari, 60/menit (sumber berbeda, cek ulang). Fork dari Gemini CLI | Coder utama, menjalankan test |
| **S** | OpenCode + Zen free | Model gratis berganti-ganti (DeepSeek V4 Flash, MiMo-V2.5, Nemotron 3 Ultra, Big Pickle), "untuk waktu terbatas", batas tidak jelas, ada laporan "Free usage exceeded" | Harness utama dan implementer paralel (satu `opencode serve` per worktree) |
| **A** | MiMo Code (Xiaomi) | Kanal **MiMo Auto** gratis untuk waktu terbatas (anonim, tanpa konfigurasi). Fork dari OpenCode, MIT. Login resmi butuh saldo atau Token Plan | Coder paralel gratis (konteks 1M) selagi promo jalan |
| **A** | Kimi Code CLI (Moonshot) | Tier gratis ada, batas harian terasa ketat. Membership ~$19/bln. Punya parallel subagent | Planner untuk tugas sulit saja |
| **A** | Codex CLI | Gratis untuk pengguna ChatGPT Free/Go sejak Maret 2026, sifatnya sementara | Reviewer. Jangan jadi tulang punggung |
| **A** | Kilo Code (CLI) | Model gratis bergilir (bisa antre/rate limit), kredit starter $20, atau BYOK | Debugger dan cadangan |
| **A** | Muse Code (Meta, beta) | Aplikasi gratis, **modelnya berbayar** (kredit $20 untuk akun API baru). Tier Contributor lebih murah tapi datamu dipakai Meta | Agent terminal alternatif. Jangan pakai tier Contributor untuk kode privat |
| **B** | Cline | OSS gratis, BYOK (bayar provider sendiri) | Agent kedua dengan model gratis dari router |
| **B** | Goose (Block) | Apache 2.0, BYOK | Cadangan dengan model gratis dari router |
| **B** | Crush (Charm) | BYOK | Cadangan. Kompatibel dengan router |
| **B** | Aider | BYOK, kuat di alur Git | Edit kecil dengan commit rapi |
| **B** | Freebuff | Gratis, didukung iklan, tanpa API key. Memakai model open-source (DeepSeek, Kimi, MiniMax) | Boilerplate dan edit kecil |
| **B** | Qoder | Kuota gratis terbatas (Qoder CN: trial Pro 2 minggu, 300 kredit) | Cadangan tugas kecil |
| **C** | Copilot CLI | 50 premium request/bulan | Darurat |
| **C** | Command Code | Kredit gratis $10, proprietary, model taste-1 atau Claude (BYOK) | Tugas premium sesekali |
| **C** | GLM Coding Plan (z.ai) | Berbayar | Dilewati |

**Belum diverifikasi (hanya nama):** Antigravity CLI, Auggie CLI, Blackbox AI CLI, Cursor CLI, Droid CLI, Grok Build CLI, Groq Code CLI, Jules CLI, Junie CLI, Kiro CLI, Letta Code, Neovate Code, OpenHands CLI, Poolside Agent CLI, Rovo Dev CLI, Warp Agent CLI, Trae, CodeBuddy.

---

## 2. Sumber model gratis lewat API (dipasang ke router/harness)

| Tier | Sumber | Limit gratis | Role |
|---|---|---|---|
| **A** | z.ai API: GLM-4.7-Flash, GLM-4.5-Flash | Gratis permanen, tapi **1 request bersamaan** | Reviewer ringan, pembaca log (lewat antrian) |
| **A** | z.ai API: GLM-4.6V-Flash | Gratis (vision) | Baca screenshot dan OCR (ada MCP `mcp-glm-ocr`) |
| **A** | OpenRouter `z-ai/glm-5.2:free` | ~20 req/menit, 50-1.000 req/hari (cek ulang) | Konsultan otomatis tanpa browser |
| **A** | Meta Model API (Muse Spark) | $20 kredit gratis akun baru, lalu bayar per token. `https://api.meta.ai/v1`, model `muse-spark-1.3`. Kompatibel OpenAI/Anthropic SDK. Cek ketersediaan di Indonesia | Planner/reviewer selama kredit ada |
| **B** | NVIDIA NIM free tier (lewat gateway seperti BlockRun) | Endpoint gratis ke banyak model (DeepSeek V4, Qwen3, GLM-4.7, Llama 4, Mistral) | Sumber model untuk OpenCode |
| **B** | OpenCode Zen API | Model gratis sementara, API key dari opencode.ai/auth, endpoint OpenAI-compatible | Cadangan di router |
| **B** | Gemini AI Studio API | Gratis, angka berbeda antar sumber (RPD turun sejak Des 2025) | Konteks panjang, sumber untuk router |
| **B** | MiMo API resmi | Berbayar murah (~$0,435/$0,87 per juta token untuk V2.5-Pro) | Cadangan saat kuota gratis habis |
| **C** | Mistral API | Dilaporkan ~1 req/detik dan ~1.000 call/hari *(sumber lemah, belum diverifikasi)* | Output JSON terstruktur |

---

## 3. AI chat di web/app (tanpa API, masuk lewat Git bus)

| Tier | AI | Limit gratis | Role |
|---|---|---|---|
| **S** | ChatGPT Free | Chat teks tidak dibatasi sejak Agustus 2026, file/gambar/suara tetap dibatasi | Konsultan harian dan second opinion |
| **S** | DeepSeek (chat) | Tanpa batas resmi, hanya ambang anti-bot ~500 pesan/jam | Konsultan volume tinggi: reasoning, debugging |
| **A** | Claude Free | ~15-40 pesan per jendela 5 jam | Reviewer dan penulis spec. Simpan untuk keputusan penting |
| **A** | Gemini (web) | Tier Pro berbayar sejak April 2026, Flash gratis | Pembaca dokumen/konteks panjang |
| **A** | chat.z.ai (GLM-5.2) | Gratis, tanpa API | Konsultan/arsitek via Git bus |
| **A** | Manus | 300 kredit/hari (reset 00:00 UTC), hanya model Lite, maksimal 1.500/bulan, 1 task bersamaan | Agent latar belakang: riset, slide, situs kecil |
| **A** | Meta AI app (Muse Spark, mode Thinking) | Gratis, cek ketersediaan di regionmu | Konsultan via Git bus |
| **B** | Perplexity | Pencarian cepat tak terbatas, ~3-5 Pro search/hari (sumber berbeda) | Peneliti dengan sitasi |
| **B** | Mistral Le Chat | Gratis, ada code interpreter | Cadangan dan output terstruktur |
| **B** | Xiaomi MiMo Studio (aistudio.xiaomimimo.com) | Gratis di web, tanpa API resmi | Konsultan via Git bus |
| **B** | Grok | ~10 pesan per 2 jam, model ringan | Info real-time. Prioritas rendah |
| **C** | Copilot (chat), Kimi (chat web) | **(belum diverifikasi)** | - |

---

## 4. Orkestrator, router, dan alat bantu

| Tool | Fungsi | Catatan |
|---|---|---|
| **free-coding-models** | Memantau 228 model gratis dari 24 provider, plus Smart Model Router (daemon lokal kompatibel OpenAI dengan auto-failover) | Kandidat utama untuk router |
| **workmux** (raine) | Skill `/worktree` dan `/coordinator` untuk banyak agent di worktree; mendukung OpenCode dan Claude Code | Berbasis tmux, cocok di VPS |
| **Orchestrator.inc** (agent-orchestrator) | Mengelola banyak coding agent, satu worktree per worker | Mendukung OpenCode, Aider, Copilot, Gemini CLI |
| **herd-orchestrator** (Twinber) | MCP server + command OpenCode: buat worktree, jalankan agent, kirim tugas, pantau | Perlu klien yang mendukung MCP |
| **ai-dispatch** | Orkestrator multi-CLI (Gemini, Qwen, Codex, Copilot, OpenCode, Command Code, Kilo, MiMo, Droid, dll.) | Belum diuji |
| **endy-multiplexor** | Routing subagent ke CLI gratis dengan skor prioritas dan fallback | Belum diuji |
| **claudy** | Launcher multi-provider dengan katalog template headless | Belum diuji |
| **free-claude-code** (chinfeng) | Proxy kompatibel Anthropic + bot Discord/Telegram untuk menjalankan sesi agent dari jauh | Belum diuji |
| **opencode-agentic-workflows** (ABIvan-Tech) | Orchestrator + subagent di dalam satu OpenCode | Konfigurasi siap pakai |
| **opencode-workspace** (kdcokenny) | Bundel agent + plugin worktree dan background-agents | Satu repo saja |
| **opencode-manager** (nycksw) | Kelas Python untuk mengorkestrasi server OpenCode | Terkunci ke versi lama, referensi saja |
| **OpenUsage** | Memantau kuota dan pemakaian lintas agent dalam satu dashboard | Berguna untuk menjaga kuota gratis |

---

## 5. Pembagian role (ringkas)

| Role | Tugas | Kandidat utama | Cadangan |
|---|---|---|---|
| **Planner** | Memecah tugas, desain | Kimi Code, Muse Spark | Claude Free, ChatGPT Free |
| **Explorer** | Membaca repo besar, merangkum | Gemini CLI | Gemini web, MiMo Code (1M) |
| **Coder utama** | Implementasi, menjalankan test | Qwen Code, OpenCode | MiMo Code, Kilo Code |
| **Coder paralel** | Banyak worktree sekaligus | OpenCode (satu server per worktree) | Cline, Goose, Crush |
| **Reviewer** | Memeriksa diff sebelum merge | Codex CLI, Claude Free | z.ai GLM-4.7-Flash |
| **Debugger** | Cari penyebab bug | Kilo Code, DeepSeek | Qwen Code |
| **Peneliti** | Riset dengan sitasi | Perplexity | Manus, Gemini web |
| **Vision** | Baca screenshot | GLM-4.6V-Flash | Gemini |
| **Tugas ringan** | Boilerplate, rename | Freebuff | Qoder, Aider |
| **Konsultan (Git bus)** | Jawaban teks/diff dari chat web | chat.z.ai, ChatGPT, DeepSeek | Meta AI, MiMo Studio |
| **Agent latar belakang** | Tugas sampingan harian | Manus | - |
| **Router/failover** | Pindah provider saat kena limit | free-coding-models | endy-multiplexor |

---

## 6. Desain Git bus (z.ai dan AI chat lain)

Repo terpisah `agent-bus` (bukan repo kode produk):

```
inbox/    brief dari orchestrator untuk AI chat
outbox/   jawaban dari AI chat
status/   state tiap tugas
```

**Alur:**

```
Planner -> brief ke inbox/ -> AI chat (konsultan) -> outbox/ + diff
-> coder menerapkan di worktree -> test -> reviewer -> merge
```

**Aturan:**

1. **Paket konteks:** AI chat web tidak melihat repo, jadi orchestrator menyusun file relevan jadi satu prompt (misalnya dengan repomix). Jawaban wajib berformat tetap: ringkasan lalu satu blok diff.
2. **State machine:** `needs-zai` -> `zai-replied` -> `ready-for-coder` -> `needs-review` -> `done`. Agent mengklaim tugas dengan commit file `claimed-by`.
3. **Push jawaban:** semi-manual lewat script `chat-push` (tempel jawaban, script commit dan push). Mengotomasi UI chat konsumen sering melanggar ToS dan membuat akun diblokir, jadi otomatisasi penuh hanya opsional.
4. **Pemicu:** watcher di VPS (`git fetch` tiap menit atau webhook), bukan GitHub Actions.
5. **Keamanan:** output AI chat adalah input tidak tepercaya. Selalu lewat branch/PR, terapkan hanya setelah test lulus dan reviewer setuju, jangan masukkan secret atau data pelanggan ke paket konteks, aktifkan branch protection di `main`.
6. **Batasi putaran:** maksimal 2 bolak-balik per tugas.
7. **Kuorum:** untuk keputusan penting, kirim brief yang sama ke 2-3 AI lalu biarkan agent pemutus memilih.

---

## 7. Aturan kuota

- Kuota Gemini dihitung **per user**, bukan per agent. Jangan jadikan semua agent paralel memakai satu akun.
- z.ai API gratis hanya **1 concurrency**: pasang antrian, jangan paralel.
- Pakai satu akun per layanan. Membuat banyak akun untuk menyiasati limit bisa melanggar ToS.
- Simpan role di config yang mudah diganti, karena promo gratis (Codex, model Zen, MiMo Auto) bisa hilang kapan saja.
- Jangan kirim kode privat ke tier yang melatih dari datamu (misalnya Meta Contributor Tier).

---

## Sumber

- Gemini CLI: https://jang.com.pk/en/41287-google-introduces-gemini-cli-to-developers-terminals-for-free-news , https://developers.google.com/gemini-code-assist/resources/quotas
- Qwen Code: https://www.npmjs.com/package/@qwen-code/qwen-code-core
- OpenCode Zen: https://opencode.ai/docs/zen , https://github.com/anomalyco/opencode/issues/28055
- Free AI CLI tools ranked: https://termdock.com/en/blog/free-ai-cli-tools-ranked
- Command Code: https://terminaltrove.com/compare/ai-coding-agents/codex-cli-vs-commandcode/
- Kimi Code CLI: https://kai.nguyenphivan.com/tools/kimi-code-cli
- Kilo Code / Cline: https://fast.io/resources/kilo-code-vs-cline/ , https://levelup.gitconnected.com/free-ai-coding-agents-ai-gateways-for-2026-ec7bf3ca8b17
- Freebuff / Qoder: https://github.com/codertesla/ai-coding-deals/wiki
- free-coding-models: https://raw.githubusercontent.com/vava-nessa/free-coding-models/main/README.md
- z.ai gratis: https://blogs.novita.ai/glm-free-api/ , https://pypi.org/project/mcp-glm-ocr/
- Meta Muse: https://developer.meta.com/ai/products/meta-model-api/ , https://www.orcarouter.ai/blog/meta-muse , https://www.verdent.ai/guides/agents/what-is-muse-code
- MiMo: https://github.com/Agustd123/mimo-code , https://mimo.mi.com/docs/en-US/tokenplan/integration/mimo-code , https://www.llmreference.com/agents/mimo-code
- Chat gratis: https://felloai.com/best-free-ai-chatbot/ , https://nexodatech.com/grok-free-tier-limits/
- Manus: https://www.usecarly.com/blog/manus-pricing/
- Perplexity: https://www.usecarly.com/blog/perplexity-limits/
- Orkestrator: https://workmux.raine.dev/guide/skills.md , https://github.com/OrchestratorInc/agent-orchestrator/wiki , https://glama.ai/mcp/servers/Twinber/herd-orchestrator/tree , https://pypi.org/project/endy-multiplexor/ , https://docs.rs/crate/ai-dispatch/10.18.0/source/src/types/agent.rs

---

## Changelog

- **2026-10-11 (v1):** versi awal. Menggabungkan CLI agent, sumber model API, AI chat web, orkestrator, pembagian role, desain Git bus (termasuk z.ai), dan Muse/MiMo.
