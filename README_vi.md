# Workout Player — 30 phút (DB + Thảm)

Web app giúp tập tại nhà với **video hướng dẫn + đồng hồ đếm + tự chuyển bài**. Có **ứng dụng React (Vite + TypeScript + Tailwind)** và **bản HTML chạy ngay** để upload thẳng lên GitHub Pages/Netlify.

## Tính năng
- ⏱️ Đếm ngược cho từng bài, tự chuyển **Work → Rest → Next**.
- ▶️ Nhúng video YouTube/mp4 cho mỗi bài.
- 🔔 (React) Beep 3–2–1 trước khi hết set.
- 💾 (React) Import/Export JSON bài tập, lưu `localStorage`.
- 🗓️ (HTML) **Auto Schedule** theo thứ trong tuần (Mon→A, Tue→B, Wed→REST, Thu→A, Fri→B, Sat→C, Sun→REST).
- ⌨️ Phím tắt: `Space` (Pause/Resume), `←/→` (Prev/Next), `R` (Reset).

## Thư mục & tệp chính
```
standalone/
  ├─ workout_player_standalone_v2.html          # 1 buổi mặc định
  ├─ workout_player_30min_multiplan_v2.html     # chọn A/B/C
  └─ workout_player_auto_schedule_v2.html       # tự chọn theo thứ + màn hình REST
src/
  App.tsx, main.tsx, components/, reducer/, hooks/, data/, utils/
```
> Các bản HTML demo dùng Tailwind CDN + Babel cho thử nhanh. Với production nên dùng bản React đã build.

## Dùng nhanh (HTML)
- Mở trực tiếp 1 trong các file trong `standalone/` **(double‑click)**, hoặc
- Serve tĩnh:
  ```bash
  python -m http.server 8080
  # hoặc
  npx serve -p 8080 .
  ```

## Cài đặt & chạy (React + Vite)
```bash
npm install
npm run dev            # http://localhost:5173
npm run build && npm run preview
npm run test
```
Phụ thuộc chính: `react`, `vite`, `tailwindcss`, `framer-motion`, `lucide-react`, `vitest`, `@testing-library/react`.

## Tuỳ chỉnh nhanh
- Chỉnh bài mặc định tại `src/data/defaultWorkout.ts` (mỗi bài: `title`, `durationSec`, `restSec?`, `videoUrl?`, `tips?`).
- (HTML Auto) Sửa lịch trong `DAY_PLAN` nếu muốn đổi ngày REST.
- Nguồn video đã thay ổn định hơn cho: Goblet Squat, DB Floor Press, DB RDL, Dead Bug, Cooldown/Mobility.

## Deploy
- **React**: Vercel/Netlify (Build: `npm run build`, Output: `dist/`). GitHub Pages cần cấu hình `base` trong `vite.config.ts` nếu deploy dưới subpath.
- **HTML demo**: upload nguyên file `.html` trong `standalone/` lên Pages/Netlify/S3 là xong.

## Giấy phép
**MIT** — tự do sử dụng & tuỳ biến. Vui lòng ghi nguồn video khi cần.
