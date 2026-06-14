# Bai_tap_2_Vietapsudung_Android_stdio

2.1.	Đề bài

Viết app sử dụng Android Studio

6.	Android manifest.xml => mô tả gì? app cần quyền để do-st: khai báo ntn? để làm gì?

7.	Vòng đời của 1 ứng dụng android. Code tự sinh sau khi tạo 1 project: có sẵn hàm oncreate: tại sao???

8.	Code: java language.

•	App cần check xem có quyền để do-st? : code ntn? Ý nghĩa?

•	Giao diện: (res/layout) mô tả bằng file XML + UI Design review

9.	Thuộc tính text, hoặc các thuộc tính khác: giá trị hardcode => lưu vào nới khác, tham chiếu tới nó:


•	Cú pháp của việc tham chiếu là gì?

•	Ưu điểm của việc tham chiếu này?


•	Os hỗ trợ auto việc lấy giá trị tham chiếu theo location, language, theme

•	Việc hỗ trợ auto này giúp app làm được điều gì?

10.	Đối tượng chứa: gộp các đối tượng con lại: cùng 1 quy luật sắp xếp để hiển thị

•	Các đối tượng con nằm kề nhau theo chiều dọc | hoặc ngang, gravity code tương tác với layout: vd hiển thị text

•	Mong muốn text hiển thị phù hợp với thiết lập location, language, theme của người dùng thì làm ntn? (tránh hardcode)

•	Event (sự kiện) người dùng tác động vào app: click vào button, click vào text,...với 1 sự kiện nào đó, muốn chạy 1 đoạn code để do-st thì laytout cần làm gì?
CODE viết như nào (2 cách)
 

2.2.	Bài làm

1.	Android manifest.xml

•	AndroidManifest.xml là file mô tả toàn bộ ứng dụng Android.

•	Khai báo:

o	Tên package của ứng dụng

o	Các Activity

o	Service

o	Broadcast Receiver

o	Content Provider

o	Quyền (Permission)

o	Phiên bản Android hỗ trợ

o	Icon, Theme của app

•	Ví dụ:
<manifest>
<uses-permission android:name="android.permission.CAMERA"/>
<application>
<activity android:name=".MainActivity">
<intent-filter>
<action
android:name="android.intent.action.MAIN"/>
<category android:name="android.intent.category.LAUNCHER"/>
</intent-filter>
</activity>
</application>
</manifest>
•	Android bảo vệ dữ liệu người dùng.
 

Muốn sử dụng:
o	Camera
o	GPS
o	Danh bạ
o	Bộ nhớ
o	Micro
Thì phải xin quyền.
•	Ví dụ
<uses-permission android:name="android.permission.CAMERA"/>
•	Ý nghĩa: Cho phép ứng dụng truy cập Camera.
2.	Vòng đời (Lifecycle) của Activity Vì:
•	Activity phải được khởi tạo trước khi chạy.
•	Android Framework tự động gọi onCreate().
3.		App cần kiểm tra quyền (Permission) Từ Android 6.0 trở lên:
•	Không chỉ khai báo trong Manifest
•	Phải xin quyền lúc chạy
-	Bước 1: Manifest
<uses-permission android:name="android.permission.CAMERA"/>
-	Bước 2: Kiểm tra quyền
if(ContextCompat.checkSelfPermission( this, Manifest.permission.CAMERA)
!= PackageManager.PERMISSION_GRANTED)
{
ActivityCompat.requestPermissions( this,
 

new String[]{
Manifest.permission.CAMERA
},
1);
}
•	Ý nghĩa
o	Checkselfpermission() : Kiểm tra đã có quyền chưa.
o	Requestpermissions() : Hiện hộp thoại xin quyền.

•	Giao diện Android Ví dụ :
<Button
android:id="@+id/btnLogin" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Đăng nhập"/>
o	UI Design : Android Studio hỗ trợ
o	Design : Kéo thả.
o	Code : Viết XML.
o	Split : Xem cả hai.
4.	Thuộc tính text, hoặc các thuộc tính khác: giá trị hardcode => lưu vào nới khác, tham chiếu tới nó:
•	Cú pháp của việc tham chiếu
o	Cú pháp chung : @loai_tai_nguyen/ten_tai_nguyen
o	Tham chiếu String : android:text="@string/hello"
o	Tham chiếu Color : android:textColor="@color/red"
o	Tham chiếu Drawable (ảnh) : android:src="@drawable/logo"
o	Tham chiếu Kích thước (Dimension) android:textSize="@dimen/text_size"
 

•	Ưu điểm của việc tham chiếu :
o	Dễ bảo trì
o	Tái sử dụng
o	Hỗ trợ đa ngôn ngữ
o	Hỗ trợ Theme
•	Os hỗ trợ auto việc lấy giá trị tham chiếu theo location, language, theme OS tự lấy theo Language, Location, Theme
Ví dụ :
o	values-en :
<string name="hello"> Hello
</string>
o	values-vi :
<string name="hello"> Xin chào
</string>
o	Code : android: text="@string/hello"
o	Người dùng đổi ngôn ngữ:
English → Hello Tiếng Việt → Xin chào
•	Việc hỗ trợ auto này giúp app làm được :
o	Hỗ trợ nhiều quốc gia
o	Hỗ trợ nhiều ngôn ngữ
o	Hỗ trợ Dark Mode
o	Không cần sửa code Java
5.	Đối tượng chứa: gộp các đối tượng con lại: cùng 1 quy luật sắp xếp để hiển thị
•	Các đối tượng con nằm kề nhau theo chiều dọc | hoặc ngang, gravity code tương tác với layout: vd hiển thị text
 

