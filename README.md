# docker-library
Bookmarks favorite personal docker images

| Filename | Description |
| --- | --- |
| python-bash | bash with available python is executed |
| python-main | main\.py is executed |
| python-nb | jupyter notebook server is executed. TODO: auth-token should be deleted |
| gcc-bash | bash with available g++ is executed |

---

## Common

해당 디렉토리에서 다음 명령어를 실행하여 이미지 빌드
```
> docker build -t (IMAGENAME) .
```

---

## python-bash

다음 명령어를 실행하여 container 접속
```
> docker run --rm -it -v (PATH_TO_DIRECTORY):/volume (IMAGENAME)
```

container 내부에서 다음 명령어를 실행하여 작성한 코드 실행 (예시)
```
> python main.py
```

### \+ tensorboard

requirements.txt에 'tensorboard'를 작성 후, container 내부에서 다음 명령어를 실행하여 tensorboard 실행
```
> docker run --rm -it -v (PATH_TO_DIRECTORY):/volume -p 6006:6006 (IMAGENAME)
```

container 내부에서 다음 명령어를 실행한 후 브라우저에서 'localhost:6006'으로 접속
```
> tensorboard --logdir runs --host=0.0.0.0
```

---

## python-main

해당 디렉토리에 main\.py 작성 후, 다음 명령어를 실행하여 파이썬 파일 실행
```
> docker run --rm -v (PATH_TO_DIRECTORY):/volume (IMAGENAME)
```

---

## python-nb

1. 다음 명령어를 실행하여 jupyter notebook을 실행
2. 브라우저에서 'localhost:5000'으로 접속
3. 터미널의 token을 비밀번호로 입력하여 jupyter notebook 접속
```
docker run --rm -it -v path/to/directory:/volume -p 5000:8888 (IMAGENAME)
```

---

## gcc-bash

다음 명령어를 실행하여 container 실행
```
> docker run -it -v path/to/directory:/volume (IMAGENAME)
```

컨테이너 내부에서 다음 명령어를 실행하여 c 파일 컴파일 후 실행
```
> gcc path/to/filename.c
> ./filename
```