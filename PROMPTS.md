# PROMPTS.md

## 과제 정보
- 과제: AI Coding Tools를 이용한 논문 실험 파트 구현
- 대상 논문: *A deep context learning based PCB defect detection model with anomalous trend alarming system*
- 공개 코드 저장소: `JiaLim98/YOLO-PCB`
- 구현 파일: `YOLO_PCB_submission_colab.ipynb`
- 사용 AI Coding Tool: ChatGPT

## 기록 작성 기준
아래 내용은 PCB 결함 검출 추론 재현 코드를 구성하고 제출 자료를 정리하기 위해 입력한 요청을 제출 형식에 맞추어 정리한 것이다.  
교수님께서 대화 원문 자체를 요구하시는 경우에는 실제 대화창에서 사용한 원문 프롬프트와 응답 화면을 추가로 첨부한다.

---

## Prompt 1. 논문 실험 재현용 코드 요청
```text
논문 "A deep context learning based PCB defect detection model with anomalous trend alarming system"의 공개 GitHub 저장소 JiaLim98/YOLO-PCB를 바탕으로, Google Colab에서 바로 실행할 수 있는 아주 간단한 실험 코드를 작성해줘. 공개된 pretrained weight를 이용하여 sample PCB 이미지에 대해 defect detection inference를 실행하고, 결과 이미지를 확인할 수 있게 해줘.
```

### 목적
논문 저자가 공개한 모델과 사전학습 가중치를 이용하여 PCB 결함 검출 추론 과정을 재현하기 위함.

---

## Prompt 2. 제출용 노트북 구조화 요청
```text
제출용으로 사용하기 쉽게 코드를 단계별 셀로 정리해줘. GPU 확인, GitHub 저장소 clone 및 패키지 설치, 모델 실행, 결과 이미지 확인, 예측 label txt 확인 및 해석 단계가 포함되도록 작성해줘.
```

### 목적
Colab에서 위에서부터 순차적으로 실행할 수 있고, 보고서의 구현 매뉴얼과 대응되는 형태로 정리하기 위함.

---

## Prompt 3. Colab 호환성 오류 해결 요청
```text
Colab에서 YOLO-PCB 코드를 실행할 때 PyTorch 또는 Python 버전 문제로 오류가 발생할 수 있으니, torch.load 관련 오류와 check_requirements 관련 오류를 해결할 수 있도록 전체 코드를 수정해줘. 복사해서 바로 실행할 수 있는 형태로 작성해줘.
```

### 목적
기존 저장소가 작성된 환경과 최신 Colab 환경 사이의 호환성 문제를 해결하기 위함.

### 반영된 수정
- `models/experimental.py`에서 `torch.load(..., weights_only=False)`가 적용되도록 패치
- `detect.py`의 `check_requirements()` 호출을 Colab Python 3.12 환경에서 우회하도록 패치

---

## Prompt 4. 결과 확인 코드 요청
```text
추론 결과 이미지가 저장된 경로를 확인하고 Colab 화면에 출력하는 코드를 작성해줘. 또한 --save-txt와 --save-conf로 생성된 label txt 파일을 읽어서 class 이름, bounding box 위치와 크기, confidence를 쉽게 확인할 수 있도록 해줘.
```

### 목적
실험 결과를 시각적으로 확인하고, 모델이 예측한 결함 종류와 신뢰도를 보고서에 정리하기 위함.

---

## Prompt 5. 제출 자료 작성 요청
```text
첨부된 코드를 바탕으로 아래의 과제를 하려는데, 코드를 어떻게 저장해서 Github에 로그인해서 어떤 버튼을 눌러야 하는지 알려줘, 그리고 보고서를 작성해줘.

- 보고서(순차적 구현 매뉴얼, 프롬프트 입력 내용 등 포함)
- 프롬프트 로그(본인의 깃허브에 PROMPTS.md 파일 업로드 및 메일로 송부)
```

### 목적
최종 제출에 필요한 GitHub 업로드 절차, 프롬프트 기록 파일, 보고서 초안을 준비하기 위함.

---

## AI 활용 범위 및 직접 확인 사항
- AI를 활용하여 Colab 실행 순서, 호환성 패치 코드, 결과 확인 코드 및 문서 초안을 작성하였다.
- 공개 저장소와 pretrained weight를 사용한 추론 재현이며, 새로운 모델 학습 또는 논문 전체 성능 지표의 재측정은 수행 범위에 포함하지 않았다.
- 제출 전 Colab에서 모든 셀을 직접 실행하고, 결과 이미지와 실행 로그가 저장된 상태의 노트북을 업로드한다.
- 실행 결과에 따라 보고서의 결과 캡처 및 탐지 결과 표는 본인이 직접 채운다.