Trong Android, Layout thường dùng để sắp xếp các View con theo chiều dọc hoặc chiều ngang.
o	Sắp xếp theo chiều dọc : Các đối tượng sẽ hiển thị từ trên xuống dưới.
<LinearLayout android:layout_width="match_parent" android:layout_height="match_parent" android:orientation="vertical">
<TextView android:text="Họ tên"/>
<Button
android:text="Lưu"/>
</LinearLayout>
o	Sắp xếp theo chiều ngang : Các đối tượng sẽ hiển thị từ trái sang phải.
<LinearLayout android:layout_width="match_parent" android:layout_height="wrap_content" android:orientation="horizontal">
<Button
android:text="Có"/>
<Button
android:text="Không"/>
</LinearLayout>
o	Thuộc tính Gravity : Gravity dùng để căn chỉnh vị trí hiển thị của nội dung bên trong View hoặc Layout.
<TextView android:layout_width="match_parent" android:layout_height="wrap_content"
 

android:text="Xin chào" android:gravity="center"/>
o	Một số giá trị thường dùng:
-	Center
-	Left
-	Right
-	Top
-	Bottom
-	Center_horizontal
-	Center_vertical
•	Mong muốn text hiển thị phù hợp với thiết lập LOCATION, LANGUAGE, THEME của người dùng thì làm ntn? (tránh hardcode)
Trong Android không nên ghi trực tiếp văn bản vào mã nguồn hoặc giao diện vì sẽ gây khó khăn khi thay đổi ngôn ngữ hoặc giao diện.
o	Lưu chuỗi trong strings.xml
-	File: res/values/strings.xml
-	Nội dung:
<resources>
<string name="hello">Xin chào</string>
</resources>
Sử dụng: android:text="@string/hello" hoặc txtHello.setText(R.string.hello);
o	Hỗ trợ nhiều ngôn ngữ :
-	Tạo nhiều thư mục tài nguyên:
res/values/ res/values-vi/ res/values-en/ Ví dụ:
o	values-en/strings.xml : <string name="hello">Hello</string>
 

o	values-vi/strings.xml : <stringname="hello">Xinchào</string> Android sẽ tự động hiển thị ngôn ngữ tương ứng với thiết lập của người dùng.

•	Tạo app1 sử dụng cơ chế Dữ liệu chuẩn bị trước trong Assets
 <img width="657" height="370" alt="image" src="https://github.com/user-attachments/assets/88d2ad01-8913-4347-b45f-23f34b17c426" />


o	Tạo file dữ liệu mẫu trong thư mục Assets (nganhhoc.json)
 <img width="660" height="371" alt="image" src="https://github.com/user-attachments/assets/27794d77-329b-4ad2-b80b-abdf56e1d6da" />

o	Xây dựng lớp Model NganhHoc.java để ánh xạ dữ liệu JSON
 <img width="639" height="351" alt="image" src="https://github.com/user-attachments/assets/c7cfcf1f-7b07-4e48-b715-e3ac0a124354" />


 
o	Giao diện màn hình tra cứu ngành học khi khởi động ứng dụng

 <img width="685" height="385" alt="image" src="https://github.com/user-attachments/assets/23e033a2-5aec-4463-bd46-b43490221666" />

Code đọc dữ liệu JSON từ thư mục Assets
 <img width="694" height="390" alt="image" src="https://github.com/user-attachments/assets/df005096-7069-4657-9449-4ecada293c63" />

o	Thuật toán phân tích (Parse) dữ liệu JSON bằng JSONArray
 
<img width="786" height="442" alt="image" src="https://github.com/user-attachments/assets/e8a818c7-f3fb-4219-9f46-ec8d831a24f0" />

 
o	Thiết kế giao diện Activity chính bằng XML

o	Kết quả hiển thị danh sách ngành học sau khi xử lý dữ liệu

 	 
 <img width="351" height="781" alt="image" src="https://github.com/user-attachments/assets/f453378e-9cd9-4623-8c9e-0ab005a8ebde" />
<img width="367" height="816" alt="image" src="https://github.com/user-attachments/assets/8f672a06-7616-4570-b5ed-4d7dffde04c6" />


o	Kết quả chạy Activity About trên thiết bị Android
  
<img width="443" height="985" alt="image" src="https://github.com/user-attachments/assets/a739694a-a8e9-42b1-a3e8-2822141baf66" />

o	Kết quả chạy Activity Giải Toán và hiển thị kết quả
 
 <img width="526" height="1168" alt="image" src="https://github.com/user-attachments/assets/78bff870-277e-41ab-a275-4e086c25a062" />
n

o	Kết quả chạy Activity WebView truy cập web https://k58kmt.tdh.io.vn?masv=K225480106094
 
 <img width="560" height="1243" alt="image" src="https://github.com/user-attachments/assets/3bb77d42-551b-4f69-9295-bc030d45b760" />

