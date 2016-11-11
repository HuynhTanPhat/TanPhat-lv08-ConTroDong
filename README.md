>#**Huỳnh Tấn Phát**
>
>###**BÁO CÁO HỌC CON TRỎ ĐỘNG**

>>[1.Khái niệm biến động](#Khái niệm biến động)  
>>[2.Cách tạo và truy nhập biến động](#Cách tạo và truy nhập biến động)  
>>[3.Cấp phát và giải phóng bộ nhớ động](#Cấp phát và giải phóng bộ nhớ động)  
>>[4.Bộ nhớ HEAP và cơ chế tạo biến động](#Bộ nhớ HEAP và cơ chế tạo biến động)  

<a name="Khái niệm biến động">
##1.Khái niệm biến động  
* Biến động là các biến được tạo ra lúc chạy chương trình, tùy nhu cầu.  
* Số biến này không được xác định từ trước.  
* Các biến động không có tên xác định mà chỉ là gán cho nó một địa chỉ xác định.  

<a name="Cách tạo và truy nhập biến động">
##2.Cách tạo và truy nhập biến động  
* Việc tạo ra biến động và xóa nó đi nhờ vào các hàm như `malloc()` và `free()` có sẵn trong thư viện stdlip.h.  
* Việc truy nhập đến các biến động nhờ các biến con trỏ, các biến con trỏ được dùng để chứa địa chỉ các biến động.  
```sh
VD:
`int *p; /* Khai báo biến con trỏ p*/
p= (int *) malloc(100);/* Tạo biến động*/`
Ðoạn chương trình trên sẽ cấp phát 100 bytes trong bộ
nhớ và gán địa chỉ khối bộ nhớ này cho p
```

<a name="Cấp phát và giải phóng bộ nhớ động">
##3.Cấp phát và giải phóng bộ nhớ động  

>>[3.1 Cấp phát bộ nhớ động bằng hàm malloc( )](#Cấp phát bộ nhớ động bằng hàm malloc)  
>>[3.2 Cấp phát bộ nhớ động bằng hàm calloc](#Cấp phát bộ nhớ động bằng hàm calloc)  
>>[3.3 Cấp phát bộ nhớ động bằng hàm relloc](#Cấp phát bộ nhớ động bằng hàm relloc)  
>>[3.4 Giải phóng bộ nhớ bằng hàm free](#Giải phóng bộ nhớ bằng hàm free)  

<a name="Cấp phát bộ nhớ động bằng hàm malloc">
##3.1 Cấp phát bộ nhớ động bằng hàm malloc  
> + **Cú pháp: `void *malloc(kiểu _dl size)`**   
> + **Chức năng:** Hàm malloc cấp phát một vùng nhớ có kích thước là size.(Size là một giá trị kiểu_dl (là một kiểu dữ liệu định sẵn trong thư viện stdlib.h).  
> + Hàm malloc trả về con trỏ kiểu void chứa địa chỉ ô nhớ đầu của vùng nhớ được cấp phát. Nếu không đủ vùng nhớ để cấp phát hàm trả về giá trị **NULL**, vì vậy phải kiểm tra giá trị trả về khi sử dụng hàm malloc.  

<a name="Cấp phát bộ nhớ động bằng hàm calloc">
##3.2 Cấp phát bộ nhớ động bằng hàm calloc  
> - **Cú pháp: `(datatype *) calloc(n, sizeof(object));`**  
> - Hàm calloc cấp phát bộ nhớ động cho các kiểu dữ liệu  
**Trong đ ó:**  
+`(datatype *)` là kiểu con trỏ trỏ tới kiểu dữ liệu datatype.  
+n là số lượng object thuộc kiểu datatype cần cấp phát bộ nhớ.  
+`Datatype` có thể là kiểu dữ liệu cơ sở hoặc kiểu dữ liệu mới.  

<a name="Cấp phát bộ nhớ động bằng hàm relloc">
##3.3 Cấp phát bộ nhớ động bằng hàm relloc  
>**-Cú pháp: `(datatype *) realloc(buf _p, newsize);`**  
>-Hàm có chức năng cấp phát lại bộ nhớ  
**Trong đó:**  
+`buf_p` là con trỏ đang trỏ đến vùng ô nhớ đã được cấp phát từ trước.  
+`newsize` là kích thước mới cần cấp phát, có thể lớn hoặc nhỏ hơn.  

<a name="Giải phóng bộ nhớ bằng hàm free">
##3.4 Giải phóng bộ nhớ bằng hàm free
>**-Cú pháp: `void free( void *prt)`**  
+Hàm free giải phóng vùng nhớ được trỏ đến bởi con trỏ ptr.  
+Nếu con trỏ ptr = NULL thì hàm free không làm gì cả.  

<a name="Bộ nhớ HEAP và cơ chế tạo biến động">
##4.Bộ nhớ HEAP và cơ chế tạo biến động
* Cơ chế biến động do malloc tạo ra được C xếp vào một vùng ô nhớ tự do sắp xếp theo kiểu xếp chồng đgl HEAP.  
* C quản lý HEAP thông qua con trỏ của HEAP là HEAPPTR.  
* Mỗi lần gọi malloc(), con trỏ của HEAP được dịch chuyển về phía đỉnh của vùng ô nhớ tự do một số byte tương ứng với kích thước của biến động mới tạo ra.  
* Mỗi khi giải phóng bộ nhớ biến động, bộ nhớ biến động được thu hồi.  
                 **************_____________________________________the end__________________________________**************

