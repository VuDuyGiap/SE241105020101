1. Single Responsibility Principle (SRP)
* Ý nghĩa:
* Nguyên tắc này nhấn mạnh rằng mỗi lớp hoặc module chỉ nên thực hiện một nhiệm vụ duy nhất. Điều này đảm bảo mỗi lớp có một lý do duy nhất để thay đổi.

* Ứng dụng trong Bank Statement Analyzer:

* BankTransaction: Lưu trữ thông tin chi tiết của một giao dịch (ngày, số tiền, mô tả).
* TransactionParser: Đảm nhận việc phân tích dữ liệu từ file CSV để tạo danh sách các BankTransaction.
* TransactionAnalyzer: Phân tích danh sách giao dịch, thực hiện các phép tính như tổng số tiền giao dịch, đếm giao dịch theo tháng.
* Lợi ích:
* Việc chia nhỏ trách nhiệm giúp dễ bảo trì, mở rộng và kiểm thử từng thành phần độc lập. Mỗi lớp chỉ cần tập trung thực hiện tốt nhiệm vụ của mình.

2. Cohesion (Độ gắn kết)
* Ý nghĩa:
* Cohesion đo lường mức độ các phần bên trong một lớp/module hỗ trợ nhau để thực hiện một nhiệm vụ chung.

* Cohesion cao: Các thành phần trong lớp tập trung vào một nhiệm vụ cụ thể.
* Cohesion thấp: Lớp chứa nhiều chức năng không liên quan, dẫn đến khó quản lý.
* Ứng dụng trong Bank Statement Analyzer:

* BankTransaction: Tất cả thuộc tính (date, amount, description) và phương thức đều phục vụ quản lý thông tin của một giao dịch duy nhất.
* TransactionParser: Chỉ tập trung vào việc đọc và phân tích file, không xử lý logic khác.
* TransactionAnalyzer: Chỉ thực hiện các phép toán phân tích trên danh sách giao dịch, đảm bảo tập trung vào nhiệm vụ của mình.
* Lợi ích:
* Mã nguồn trở nên rõ ràng hơn, dễ bảo trì và giảm thiểu lỗi do các nhiệm vụ không liên quan gây ra.

3. Coupling (Độ kết nối)
* Ý nghĩa:
* Coupling mô tả mức độ phụ thuộc giữa các module/lớp trong hệ thống.

* Coupling thấp: Các thành phần độc lập, dễ thay đổi và mở rộng.
* Coupling cao: Các thành phần phụ thuộc chặt chẽ vào nhau, gây khó khăn khi chỉnh sửa hoặc thay thế.
* Ứng dụng trong Bank Statement Analyzer:

* Giảm phụ thuộc giữa các lớp:
* TransactionParser chỉ tạo ra danh sách BankTransaction mà không biết TransactionAnalyzer xử lý danh sách đó như thế nào.
* TransactionAnalyzer chỉ làm việc với danh sách giao dịch, không cần biết chúng được tạo ra bởi TransactionParser.
* Sử dụng đối tượng thay vì chi tiết cụ thể:
* Các lớp giao tiếp thông qua danh sách BankTransaction, không trực tiếp sử dụng các thuộc tính cụ thể của lớp khác.
* Lợi ích:
* Sự thay đổi trong một thành phần sẽ không ảnh hưởng đến các thành phần khác. Điều này giúp hệ thống linh hoạt và dễ mở rộng.

