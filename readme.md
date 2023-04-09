# 伴走くん API サーバー

## Dependency

* Java 17
* Tomcat 10
* Spring MVC 6 
  * Tomcat 10 で Spring Framework を動かす場合 v6 以上が必須です
* Maven （パッケージ管理）

## IntelliJ IDEA での開発

IntelliJ IDEA 23 の場合の手順です

### Java の設定

File > Project Structure を開き、Project Settings の Project を開く
* SDK に Java 17 を指定
  * Java 17 が無い場合は、Add SDK を選択し、SDK を追加する
  * すでに PC にインストールされている JDK のパスを追加するか、新しく Java 17 の SDK をダウンロードする

### Tomcat のインストール

https://tomcat.apache.org/download-10.cgi から、 ZIP をダウンロードし、適当な場所に解凍しておきます

### Smart Tomcat のインストールと設定

※ IntelliJ IDEA Ultimate （有料版）を使っている場合は、デフォルトで Tomcat のプラグインが入っているため、そちらを利用しても OK。

Community Edition （無料版）を使っている場合、Tomcat のプラグインが入っていないため、Simple Tomcat プラグインを利用します。

File > Settings （Windows版の場合）を開く

* Plugins を選択
* Smart Tomcat （[https://plugins.jetbrains.com/plugin/9492-smart-tomcat）をインストール

Smart Tomcat の設定

* IntelliJ 画面右上にあるビルドパネルのプルダウンを選択し、「Edit Configurations...」を選択
* 左上の + ボタンをクリックして、 Smart Tomcat を選択
* Name にはわかりやすい名前（`Bansokun Smart Tomcat` など）を入れておく
* Tomcat server で Tomcat 10 を選択
  * まだ Tomcat の設定が無い場合は、Configure... をクリックして、Settings を開き、 Tomcat Server を追加する。 + を押して、先程解凍した tomcat のフォルダ（`apache-tomcat-XX.X.X` みたいな名前のフォルダ）を選択する。
* Deployment directory: に、 `bansokun-app-api/src/main/webapp` ディレクトリを指定する
* Use classpath of module: bansokun
* Context path: /
* Server port: 8080
* VM options, Environment variables, Extra JVM classpath は空のままでよい
* Before launch に「Build」があることを確認する
* OK を選択して設定画面を閉じる

Smart Tomcat の起動

* 右上のビルドパネルのプルダウンで Smart Tomcat を選択した状態で、 Run ボタン（矢印のボタン）または Debug ボタン（虫のボタン）をクリックすると tomcat サーバーが起動する
* http://localhost:8080/ にアクセスしてサーバーが起動していることを確認する
