## 문제
```
$ gradle -v

Please set the JAVA_HOME variable in your environment to match the location of your Java installation
```

## 해결
1. Gradle 파일 설치 후, 환경 변수 설정까지 해줬는데 다음과 같은 오류 메세지가 뜸
```
$ gradle -v
```
```
Please set the JAVA_HOME variable in your environment to match the location of your Java installation
```
2. https://laily.tistory.com/1 참고하여 java 버전 맞춰줌
3. 그 후에도 에러나서 그냥 jdk를 새로 설치(https://d2fault.github.io/2018/07/11/20180711-install-jdk-at-windows10/ 참고)
4. `$ echo $JAVA_HOME` 명령어와 `$java -version` 확인 해봤을 때 버전 동일함을 확인
```
$ echo $JAVA_HOME
C:\Program Files\Java\jdk1.8.0_231;
$ java -version
java version "1.8.0_231"
Java(TM) SE Runtime Environment (build 1.8.0_231-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.231-b11, mixed mode)
```
5. `$ javac -version` 명령어를 입력해봤는데 다음과 같은 결과가 떠서
https://macchiato.tistory.com/9 참고하여 고쳐줌
```
$ javac -version
javac 1.8.0_151
```
6. 근데도 오류가 뜬다. 대체 뭐가 문제지
```
$ java -version
java version "1.8.0_231"
Java(TM) SE Runtime Environment (build 1.8.0_231-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.231-b11, mixed mode)

$ javac -version
javac 1.8.0_231

$ gradle -v

ERROR: JAVA_HOME is set to an invalid directory: C:\Program Files\Java\jdk1.8.0_231;

Please set the JAVA_HOME variable in your environment to match the
location of your Java installation.
```
7. 알고 보니까 $JAVA_HOME 환경변수 설정할 때 끝에 ;를 붙인 게 문제였다. win10 쓰는데 PATH 환경 변수처럼 환경 변수 편집 창에 들어가면 ;이 안보인다. 그래서 ;이 있는 줄은 몰랐다 ,,, 
https://stackoverflow.com/questions/45182717/java-home-is-set-to-an-invalid-directory
여기 사이트를 참고 함
8. 저도 반가워요 Gradle씨 ,,,
```
$ gradle -v

Welcome to Gradle 6.0.1!

Here are the highlights of this release:
 - Substantial improvements in dependency management, including
   - Publishing Gradle Module Metadata in addition to pom.xml
   - Advanced control of transitive versions
   - Support for optional features and dependencies
   - Rules to tweak published metadata
 - Support for Java 13
 - Faster incremental Java and Groovy compilation
 - New Zinc compiler for Scala
 - VS2019 support
 - Support for Gradle Enterprise plugin 3.0

For more details see https://docs.gradle.org/6.0.1/release-notes.html


------------------------------------------------------------
Gradle 6.0.1
------------------------------------------------------------

생략
```
