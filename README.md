# 20150817-jacoco-example

## git clone ##

* git clone https://github.com/tempest200903/20150817-jacoco-example.git

## JaCoCoカバレッジレポート計測実行手順 ##

```
$ mvn clean test site
$ ls target/site/jacoco/index.html
$ cygstart target/site/jacoco/index.html
```

## 成功例 ##

```
$ git checkout 22e8167f0a0cf0fbb19a87caff524a9ff7d38888
$ mvn clean test site
$ cygstart target/site/jacoco/index.html
$ cygstart src/resources/WS-y2015-0560.JPG
```

![スクリーンショット](https://raw.githubusercontent.com/tempest200903/20150817-jacoco-example/master/src/resources/WS-y2015-0560.JPG "スクリーンショット")

## 失敗例1 jacocoArgs プロパティを自分で定義する ##

```
$ git checkout 0ed0543b502479bb70e061696ba22f5bdc3e4358
$ fgrep -C 4 '<jacocoArgs>' pom.xml
 <properties>
  <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  <plugin.version.jacoco>0.7.4.201502262128</plugin.version.jacoco>
  <!-- jacocoArgs プロパティを自分で定義すると、カバレッジ計測が失敗する。 -->
  <jacocoArgs></jacocoArgs>
 </properties>
$ cygstart target/site/jacoco/index.html
$ ls target/site/jacoco/index.html
$ cygstart src/resources/WS-y2015-0560.JPG
```

![スクリーンショット](https://raw.githubusercontent.com/tempest200903/20150817-jacoco-example/master/src/resources/WS-y2015-0561.JPG "スクリーンショット")

## 失敗例2 maven-surefire-plugin argLine に ${jacocoArgs} を記していない ##

* https://github.com/tempest200903/20150817-jacoco-example/commit/06c98a134d25913d5e4befff0dc39bb4d3baf224

```
$ mvn clean test site
$ ls target/site/jacoco/index.html
ls: cannot access target/site/jacoco/index.html: No such file or directory
```
