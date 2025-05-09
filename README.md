# YourTube 
**구독 중인 유튜브 영상들을 사용자의 기준에 따라 분류·탐색할 수 있는 크롬 확장 프로그램 + 백엔드 서비스**

<div align="center">
  <img src="docs/images/yourtube_title.png" alt="YourTube Title Logo" width="80%" />
</div>

<a href="https://yourtube.my" target="_blank">랜딩 페이지 바로가기</a>

*비용 문제로 인해 서버가 닫혀 있을 수 있음을 양해 부탁드립니다.

---

## 📌 프로젝트 소개

YouTube 사용자들은 추천 알고리즘으로 인해 자신이 원하던 목적과 다른 콘텐츠를 소비하게 되는 경우가 많습니다.  
YourTube는 사용자가 구독 중인 채널의 영상들을 **카테고리별로 분류하고**, 사용자가 직접 설정한 기준으로 **세부 필터링**할 수 있도록 도와주는 서비스입니다.  
**크롬 확장 + 백엔드 + ML 기반 분류 시스템**으로 구성된 프로젝트입니다.

---

## 🎯 문제 정의
**프로그램 실행 전**

<img src="docs/images/before.png" alt="YourTube before" width="80%" />

**프로그램 실행 후**

<img src="docs/images/after.png" alt="YourTube after" width="80%" />

<img src="docs/images/after2.png" alt="YourTube Popup" width="80%" />

**카테고리 분류 후**

<img src="docs/images/after_categorizing.png" alt="YourTube after categorizing" width="80%" />

<img src="https://github.com/user-attachments/assets/4dd33323-e8d8-462d-91d4-0cf6fa4ae9ce" width="80%" />

- 사용자가 구독 중인 채널 수가 많아질수록 영상 탐색의 효율이 떨어짐
- YouTube 기본 카테고리 분류만으로는 개인화된 탐색이 어려움
- 이를 해결하기 위한 **사용자 주도형 영상 분류 시스템**이 필요함

---

## 🧩 세부 목표

1. 유튜브 API를 통해 사용자의 구독 채널 및 최신 영상 데이터 수집
2. 영상들을 YouTube 기본 카테고리에 따라 자동 분류
3. 사용자가 직접 설정한 세부 카테고리 기준으로 추가 분류
4. 분류 결과를 확장 프로그램 UI를 통해 제공
5. 자동화 파이프라인 및 DB 연동 구성

---

## 🛠 기술 스택

| 영역 | 기술                                                                     |
|------|------------------------------------------------------------------------|
| Backend | Flask, OAuth 2.0, YouTube Data API                                     |
| Frontend | JavaScript, HTML, Chrome Extension (Manifest.json)                     |
| Modeling | BERT (Multilingual), Sentence Transformers, OpenAI GPT-4o              |
| Infra | Docker / AWS EC2, Route 53 / GCP Storage, Cloud Run, Artifact Registry |

---

## 🧭 시스템 아키텍처
<img src="docs/images/architecture.png" alt="YourTube Architecture" width="80%" />

- `YouTube Data API`: 사용자의 구독 채널 및 영상 정보 수집
- `BERT`: 기본 카테고리 분류 (Multi-label classification)
- `Sentence Transformer`: 사용자 정의 세부 카테고리 분류
- `GPT-4o`: default 카테고리(22번) 재분류 처리
- `Flask`: 프론트와의 통신, OAuth 인증, Rest API 제공
- `크롬 확장(Client)`: 영상 요청, 필터링 결과 UI 출력

---

## ⚙️ 서비스 주요 기능

- 구독 채널 영상 최신 목록 불러오기
- 카테고리 및 세부 기준으로 분류
- 유저 친화적인 UI로 영상 탐색

---

## 🛠️ 문제 해결 및 디버깅 사례

디버깅 기록 보기 👉 [docs/debugging-log.md](./docs/debugging-log.md)

---

## 👥 팀 구성 및 역할

| 이름  | 역할        | 담당 영역                                               |
|:-----:|:----------|:----------------------------------------------------|
| [김현호](https://github.com/smthswt) | 파이프라인, 리드 | 기획, 파이프라인 설계, 확장프로그램(클라이언트) 설계 및 구현, 백엔드 설계 및 구현, 모델 배포 |
| [임종혁](https://github.com/2000may24th) | 파이프라인     | 기획, 디자인, 랜딩페이지 설계, 구현 및 배포                          |
| [조윤영](https://github.com/younyoungieo) | 파이프라인     | 기획 팀장, OAuth 2.0 인증, 백엔드 설계 및 배포                       |
| [김예진](https://github.com/gina261) | 모델(ML)    | 대분류 모델 및 세부 분류 모델 개발 (BERT)                         |

---

## 💬 프로젝트 회고

- 사용자 중심의 기능 기획과 시연을 목표로 삼았으며, 실제 사용자의 피드백을 반영해 threshold 조정 등 반복적인 개선을 수행했습니다.
- 모델과 파이프라인 간 통신 문제, 인증 처리 등 실무에서도 흔히 발생하는 이슈를 해결하며 **엔드투엔드 아키텍처**에 대한 이해를 높일 수 있었습니다.

---

## 📎 부록
- [기획 발제자료](https://github.com/YBIGTA/YourTube_Service/blob/main/docs/presentations/%EB%B0%9C%EC%A0%9C_%EC%9C%A0%ED%8A%9C%EB%B8%8C%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98%20%EC%84%B8%ED%83%81%EA%B8%B0.pdf)
- [중간 발표자료](https://github.com/YBIGTA/YourTube_Service/blob/main/docs/presentations/%EC%A4%91%EA%B0%84%EB%B0%9C%ED%91%9C.pdf)
- [컨퍼런스 최종발표자료](docs/presentations/컨퍼런스_최종발표.pdf)
