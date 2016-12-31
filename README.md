####slf4j-log4j配置说明


1. log4j.rootLogger 这个配置是必须的，它的定义格式：  
    ```properties
    log4j.rootLogger = level  , appenderName, appenderName, …  
    ```    
    lelve是定义的输出级别，低于该级别的将不会输出，主要级别有OFF、ALL、FATAL、ERROR、WARN、INFO、DEBUG或自定义级别，其中OFF设定的话将不输出任何信息，ALL设定的话将输出所有信息；  
    另外5个的级别FATAL>ERROR>WARN>INFO>DEBUG，如果你的lenel设定为INFO，那么不能输出DEBUG信息；appenderName是指定日志信息输出到哪个地方，控制台，文件等等，可同时指定多个输出目的地。  
    appenderName是指定日志信息输出到哪个地方，控制台，文件等等，可同时指定多个输出目的地。  
    
2. log4j.appender 这个也是必须配置的，它是负责控制日志记录操作的输出。它的定义格式如下：  
    ```properties
    log4j.appender.appenderName=someAppender(选择一种输出平台)  
    log4j.appender.appenderName.File=文件名(文件输出定义路径)  
    log4j.appender.appenderName.layout=输出布局  
    log4j.appender.appenderName.layout.ConversionPattern=输出格式  
    ```
    log4j.appender.appenderName指定输出appender，Log4J提供了一下几种appender: 
    ```properties
    org.apache.log4j.ConsoleAppender（控制台）  
    org.apache.log4j.FileAppender（文件）
    org.apache.log4j.DailyRollingFileAppender（每天产生一个日志文件）  
    org.apache.log4j.RollingFileAppender（文件大小到达指定尺寸的时候产生一个新的文件，可通过log4j.appender.R.MaxFileSize=100KB设置文件大小，还可通过log4j.appender.R.MaxBackupIndex=1设置为保存一个备份文件）。  
    org.apache.log4j.WriterAppender（将日志信息以流格式发送到任意指定的地方）
    ```
    
    log4j.appender.appenderName.layout指定日志信息的格式（布局）Layout，它负责格式化Appender的输出。Log4j提供的layout有以下几种：
    ```properties
    org.apache.log4j.HTMLLayout（以HTML表格形式布局）
    org.apache.log4j.PatternLayout（可以灵活地指定布局模式）
    org.apache.log4j.SimpleLayout（包含日志信息的级别和信息字符串）
    org.apache.log4j.TTCCLayout（包含日志产生的时间、线程、类别等等信息）。
    ```
    log4j.appender.appenderName.layout.ConversionPattern格式化日志信息，Log4J采用类似C语言中的printf函数的打印格式格式化日志信息，打印参数如下：
    ```properties
     %m 输出代码中指定的消息
     %p 输出优先级，即DEBUG，INFO，WARN，ERROR，FATAL
     %r 输出自应用启动到输出该log信息耗费的毫秒数
     %c 输出所属的类目，通常就是所在类的全名
     %t 输出产生该日志事件的线程名
     %n 输出一个回车换行符，Windows平台为“rn”，Unix平台为“n”
     %d 输出日志时间点的日期或时间，默认格式为ISO8601，也可以在其后指定格式，比如：%d{yyyy MMM dd HH:mm:ss,SSS}，输出类似：2012年06月24日 23：55：28，92
     %l 输出日志事件的发生位置，包括类目名、发生的线程，以及在代码中的行数。
    ```     
3. log4j.logger  
这个不是必需的，如果不配置这个，则采用log4j.rootLogger的level级别。它主要是具体到package、Class级别的info，它的定义格式如下：  
    ```properties
    log4j.logger.packageName[.ClassName]=level[,appender]
    ```  
    它也可以输出到指定的appender，也可以不指定输出到默认appender。

    