* Lợi ích chung của thiết kế này:
* Dễ bảo trì:
* Các thay đổi ở một lớp không gây ảnh hưởng đến toàn bộ hệ thống.
* Dễ mở rộng:
* Có thể thêm các tính năng mới như hỗ trợ file JSON hoặc Excel mà không làm thay đổi các chức năng hiện tại.
* Dễ kiểm thử:
* Kiểm thử từng lớp đơn lẻ dễ dàng hơn vì các trách nhiệm được phân tách rõ ràng.
* Biểu đồ UML minh họa
* Class:
* Class:
*  ![Diagram](https://www.planttext.com/?text=PP71IWCn48Rl2_iESsoXz07QWzMAHn5Q1OzfEhk9ficIIP3w2Ztr89wbLmL1J-vnnVVODt4s2XPxosHcll-VcGa5uKDScJnBhpmRNH9wY9LnOabGQ8FZFBCk87XTgZ22C_w2IhKVEmsoUOFFRLjlh89b-_5aIvZEhXXo8JnXweP8ch_dNbWICcXdKyupLHVGwu8kJr5A92gYEUf3K6YXTutKppE0qTIZOFqJOM_tCE0MDoW3ZRkQVODpDkAIhQs6yFNQrZiMaCh1ggqVDPHQE7PRRwHA-6ChpFeU8VonwT3rRvK_b6jUUFhGrW-s730aSj-YURPg0CFXC2cSQggCM8Fe6AG9F58qoJeQtbFltFrCEbFk3j1xvs75sn0b7igfvZqfy8mcpVFl0DtIcMkNkkYEwgeyct34D_u6)
* Use Case:
*  ![Diagram](https://www.planttext.com/?text=ZP5DYy9038RlXVw775lM_e5X4R_mj0iBYlSu7TV1QKOcwK75_-xK-j7L5Rm4Cidxv4rcm891wigbYNR832EapJmWCMgndk2G9W05b2X6mIJ6DiVAroGAIbyltUMjDAo3tJOo1JC9bdxJv9WcLtG7-uE1JMZX7x1jil5iaQsiYrEcCUOAlYpBvuET_YlWaD3jzdUaHgTh5-tElQ3BvDx9ByXvTva8QFRhr7cq-_OawtTGFQYQLWMM93_7Y-td2nH5_-da2dGmqJh_4Tms_5-2RJbg1eRA-A4d)
* Activity:
* ![Diagram](https://www.planttext.com/?text=LT2_JiCm40RmtPBVuLFt3gHR1bG9X1WH48dL99S_mh6BVHagnCJ0m4iWiI4GUoF4a2Vnc-2qKTKkjZxR-jtvbfwLuwxLKgYShKFcoKdXA6TbAasuMNkc5azI09sdN7d2B5jfgmfSD9fcK1xPsSbuRomJD9KCMuvdAMx3vgE17ZuDolWOHUX_e9lGltP7u9LoSJlmahtdcggUm2J5NUY_e_TxA86TDTMsm15wtlYLLcjSa-yq-qbUxELxospR7Rr8SHcn5mEkG_-6Xx3vOpnsiV_8Z_stmxj1FNoPMefdAQGO9uNvwUxpSS5y6v8n95E8nPPaYZZVVm00)
* Giải thích cách tác giả sử dụng để giải quyết các vấn đề về: SRP, cohesion, coupling:
1 Single Responsibility Principle (SRP)
* SRP là nguyên tắc cho rằng mỗi lớp nên chỉ có một lý do để thay đổi, hay nói cách khác, mỗi lớp nên chỉ đảm nhận một trách nhiệm riêng.
* Trong mã của chúng ta, SRP đã được áp dụng thông qua việc chia chương trình thành ba lớp khác nhau:
* BankTransaction: Chịu trách nhiệm lưu trữ thông tin về một giao dịch (ngày, số tiền, mô tả).
* TransactionParser: Chịu trách nhiệm đọc và phân tích dữ liệu từ file CSV để tạo ra danh sách các BankTransaction. Lớp này chỉ tập trung vào việc xử lý các file đầu vào và không chứa logic ứng dụng khác.
* TransactionAnalyzer: Chịu trách nhiệm thực hiện các phép toán phân tích trên danh sách giao dịch, như tính tổng số tiền giao dịch và đếm số lượng giao dịch trong một tháng nhất định.
* Bằng cách tách biệt các chức năng này thành các lớp riêng biệt, tác giả đã đảm bảo rằng mỗi lớp chỉ có một trách nhiệm duy nhất, giúp tăng cường khả năng bảo trì và mở rộng trong tương lai.
2 Cohesion
* Cohesion đề cập đến mức độ mà các phần phức tạp của một lớp hoặc module tương tác với nhau để thực hiện một công việc duy nhất. Trong thiết kế của chúng ta, mỗi lớp đều có high cohesion:
* BankTransaction: Tất cả các phương thức và thuộc tính trong lớp này đều liên quan đến một giao dịch ngân hàng, như ngày, số tiền, và mô tả. Điều này làm cho lớp có mức độ tập trung cao và dễ hiểu.
* TransactionParser: Lớp này tập trung hoàn toàn vào việc phân tích dữ liệu từ file, không chứa bất kỳ logic nào liên quan đến việc phân tích giao dịch. Tất cả các phương thức đều liên quan đến hoạt động đọc và phân tích file.
* TransactionAnalyzer: Tương tự, lớp này chỉ xử lý các phép toán phân tích dữ liệu giao dịch. Mọi phương thức ở đây đều hướng tới việc tính toán và phân tích kết quả.
* Tất cả các lớp đều có mục tiêu rõ ràng và giữ cho các chức năng của nó liên kết chặt chẽ, do đó đạt được sự gắn kết cao.

3 Coupling
* Coupling mô tả mức độ phụ thuộc giữa các lớp trong một hệ thống. Trong thiết kế này, tốc độ thấp về coupling đã được đảm bảo:
* Các lớp trong chương trình tương tác với nhau thông qua các đối tượng chứ không phải thông qua các thuộc tính trực tiếp.
* Ví dụ:
* TransactionParser tạo ra danh sách các BankTransaction, nhưng không biết gì về cách mà TransactionAnalyzer sử dụng chúng.
* TransactionAnalyzer nhận vào danh sách các giao dịch mà không cần biết lớp TransactionParser đã tạo ra danh sách này như thế nào.
* Điều này có nghĩa là nếu cần thay đổi logic trong lớp TransactionParser hoặc TransactionAnalyzer, điều đó sẽ không ảnh hưởng đến các lớp khác. Sự giảm thiểu coupling này giúp cho hệ thống dễ dàng bảo trì và mở rộng.
