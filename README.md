# genshin_dialog_generator

원신(Genshin Impact) 스타일 대화창 이미지를 만드는 웹 편집기입니다.
포토샵 없이 브라우저에서 이름·대사·선택지를 입력하고 PNG로 저장할 수 있습니다.

## 사용법

`index.html`을 브라우저에서 열면 끝. 설치·빌드·서버가 필요 없습니다.

1. **이미지 업로드** — 캔버스로 쓸 배경/캐릭터 이미지를 올립니다.
2. 이미지의 가로·세로 비율을 읽어 **대화창과 선택지가 자동 배치**됩니다.
   (832×1216 같은 세로형, 1920×1080 같은 가로형 모두 지원)
3. **이름 / 부제 / 대사 / 선택지**를 입력합니다. 선택지는 인게임처럼 화면 오른쪽 끝에 붙습니다.
4. **PNG로 저장** — 업로드한 이미지의 원본 해상도 그대로 렌더링됩니다.

## 리소스 출처

- `assets/genshin/talk/` — [PathOfGenshin/resources](https://github.com/PathOfGenshin/resources)에서
  추출한 인게임 UI 스프라이트 (자세한 내용은 해당 폴더의 README 참고)
- 배치 기준 — 실제 인게임 스크린샷 및
  [Kaerralind의 Genshin Dialogue Template](https://www.deviantart.com/kaerralind/art/Genshin-Dialogue-Template-922592432)
  (무료 사용, 크레딧 불요 명시)
- 폰트 — 원신 인게임 폰트는 상용이라 내장하지 않고, Noto Sans KR(온라인 시)로 근사합니다.

이미지 리소스의 저작권은 miHoYo/HoYoverse에 있으며, 팬 창작 목적으로만 사용됩니다.
