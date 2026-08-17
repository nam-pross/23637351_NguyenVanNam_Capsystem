# CAB SYSTEMS

## Vấn đề hiện tại là gì

>Vấn đề của bài toán là Công ty ABC hiện đang gặp nhiều hạn chế trong việc quản lý và vận hành dịch vụ đặt xe. Quy trình đặt xe và phân công tài xế còn phụ thuộc nhiều vào thao tác thủ công, khiến việc tìm tài xế phù hợp mất thời gian, khó tối ưu và dễ xảy ra sai sót. Khách hàng cũng chưa có khả năng theo dõi đầy đủ trạng thái chuyến đi, thông tin tài xế, thời gian dự kiến đến và kết quả thanh toán. Bên cạnh đó, dữ liệu khách hàng, tài xế, chuyến đi và giao dịch chưa được quản lý tập trung, gây khó khăn cho nhân viên vận hành trong việc giám sát, xử lý sự cố và lập báo cáo. 

>Hệ thống hiện tại cũng chưa đáp ứng tốt yêu cầu mở rộng khi số lượng khách hàng và tài xế tăng lên, đồng thời còn phụ thuộc vào các thành phần như thanh toán và thông báo. Đặc biệt, nhiều quy tắc nghiệp vụ quan trọng như cách tính cước, tiêu chí lựa chọn tài xế, thời gian phản hồi, chính sách hủy chuyến, xử lý thanh toán thất bại và mất kết nối vẫn chưa được xác định rõ. Vì vậy, doanh nghiệp cần xây dựng một nền tảng CAB mới có khả năng tự động hóa toàn bộ quy trình từ đặt xe, tìm và phân công tài xế, theo dõi chuyến đi, tính cước, thanh toán, thông báo đến đánh giá, đồng thời đảm bảo tính bảo mật, ổn định, khả năng mở rộng và linh hoạt để đáp ứng các nhu cầu phát triển trong tương lai.

## Stakeholder của hệ thống
| Stakeholder | Vai trò trong hệ thống |
| :--- | :--- |
| **Khách hàng (Customer)** | Đăng ký tài khoản, đặt xe, theo dõi chuyến đi, thanh toán, xem lịch sử và đánh giá tài xế. |
| **Tài xế (Driver)** | Quản lý hồ sơ, phương tiện, trạng thái hoạt động, nhận/từ chối chuyến và cập nhật tiến trình chuyến đi. |
| **Nhân viên vận hành (Operator)** | Theo dõi chuyến đang diễn ra, quản lý trạng thái tài xế, hỗ trợ xử lý sự cố và tra cứu giao dịch. |
| **Quản trị viên (Administrator)** | Quản lý người dùng, tài xế, phương tiện, phân quyền truy cập và cấu hình hệ thống cốt lõi. |
| **Ban lãnh đạo (Management)** | Theo dõi hiệu quả kinh doanh, xem báo cáo doanh thu, tỷ lệ hoàn thành/hủy chuyến để ra quyết định. |
| **Nhà cung cấp thanh toán (Payment Provider)** | Cung cấp dịch vụ thanh toán điện tử, xử lý giao dịch an toàn mà không lưu trữ dữ liệu nhạy cảm. |
| **Nhà cung cấp thông báo (Notification Provider)** | Cung cấp hạ tầng gửi Push Notification, SMS hoặc Email cho hệ thống. |
| **Bộ phận hỗ trợ khách hàng (Customer Support)** | Xử lý khiếu nại, sự cố chuyến đi, lỗi thanh toán và hỗ trợ người dùng khi cần thiết. |
| **Bộ phận tài chính / kế toán (Finance/Accounting)** | Sử dụng dữ liệu giao dịch và doanh thu để đối soát, kiểm tra tài chính doanh nghiệp. |

## 📊 Ma trận các bên liên quan (Stakeholder Matrix)

```mermaid
quadrantChart
    title Ma trận các bên liên quan (Power vs. Interest) - CAB Systems
    x-axis "Mức độ quan tâm Thấp" --> "Mức độ quan tâm Cao"
    y-axis "Quyền lực Thấp" --> "Quyền lực Cao"
    quadrant-1 "Giữ hài lòng (Keep Satisfied)"
    quadrant-2 "Quản lý chặt chẽ (Manage Closely)"
    quadrant-3 "Theo dõi tối thiểu (Monitor)"
    quadrant-4 "Cung cấp đủ thông tin (Keep Informed)"
    
    "Ban lãnh đạo": [0.80, 0.85]
    "Quản trị viên": [0.70, 0.75]
    "Phòng Tài chính": [0.35, 0.80]
    "Nhà cung cấp (Payment/Noti)": [0.25, 0.70]
    "Khách hàng": [0.90, 0.35]
    "Tài xế": [0.85, 0.30]
    "Nhân viên vận hành": [0.75, 0.40]
    "Bộ phận CSKH": [0.65, 0.25]
```

## 🏢 Các Đơn vị kinh doanh & Bộ phận (Business Units)

| Tên Business Unit / Bộ phận | Vai trò và Chức năng chính trong hệ thống |
| :--- | :--- |
| **Khối Vận hành (Operations Unit)** | • Quản lý và giám sát toàn bộ hoạt động đặt xe hằng ngày.<br>• Theo dõi trạng thái tài xế, chuyến đi đang diễn ra.<br>• Xử lý các sự cố phát sinh (hủy chuyến, tranh chấp, lỗi điều phối). |
| **Khối Kinh doanh & Phát triển (Business Development Unit)** | • Quản lý chiến lược phát triển mạng lưới khách hàng và tài xế.<br>• Đưa ra các chính sách giá cước, chương trình khuyến mãi, ưu đãi.<br>• Phân tích hiệu quả kinh doanh dựa trên báo cáo doanh thu và tỷ lệ hoàn thành chuyến. |
| **Khối Hỗ trợ Khách hàng / CSKH (Customer Support Unit)** | • Tiếp nhận và giải quyết khiếu nại, thắc mắc từ phía Khách hàng và Tài xế.<br>• Hỗ trợ xử lý các vấn đề liên quan đến thanh toán thất bại, sự cố chuyến đi. |
| **Khối Tài chính - Kế toán (Finance & Accounting Unit)** | • Đối soát giao dịch, dòng tiền giữa hệ thống, tài xế và nhà cung cấp thanh toán.<br>• Kiểm tra doanh thu, chiết khấu hoa hồng và quản lý tài chính doanh nghiệp. |
| **Khối Công nghệ & Quản trị Hệ thống (IT & Admin Unit)** | • Quản trị hệ thống lõi, cấu hình phân quyền và bảo mật dữ liệu.<br>• Quản lý thông tin tài khoản người dùng, tài xế và phương tiện.<br>• Tích hợp các bên thứ ba (Cổng thanh toán, Dịch vụ thông báo). |
