---
layout: post
title:  "Qui tắc đặt tên (naming convention) trong Android"
date:   2017-02-17 23:32:17 +0700
categories: Android
---
Đây là bài viết đầu tiên cho blog cá nhân của mình. Mình muốn viết về qui tắc đặt tên biến, hàm, class... trong lập trình Android. Đây là một phần nhỏ trong các qui tắc để có được "code đẹp".

"Code đẹp" là một khái niệm trừu tượng. Tại sao phải code đẹp? chắc các bạn cũng biết về những lý do để mọi người hướng đến code đẹp. Theo mình thì có các nguyên nhân sau:
- Thứ nhất, đơn giản vì mọi người yêu cái đẹp nên muốn code mình viết ra nó cũng phải đẹp.
- Thứ hai, code đẹp thì dễ đọc, dễ hiểu. Mà như vậy thì sẽ rất có ích khi chính mình đọc lại code, hoặc code chung project với team. 
- Thứ ba, code đẹp thì ít bug, đơn giản vì chúng ta dành nhiều thời gian hơn để chú ý về logic thay vì phải dành đầu óc để đọc hiểu những dòng code cũ.

Về qui tắc đặt tên trong Android thì không có một qui tắc chung nào cả. Cũng giống như các ngôn ngữ lập trình khác, việc đặt tên biến, hàm, hay class chỉ đơn giản là bạn tự tạo ra cho mình một qui tắc để dễ nhớ, dễ đọc và cố gắng thỏa mãn các mục tiêu của "code đẹp". Nếu bạn vẫn chưa có 1 qui tắc cụ thể, hãy nghía qua các qui tắc sau đây.

## I. Đặt tên package
Theo kinh nghiệm cá nhân của mình thì có 2 cách đặt tên phổ biến:
1. Nhóm các file java theo từng loại. Cụ thể là activity riêng, model riêng, service riêng, Với cách này mỗi khi bạn cần một activity thì cứ đơn giản là vào package activities là được.
    <br>`com.client.app` - chỉ có class Application
    <br>`com.client.app.views` - bao gồm các activities
    <br>`com.client.app.fragments` - bao gồm các fragments
    <br>`com.client.app.webservice` - bao gồm các web services
    <br>`com.client.app.adapters` - bao gồm các adapters
    <br>`com.client.app.db` - bao gồm các classes liên quan đến db
    <br>`com.client.app.models` - bao gồm các models
    <br>`com.client.app.utils` - bao gồm các class utility
    <br>`com.client.app.widgets` - bao gồm các extended/custom views
    <br>`com.client.app.services` - bao gồm các services
    <br>`com.client.app.animation` - bao gồm các animations

2. Nhóm các file theo từng chức năng.
- Các package chung, có cấu trúc giống cách 1
    <br>`com.client.app` - chỉ có class Application
    <br>`com.client.app.webservice` - bao gồm các web services
    <br>`com.client.app.db` - bao gồm các classes liên quan đến db
    <br>`com.client.app.models` - bao gồm các models
    <br>`com.client.app.utils` - bao gồm các class utility
    <br>`com.client.app.services` - bao gồm các services
- Các package theo chức năng, ví dụ chức năng login
    <br>`com.client.app.login.views` - bao gồm activity login
    <br>`com.client.app.login.fragments` - bao gồm các fragments của màn hình login
    <br>`com.client.app.login.adapters` - bao gồm các adapters của màn hình login
    <br>`com.client.app.login.animation` - bao gồm các animations của màn hình login
    <br>`com.client.app.login.widgets` - bao gồm các extended/custom views của màn hình login

## II. Code Java
### 1. Tên class
Cách đặt tên class trong Android tuân thủ cách đặt tên class của Java, và cũng khá quen thuộc với mọi người. Đó là [UpperCamelCase](http://en.wikipedia.org/wiki/CamelCase)

vd: LoginActivity, CommonUtil, UserService, DetailAdapter ...
### 2. Tên biến trong class
Các biến toàn cục nên được đặt đầu file. Ngay sau lời gọi hàm constructor và nên tuân thủ các quy tắc sau.

* Private, non-static field được bắt đầu với __m__.
* Private, static field được bắt đầu với __s__.
* Other fields bắt đầu với một ký tự viết thường.
* Static final fields (định nghĩa) nên được viết hoa và sử dụng "__\___" ALL_CAPS_WITH_UNDERSCORES.

Example:

```java
public class MyClass {
    public static final int SOME_CONSTANT = 42;
    public int publicField;
    private static MyClass sSingleton;
    int mPackagePrivate;
    private int mPrivate;
    protected int mProtected;
}
```

## III. Đặt tên file resource
Tên resources file được viết theo format __lowercase_underscore__.

### 1. Drawable files

Qui tắc

| Asset Type   | Prefix            |		Example              |
|--------------|-------------------|-----------------------------|
| Action bar   | `ab_`             | `ab_stacked.9.png`          |
| Button       | `btn_`	           | `btn_send_pressed.9.png`    |
| Dialog       | `dialog_`         | `dialog_top.9.png`          |
| Divider      | `divider_`        | `divider_horizontal.9.png`  |
| Icon         | `ic_`	           | `ic_star.png`               |
| Menu         | `menu_	`          | `menu_submenu_bg.9.png`     |
| Notification | `notification_`   | `notification_bg.9.png`     |
| Tabs         | `tab_`            | `tab_pressed.9.png`         |

Qui tắc đặt tên cho icons

| Asset Type                      | Prefix             | Example                      |
| --------------------------------| ----------------   | ---------------------------- |
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

Qui tắc đặt tên cho các trạng thái của view.

| State	       | Suffix          | Example                     |
|--------------|-----------------|-----------------------------|
| Normal       | `_normal`       | `btn_order_normal.9.png`    |
| Pressed      | `_pressed`      | `btn_order_pressed.9.png`   |
| Focused      | `_focused`      | `btn_order_focused.9.png`   |
| Disabled     | `_disabled`     | `btn_order_disabled.9.png`  |
| Selected     | `_selected`     | `btn_order_selected.9.png`  |


#### 2. Layout files

Layout file được đặt tên theo hình thức: <WHAT>_<WHERE>

| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Partial layout   | ---                    | `partial_stats_bar.xml`       |

#### 3. Menu files

Tương tự như layout file, các file menu cũng bắt đầu bằng từ khoá chỉ ý nghĩa __menu\___

#### 4. Values files

Các file trong thư mục values thường được sử dụng dạng số nhiều (__plural__).

vd: `strings.xml`, `styles.xml`, `colors.xml`, `dimens.xml`, `attrs.xml`

Trong phần kế tiếp, mình sẽ nói nhiều hơn đến các convention khác trong Android chứ không hẳn chỉ là cách đặt tên. Hi vọng mọi người có thể cải thiện được style code của mình.