# toCatter — AI 멀티모달 10초 광고 제작

## 프로젝트 개요

가상 브랜드 **toCatter**(고양이용 캣닙 음료)의 10초 광고를, 모든 시각·청각 소스를 생성형 AI로 제작한 프로젝트입니다.
"기획 → 이미지 생성 → 이미지 편집/합성 → 영상 변환 → 오디오 생성 → 통합 편집"의 파이프라인을 직접 설계하고, 각 단계에서 도구를 선택한 근거와 실패·수정 과정을 기록했습니다.

| 구분 | 내용 |
|---|---|
| 브랜드 | toCatter — cat together |
| 제품 | 고양이 캣닙 음료 (240ml 캔) |
| 핵심 메시지 | "고양이도 가족이니까" |
| 구조 | 일상(공유) → 문제(소외) → 해결(참여) → 브랜드 |
| 가치 | 고양이용 음료를 함께하는 시간을 공유함으로서 가족으로 더 가깝게 느낄수 있음 |
| 길이 | 10초 / 4씬 |
| 사용 도구 | Claude · Midjourney · Gemini · Kling · ElevenLabs · Suno · CapCut |

---

## 제출물

| 산출물 | 내용 | 바로가기 |
|---|---|---|
| `story_board.md` | 브랜드 아이덴티티 · 사용 도구 목록 · 에셋 · 씬별 스토리보드 · 프롬프트 원문 · 수정 전/후 기록 · 효과음 · 보너스 | [story_board.md](./story_board.md) |
| `toCatter.mp4` | 최종 광고 영상 (10초 / 1080p / H.264 / AAC) | [toCatter.mp4](./toCatter.mp4) |
| `toCatter.AAC` | 최종 영상의 오디오 트랙 | [toCatter.AAC](./toCatter.AAC) |

---

## 디렉터리 구조

| 폴더 | 내용 |
|---|---|
| [`asset_img/`](./asset_img) | 씬에 걸쳐 재사용되는 고정 에셋 (고양이 · 가족 · 로고 · 제품) |
| [`asset_bgm/`](./asset_bgm) | 배경음악 |
| [`scene_img/`](./scene_img) | 씬별 생성·편집 이미지 (영상 입력 프레임) |
| [`scene_vid/`](./scene_vid) | 씬별 생성 영상 |
| [`scene_nar/`](./scene_nar) | 나레이션 · 대사 |
| [`scene_snd/`](./scene_snd) | 효과음 |
| [`scene_frame/`](./scene_frame) | 영상에서 추출한 연결용 프레임 |
| [`scene_extract/`](./scene_extract) | 영상에서 추출·가공한 음성 소스 |
| [`screenshot/`](./screenshot) | 편집 지시용 참조 캡처 |

### 파일명 규칙

```
asset(또는 scene)_종류_설명_원본시도번호_수정번호
```

- `asset_` : 여러 씬에 걸쳐 재사용되는 고정 소스
- `scene_` : 특정 씬 전용 소스
- 원본시도번호 = 새로 생성한 횟수, 수정번호 = 그 결과를 편집한 횟수
- 프레임·스크린샷·추출 파일은 시도/수정 번호를 갖지 않음

