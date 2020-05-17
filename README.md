# 고구마 사전예약 사이트 만들기

> 아버지께서 퇴직 후, 취미아닌 취미로 고구마를 비롯한 몇 개의 작물을 재배하시고 소량 판매하시기에 구매를 원하는 지인들의 목록을 얻어보고자 웹 사이트 제작을 생각함.
>
> 현재까지 배운 Django와 Bootstrap, HTML&CSS 이용해 아주 간단하게 제작을 생각함.
>
> 사전 예약 형식으로 최대 100 박스를 예약 받도록 만들 예정.



## 1. 사이트 1차 구상

- 메인, 예약 신청, 예약 신청 확인, 예약 수정, 안내&공지, 물품 정보 페이지로 구성
- 회원가입의 번거로움이 없도록 만들 것

- 확정해야 하는 것
  1. 사전 예약 개수를 미리 정한 뒤, 개수 초과시 신청 불가로 만들 것 인지
  2. 개수 제한 없이 일단 모든 신청을 받은 후, 정해둔 개수 초과시 안내가 가도록 만들 것 인지
- 위에서 1번으로 정했다면
  - 정확한 개수를 어떤 방식으로 카운트
- 2번으로 정했다면
  - 어떤 방식으로 안내



## 2. 사용한 것

- Python (3.7.6)
- Django (2.1.15)
- Bootstrap (v4.4.1)



## 3. 설치&기초 setting

pip을 사용하여 터미널에서

```bash
$ pip install django==2.1.15
```

예약 받을 페이지를 담당할 app인 reservation과 사용자들을 관리할 app인 accounts를 settings.py에 추가

- 먼저 bash에서 

  ```bash
  $ python manage.py startapp reservation
  $ python manage.py startapp accounts
  ```

- 그 후 settings.py에서

  ```python
  INSTALLED_APPS = [
      ...
      'reservation',
      'accounts',
  ]
  ```

- static폴더 사용

  ```python
  #settings.py에서
  STATICFILES_DIRS = (
         os.path.join(BASE_DIR, 'static'),
  ) #추가
  ```

## 4. Model, Form 설정

- 가장 먼저, 고구마를 신청할 모델과 고구마 정보를 올릴 모델을 만드려고 했음
- 하지만 고구마 정보는 내가 직접 올리기 때문에 모델을 설정할 필요가 없음
- 그래서 사용자들의 건의사항과 문의사항을 받을 게시글 모델을 설정

## 5. 기본 동작 구조

1. 홈 페이지에서 네비게이션 바를 이용한 페이지 이동
2. 따로 회원가입이 존재하지 않고, 고구마를 신청하는 페이지를 통해 필요한 주소 및 핸드폰 번호, 수량, 종류를 받음과 동시에 회원가입 진행
3. 가입 후 로그인을 통해 고구마 신청 정보 조회 및 수정, 삭제
4. QandA는 따로 게시판을 이용
5. 공지사항과 안내사항을 보여주는 페이지 존재

## 6. 2차 구상

1. Q&A를 위한 페이지 작성
   - 본인 글만 확인, 수정, 삭제 가능
   - 댓글 작성 가능
2. 세부적인 UI UX 디자인(도움 필요)