# youbin-shin.github.io

알고리즘 풀이 해설 및 web 등 배운 내용을 공유하는 블로그입니다.

## 로컬 실행 방법

If you would like to run or build the project on your local machine, please follow the [Jekyll Docs](https://jekyllrb.com/docs/installation/) to complete the installation of `Ruby`, `RubyGems`, `Jekyll` and `Bundler`.

Before running or building for the first time, please complete the installation of the Jekyll plugins. Go to the root directory of project and run:

```bash
$ bundle install # 설치되어 있다면 생략 가능
$ bundle exec jekyll s
```

`bundle` will automatically install all the dependencies specified by `Gemfile`.

---

## 참고

### Setting up Docker environment (optional)

If you're a loyal fan of [**Docker**](https://www.docker.com/) or just too lazy to install the packages mentioned in [_Setting up the local envrionment_](#setting-up-the-local-envrionment), please make sure you have **Docker Engine** installed and running, and then get Docker image `jekyll/jekyll` from Docker Hub by the following command

```console
$ docker pull jekyll/jekyll
```

### Run on Docker

Run the site on Docker with the following command:

```terminal
$ docker run -it --rm \
    --volume="$PWD:/srv/jekyll" \
    -p 4000:4000 jekyll/jekyll \
    jekyll serve
```

