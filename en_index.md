## JNet Lib



This is a netwok lib ,developer on Java, suppor Java And Android.  support some platform, eg: github 、 gitee.



### Build Lib

``` shell
mvn install
```

### Use Method

> support gradle and maven

* **maven*

``` xml
<!-- https://mvnrepository.com/artifact/com.github.netcapture/Jnt -->
<!-- https://repo1.maven.org/maven2/com/github/netcapture/Jnt/ -->
<dependency>
    <groupId>com.github.netcapture</groupId>
    <artifactId>Jnt</artifactId>
    <version>2.2.4</version>
</dependency>

```

* **gradle**

``` groovy
implementation 'com.github.netcapture:Jnt:2.2.4'
```



#### api



api support two way:

* The result of the request is returned directly. At this time, if the network request is successful (200), the response text is returned, otherwise, the error log is returned. If it is still empty, the output log is returned. Serial API:

``` java
//  http get request
Jnt.get
//  http post request
Jnt.post
//  http custom request
Jnt.request

//new api
NJnt.xx.get()

```

* Directly returns the response of the request, the response contains the status value, HTTP response HEADER and other values, series API:

``` java
//  http get request
Jnt.getResp
//  http post request
Jnt.postResp
//  http custom request
Jnt.requestResp
```

#### APIs for supported platforms

* github api

``` java
// create a new file
GithubHelper.createFile
// update file
GithubHelper.updateContent
// append text 
GithubHelper.append
// Query the sha value of a file
GithubHelper.getSha
// 删除文件
GithubHelper.deleteFile
```

* gitee api

``` java
GiteeHelper.createFile
GiteeHelper.updateContent
GiteeHelper.getSha
GiteeHelper.deleteFile
```

* github already supports shell upload

This part of the api is extracted from [uploadGithub](https://github.com/hhhaiai/uploadGithub/), and the supported usage is as follows:

``` 
github usage:
	-o: github [user] name
	-u: github [user] name
	-r: github [project] name
	-s: github [upload directory] name
	-p: github [target file] name
	-f: github will upload the local file name
	-t: github personal token
	-c: github uploads [not base64] content
	-b: github uploads [base64] content
	-m: github upload commit content
	-a: The username used for github uploads (auther)
	-l: Email name used for github upload
```

Example usage, used in production

``` shell
java -jar uploadGithubService-1.1-jar-with-dependencies.jar  
    -owner hhhaiai -repo Git_result 
    -target-dir-full-name  $upload_file_name 
    -native-file ${file_name}  
    -token ${{ secrets.GTOKEN }} 
    -commit-messge  "GitHubAction: Build&Monkey ${{ github.repository }} Job ${{ github.job }}, created by ${{ github.workflow }} " 
    -commit-auther "GitHubAction"
    -commit-email "sanbo.xyz@gmail.com"
```

#### for project

* [uploadGithub](https://github.com/hhhaiai/uploadGithub)
