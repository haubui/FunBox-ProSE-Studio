# Studio — Kho skill Claude Code làm game & video

Một project gom sẵn các skill (lệnh `/...`) cho Claude Code để **làm game**, **làm video bán hàng TikTok**, **phim ngắn** và **phim hoạt hình**. Mở thư mục này bằng Claude Code là dùng được ngay các skill trong `.claude/skills/`.

## Cấu trúc

```
studio/
├── .claude/
│   ├── skills/      # 147 skill đang bật (gõ /tên-skill để dùng)
│   ├── agents/      # 49 agent của Game Studios (game-designer, qa-lead, ...)
│   ├── docs/        # tài liệu mà các skill làm game tham chiếu
│   ├── rules/       # quy tắc code theo thư mục (Game Studios)
│   ├── hooks/       # script phụ trợ (CHƯA bật tự chạy, xem ghi chú)
│   ├── scripts/
│   └── references/  # hồ sơ giọng văn cho các skill tt-*
└── sources/         # mã nguồn gốc đầy đủ của từng repo (để tham khảo / cập nhật)
    ├── SOURCES.tsv  # repo gốc + commit đã lấy
    ├── game/        # Claude-Code-Game-Studios
    ├── general/     # awesome-claude-skills (gồm cả 832 skill Composio, không bật)
    └── video/       # Remotion + các skill video
```

## Skill theo nhóm

### 🎮 Làm game (Claude Code Game Studios — 74 skill)
`/start`, `/brainstorm`, `/quick-design`, `/design-system`, `/art-bible`, `/create-architecture`, `/create-epics`, `/create-stories`, `/prototype`, `/vertical-slice`, `/dev-story`, `/story-done`, `/balance-check`, `/qa-plan`, `/smoke-check`, `/perf-profile`, `/release-checklist`, `/team-ui`, `/team-audio`, `/team-level`, … — gõ `/help` để xem hướng dẫn.

### 🛒 Video bán sản phẩm / TikTok
| Skill | Làm gì | Cần |
|---|---|---|
| `/reel-studio` | Video quảng cáo dọc (Reels/TikTok/Shorts) bằng code, phụ đề tự động | FFmpeg, Playwright, Whisper (ElevenLabs tuỳ chọn) — **miễn phí** |
| `/video-ad-generator` | Dán link sản phẩm → video quảng cáo | API Creatify (trả phí) |
| `/ugc-video-prompt` | Video kiểu review UGC qua Seedance/Kling/Veo | API key mô hình (trả phí) |
| `/product-reveal`, `/add-text` | Làm lại cảnh khoe sản phẩm theo TikTok mẫu; chèn chữ kiểu TikTok | Higgsfield (trả phí); `add-text` chỉ cần FFmpeg |
| `/tt-hook-scripter`, `/tt-caption-writer`, `/tt-trend-mapper`, `/tt-content-planner`, `/tt-humanizer`, `/tt-repurposer`, `/tt-profile-optimizer`, `/tt-audience-insights` | Kịch bản 3 giây đầu, caption, bắt trend, lịch đăng | Không cần gì (đăng bài qua Publora là tuỳ chọn) |

### 🎬 Phim ngắn / phim hoạt hình
| Skill | Làm gì | Cần |
|---|---|---|
| `/cartoon-3d-short` | Phim dọc 55–70s, nhân vật 2D trong thế giới 3D | Remotion + three.js — **miễn phí** |
| `/story-animator` | Ý tưởng 1 câu → phim hoạt hình 2D có giọng kể (truyện thiếu nhi, truyện ngủ) | Remotion, ElevenLabs |
| `/claude-animation` | Hoạt hình 2D kiểu vẽ tay / màu nước | Node 20+, FFmpeg — **miễn phí** |
| `/short-drama` + 11 skill `short-drama-*` | Phim ngắn nhiều tập: kịch bản → phân cảnh → prompt → dựng | Một số bước cần API MiniMax/OpenAI |
| `/shortfilm-prompt` | Ý tưởng → prompt điện ảnh cho Sora/Kling/Veo/Seedance | Không cần gì |
| `/ai-video` | Tạo video AI qua 6 mô hình, có kiểm tra chất lượng | Replicate / fal.ai (trả phí) |

### 🎞️ Remotion (dựng video bằng React — 13 skill)
`/remotion-best-practices` (điểm bắt đầu), `/remotion-create`, `/remotion-markup`, `/remotion-studio`, `/remotion-render`, `/remotion-captions`, … Remotion miễn phí cho cá nhân và công ty ≤ 3 người.

### 🧰 Tiện ích chung (awesome-claude-skills)
`/artifacts-builder`, `/canvas-design`, `/theme-factory`, `/image-enhancer`, `/slack-gif-creator`, `/webapp-testing`, `/skill-creator`, `/docx`, `/pdf`, `/pptx`, `/xlsx`, …

## Ghi chú
- **Hook chưa bật.** Game Studios có 15 hook tự chạy khi commit/push/ghi file. Script đã có trong `.claude/hooks/` (một số skill gọi tới), nhưng `settings.json` kích hoạt chúng **không** được chép vào. Muốn bật: copy `sources/game/Claude-Code-Game-Studios/.claude/settings.json` vào `.claude/`.
- **Workflow làm game đầy đủ** cần `CLAUDE.md` và các thư mục `design/`, `production/`, `src/` — bản gốc ở `sources/game/Claude-Code-Game-Studios/`. Nên tạo project game mới từ đó.
- **Skill Composio (832 cái)** chỉ để trong `sources/general/`, không bật vì cần tài khoản Composio và sẽ làm rối danh sách skill.
- Chưa có skill nào làm sẵn cho video tiếng Việt — cần chỉnh giọng đọc/phụ đề khi dùng.
- API key nhập qua biến môi trường, **không** commit vào repo.

## Giấy phép
Mỗi repo trong `sources/` giữ nguyên LICENSE gốc: MIT (Game Studios và các skill video), Apache-2.0 (awesome-claude-skills), CC0 (awesome-claude-video-skills); bộ skill Remotion theo điều khoản của Remotion. Danh sách repo gốc và commit: `sources/SOURCES.tsv`.
