##### **14 lệnh hay dùng của Amazon AWS EC2 CLI Command (AWS CLI)**

*>>>Tác giả: Nguyen Van Duong<<<*

Nối tiếp bài trước tổng hợp những lệnh hay gặp của aws cli với s3, sns .., hôm nay minh xin giới thiệu 15 lệnh hay gặp của EC2. Ở bài trước mình đã hướng dẫn cài đặt và config aws cli rồi, nên bàu này mình không hướng dẫn lại nữa.

EC2 là gì ?

Amazon EC2 cung cấp các ứng dụng máy tính ảo hoá có thể mở rộng về khả năng xử lý cùng các thành phần phần cứng ảo như bộ nhớ máy tính (ram), vi xử lý, linh hoạt trong việc lựa chọn các phân vùng lưu trữ dữ liệu ở các nền tảng khác nhau và sự an toàn trong quản lý dịch vụ bởi kiến trúc ảo hoá đám mây mạnh mẽ của AWS. Hay nói gắn gọn nó chính là một vps để chúng ta cài source code lên đó.

Tham khảo: [https://viblo.asia/p/tim-hieu-ve-amazon-ec2-maGK7jRe5j2](https://l.facebook.com/l.php?u=https%3A%2F%2Fviblo.asia%2Fp%2Ftim-hieu-ve-amazon-ec2-maGK7jRe5j2%3Ffbclid%3DIwAR0lE0nujwJcuZD-J8-NoVZXpiDzdh_U53JW3lgF1S9AZu59rYjvPhNnnF0&h=AT3H0Yr41y8n0q9L--V9A6Ncwr2k7_qJESCwhNRm6Assfz7geWUge1xm1nbC2YSR1yQCoLjRHHDdBkdFpfKWpu6lALNCkSYsEcFKukBpEYmoKjeb7l2gY18eGJRMMaVfbi7eZV3MHl-n3cG1Mrfg&__tn__=-UK-y-R&c[0]=AT0XT9gkb675MyA65JMWdn8SkTJmHbd2mCbrubiiHxqgTocaT4-_zMZUPEJDFhWFg01OrkwFkSX6TO4JTUjtnLQUV1_ZgfXEljaYZkpuHco_ahHQME9ooJ8P4mhcG_jOKglyoQO3IgqD29KH9xBflDEHwg70K0K5Si-e_7ByrSBpkBjolDrLyWFw5WPCNtG9yn_KTK4lUHlHA7L1UxOvJLxyTVsndaQ8pjTeU2wJGCxTouTSNdJnUnjz)

**Command**

***1.Xem status của 1 Instance\***

aws ec2 describe-instances

aws ec2 describe-instances --filter Name=tag:Name,Values=dev-server # filter

***2.Start 1 instance\***

aws ec2 start-instances --instance-ids i-dddddd70

aws ec2 start-instances --instance-ids i-5c8282ed i-44a44ac3 # start nhiều instance cùng lúc

i-dddddd70 chính là instance id, bạn có thể lấy nó ở lệnh 1.

***3.Stop 1 instance\***

aws ec2 stop-instances --instance-ids i-5c8282ed

aws ec2 stop-instances --instance-ids i-5c8282ed i-e5888e46 # stop nhiều instance

aws ec2 stop-instances --force --instance-ids i-dddddd70 # force stop, not cache filesystem

***4.Xoá instance\***

aws ec2 terminate-instances --instance-ids i-44a44ac3

***5.Thêm tên hoặc tag cho instance\***

aws ec2 create-tags --resources i-dddddd70 --tags Key=Department,Value=Finance

***6.Khởi chạy một instance mới\***

aws ec2 run-instances --image-id ami-22111148 --count 1 --instance-type t1.micro --key-name stage-key --security-groups my-aws-security-group

Lệnh này sẽ tạo một instance mới đựa vào một instance đã có sẵn và khởi chạy chúng.

***7.Restart instance\***

aws ec2 reboot-instances --instance-ids i-dddddd70

***8.Thay đổi Instance Type\***

***8.1.Lấy thông tin instance:\***

aws ec2 describe-instances

"InstanceId": "i-44a44ac3",

..

"InstanceType": "t1.micro",

***8.2.Stop instance and change type\***

aws ec2 stop-instances --instance-ids i-44a44ac3

aws ec2 modify-instance-attribute --instance-id i-44a44ac3 --instance-type "{\"Value\": \"m1.small\"}"

thay đổi từ t1.micro lên m1.small

***9.Tạo một image\***

aws ec2 create-image --instance-id i-44a44ac3 --name "Dev AMI" --description "AMI for development server"

{

"ImageId": "ami-2d574747"

}

**Kiểm tra:**

aws ec2 describe-images --image-ids ami-2d574747

{

"Images": [

{

"VirtualizationType": "paravirtual",

"Name": "Dev AMI",

"Hypervisor": "xen",

...

}

***10.Xoá image\***

aws ec2 deregister-image --image-id ami-2d574747

aws ec2 delete-snapshot --snapshot-id snap-4e665454

***11.Bật Instance Termination Protection\***

Mặc định khi chạy lệnh xoá instance aws sẽ khoá ngay, khi bật bảo vệ không cho xoá thì sẽ không bị xoá khi lỡ tay:

aws ec2 modify-instance-attribute --instance-id i-44a44ac3 --disable-api-termination

***Tắt đi bằng lệnh:\***

aws ec2 modify-instance-attribute --instance-id i-44a44ac3 --no-disable-api-termination

***12.Xem log xem log system của 1 instance chạy lệnh sau:\***

aws ec2 get-console-output --instance-id i-44a44ac3

***13.Enable Cloudwatch Monitoring for an Instance\***

aws ec2 monitor-instances --instance-ids i-44a44ac3

{

"InstanceMonitorings": [

{

"InstanceId": "i-44a44ac3",

"Monitoring": {

"State": "enabled"

}

}

]

}

để disable:

aws ec2 unmonitor-instances --instance-ids i-44a44ac3

{

"InstanceMonitorings": [

{

"InstanceId": "i-44a44ac3",

"Monitoring": {

"State": "disabled"

}

}

]

}

***14.AWS EC2 Key Pairs\***

Xem key pairs:

aws ec2 describe-key-pairs

{

"KeyPairs": [

{

"KeyName": "prod-key",

"KeyFingerprint": "61:7c:f1:13:53:b0:3a:01:dd:dd:6c:90"

},

{

"KeyName": "stage-key",

"KeyFingerprint": "41:6c:d1:23:a3:c0:2a:0a:dc:db:60:4c"

}

]

}

Tạo:

aws ec2 create-key-pair --key-name dev-servers

{

"KeyName": "dev-servers",

"KeyMaterial": "-----BEGIN RSA PRIVATE KEY-----\n

dYXbKYMRlI59J5XKyPgC/67GL8\nXg

....

n-----END RSA PRIVATE KEY-----",

"KeyFingerprint": "3d:c2:c8:7f:d2:ee:1d:66"

}

để xoá:

aws ec2 delete-key-pair --key-name dev-servers

Tham khảo:

[https://docs.aws.amazon.com/.../use.../cli-services-ec2.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-services-ec2.html?fbclid=IwAR0dnRyGgHsP8vNy0P7Ji0rUt3YhI0gHVDHuGsmuN2PpeEA4wGrkU_sG6-o)

[https://www.thegeekstuff.com/2016/04/aws-ec2-cli-example14](https://www.thegeekstuff.com/2016/04/aws-ec2-cli-example14?fbclid=IwAR3YuLRGnq_JRIy7n28UpYAR-GNQqA1Y8fPfYnaUpHEfGivLWBSIBtj0Ago)

[#Devops](https://www.facebook.com/hashtag/devops?__eep__=6&__cft__[0]=AZUGHpgipOnWTTjT0YhV8T2RgARXqSmoOVhjzv0tICL7eHpiwKKfO23PYrv8csxRUfXzSmZMsgFhVSrmVydr6R036-LOmU_PnX4Bw9unnFZ5m-o02J6t2rYU2dGl3JSzrj0xzeE-P3NCjedjdXb714AxeMJRw7cGJN38wukCEz7mESI-osFlaFRyYNVo16wdzo9oZzTddLwSimDeIn6u9rkqhotEKIZT0hvG3vUz5ERhoQ&__tn__=*NK-y-R) [#Chiasekienthuc](https://www.facebook.com/hashtag/chiasekienthuc?__eep__=6&__cft__[0]=AZUGHpgipOnWTTjT0YhV8T2RgARXqSmoOVhjzv0tICL7eHpiwKKfO23PYrv8csxRUfXzSmZMsgFhVSrmVydr6R036-LOmU_PnX4Bw9unnFZ5m-o02J6t2rYU2dGl3JSzrj0xzeE-P3NCjedjdXb714AxeMJRw7cGJN38wukCEz7mESI-osFlaFRyYNVo16wdzo9oZzTddLwSimDeIn6u9rkqhotEKIZT0hvG3vUz5ERhoQ&__tn__=*NK-y-R)