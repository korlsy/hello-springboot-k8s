

export JAVA_HOME=/home/sangyeol/app/jdk-17.0.2
export PATH=$PATH:$JAVA_HOME/bin
export PATH=$JAVA_HOME/bin:$PATH
java -version
 
mvn clean package -DskipTests
or
./mvnw -v        # Maven Wrapper 확인
./mvnw clean package -DskipTests



ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
직접 pod 접속해서 TEST
	kubectl exec -it hello-k8s-59f6b9fdb4-8rsj5 -- curl -s http://localhost:8180/hello
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
minikube ssh -- 'curl 10.244.0.171:8180/hello'

[pod ip]
	kubectl get pods -o wide|grep "hello"
		hello-k8s-59f6b9fdb4-9n2dl                1/1     Running   0               6m1s    10.244.0.171   minikube   <none>           <none>
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

외부 host에서 접속하기 위해 port-forward 실행.
	kubectl port-forward svc/hello-k8s-svc 8080:80
	curl http://localhost:8080/hello