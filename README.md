####slf4j-log4j����˵��


1. log4j.rootLogger ��������Ǳ���ģ����Ķ����ʽ��  
    ```properties
    log4j.rootLogger = level  , appenderName, appenderName, ��  
    ```    
    lelve�Ƕ����������𣬵��ڸü���Ľ������������Ҫ������OFF��ALL��FATAL��ERROR��WARN��INFO��DEBUG���Զ��弶������OFF�趨�Ļ���������κ���Ϣ��ALL�趨�Ļ������������Ϣ��  
    ����5���ļ���FATAL>ERROR>WARN>INFO>DEBUG��������lenel�趨ΪINFO����ô�������DEBUG��Ϣ��appenderName��ָ����־��Ϣ������ĸ��ط�������̨���ļ��ȵȣ���ͬʱָ��������Ŀ�ĵء�  
    appenderName��ָ����־��Ϣ������ĸ��ط�������̨���ļ��ȵȣ���ͬʱָ��������Ŀ�ĵء�  
    
2. log4j.appender ���Ҳ�Ǳ������õģ����Ǹ��������־��¼��������������Ķ����ʽ���£�  
    ```properties
    log4j.appender.appenderName=someAppender(ѡ��һ�����ƽ̨)  
    log4j.appender.appenderName.File=�ļ���(�ļ��������·��)  
    log4j.appender.appenderName.layout=�������  
    log4j.appender.appenderName.layout.ConversionPattern=�����ʽ  
    ```
    log4j.appender.appenderNameָ�����appender��Log4J�ṩ��һ�¼���appender: 
    ```properties
    org.apache.log4j.ConsoleAppender������̨��  
    org.apache.log4j.FileAppender���ļ���
    org.apache.log4j.DailyRollingFileAppender��ÿ�����һ����־�ļ���  
    org.apache.log4j.RollingFileAppender���ļ���С����ָ���ߴ��ʱ�����һ���µ��ļ�����ͨ��log4j.appender.R.MaxFileSize=100KB�����ļ���С������ͨ��log4j.appender.R.MaxBackupIndex=1����Ϊ����һ�������ļ�����  
    org.apache.log4j.WriterAppender������־��Ϣ������ʽ���͵�����ָ���ĵط���
    ```
    
    log4j.appender.appenderName.layoutָ����־��Ϣ�ĸ�ʽ�����֣�Layout���������ʽ��Appender�������Log4j�ṩ��layout�����¼��֣�
    ```properties
    org.apache.log4j.HTMLLayout����HTML�����ʽ���֣�
    org.apache.log4j.PatternLayout����������ָ������ģʽ��
    org.apache.log4j.SimpleLayout��������־��Ϣ�ļ������Ϣ�ַ�����
    org.apache.log4j.TTCCLayout��������־������ʱ�䡢�̡߳����ȵ���Ϣ����
    ```
    log4j.appender.appenderName.layout.ConversionPattern��ʽ����־��Ϣ��Log4J��������C�����е�printf�����Ĵ�ӡ��ʽ��ʽ����־��Ϣ����ӡ�������£�
    ```properties
     %m ���������ָ������Ϣ
     %p ������ȼ�����DEBUG��INFO��WARN��ERROR��FATAL
     %r �����Ӧ�������������log��Ϣ�ķѵĺ�����
     %c �����������Ŀ��ͨ�������������ȫ��
     %t �����������־�¼����߳���
     %n ���һ���س����з���Windowsƽ̨Ϊ��rn����Unixƽ̨Ϊ��n��
     %d �����־ʱ�������ڻ�ʱ�䣬Ĭ�ϸ�ʽΪISO8601��Ҳ���������ָ����ʽ�����磺%d{yyyy MMM dd HH:mm:ss,SSS}��������ƣ�2012��06��24�� 23��55��28��92
     %l �����־�¼��ķ���λ�ã�������Ŀ�����������̣߳��Լ��ڴ����е�������
    ```     
3. log4j.logger  
������Ǳ���ģ��������������������log4j.rootLogger��level��������Ҫ�Ǿ��嵽package��Class�����info�����Ķ����ʽ���£�  
    ```properties
    log4j.logger.packageName[.ClassName]=level[,appender]
    ```  
    ��Ҳ���������ָ����appender��Ҳ���Բ�ָ�������Ĭ��appender��

    