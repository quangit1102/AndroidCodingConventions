# 1. Project guidelines 
## 1.1 Project structure 
Các dự án mới nên theo cấu trúc dự án : Android Gradle project structure [Android Gradle plugin user guide](http://tools.android.com/tech-docs/new-build-system/user-guide#TOC-Project-Structure).
## 1.2 File naming(Quy tắc đặt tên trong project).
### 1.2.1 Class files 
Tên Class được viết giống như [UpperCamelCase](http://en.wikipedia.org/wiki/CamelCase) - Các chữ cái sẽ được viết hoa giống như bướu của lạc đà .

For example: `SignInActivity`, `SignInFragment`, `ImageUploaderService`, `ChangePasswordDialog`.
### 1.2.2 Resources files
* Tất cả tên resoures đặt theo convention sau.
```java
<WHAT>_<WHERE>_<DESCRIPTION>_<SIZE> 
```
```java
<WHAT> Chỉ ra nguồn resouce này đại diện cho cái gì, thường là tên của View Class để giới hạn sự lựa chọn của resoure này. VD : MainActivity → activity , BaseFragment → fragment ...
 ```
```java
<WHERE> Mô tả nơi resouce này nằm ở đâu trong app. Các resourec sử dụng ở nhiều màn thường đặt là all, còn các phần cụ thể khác sẽ phải chỉ cụ thể vị trị của phần đó VD : MainActivity → main, MovieFragment → movie ... 
```
```java
<DESCRIPTION> Mô tả thuộc tính của resouce trên màn hình VD : title, sub_title ...
```
```java
<SIZE> (optional) Chỉ rõ kích thước của resoure này, thường dành cho và dimensions VD : 24dp, small, big …
```
* Advantages(Ưu điểm)
1. Sắp xếp vị trí resoures theo màn hình
```java
<Where> đã mô tả nơi resoure này nằm ở màn hình nào. Vì vậy ta có thể lấy các resourecs như ảnh, dimens, string ở màn hình cụ thể
```
2. Gắn kết với resoures IDs
```java 
<What> mô tả tên class nằm ở element xml, sẽ dễ dàng cho ta khi gọi findViewById() 
```
3. Tổ chức resoures tốt hơn
Browser của IDE thường sắp xếp theo thứ tự alphabe, cho nên các resoures sẽ đc sắp theo theo group ứng với (What) (activity, fragment, dialog … ) và (Where) để biết resoures nằm ở màn nào.
