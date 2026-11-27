# 🏢 피클 합동 비서실 (Pickle Joint Office)

피클들이 함께 쓰는 픽셀 오피스. 방 4개에 각자의 피클이 머물고, 방마다 할 일·메모·안건 보드가 따로 있어요.

- 📦 **납품·사업방** — 판매용품, 무역·발주·납품, 쿠팡·스마트스토어
- ✈️ **여행·블로그방** — 여행 기록, 블로그 초안
- ✍️ **리뷰·이벤트방** — 리뷰, 체험단, 설문·퀴즈 응모
- 💳 **구독 관리방** — 구독 점검·해지 체크
- 🛋️ 가운데 **라운지** — 모두가 모이는 대화 공간

## 쓰는 법

| 하고 싶은 것 | 방법 |
| --- | --- |
| 캐릭터 움직이기 | 방향키 / WASD / 클릭·터치한 곳으로 이동, `1`~`4`로 방 순간이동 |
| 말 걸기 | 캐릭터 클릭 → 아래 입력창, 또는 오른쪽 채팅 |
| 그 방 보드 보기 | 방에 들어가면 자동으로 열림 · 방 이름표나 보드 위 칩을 눌러도 됨 |
| 다른 피클 부르기 | 상단 👥 → 이름·자음(ㄱ~ㅎ)·색·역할 고르고 입장, 또는 초대 링크 복사 |
| 내 피클 꾸미기 | ⚙️ → 내 피클 (이름·자음·색·역할) |
| AI 회의 시키기 | ⚙️ → AI 회의에 **Gemini API 키**(무료)를 넣고 ‘방에 부르기’ → 채팅에서 **🤖 AI 회의** 를 누르거나 채팅을 보내면 💎 제미나이가 답하고, **OpenAI 키**가 있으면 🤖 챗GPT가 이어서 답합니다 |

## AI 회의 (제미나이 · 챗GPT)

- 💎 **제미나이**는 Google AI Studio에서 발급한 **무료 등급** Gemini API 키로 동작합니다 (`aistudio.google.com/apikey`).
- 🤖 **챗GPT**는 OpenAI API 키(`gpt-4o-mini`)를 넣으면 제미나이 발언을 이어받아 다른 각도로 답합니다.
- 키는 **이 브라우저의 localStorage에만** 저장됩니다. `index.html`·GitHub에는 절대 올라가지 않습니다. 폰·PC 각각 ⚙️에서 한 번씩 넣어주세요.
- 모델은 무료로 열려 있는 flash 계열을 앞에서부터 시도하고(3.8 → 3.7 → flash-latest → 3.5 → 3.5-lite), 되는 모델을 기억합니다. AI Studio에서 2.5-flash는 신규 사용자에게 더 이상 제공되지 않습니다.

## 저장·동기화

1. **로컬 저장** — 기본. 이 브라우저에 저장되고, 같은 브라우저의 여러 탭은 자동으로 맞춰집니다.
2. **공유 링크** — `🔗` 를 누르면 지금 방 상태(피클·보드·대화)가 링크에 담겨 복사됩니다.
3. **실시간 동기화(무료 Firebase)** — 이미 켜져 있어요. 기본 주소는 `https://pickle-office-e1151-default-rtdb.asia-southeast1.firebasedatabase.app` (Firebase 프로젝트 `pickle-office-e1151`, Spark 무료 요금제, 싱가포르 리전)이고, 주소를 따로 넣지 않아도 접속하면 자동으로 연결됩니다. ⚙️ 설정에서 다른 주소를 넣으면 그 주소가 우선하고, ‘해제’를 누르면 로컬 저장만 씁니다.
   - 직접 새로 만들려면: console.firebase.google.com → Realtime Database 만들기 → 규칙을 아래로 바꾸고 게시 → 데이터 탭의 `https://…-default-rtdb.firebaseio.com` 주소를 붙여넣기

```json
{
  "rules": {
    "pickleOffice": {
      ".read": true,
      ".write": true
    }
  }
}
```

서버가 끊기거나 주소가 틀려도 화면과 입력은 멈추지 않고 로컬 저장으로 계속 동작합니다.

## 구조

정적 파일 하나(`index.html`)로 동작합니다. 빌드 없음, 의존성 없음.

## 배포

- 사이트: **https://keh4544.github.io/Pickle-office/**
- GitHub Pages가 `gh-pages` 브랜치(루트)를 바라보고 있습니다. 수정한 뒤 배포하려면:

```bash
git add -A && git commit -m "update" && git push origin main
git push origin main:gh-pages
```

- 저장소 Settings → Pages → Source를 `main` / `(root)`로 바꾸면 main에 push만 해도 자동 배포됩니다.
