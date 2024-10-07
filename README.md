# AI_1st_project
말달리자 프로젝트(1위 경주마 예측 모델)

이용한 데이터 : https://www.data.go.kr/data/15116930/fileData.do (한국마사회_경주상세정보(제주_부경) 데이터)

# 전처리 과정 

참고한 데이터(경마장에 처음 들어서면 이와 같은 형식으로 팜플렛(?)을 준다고 함) 
https://knetz.kra.co.kr/infoHowGetWinHorse.do

잘 뛰는 말 고르기 경주성적이 좋은 말 : ① ② 참조

경주기록이 빠른 말 : ③ ④ ⑤ 참조 (해당 거리에서 기록이 빠른 말이나 최근 경주에서 빠른 기록을 달성한 말)

과거 경주에서 우승했을 때 뒷말과 차이가 많이 난 말 : ⑤ ⑥ 참조

부담중량이 높은 말: ⑦ 참조

선행말은 단거리(1000m~1300m)일 때, 안쪽 번호일 때, 경주로 상태가 불량할 때 유리: ⑧ ⑨ ⑩ 참조

아래사항들을 체크해 보고 예시장이나 경주로에서 말의 컨디션이나 걸음걸이를 확인하기
과거에 같은 경주에 출전해서 누가 이겼는지
한 달에 한 번 출전하는 정상적인 출전간격(4주 또는 5주)인지 아닌지
말 체중이 10kg을 초과해서 줄어있거나 늘어있지는 않은지 좋은선수 판단하기 통산 우승횟수가 많고 통산 승률이 높은 선수: ⑪ 참조
최근 1년간 우승횟수가 많은 선수: ⑪ 참조

해당마에 기승하여 좋은 성적을 거둔 선수: ⑫ 참조

시각화 : heatmap, PCA, violinplot

# 샘플링 

rus, enn, ros, smo, smoenn 중 accuracy는 크게 의미없다고 판단, Precision과 Recall을 기반으로 하여 ros(random oversampling) 선정. 

# 모델링 

1. 처음엔 knn, decisiontree, randomforest, adaboost, xgboost 만 사용.
2. 하지만 효율이 좋지 못해서(precision 값이 0.21로 값이 너무 낮음)
3. RandomForest 는 비교적 precision 값이 높고 adaboost는 recall 값이 높으므로 stacking 모델로 조합하면 데이터 불균형에 대해 개선될 것이라고 예상하고 구성하여 실험.
