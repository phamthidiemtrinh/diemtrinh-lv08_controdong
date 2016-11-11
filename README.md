# Báo cáo học Con Trỏ Động

## 1.Biến động.
### 1.1 Khái niệm:
 - Là biến phát sinh trong quá trình chạy chương trình, không được xác định trước và không có tên biến.
 - **Ưu điểm:**
   * Có thể thay đổi kích thước, vùng nhớ và  địa chỉ của vùng nhớ được cấp phát cũng thay đổi được trông quá trình thực hiện chương trình.
   * Có thể giải phóng biến động sau khi sử dụng để tiết kiệm bộ nhớ.
 - **Nhược điểm:**  không thể truy cập tới biến động và nó không có địa chỉ nhất định . Để khác phục nhược điểm này người ta sử dụng loại biến con trỏ.

### 1.2 Cách tạo và truy nhập biến động:
- việc tạo và thu hồi( giải phóng) biến động dưa vào hàm **malloc()** và **free()** trong thư viện **stdlib.h**
- Việc truy nhập dựa vào các biến con trỏ được khai báo ở đầu chương trình dùng để lưu trữ địa chỉ biến động.

*Ví dụ:*

````````````
int *a;
a= (int*)malloc(10);
free(a);
`````````````````
Trong ví dụ này, biến con trỏ a được gán địa chỉ một khối bộ nhớ gồm 10byte và có thể lưu trữ được 10 số nguyên trong vùng nhớ này, sau đó hàm free giả giải phóng bộ nhớ của cont rỏ a.

## 2. Cấp phát và giải phóng bộ nhớ động.
*Sử dụng các hàm có sẵn trong thư viện*  **Stdlib.h** và **alloc.h**
### 2.1 Cấp phát bộ nhớ động bằng hàm malloc()
- **Cú pháp:** `void *malloc(size_t size)`
  trong đó: size là một giá trị kiểu size_t (đã được định nghĩa sẵn)
- chức năng : cấp phát một vùng nhớ có kích thước size, trả về con trỏ kiểu void chứa địa chỉ ô nhớ đầu của vùng nhớ được cấp phát. Nếu khôngđủ vùng nhớ nó sẽ trả lại giá trị null.
- nếu muốn cấp phát vùng nhớ để lưu dữ liệu xác định thì có thể ép kiểu đối với con trỏ trả về của hàm. 
 *Ví dụ:*
 ``````````
 int *p;
 p=(int*)malloc(10);
 ````````````````````
 - Có thể kiểm tra kích cỡ byte của một kiểu dữ liệu nhờ vào toán tử **Sizeof()**.nhờ đó, có thể đảm bảo đủ vùng nhớ cấp phát. Ta viết ví dụ trên lại như sau:
 ````````
 int *p;
 p= (int*)malloc(10*sizeof(int));
 ``````````
 ### 2.2 Cấp phát bộ nhớ động bằng hàm calloc()
 - **Cú pháp:** `(datatype*)calloc(n,sizeof(object));`
    trong đó: datatype là kiểu con trỏ tới kiểu dữ liệu datatype, n là số lượng object cần cấp phát bộ nhớ.
 - chức năng: cấp phát bộ nhớ động cho các kiểu dữ liệu.
 
 *Ví dụ:* cấp phát bộ nhớ cho 10 phần tử kiểu hocluc
 ```````
 hocluc 
 {
 float diem;
   char loai[10];
   }
   hocluc *sv;
   calloc(10,sizeof(hocluc));
  ````````````
 ### 2.3 Cấp phát bộ nhớ đông bằng hàm relloc()
- **Cú pháp:** `(datatype*)relloc(buf_p,newsize);
    trong đó buf_p là con trỏ trỏ tới ùng nhớ được cấp phát từ trước, newsize là kích thước mới cần cấp phát.
- chức năng: cấp phát lại bộ nhớ cho con trỏ đã được cấp phát bộ nhớ trước đó

*Ví dụ:*
`````
int *a=(int*)calloc(10*sizeof(int));
  a=(int*) relloc(*a,100);
````````````
### 2.4 Giải phóng bộ nhớ bằng hàm free();
- **Cú pháp:** ` void free(void *p);`
- chức năng : giải phóng vùng được trỏ đến bởi con trỏ p.

*ví dụ:*
````````````
int *a;
a= (int*)malloc(10);
free(a);
`````````````````


 
 
