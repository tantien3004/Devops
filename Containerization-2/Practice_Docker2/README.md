Trong Docker,
	*CMD được sử dụng để chỉ định lệnh mặc định mà container sẽ thực thi khi chạy. Nếu không có chỉ thị `CMD` được chỉ định trong Dockerfile, Docker sẽ sử dụng câu lệnh mặc định(default command) của base image.
		+Bạn có thể sử dụng ký tự `CMD` trong Dockerfile để chỉ định 1 lệnh Linux hoặc 1 chương trình được thực thi khi container khởi chạy. Chỉ thị `CMD` có thể được sử dụng trong Dockerfile 1 hoặc nhiều lần. Tuy nhiên, chỉ có lệnh `CMD` cuối cùng sẽ được sử dụng khi chạy container.
		+Cú pháp của chỉ thị `CMD` là:
			CMD ["executable", "param1", "param2"]
		trong đó, executable là chương trình hoặc lệnh mà bạn muốn container thực thi khi khởi động và param1 và param2 là các tham số bạn muốn truyền vào cho lệnh đó.
	
	
	*ENTRYPOINT là 1 chỉ thị được sử dụng để chỉ định lệnh hoặc chương trình chạy mặc định mà container sẽ thực thi khi khởi động. Nếu không có chỉ thị `ENTRYPOINT` thì Docker sẽ sử dụng câu lệnh mặc định của base image.
		+Cú pháp của chỉ thị `ENTRYPOINT` là 
			ENTRYPOINT ["executable", "param1", "param2"]




	*Sự khác nhau giữa CMD và ENTRYPOINT là:
		+`CMD` được sử dụng để chỉ định lệnh mặc định khi container được khởi động nhưng nếu có nhiều hơn 1 `CMD` thì `CMD` cuối cùng sẽ được sử dụng. Còn với `ENTRYPOINT` thì nếu có nhiều hơn 1 `ENTRYPOINT` thì tất cả cửa sổ lệnh sẽ được thêm vào cuối chỉ thị `ENTRYPOINT` đầu tiên và nếu có `CMD` thì nó sẽ được bổ sung vào cuối chỉ thị `ENTRYPOINT`
		+1 điểm khác nhau nữa là: `CMD` chỉ định cho lệnh được chạy khi không có tham số được truyền vào từ command line, trong khi `ENTRYPOINT` cho phép liên kết các tham số được truyền vào từ command line để các tham số đó trở thành phần của lệnh. 