→ 상세: [결과 파일명 기준](./story_board.md#결과-파일명-기준)

---

## 평가 항목 대응

### 항목 1 — 기능 동작 검증

| 평가 항목 | 대응 문서 | 해당 절 |
|---|---|---|
| 브랜드 아이덴티티(타겟/톤앤매너/USP)와 핵심 메시지 정의 | story_board.md | [브랜드 아이덴티티](./story_board.md#브랜드-아이덴티티) |
| 씬별 구성 및 필수 필드 포함 | story_board.md | [스토리보드](./story_board.md#스토리보드-총-10초--4컷) |
| 최소 1개 씬 프롬프트 수정 전/후 + 수정 이유 | story_board.md | [씬 1 수정프롬프트 이미지](./story_board.md#수정프롬프트) · [씬 2 수정프롬프트 영상](./story_board.md#수정프롬프트-1) |
| 이미지 생성 도구 1종 이상 | story_board.md | [사용 도구 목록](./story_board.md#사용-도구-목록) · [에셋](./story_board.md#에셋) |
| 비디오 생성(변환) 도구 1종 이상 | story_board.md | [씬 1 비디오 프롬프트](./story_board.md#프롬프트1) |
| 오디오 생성 도구 1종 이상 | story_board.md | [bgm](./story_board.md#bgm) · [효과음](./story_board.md#효과음) |
| 최종 영상 10초 이내 | toCatter.mp4 | [영상 스펙](./story_board.md##최종-영상-파일-정보) |
| AI 생성 시각 요소 + 청각 요소 포함 | story_board.md | [스토리보드](./story_board.md#스토리보드-총-10초--4컷) |
| 직접 촬영/유료 스톡 미사용 | README | [제약 사항 준수](#제약-사항-준수) |
| 마지막 3~5초 브랜드 인지 장치 | story_board.md | [씬 3](./story_board.md#씬-3-전환--해결제안--따라준다) · [씬 4](./story_board.md#씬-4-브랜드-로고) |
| 보너스 1 — 립싱크 | 씬 2 고양이 대사 "나는?"을 Kling Native Audio로 립싱크 생성 → 음성 추출 → ElevenLabs Voice Change로 캐릭터 보이스 교체 | [Bonus — 더빙](./story_board.md#더빙) |

---

## 파라미터 표준

| 대상 | 고정값 | 목적 |
|---|---|---|
| 씬 이미지 비율 | `--ar 16:9` | 최종 영상 비율과 일치시켜 크롭 손실 방지 |
| 렌더 스타일 | `--raw` | Midjourney 자동 미화를 억제하고 실사 광고 톤 유지 |
| 스타일 강도 | `--stylize 120~130` | 미적 재해석보다 프롬프트 충실도 우선 |
| 변형 | `--weird 0` | 상업 광고에 부적합한 변형 배제 |
| 캐릭터 일관성 | `--ow 400` | Omni Reference 강도 상향으로 인물 동일성 확보 |
| 영상 해상도 | Kling 1080p | 전 클립 동일 해상도로 통일 |
| 영상 오디오 | Native Audio off (립싱크 씬만 on) | 크레딧 절약 + 오디오는 전용 도구로 제작 |

## 제약 사항 준수

| 제약 항목 | 준수 내용 |
|---|---|
| 직접 촬영 영상 미사용 | 모든 시각 소스는 Midjourney / Gemini 생성물 |
| 유료 스톡 소스 미사용 | 사용하지 않음. 효과음·BGM 포함 전부 AI 생성 |
| 청각 소스 AI 생성 | 나레이션·대사·효과음 = ElevenLabs / BGM = Suno |
| 실존 상표 미사용 | 씬 1에서 생성된 콜라 상표를 Gemini 편집으로 무지 캔으로 대체 |
| 실존 인물·딥페이크 미사용 | 등장 인물은 전원 생성 이미지 |
| 편집 도구 사용 범위 | CapCut을 컷 편집·불필요 구간 음소거·오디오 레벨 조정에만 사용. 새로운 시각 요소 추가 없음 |
| 캐릭터 일관성 기능 활용 | Omni Reference 강도 상향으로 인물 동일성 확보 [씬 1 수정프롬프트](./story_board.md#수정프롬프트)에서 이유 설명 |
| 최종 스펙 | 1080p / 30fps / H.264 / AAC / 10초 |

---

## 개념 정리

| 개념 | 설명 |
|---|---|
| T2I (Text to Image) | 텍스트로 이미지를 생성 |
| I2V (Image to Video) | 확정된 이미지에 모션을 부여해 영상으로 변환 |
| oref / `--ow` | Omni Reference. 특정 인물·사물의 동일성을 유지하는 참조와 그 강도 |
| sref / `--sw` | Style Reference. 색감·조명·질감만 참조 |
| Start / End Frame | I2V에서 시작·종료 시점의 화면을 지정해 카메라 움직임을 통제 |
| Voice Design | 텍스트 서술로 목소리 자체를 설계 |
| Voice Change (STS) | 원본 억양·타이밍을 유지한 채 목소리만 교체 |
