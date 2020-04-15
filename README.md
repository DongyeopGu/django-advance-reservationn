# 간단한 예약 사이트 만들기

> 아버지께서 퇴직 후, 취미아닌 취미로 고구마를 비롯한 몇 개의 작물을 재배하시고 소량 판매하시기에 구매를 원하는 지인들의 목록을 얻어보고자 웹 사이트 제작을 생각함.
>
> 현재까지 배운 Django와 Bootstrap, HTML&CSS 이용해 아주 간단하게 제작을 생각함.
>
> 사전 예약 형식으로 최대 100 박스를 예약 받도록 만들 예정.

## 1. 사용한 것

- Python (3.7.6)
- Django (2.1.15)
- Bootstrap

## 2. 설치&기초 setting

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

