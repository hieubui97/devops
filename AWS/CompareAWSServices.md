#### **COMPARE AWS SERVICES: ELASTIC BEANSTALK VS CLOUDFORMATION VS OPSWORKS VS CODEDEPLOY**

*![🎓](https://static.xx.fbcdn.net/images/emoji.php/v9/t25/1/16/1f393.png)![🎓](https://static.xx.fbcdn.net/images/emoji.php/v9/t25/1/16/1f393.png) >>> Tác giả: Nguyễn Huy Hoàng <<<*

**AWS Elastic Beanstalk**

- AWS Elastic Beanstalk giúp các nhà phát triển triển khai nhanh và quản lý các ứng dụng trên AWS Cloud dễ dàng hơn. Các nhà phát triển chỉ cần tải lên ứng dụng của họ và Elastic Beanstalk tự động xử lý các chi tiết triển khai về cung cấp dung lượng, cân bằng tải, tự động mở rộng quy mô và theo dõi tình trạng ứng dụng.
- This platform-as-a-service solution is typically for those who want to deploy and manage their applications within minutes in the AWS Cloud without worrying about the underlying infrastructure.
- Giải pháp platform-as-a-service này thường dành cho những người muốn triển khai và quản lý các ứng dụng của họ trong vòng vài phút trên AWS Cloud mà không cần lo lắng về cơ sở hạ tầng bên dưới.
- AWS Elastic Beanstalk hỗ trợ các ngôn ngữ và stack phát triển sau:

\+ Apache Tomcat cho các ứng dụng Java

\+ Apache HTTP Server cho các ứng dụng PHP

\+ Apache HTTP Server cho các ứng dụng Python

\+ Nginx hoặc Apache HTTP Server cho các ứng dụng Node.js

\+ Ứng dụng Passenger hoặc Puma cho Ruby

\+ Microsoft IIS cho các ứng dụng .NET

\+ Java SE

\+ Docker

\+ Go

- Elastic Beanstalk cũng hỗ trợ phiên bản triển khai. Nó duy trì một bản sao của các triển khai cũ hơn để nhà phát triển dễ dàng khôi phục bất kỳ thay đổi nào được thực hiện trên ứng dụng.

**AWS CloudFormation**

- AWS CloudFormation là một dịch vụ cung cấp cho các nhà phát triển và các doanh nghiệp một cách dễ dàng để tạo ra một tập hợp các resource AWS liên quan và cung cấp cho họ một cách có trật tự và dự đoán được. Điều này thường được gọi là infrastructure as code
- Sự khác biệt chính giữa CloudFormation và Elastic Beanstalk là CloudFormation xử lý nhiều hơn cơ sở hạ tầng AWS hơn là các ứng dụng.
- AWS CloudFormation giới thiệu hai khái niệm:

**Template:** một tập tin dựa trên văn bản định dạng JSON hoặc YAML mô tả tất cả các resource AWS và cấu hình bạn cần phải triển khai để chạy ứng dụng của bạn.

**Stack:** là tập hợp các resource AWS được tạo ra và quản lý như một đơn vị duy nhất khi AWS CloudFormation khởi tạo một template

- CloudFormation cũng hỗ trợ tính năng khôi phục thông qua các điều khiển phiên bản template. Khi bạn cố gắng cập nhật stack của mình nhưng việc triển khai không thành công giữa chừng, CloudFormation sẽ tự động hoàn nguyên các thay đổi về trạng thái hoạt động trước đó của chúng.
- CloudFormation hỗ trợ các môi trường ứng dụng Elastic Beanstalk. Ví dụ: điều này cho phép bạn tạo và quản lý ứng dụng được lưu trữ trên AWS Elastic Beanstalk cùng với cơ sở dữ liệu RDS để lưu trữ dữ liệu ứng dụng.
- AWS CloudFormation có thể được sử dụng để khởi động cả phần mềm Chef (Server và Client) và Puppet (Master và Client) trên các phiên bản EC2 của bạn.
- CloudFormation cũng hỗ trợ OpsWorks. Bạn có thể lập mô hình các thành phần OpsWorks (stacks, layers, instances và ứng dụng) bên trong các template CloudFormation và cung cấp chúng dưới dạng stack CloudFormation. Điều này cho phép bạn lập tài liệu, kiểm soát phiên bản và chia sẻ cấu hình OpsWorks của mình.
- AWS CodeDeploy là một phần mềm hỗ trợ được đề xuất cho CloudFormation để quản lý các bản cập nhật và triển khai ứng dụng.

**AWS OpsWorks**

- AWS OpsWorks là một dịch vụ quản lý cấu hình cung cấp các phiên bản Chef và Puppet được quản lý . OpsWorks cho phép bạn sử dụng Chef và Puppet để tự động hóa cách máy chủ được định cấu hình, triển khai và quản lý trên các phiên bản EC2 hoặc môi trường máy tính tại chỗ của bạn.
- OpsWorks cung cấp ba dịch vụ:

\+ Chef Automate

\+ Puppet Enterprise

\+ OpsWorks Stacks

- OpsWorks với Puppet Enterprise cho phép bạn sử dụng Puppet để tự động hóa cách các node được định cấu hình, triển khai và quản lý, cho dù chúng là phiên bản EC2 hay thiết bị tại chỗ.
- OpsWorks với Chef Automate cho phép bạn tạo các máy chủ Chef do AWS quản lý và sử dụng Chef DK và công cụ Chef khác để quản lý chúng.
- OpsWorks Stacks cho phép bạn tạo các ngăn xếp, giúp bạn quản lý tài nguyên đám mây trong các nhóm chuyên biệt được gọi là các lớp (layers). Một lớp đại diện cho một tập hợp các instance EC2 phục vụ một mục đích cụ thể. Các lớp phụ thuộc vào Chef recipes của Chef để xử lý các tác vụ như cài đặt gói trên phiên bản, triển khai ứng dụng và chạy tập lệnh.
- So với CloudFormation, OpsWorks tập trung nhiều hơn vào điều phối và cấu hình phần mềm, đồng thời ít tập trung hơn vào việc tài nguyên AWS nào được triển khai hay triển khai như nào.

**AWS CodeDeploy**

- AWS CodeDeploy là một dịch vụ điều phối việc triển khai ứng dụng trên các phiên bản EC2 và phiên bản đang chạy tại chỗ. Nó giúp bạn nhanh chóng phát hành các tính năng mới dễ dàng hơn, giúp bạn tránh thời gian chết trong quá trình triển khai và xử lý sự phức tạp của việc cập nhật ứng dụng của bạn.
- Không giống như Elastic Beanstalk, CodeDeploy không tự động xử lý việc cung cấp capacity, mở rộng quy mô và giám sát.
- Không giống như CloudFormation và OpsWorks, CodeDeploy không xử lý cấu hình và điều phối cơ sở hạ tầng.
- AWS CodeDeploy là một dịch vụ khối xây dựng, tập trung vào việc giúp các nhà phát triển triển khai và cập nhật phần mềm trên mọi phiên bản, bao gồm phiên bản EC2 và phiên bản đang chạy tại chỗ. AWS Elastic Beanstalk và AWS OpsWorks là các giải pháp quản lý ứng dụng đầu cuối.
- Bạn tạo tệp cấu hình triển khai (deployment configuration file) để chỉ định cách triển khai tiến hành.
- CodeDeploy bổ sung tốt cho CloudFormation khi triển khai mã cho cơ sở hạ tầng được cung cấp và quản lý bằng CloudFormation.

**Summary**

- Elastic Beanstalk, CloudFormation hoặc OpsWorks đặc biệt hữu ích cho phương pháp blue-green deployment vì chúng cung cấp một cách đơn giản để sao chép ngăn xếp ứng dụng đang chạy của bạn.
- CloudFormation và OpsWorks phù hợp nhất cho các AMI
- CodeDeploy và OpsWorks phù hợp nhất để thực hiện nâng cấp ứng dụng tại chỗ. Đối với các bản nâng cấp dùng một lần, bạn có thể thiết lập môi trường nhân bản với Elastic Beanstalk, CloudFormation và OpsWorks.

**Ref**

[https://aws.amazon.com/CloudFormation/faqs/](https://l.facebook.com/l.php?u=https%3A%2F%2Faws.amazon.com%2FCloudFormation%2Ffaqs%2F%3Ffbclid%3DIwAR2G0RyCf9MiDOoBCTbBcuY_V0qtEI8jiiKtAhqd4WVoL5HrxF3hYv0Mh_4&h=AT2AKXN3ijBhVk5xSvEtK_f8A9jsMuEdoP8vrit8EHqNwRaAbRjV54sXJuCM5kMrGOduoYsuPoLcZJ3NwJakdnx-4yZTLFZTdqUmhg5Gd3jEk_x6vwMESFqI9zTiJjxmMq3uX6b3J4GI1p90ujao&__tn__=-UK-R&c[0]=AT3yWDE0ZKr4i5liOMKOSv3u1KID13zA6dat7rAHpZOM-JvcjyIH1XKTQueVBeK1sYa_aKMpH4AmQnebSfMMan5VbDYIwd3kSGM90XowJ1L_WC5_y5R8jmjDKPCoKkmsAi9NAuqC783P34YwV9WfU5wuxvlKWcmmJkFgCBkspJsjC2_cpWRH_IOYhzAca4oBr8kPN-z8a2E)

[https://aws.amazon.com/elasticbeanstalk/faqs/](https://aws.amazon.com/elasticbeanstalk/faqs/?fbclid=IwAR3GgoNw9-S3YJfSSrh6DqZriWhbsJemq_dPcPg1t34dwweMpTROIJwrcng)

[https://d1.awsstatic.com/.../overview-of-deployment...](https://d1.awsstatic.com/whitepapers/overview-of-deployment-options-on-aws.pdf?fbclid=IwAR0FpKV8wGulXgkDRtVIP2e6a1aouh6wYqaztTcTPLryC3ebdyPET1OR5cE)

[https://aws.amazon.com/.../aws-CloudFormation-supports.../](https://l.facebook.com/l.php?u=https%3A%2F%2Faws.amazon.com%2Fabout-aws%2Fwhats-new%2F2014%2F03%2F03%2Faws-CloudFormation-supports-aws-opsworks%2F%3Ffbclid%3DIwAR0zF9z3689DgPAFReNMbJuqwIG332UEFIXtWRvouIXKUY_rFNQrUEmeR7o&h=AT0SYEhv0URgzYT9_eO-otAz3vIj1RTignwhLti5Kep4a8-jHKpCZgRD1o1-0uDdngbDUT5TZVPmhfug8ARHZY3CF40kjWwJsvZU93IlHxuZjMV6rAhP9-FCc8SWeHVC2cfLVHRzZPj26K3woEJd&__tn__=-UK-R&c[0]=AT3yWDE0ZKr4i5liOMKOSv3u1KID13zA6dat7rAHpZOM-JvcjyIH1XKTQueVBeK1sYa_aKMpH4AmQnebSfMMan5VbDYIwd3kSGM90XowJ1L_WC5_y5R8jmjDKPCoKkmsAi9NAuqC783P34YwV9WfU5wuxvlKWcmmJkFgCBkspJsjC2_cpWRH_IOYhzAca4oBr8kPN-z8a2E)

[https://aws.amazon.com/codedeploy/faqs/](https://aws.amazon.com/codedeploy/faqs/?fbclid=IwAR23yJDqB-qsfGFErxIK3nEYelxwE24qUOsfA7HJahQzp6VrZbskzxuqxD8)

[https://tutorialsdojo.com/elastic-beanstalk-vs.../](https://tutorialsdojo.com/elastic-beanstalk-vs-cloudformation-vs-opsworks-vs-codedeploy/?fbclid=IwAR35QnDQSItoHivaUrPSzxUScaffRKRVf2MXkcngBXJW7lsWOaly6x2scos)

[#Chiasekienthuc](https://www.facebook.com/hashtag/chiasekienthuc?__eep__=6&__gid__=819929035387216&__cft__[0]=AZUP3N1vG12nG91pZ5d8DsbgRFfcZrl1oVzclZW3493SaXko9nxwIRsz123w5KxZ9f5XqBEFEL8WTkc-hFnepXHf2_SWZDZN6eMTuZzTPD1ai8kX58NBxTcQEvPjojZ_tVMyF6QFhNq-uBc-yJxz7KmoELz-hZiAcWGPA2_H_mLGdFpmVJrkVsv7UdMXmZniWbU&__tn__=*NK-R) [#CompareAWSService](https://www.facebook.com/hashtag/compareawsservice?__eep__=6&__gid__=819929035387216&__cft__[0]=AZUP3N1vG12nG91pZ5d8DsbgRFfcZrl1oVzclZW3493SaXko9nxwIRsz123w5KxZ9f5XqBEFEL8WTkc-hFnepXHf2_SWZDZN6eMTuZzTPD1ai8kX58NBxTcQEvPjojZ_tVMyF6QFhNq-uBc-yJxz7KmoELz-hZiAcWGPA2_H_mLGdFpmVJrkVsv7UdMXmZniWbU&__tn__=*NK-R)