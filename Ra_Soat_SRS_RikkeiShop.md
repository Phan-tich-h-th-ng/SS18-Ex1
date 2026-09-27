# BÀI TẬP: RÀ SOÁT TỔNG HỢP BẢN THẢO SRS RIKKEISHOP

## Bước 1: Xác định đúng vị trí IEEE 830 cho toàn bộ nội dung/sơ đồ

| Nội dung | Vị trí đề xuất | Đúng/Sai — vị trí đúng nếu sai |
| :--- | :--- | :--- |
| Mục A (định nghĩa "Giỏ hàng") | 3.2 Functional Requirements | Sai — đúng là **1.3 Definitions, acronyms, and abbreviations** (thuộc Chương 1: Introduction) |
| Mục B (3 yêu cầu chức năng) | 3.2 Functional Requirements | Đúng |
| Danh sách Actor/Use Case tổng thể | **2.2 Product functions** (thuộc Chương 2: Overall Description) | — |
| Sơ đồ Sequence áp mã giảm giá (minh họa REQ-02) | **3.2 Functional Requirements** (Đặt ngay dưới phần mô tả chi tiết của yêu cầu REQ-02 để minh họa luồng tương tác giữa Khách hàng, RikkeiShop App và PromoService) | — |

## Bước 2: Chuẩn hóa các yêu cầu chức năng theo đặc tính vàng

| Mã | Đặc tính vàng bị vi phạm | Viết lại đạt chuẩn |
| :--- | :--- | :--- |
| REQ-02 | **Complete (Đầy đủ)**: Thiếu các trường hợp ngoại lệ (Alternative flows/Exceptions). Cụ thể theo Sequence Diagram, hệ thống cần xử lý nhánh khi `PromoService` trả về kết quả mã không hợp lệ. | Khi Khách hàng nhập mã giảm giá, RikkeiShop App gửi yêu cầu xác thực tới PromoService. <br>- Nếu hợp lệ: App trừ số tiền giảm tương ứng (dựa trên kết quả PromoService trả về) vào tổng hóa đơn. <br>- Nếu không hợp lệ: App từ chối áp dụng và hiển thị thông báo lỗi (ví dụ: "Mã sai hoặc hết hạn") cho Khách hàng. |
| REQ-03 | **Verifiable (Có thể kiểm chứng)**: Vi phạm do sử dụng các từ ngữ định tính, cảm tính ("nhanh chóng", "ổn định") khiến cho việc đo lường, nghiệm thu và test không thể thực hiện một cách khách quan. *(Lưu ý thêm: Đây thực chất là yêu cầu phi chức năng - Performance/Reliability Requirement, nên được chuyển sang mục tương ứng như 3.X thay vì để ở Functional Requirements).* | Hệ thống phải hoàn thành việc gửi yêu cầu thanh toán tới cổng thanh toán và nhận phản hồi trong thời gian tối đa là **3 giây** kể từ khi khách hàng nhấn nút xác nhận, với tỷ lệ giao dịch xử lý thành công không bị lỗi hệ thống đạt **99.9%**. |
