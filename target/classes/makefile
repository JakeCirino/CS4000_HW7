HADOOP_CLASSPATH=$(shell hdfs classpath)

secret: SecretMessage.java 
	javac -classpath $(HADOOP_CLASSPATH) SecretMessage.java
	jar -cvf secret.jar SecretMessage*.class

general: GeneralMessage.java
	javac -classpath $(HADOOP_CLASSPATH) GeneralMessage.java
	jar -cvf general.jar GeneralMessage*.class
	
runsecret: SecretMessage.java
	rm -rf output
	yarn jar secret.jar SecretMessage $(INPUT) output

rungeneral: GeneralMessage.java
	rm -rf output
	yarn jar general.jar GeneralMessage $(SECRET_MESSAGE) $(INPUT) output
