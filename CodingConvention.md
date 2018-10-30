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
* Advantages (Ưu điểm)
1. Sắp xếp vị trí resoures theo màn hình
```java
<Where> đã mô tả nơi resoure này nằm ở màn hình nào. Vì vậy ta có thể lấy các resourecs như ảnh, dimens, string ở màn hình cụ thể
```
2. Gắn kết với resoures IDs
```java 
<What> mô tả tên class nằm ở element xml, sẽ dễ dàng cho ta khi gọi findViewById() 
```
3. Tổ chức resoures tốt hơn
Browser của IDE thường sắp xếp theo thứ tự alphabe, cho nên các resoures sẽ đc sắp theo theo group ứng với (What) là (activity, fragment, dialog … ) và (Where) để biết resoures nằm ở màn nào.
4. Autocomplete hiệu quả hơn
```java
Các prefix <What> và <Where> giúp việc tìm kiếm trên browser hiệu quả hơn khi chỉ cần nhập keyword các prefix này để thu gọn kết quả danh sách tìm k
```
5. Không còn name conflict
Các resoures ở các màn hình khác nhau hoặc dùng từ khóa “all” còn không sẽ có 1 (Where) riêng biệt sẽ giúp tránh khỏi việc conflict name
6. Resouces name clean hơn
Tên resourecs được đặt 1 cách logic sẽ khiến project của chúng ta cũng clean hơn rất nhiều.
7. Tools support
Convention này đc Android Studio supports trong việc inspect code và giúp dễ dàng preview các màn hình.

#### 1.2.2.1 Layout files
* Layout convention 
```java
<WHAT>_<WHERE>.xml
```
```java
<What> là một trong các tên sau:  
```
activity : content view trong activity fragment : content view trong fragment view : custom inflated view item : layout sử dụng trong recycler view, grid view … layout : layout sử dụng trong thẻ include.
VD : activity_main, fragment_movie, view_menu, item_article, layout_action_bar

| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Partial layout   | ---                    | `partial_stats_bar.xml`       |

#### 1.2.2.2 Strings files
* Strings convention .

Nếu strings này sử dụng ở màn cụ thể và duy nhất, ta chỉ định (Where) cho string đó 
```java
WHERE>_<DESCRIPTION>
```
hoặc nếu strings đc sử dụng toàn app thì dùng 
```java
all_<DESCRIPTION>
```
VD : article_title, error_message, all_ok, all_close

#### 1.2.2.3 Drawables files
Drawables convention 
