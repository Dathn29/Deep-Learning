# Backpropagation (Lan truyền ngược)

## 1. Giới thiệu (Introduction)
* Backpropagation (lan truyền ngược) là 1 phương pháp để tính đạo hàm
* Backprogapation là quá trình tính đạo hàm hay gradient cho hệ số của từng layer kể từ layer cuối cùng trên hàm loss
* Tính toán dựa theo quy tắc chuỗi của hàm hợp (chain rule)
![1.png](https://github.com/Dathn29/Deep-Learning/blob/master/Backpropagation/img/1.png)

## 2. Mô tả thuật toán

### 2.1. Loss function (hàm loss)

Hàm loss có dạng cross-entropy

![2.png](https://github.com/Dathn29/Deep-Learning/blob/master/Backpropagation/img/2.png)

### 2.2. Chain rule (quy tắc chuỗi)

![3.png](https://github.com/Dathn29/Deep-Learning/blob/master/Backpropagation/img/3.png)

### 2.3.	Backpropagation (Lan truyền ngược)

![5.png](https://github.com/Dathn29/Deep-Learning/blob/master/Backpropagation/img/5.png)

-	Ví dụ 1 mạng NN như trên, thuật toán lan truyền ngược (backpropation) áp dụng để tìm đạo hàm của w1, b1 dựa trên hàm loss bằng 6 công thức sau:

![6.png](https://github.com/Dathn29/Deep-Learning/blob/master/Backpropagation/img/6.png)

-	Ảnh bên dưới sẽ là ví dụ để tìm ra các công thức này

![7.png](https://github.com/Dathn29/Deep-Learning/blob/master/Backpropagation/img/7.png)

-	Bên trên là công thức tính đạo hàm của Z2 theo hàm loss, những công thức ta cũng chứng minh tương tự sử dụng chain rule
-	Thay vì sử dụng vòng lặp để tính với mạng NN có nhiều lớp ta sử dụng vector hóa sẽ nhanh hơn rất nhiều.
- Sau đây là các công thức đã được vector hóa

![8.png](https://github.com/Dathn29/Deep-Learning/blob/master/Backpropagation/img/8.png)

-	Chú ý:
	*	Một vài công thức phải dùng ma trận chuyển vị vì phép nhân trong 
python là nhân theo hàng nên phải dùng ma trận chuyển vị
	*	Hàm sum trong python thì axis=1 sẽ tính tổng theo từng cột, axis=0 sẽ tính theo dòng, keepdims để dữ cho kích thước bằng kích thước ban đầu
	*	G’ là đạo hàm của hàm kích hoạt, trong ví dụ là hàm sigmod
-	Sau khi tìm được dw1, db1 (đạo hàm của w1, b1 với hàm loss), sử dụng thuật toán gradient descent để cập nhật lại 2 tham số này
-	Rồi tiếp tục dùng truyền xuôi để tìm a2 rồi lại tiếp tục dùng lan truyền ngược, cứ lặp đi lặp lại khi hàm loss đạt giá trị đủ nhỏ.

