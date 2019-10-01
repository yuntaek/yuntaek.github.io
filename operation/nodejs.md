---
description: Node.js의 바이너리를 패키징하는 방법에 대한 설명입니다.
---

# Nodejs 패키징

## 바이너리 다운로드 <a id="Nodejs&#xD328;&#xD0A4;&#xC9D5;-&#xBC14;&#xC774;&#xB108;&#xB9AC;&#xB2E4;&#xC6B4;&#xB85C;&#xB4DC;"></a>

패키징을 생성할 폴더로 이동 후 그곳에서 다운로드한다.

이 예제에서는  ~/deb이라는 폴더 아래서 패키징 작업을 한다. 그리고 Node.js의  작성 기준의 최신 LTS버전으로 한다.

```text
$mkdir ~/deb
$cd ~/deb
$wget https://nodejs.org/dist/v10.16.3/node-v10.16.3-linux-x64.tar.xz
```

## 바이너리 압푹 풀기 및 압축하기 <a id="Nodejs&#xD328;&#xD0A4;&#xC9D5;-&#xBC14;&#xC774;&#xB108;&#xB9AC;&#xC555;&#xD479;&#xD480;&#xAE30;&#xBC0F;&#xC555;&#xCD95;&#xD558;&#xAE30;"></a>

압축을 푼후 압축을 푼 디렉토리를 지정된 이름으로 재압축 한다.

```text
$tar xf node-v10.16.3-linux-x64.tar.xz
$tar cfz nodejs_10.16.3.orig.tar.gz ./node-v10.16.3-linux-64
```

## debian폴더 만들기 <a id="Nodejs&#xD328;&#xD0A4;&#xC9D5;-debian&#xD3F4;&#xB354;&#xB9CC;&#xB4E4;&#xAE30;"></a>

```text
$cd ./node-v10.16.3-linux64
$mkdir debian
```

## changelog 파일 만들기 <a id="Nodejs&#xD328;&#xD0A4;&#xC9D5;-changelog&#xD30C;&#xC77C;&#xB9CC;&#xB4E4;&#xAE30;"></a>

```text
//새로 작성시
$dch --create
//버전 업일 경우
$dch --newversion 10.16.3-2
//아래와 같은 형태로 changelog를 작성한다.
nodejs (10.16.3-1) UNRELEASED; urgency=medium
  [z Yuntaek Lim ]
  * Initial release. (Closes:
 -- Yuntaek Lim <yuntaek.lim@wavve.com>  Thu, 19 Sep 2019 10:43:10 +0900
```

## control 파일 만들기 <a id="Nodejs&#xD328;&#xD0A4;&#xC9D5;-control&#xD30C;&#xC77C;&#xB9CC;&#xB4E4;&#xAE30;"></a>

```text
$vim debian/control
source: nodejs
Priority: optional
Section: misc
Maintainer: Yuntaek Lim <yuntaek.lim@wavve.com>
Build-Depends: debhelper (>= 9)
Standards-Version: 3.9.8
Package: nodejs
Architecture: all
Priority: optional
Depends: ${misc:Depends}
Section: misc
Description: Foo cli utility
 See homepage for details.
 This package repackage original compiled
 java binaries for foo and provides
 additional symlinks to /usr/bin
```

## compat 파일 만들기 <a id="Nodejs&#xD328;&#xD0A4;&#xC9D5;-compat&#xD30C;&#xC77C;&#xB9CC;&#xB4E4;&#xAE30;"></a>

## rules  파일 만들기 <a id="Nodejs&#xD328;&#xD0A4;&#xC9D5;-rules&#xD30C;&#xC77C;&#xB9CC;&#xB4E4;&#xAE30;"></a>

```text
$vim debian/rules
#!/usr/bin/make -f
clean:
        @
build:
        @
binary:
        mkdir -p debian/nodejs
        mkdir -p debian/nodejs/usr/local/bin
        mkdir -p debian/nodejs/usr/local/include
        mkdir -p debian/nodejs/usr/local/share
        mkdir -p debian/nodejs/usr/local/lib
        cp -r ./lib/* debian/nodejs/usr/local/lib
        cp -r ./bin/* debian/nodejs/usr/local/bin
        cp -r ./include/* debian/nodejs/usr/local/include
        cp -r ./share/* debian/nodejs/usr/local/share
        dh_gencontrol
        dh_builddeb debian/nodejs/usr/local/share
        dh_gencontrol
        dh_builddeb
```

## build하기 <a id="Nodejs&#xD328;&#xD0A4;&#xC9D5;-build&#xD558;&#xAE30;"></a>

```text
$dpkg-buildpackage -b
dpkg-buildpackage: info: source package nodejs
dpkg-buildpackage: info: source version 10.16.3-1
dpkg-buildpackage: info: source distribution UNRELEASED
dpkg-buildpackage: info: source changed by Yuntaek Lim <yuntaek.lim@wavve.com>
dpkg-buildpackage: info: host architecture amd64
 dpkg-source --before-build node-v10.16.3-linux-x64
 fakeroot debian/rules clean
make: 'clean' is up to date.
 debian/rules build
make: 'build' is up to date.
 fakeroot debian/rules binary
mkdir -p debian/nodejs
mkdir -p debian/nodejs/usr/local/bin
mkdir -p debian/nodejs/usr/local/include
mkdir -p debian/nodejs/usr/local/share
mkdir -p debian/nodejs/usr/local/lib
cp -r ./lib/* debian/nodejs/usr/local/lib
cp -r ./bin/* debian/nodejs/usr/local/bin
cp -r ./include/* debian/nodejs/usr/local/include
cp -r ./share/* debian/nodejs/usr/local/share
dh_gencontrol
dh_builddeb
dpkg-deb: building package 'nodejs' in '../nodejs_10.16.3-1_all.deb'.
 dpkg-genbuildinfo --build=binary
 dpkg-genchanges --build=binary >../nodejs_10.16.3-1_amd64.changes
dpkg-genchanges: info: binary-only upload (no source code included)
 dpkg-source --after-build node-v10.16.3-linux-x64
dpkg-buildpackage: info: binary-only upload (no source included)
dpkg-buildpackage: warning: not signing UNRELEASED build; use --force-sign to override
```

### 참고

* [https://github.com/phusion/debian-packaging-for-the-modern-developer](https://github.com/phusion/debian-packaging-for-the-modern-developer)

