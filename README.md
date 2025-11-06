# Phân Tích Dữ Liệu Đặt Vé Xem Phim Trực Tuyến (2019–2022)

##  Giới thiệu

Dự án này phân tích **hành vi đặt vé xem phim trực tuyến** của khách hàng trong giai đoạn **2019–2022**.  
Với vai trò là **Nhà phân tích dữ liệu** trong bộ phận phát triển sản phẩm của **Kompany**, mục tiêu của dự án là cung cấp các **thông tin chi tiết (insights)** về hành vi người dùng và **đề xuất chiến lược cải thiện** để tăng trưởng doanh số cũng như giữ chân khách hàng.



## Mục tiêu

- Hiểu rõ hành vi của khách hàng khi đặt vé xem phim online trong 4 năm gần đây.  
- Đưa ra **đề xuất cụ thể** nhằm nâng cao trải nghiệm và tỷ lệ đặt vé thành công.



## Xác định vấn đề

**Đối tượng phân tích (Who):**  
- **Nội bộ:** : Các bộ phận liên quan trực tiếp đến quá trình đặt vé của người sử dụng(Dịch vụ khách hàng,bán hàng).
- **Bên ngoài:** : Khách hàng là ai?
                  •	Location: ở việt nam/ nước ngoài,khu vực(Thành thị,nông thôn,tỉnh thành).
                  •	Profile Level của khách hàng,khách hàng mới,khách hàng cũ,khách hàng có xác thực tài khoản.
                  •	Demographic: Gới tính,độ tuổi,trình trạng hôn nhân,học vấn(nếu có)

**Phân tích cái gì (What):**  
- Hành vi đặt vé xem phim thông qua **website** và **ứng dụng di động (app)**.  

**Khi nào (When):**  
- Thời điểm đặt vé phổ biến: **năm, tháng, ngày, giờ, dịp lễ, cuối tuần, thời điểm ra mắt phim mới**.

**Những thứ gì (Which):**
Khách hàng thường sử dụng các yếu tố đối tượng nào trong quá trình đặt phim online?
-	Sản phẩm: vé xem phim.
-	Thiết bị mua vé: website & app.
-	Phương thức thanh toán: các loại nguồn tiền (trong app, ngân hàng liên kết).
-	Quà tặng, chương trình khuyến mãi.

**Cách thức (How):**  
- Phân tích trải nghiệm khách hàng, tỷ lệ giữ chân, hiệu suất các bước trong quy trình đặt vé.



## Quy trình phân tích

1. **Load Data:** Nạp và kiểm tra dữ liệu gốc.  
2. **Data Cleaning:** Xử lý kiểu dữ liệu, giá trị null, trùng lặp và gộp các bảng liên quan.  
3. **Analyze:**  
   - Khắc họa **chân dung khách hàng** (độ tuổi, giới tính).  
   - Phân tích **xu hướng đặt vé theo thời gian** (tháng, tuần, giờ).  
   - Đánh giá **các yếu tố ảnh hưởng đến hành vi mua và thanh toán** (nền tảng, thiết bị, phương thức, khuyến mãi, loại phim).  
   - Phân tích **giá trị và hành vi khách hàng**, **giữ chân (Cohort Analysis)**, và **tỷ lệ thanh toán thành công**.  
4. **Visualization & Insights:** Trực quan hóa dữ liệu, rút ra xu hướng và đề xuất hành động.



## Thông tin bộ dữ liệu

- **Nguồn:** Hệ thống đặt vé xem phim trực tuyến .  
- **Thời gian:** 2019–2022  
- **Định dạng:** `.csv`  
- **Tổng cộng:** 5 bảng dữ liệu

### 1️ `customer.csv` — Thông tin khách hàng
| Thuộc tính | Mô tả |
|-------------|-------|
| `customer_ID` | Mã định danh duy nhất của mỗi khách hàng. |
| `usergender` | Giới tính của khách hàng. |
| `dob` | Năm sinh của khách hàng. |

---

### 2️ `ticket_history.csv` — Lịch sử đặt vé
| Thuộc tính | Mô tả |
|-------------|-------|
| `ticket_id` | Mã đặt vé duy nhất cho mỗi giao dịch. |
| `customer_id` | Mã khách hàng thực hiện giao dịch. |
| `paying_method` | Hình thức thanh toán được sử dụng (ví dụ: **money in app**, **bank account**, **debit card**). |
| `theater_name` | Mã hoặc tên cụm rạp nơi khách hàng đặt vé. |
| `device_number` | Mã thiết bị được sử dụng để đặt vé, liên kết với bảng `device_detail.csv`. |
| `original_price` | Giá gốc của vé trước khi áp dụng khuyến mãi (đơn vị: VND). |
| `discount_value` | Giá trị giảm giá hoặc khuyến mãi được áp dụng. |
| `final_price` | Số tiền thực tế khách hàng phải trả sau khi giảm giá. |
| `time` | Thời điểm đặt vé (định dạng giờ:phút.giây). |
| `status_id` | Mã trạng thái giao dịch, liên kết với bảng `status_detail.csv` (ví dụ: thành công, thất bại, lỗi hệ thống). |
| `campaign_id` | Mã chiến dịch marketing áp dụng cho đơn đặt vé (liên kết với `campaign.csv`). |
| `movie_name` | Tên bộ phim mà khách hàng đặt vé. |

---

### 3️ `device_detail.csv` — Thông tin thiết bị
| Thuộc tính | Mô tả |
|-------------|-------|
| `device_number` | Mã định danh thiết bị duy nhất. |
| `model` | Tên hoặc mã thiết bị cụ thể. |
| `platform` | Nền tảng hoặc kênh sử dụng để đặt vé — gồm **mobile** (thiết bị di động) và **website** (trình duyệt web).  |

---

### 4️ `campaign.csv` — Chiến dịch marketing
| Thuộc tính | Mô tả |
|-------------|-------|
| `campaign_id` | Mã chiến dịch khuyến mãi. |
| `campaign_type` | Loại của chiến dịch tiếp thị. |

---

### 5️ `status_detail.csv` — Trạng thái giao dịch
| Thuộc tính | Mô tả |
|-------------|-------|
| `status_id` | Mã định danh trạng thái giao dịch. |
| `description` | Mô tả chi tiết về trạng thái hoặc lỗi xảy ra trong quá trình thanh toán. |
| `error_group` | Nhóm nguyên nhân lỗi chính, phân loại theo nguồn gốc: **customer** (lỗi phía khách hàng), **external** (lỗi từ ngân hàng hoặc bên thứ ba), và **internal** (lỗi nội bộ hệ thống). |



## Công cụ và thư viện sử dụng

- **Ngôn ngữ:** Python  
- **Thư viện:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `plotly`, `Datetime`
- **Công cụ:** Jupyter Notebook  
- **Quản lý mã nguồn:** GitHub  



##  Một số kết quả nổi bật

- **75% khách hàng** nằm trong độ tuổi **26–35**, nhóm có thu nhập ổn định và thói quen giải trí thường xuyên.  
- **Hai mùa cao điểm** đặt vé diễn ra vào **tháng 5–7** (mùa hè) và **tháng 10–12** (mùa phim cuối năm).  
- **Doanh số cuối tuần** cao gấp **1,5 lần** so với các ngày trong tuần (thứ 2–5).  
- **89% khách hàng** đặt vé qua **ứng dụng di động**, trong đó **55% sử dụng hệ điều hành iOS**.  
- Phần lớn khách hàng đến từ **các chiến dịch khuyến mãi**, tuy nhiên **tỷ lệ quay lại thấp**, chủ yếu chỉ đặt **một lần duy nhất**.




