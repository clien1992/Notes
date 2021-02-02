# 						                                                   **Maven**

# 1.解决依赖冲突

## 	1.1 怎么解决？

​					mvn dependency:tree 用dependency插件的tree goal执行,进行依赖链条分析（idea插件：Maven Helper)

​					把A的C1.0手动排除，就会自动选择C2.0

```java
		<dependency>
			<groupId>A</groupId>
			<artifactId>A</artifactId>
			<version>1.0</version>
			<exlusions>
				<exclusion>
            		<groupId>C</groupId>
                	<artifactId>C</artifactId>
                </exclusion>
			</exlusions>
		</dependency>
```



# 2.多重仓库

![](topic/maven多层仓库架构.png)

​	2.1本地仓库

​		Windows 	默认的仓库目录 		~/.m2/repository

​		Linux  	默认路径是			/home/root/.m2/repository

​		在~/.m2/settings.xml配置文件里，可以设置：

​		<localRepository>某路径</localRepository>

 	2.2 默认的中央仓库

​		apache-maven-3.5.2\lib\maven-model-builder-3.5.2.jar\org\apache\maven\mode里面的pom-4.0.0.xml记录着中央仓库的地址

​		https://repo.maven.apache.org/maven2

 	2.3 私服

​	2.4 其它远程仓库
​		java.net，google，codehaus，jboss，还有一些其他公司自己搞的Maven仓库，有少数的依赖包可能在中央仓库里找不到，只在其他仓库里。

 	2.5 镜像仓库

​		比如说，像中央仓库在国外，很慢的，直接从中央仓库下载的话，是**很慢的**，所以一般国内的一些大型的互联网公司，**阿里云**，会搞一个**镜像仓库**，完全跟中央仓库**一模一样**的，代理了中央仓库所有的请求。你可以直接从阿里云镜像仓库去请求，如果有就直接返回了，国内网络的速度很快的，上百倍；阿里云如果自己没有，就会去从国外的中央仓库去下载。

