# 1. Project guidelines 
## 1.1 Project structure 
Các dự án mới nên theo cấu trúc dự án : Android Gradle project structure [Android Gradle plugin user guide](http://tools.android.com/tech-docs/new-build-system/user-guide#TOC-Project-Structure).
## 1.2 File naming(Quy tắc đặt tên trong project).
### 1.2.1 Class files 
Tên Class được viết giống như [UpperCamelCase](http://en.wikipedia.org/wiki/CamelCase) - Các chữ cái sẽ được viết hoa giống như bướu của lạc đà .

For example: `SignInActivity`, `SignInFragment`, `ImageUploaderService`, `ChangePasswordDialog`.
### 1.2.2 Resources files
* Tất cả tên resoures phần lớn đặt theo convention sau.
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
VD : activity_main, fragment_movie, view_menu, item_article, layout_action_bar, layout_dialog,include_header...v.v.

| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Partial layout   | ---                    | `partial_stats_bar.xml`       |

#### 1.2.2.2 IDS of Views
```java
<WHAT>_<WHERE>_<DESCRIPTION>
```
Trong đó (What) là tên View class, (Where) là vị trí của view.
VD: tablayout_main, image_menu_profile, text_movie_title,btn_login,layout_content

| Element            | Prefix            |
| -----------------  | ----------------- |
| `TextView`           | `text_`             |
| `ImageView`          | `image_`            |
| `Button`             | `button_`           |
| `Menu`               | `menu_`             |

#### 1.2.2.3 Strings files
* Strings convention .

Nếu strings này sử dụng ở màn cụ thể và duy nhất, ta chỉ định (Where) cho string đó 
```java
<WHERE>_<DESCRIPTION>
```
hoặc nếu strings đc sử dụng toàn app thì dùng 
```java
all_<DESCRIPTION>
```
VD : article_title, error_message, all_ok, all_close

| Prefix             | Description                           |
| -----------------  | --------------------------------------|
| `error_`             | An error message                      |
| `msg_`               | A regular information message         |
| `title_`             | A title, i.e. a dialog title          |
| `action_`            | An action such as "Save" or "Create"  |


#### 1.2.2.4 Drawables files
* Drawables convention 
Tùy từng trường hợp và tùy theo  yêu cầu
```java
<What>_<DESCRIPTION>_<WHERE>_<SIZE>
```
VD: ic_back_home_34dp,ic_back_blue,bg_main,
```java
<What>_<DESCRIPTION>_all
```
VD: ic_back_default,avatar_default,bg_main_default,
 
| Asset Type   | Prefix            |		Example               |
|--------------| ------------------|-----------------------------|
| Action bar   | `ab_`             | `ab_stacked.9.png`          |
| Button       | `btn_`	            | `btn_send_pressed.9.png`    |
| Dialog       | `dialog_`         | `dialog_top.9.png`          |
| Divider      | `divider_`        | `divider_horizontal.9.png`  |
| Icon         | `ic_`	            | `ic_star.png`               |
| Menu         | `menu_	`           | `menu_submenu_bg.9.png`     |
| Notification | `notification_`	| `notification_bg.9.png`     |
| Tabs         | `tab_`            | `tab_pressed.9.png`         |
 
Naming conventions for icons (taken from [Android iconography guidelines](http://developer.android.com/design/style/iconography.html)):

| Asset Type                      | Prefix             | Example                      |
| --------------------------------| ----------------   | ---------------------------- |
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

Naming conventions for selector states:

| State	       | Suffix          | Example                     |
|--------------|-----------------|-----------------------------|
| Normal       | `_normal`       | `btn_order_normal.9.png`    |
| Pressed      | `_pressed`      | `btn_order_pressed.9.png`   |
| Focused      | `_focused`      | `btn_order_focused.9.png`   |
| Disabled     | `_disabled`     | `btn_order_disabled.9.png`  |
| Selected     | `_selected`     | `btn_order_selected.9.png`  |

#### 1.2.2.5 Dimensions 
Một app android nên xác định một vài dimension cố định và có thể sử dụng lại. Thường ta hay sử dụng all cho (WHERE)
```java
<What>_all_<DESCRIPTION>_<SIZE>
```
hoặc có thể tùy chọn cho size cụ thể 
```java
<What>_<WHERE>_<DESCRIPTION>_<SIZE>
```
Trong đó <What> gồm có : width, height, size (nếu width == height) , margin, padding, elevation, keyline, textsize….
 
VD: Muốn sử dụng chung cho toàn app các các thuộc tính về chiều cáo, chiều ngang, text  size.
: text_size_32,height_48..v.vv.
Hoặc kích thước cho một số view mặc định như avatar: avartar_user_default..v.v.

###1.2.2.6 Colors files

```java
<What>_<WHERE>_<DESCRIPTION>
```
VD: text_home_title,text_error,bg_home_btn_back...vv
Hoặc một vài màu dùng chung
```java
<DESCRIPTION>
```
VD: light_green,light_grey,red,blue,black,main_color

# 2. Code guidelines

## 2.1 Java language rules
### 2.1.1 Don't ignore exceptions
- Đừng  bỏ  qua ngoại lệ - Có nghĩa là try catch những thứ mà bạn nghĩ nó có thể lỗi
```java
void setServerPort(String value) {
    try {
        serverPort = Integer.parseInt(value);
    } catch (NumberFormatException e) { }
}
```
#### Bắt ngoại lệ theo thứ tự như sau.
* Ném ngoại lệ lên cho người gọi phương thức của bạn.
```java
void setServerPort(String value) throws NumberFormatException {
    serverPort = Integer.parseInt(value);
}
```
* Ném ngoại lệ mới cho người gọi phương thứ của bạn 
```java
void setServerPort(String value) throws ConfigurationException {
    try {
        serverPort = Integer.parseInt(value);
    } catch (NumberFormatException e) {
        throw new ConfigurationException("Port " + value + " is not valid.");
    }
}
```
* Xử lý lỗi cho phù hợp và trả lại giá trị cần thiết trong catch . Dưới đây trả về mặc định serverPort = 80 khi hàm nhảy vào catch 
```java
void setServerPort(String value) {
    try {
        serverPort = Integer.parseInt(value);
    } catch (NumberFormatException e) {
        serverPort = 80;  // default port for server
    }
}
```
