# 🎓 학생 학업 성취도 요인 분석

Kaggle의 [xAPI-Edu-Data](https://www.kaggle.com/aljarah/xAPI-Edu-Data) 데이터를 활용하여,  
학생의 행동 및 배경 정보가 학업 성취도(Class)에 어떤 영향을 주는지를 분석하고 다양한 분류 모델로 예측 성능을 비교해보았습니다.  
<br>

## 📈 주요 내용

### 1. EDA 및 시각화

- 수치형 분석 : 수업참여도(`raisedhands`, `VisITedResources`), `Discussion`, `AnnouncementsView`, 부모의 관심, 과목 등 성적(Class)과의 관계 분석
- 범주형 분석 : 성별, 국적, 수강 과목, 학부모 설문 참여 유무 등과 성적의 상관관계 시각화
- Class 값 수치 변환 : `L → -1`, `M → 0`, `H → 1` 로 변환하여 평균 등급 시각화 및 인사이트 도출

### 2. 데이터 전처리

- `get_dummies()`를 활용한 One-hot Encoding 처리
- 학습/테스트 데이터 분리 (test_size=0.3)


### 3. 모델링

- 로지스틱 회귀, 결정 트리, KNN, SVM 적용 및 비교
- 평가 지표로는 precision, recall, f1-score 등 `classification_report` 사용
  
  | 모델                  | 정확도 |
  |-----------------------|--------|
  | **Logistic Regression** | 70%   |
  | **Decision Tree**       | 68%   |
  | **K-Nearest Neighbors** | 65%   |
  | **SVM (Linear)**        | 71%   |

  -> **SVM이 가장 높은 정확도 보임**


### 4. 인사이트 요약

- 수업 참여도(raisedhands, VisITedResources)가 높을수록 `H` 등급 비율 증가
- 학부모의 설문 참여 여부, 학교 만족도는 학생 성적과 높은 상관을 보임.
- **IT 과목 수강자 → 낮은 성적(L)** 경향, **Biology 과목 → 높은 성적(H)** 비율 높음
- 성별 차이 존재 : 여학생이 전반적으로 높은 성적을 받는 경향
