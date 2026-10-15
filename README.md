# Hana's Sandwich Truck

하나의 샌드위치 트럭 — 영어로 들어오는 주문을 읽고 버거·샌드위치를 만들어 파는 타이쿤 게임. 미국 2·3학년 수학·과학·영어 문제, 배달, 트럭 꾸미기, 부모님 리포트.

## 바로 해 보기

- **파일로 열기:** `www/index.html` 을 브라우저로 엽니다.
- **Linux Mint에 설치:** 이 폴더에서 실행하면 메뉴 > 게임에 아이콘이 생깁니다.

  ```bash
  sudo apt install chromium   # 주소창 없는 앱 창으로 열기 (선택)
  bash install-linux.sh       # 지울 때: bash uninstall-linux.sh
  ```

- **휴대폰에서 같은 와이파이로 테스트:** `python3 -m http.server 8000 -d www` 후 휴대폰에서 `http://<PC IP>:8000`

## GitHub에 올리기 (Linux Mint)

```bash
sudo apt install git gh
gh auth login -s workflow
cd hanas-sandwich-truck
git init -b main && git add . && git commit -m "Hana's Sandwich Truck 첫 버전"
gh repo create hanas-sandwich-truck --public --source=. --push
```

push 하면 자동으로 두 가지가 실행됩니다 (저장소 > Actions 탭에서 확인).

| 작업 | 결과 |
| --- | --- |
| 게임 공개 (`pages.yml`) | `https://<아이디>.github.io/hanas-sandwich-truck/` — 처음 한 번은 Settings > Pages > Source 를 **GitHub Actions** 로 바꾸고 Re-run |
| 안드로이드 테스트 앱 (`android-apk.yml`) | `https://github.com/<아이디>/hanas-sandwich-truck/releases/download/test-build/hanas-sandwich-truck.apk` |

## 앱으로 만들기 (Capacitor 8)

필요: Node.js 22+, Android Studio (안드로이드), Mac + Xcode (iOS)

```bash
npm install
npm run android:add     # android 폴더 생성
npm run sync            # 게임을 고칠 때마다
npm run android:open    # Android Studio에서 실행·서명·AAB 만들기
npm run ios:add && npm run ios:open   # Mac에서만
```

출시 전에 `capacitor.config.json` 의 `appId` 를 내 것으로 바꾸세요 (예: `com.eunsang.hanassandwichtruck`). 한 번 출시하면 바꿀 수 없어요.
게임 파일을 고친 뒤에는 `www/sw.js` 의 `VERSION` 을 올려야 설치한 사람에게 새 버전이 전달됩니다.
