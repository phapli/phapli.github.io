---
layout: post
title:  "Android naming convention (Qui tắc đặt tên)"
date:   2017-02-17 23:32:17 +0700
categories: Android
---
Đây là bài viết đầu tiên cho blog cá nhân của mình. Mình muốn viết về qui tắc đặt tên biến, hàm, class... trong lập trình Android. Đây là một phần nhỏ trong các qui tắc để có được "code đẹp".

"Code đẹp" là một khái niệm trừu tượng. Tại sao phải code đẹp? chắc các bạn cũng biết về những lý do để mọi người hướng đến code đẹp. Theo mình thì có các nguyên nhân sau:
- Thứ nhất, đơn giản vì mọi người yêu cái đẹp nên muốn code mình viết ra nó cũng phải đẹp.
- Thứ hai, code đẹp thì dễ đọc, dễ hiểu. Mà như vậy thì sẽ rất có ích khi chính mình đọc lại code, hoặc code chung project với team. 
- Thứ ba, code đẹp thì ít bug, đơn giản vì chúng ta dành nhiều thời gian hơn để chú ý về logic thay vì phải dành đầu óc để đọc hiểu những dòng code cũ.

Về qui tắc đặt tên trong Android thì không có một qui tắc chung nào cả. Cũng giống như các ngôn ngữ lập trình khác, việc đặt tên biến, hàm, hay class chỉ đơn giản là bạn tự tạo ra cho mình một qui tắc để dễ nhớ, dễ đọc và cố gắng thỏa mãn các mục tiêu của "code đẹp". Nếu bạn vẫn chưa có 1 qui tắc cụ thể, hãy nghía qua các qui tắc sau đây.

## Đặt tên package
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

## Đặt tên file resource
Format chung cho resource file là:

> < WHAT >_< WHERE >_< DESCRIPTION >_< SIZE >

1. drawables:

| Asset Type   | Prefix            |		Example              |
|--------------| ------------------|-----------------------------|
| Action bar   | `ab_`             | `ab_stacked.9.png`          |
| Button       | `btn_`	           | `btn_send_pressed.9.png`    |
| Dialog       | `dialog_`         | `dialog_top.9.png`          |
| Divider      | `divider_`        | `divider_horizontal.9.png`  |
| Icon         | `ic_`	           | `ic_star.png`               |
| Menu         | `menu_	`          | `menu_submenu_bg.9.png`     |
| Notification | `notification_`   | `notification_bg.9.png`     |
| Tabs         | `tab_`            | `tab_pressed.9.png`         |



https://github.com/ribot/android-guidelines/blob/master/project_and_code_guidelines.md
https://github.com/NexMM/android-naming-conventions
https://techtalk.vn/lam-the-nao-de-dat-ten-resource-mot-cach-hieu-qua-trong-lap-trinh-android.html

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
