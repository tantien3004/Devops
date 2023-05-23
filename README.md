*Clone project java về máy

*Triển khai cơ sở dữ liệu MySQL:
	+Tạo container MySQL:
		docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123 mysql
	+Import dữ liệu từ file obo.sql vào container sql vừa tạo:
		docker cp obo.sql <container-name>:/
	+Truy cập vào trong terminal của container mysql vừa tạo:
		docker exec -ti <container-name> bash
	+Tạo cơ sở dữ liệu và import từ file obo.sql vào:
		-Đăng nhập vào mysql:
			mysql -u root -p
			Nhập password: 123
		-Tạo database:
			create database <tên-database>;
			exit
	+Import cơ sở dữ liệu vào database vừa tạo:
		mysql -u root -p obo < <tên-database>.sql
	+Kiểm tra bằng cách đăng nhập lại vào mysql, use obo và show tables
	+Tạo container maven:
		-Mount volume ở ngoài vào volume ở trong container:
			docker run -ti -v $PWD:/obo-web maven bash
		-Thay thế phần cấu hình kết nối tới database
			Lấy thông tin địa chỉ IPAddress bằng cách gõ docker inspect <container-name>
			Sửa thông tin sau phần mysql:// ở file application-dev.properties
			vi src/main/resources/application-dev.properties
		-Sau khi sửa xong thì vào phần bash của container maven đã mở chạy câu lệnh:
			mvn install

*Build Docker
	+docker build -t obo-web:1.2 .
	+chạy thử xem có chạy không:
		docker run -p 8080:8080 obo-web:1.2
	+Push lên docker hub:
		docker tag obo-web tantien3004/obo-web:<tag-name>
		docker push tantien3004/obo-web:<tag-name>



*Build Kubernetes
	+Tạo file configmap.yaml:
		k create configmap obo-web --from-file=techmaster-obo-web/src/main/resources/application-dev.properties -o yaml --dry-run=client > templates/obo-web-config.yaml
	+Tạo configmap:
		k apply -f obo-web-config.yaml
	+Tạo file yaml:
		k create deployment obo-web --image tantien3004/obo-web:<tag-name> -o yaml --dry-run=client > obo-web-deploy.yaml
	+Tạo deployment:
		k apply -f obo-web-deploy.yaml
	+Khởi động ứng dụng Java ở trong pod:
		java -jar target/obo-0.0.1-SNAPSHOT.jar
	+Chuyển tiếp cổng từ pod ra máy tính:
		k port-forward deployment/obo-web --address 0.0.0.0 8080:8080 


*Chạy ứng dụng:
	curl localhost:8080
