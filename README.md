# Github-recommendation-system-using-word2vec
Github recommendation system(using word2vec)


기획의도 : 개발자라면 대부분이 깃허브를 통해 자신이 작업하는 것들을 관리하는데, 만약 모르는(궁금한) 것이 있다면 스스로 구글링을 통해 깃허브의 repository(이하 repo)를 찾는 경우가 있습니다. 
하지만 개발을 시작하는 입문자들은 어떤 내용을 검색해야 되는지조차 모르는 경우가 많이 있습니다. 
이럴 경우 입문자들의 언어 작성 빈도를 기반으로 그들과 거리가 유사한 유저가 fork한 repository를 작성한 user를 추천해줍니다

## 가정
1. 특정 사람 A가 B의 repo를 fork한다면, A는 B의 repo를 통해 학습할 의향이 있다

## 데이터 크롤링
- 셀레니움을 활용해 깃허브 유저 데이터(ID, name, country, mail_address, webpage, join_date, followers, Starred, Following, Contribution) 수집
- 유저가 작성한 repository 수집(작성자 이름, repository 이름, 사용한 언어, 언어의 빈도)
- 유저가 fork한 repository 수집(유저 이름, fork repository의 주인, fork repo 이름)

## 데이터 전처리
- pandas를 통한 데이터 전처리

## 모델링
- user-language 매트릭스를 생성해 유저간 거리 측정
- fork 데이터를 기반으로 word2vec 모델 생성해

=> input user와 근접한 user를 알려준 후, 그 user가 fork한 repository의 주인을 추천해줌

## 보완점
- 웹으로 구현해보면 좋을 것 같습니다
- 데이터 수집을 조금 더 많이 해서 다시 모델링하면 정확도가 높아질 것 같습니다
- 추후 깃허브와 관련되어 한국인들의 깃허브 사용 실태, 주 사용 언어 등을 시각화로 표현해볼 수 있을 것 같습니다.

## 자주 묻는 질문 

1) 왜 fork한 repository를 작성한 user를 추천해주나요?
- 일반적으로 깃허브는 SNS의 형태(following, follower)를 가지고 있지만 타 SNS에 비해 팔로잉하는 빈도가 적기 때문에 fork를 지표로 삼았습니다
