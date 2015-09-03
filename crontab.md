#Crontab
##1.Cron / crontab là gì
- Cron là một chương trình lập lịch công việc dựa trên thời gian trong các hệ điều hành linux/unix. Crontab là một file chứ bảng biểu(lịch) của các entry được chạy

##2. Quản lý crontab
- Khai báo user trong /etc/cron.allow (Đường dẫn trên Ubuntu 14.04) thì những user đó sẽ được sử dụng crontab
- Khai báo user trong /etc/cron.deny (Đường dẫn trên Ubuntu 14.04) thì những user đó sẽ không được sử dụng crontab
- Lưu ý: Nêu 2 file không được định nghĩa thì tất cả user sẽ có quyền sử dụng crontab

##3. Các câu lệnh crontab
- crontab -e : Sửa file crontab của user đang sử dụng
- crontab -r : remove file crontab đang sử dụng
- crontab -l : hiển thị file crontab
- crontab -i : hỏi trước khi làm gì (ví dụ: crontab -ir hỏi trước khi xóa)

##4.Crontab file
- Cú pháp crontab

<img src="https://domotiga.nl/attachments/download/1692/Crontab.png">

- Lưu ý:

  + Ngày được định nghĩa bằng 2 cách đó là ngày trong tháng và ngày trong tuần. Nếu cả 2 được định nghĩa trong cùng 1 entry thì nó sẽ được thực thi cả 2.
  + Nếu định nghĩa trường phút là /2 thì câu lệnh sẽ được thực thi 2 phút 1 lần /10 là 10 phút 1 lần. Nhưng tính năng này không phải hệ điều hành nào cũng hỗ trợ. (Đã test trên Ubuntu và có chạy)

##5. Ví dụ Crontab
`30 * * * * rm /home/saphi/tmp`

- Phút thứ 30 của mỗi giờ tất cả các ngày sẽ xóa các file trong thư mục /home/saphi/tmp

`* 17 * * * bash /home/saphi/backup.sh`

- Thực hiện script backup vào 5h chiều hàng ngày

`* 0 10,20,30 * * service apache2 restart`

- Restart dịch vụ apache2 vào lúc 0h các ngày 10,20,30 của mỗi tháng

##6. Tắt việc gửi email

Mặc định crontab gửi email cho người dùng thực hiện các công việc cron. Nếu điều này ko cần thiết có thể thêm dòng sau vào cuối file crontab

`>/dev/null 2>&1`

