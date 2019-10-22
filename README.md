Maven学习笔记
=========
一.介绍
-------
Maven作为一个***构建工具***，不仅能帮我们自动化构建，还能够抽象构建过程，提供构建任务实现;它跨平台，对外提供了一致的操作接口，这一切足以使它成为优秀的、流行的构建工具。

Maven不仅是构建工具，还是一个***依赖管理工具和项目管理工具***，它提供了中央仓库，能帮我自动下载构件。 

二.安装
-------
1. 确认是否安装了jdk
2. 官网下载对应操作系统的maven版本
3. 设置一下环境变量，将Maven安装配置到操作系统环境中，主要就是配置M2_HOME *和PATH*两项
4. 验证是否安装成功 mvn -v

三.目录介绍
-------
1. bin目录:该目录包含了mvn运行的脚本，这些脚本用来配置java命令，准备好classpath和相关的Java系统属性，然后执行Java命令。
2. boot目录:该目录只包含一个文件，该文件为plexus-classworlds-2.5.2.jar。plexus-classworlds是一个类加载器框架，相对于默认的java类加载器，它提供了更加丰富的语法以方便配置，Maven使用该框架加载自己的类库。 
3. conf目录:该目录包含了一个非常重要的文件settings.xml。直接修改该文件，就能在机器上全局地定制Maven的行为，一般情况下，我们更偏向于复制该文件至~/.m2/目录下（~表示用户目录），然后修改该文件，在用户范围定制Maven的行为。
4. lib目录:该目录包含了所有Maven运行时需要的Java类库，Maven本身是分模块开发的，因此用户能看到诸如maven-core-3.0.jar、maven-model-3.0.jar之类的文件，此外这里还包含一些Maven用到的第三方依赖如commons-cli-1.2.jar、commons-lang-2.6.jar等等。

四.Maven常用命令说明
-------
1. mvn clean：表示运行清理操作（会默认把target文件夹中的数据清理）。
2. mvn clean compile：表示先运行清理之后运行编译，会将代码编译到target文件夹中。
3. mvn clean test：运行清理和测试。
4. mvn clean package：运行清理和打包。
5. mvn clean install：运行清理和安装，会将打好的包安装到本地仓库中，以便其他的项目可以调用。
6. mvn clean deploy：运行清理和发布（发布到私服上面）。
上面的命令大部分都是连写的，大家也可以拆分分别执行，这是活的，看个人喜好以及使用需求，Eclipse Run as对maven项目会提供常用的命令。

五.设置http代理
------
```cmd
<settings>  
  ...
  <proxies>
    <proxy>  
      <id>my-proxy</id>  
      <active>true</active>  
      <protocol>http</protocol>  
      <host>218.14.227.197</host>  
      <port>3128</port>  
      <!--  
        <username>***</username>  
        <password>***</password>  
        <nonProxyHosts>  
          repository.mycom.com|*.google.com  
        </nonProxyHosts>  
      -->  
    </proxy>  
  </proxies>  
  ...  
</settings> 
```

六、Maven插件安装，基于IDEA
----
![avatar](mavenideaplug.PNG)
11111
