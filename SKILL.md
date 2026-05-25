
# SKILL.md — Quy Chuẩn Viết Tài Liệu BA

> Tài liệu này định nghĩa các quy tắc, cấu trúc và tiêu chuẩn để tạo ra các loại tài liệu BA chất lượng cao, nhất quán và có thể bảo trì.

---

## MỤC LỤC

1. [Nguyên tắc chung](#1-nguyên-tắc-chung)
2. [SRS — Software Requirements Specification](#2-srs--software-requirements-specification)
3. [Đặc tả người dùng (User Specification)](#3-đặc-tả-người-dùng-user-specification)
4. [Test Case](#4-test-case)
5. [Quy tắc ngôn ngữ và định dạng](#5-quy-tắc-ngôn-ngữ-và-định-dạng)
6. [Quy trình review tài liệu](#6-quy-trình-review-tài-liệu)

---

## 1. Nguyên tắc chung

### 1.1 Tiêu chí tài liệu tốt (SMART-C)

| Tiêu chí | Mô tả |
|----------|-------|
| **S**pecific | Rõ ràng, không mơ hồ — mỗi yêu cầu chỉ được hiểu theo một nghĩa |
| **M**easurable | Có thể đo lường, kiểm chứng được |
| **A**chievable | Khả thi về mặt kỹ thuật và nguồn lực |
| **R**elevant | Gắn với mục tiêu nghiệp vụ rõ ràng |
| **T**raceable | Có thể truy vết từ yêu cầu → thiết kế → test |
| **C**omplete | Đủ thông tin để dev/tester hiểu và thực thi |

### 1.2 Quy tắc đặt tên file

```
[Loại]_[TênDự án]_[Module]_v[Phiên bản]_[YYYYMMDD].[ext]

Ví dụ:
  SRS_EcommercePlatform_Checkout_v1.2_20260520.docx
  UserSpec_HRSystem_LeaveManagement_v1.0_20260520.md
  TestCase_MobileApp_Login_v2.1_20260520.xlsx
```

### 1.3 Quản lý phiên bản tài liệu

Mỗi tài liệu phải có bảng lịch sử thay đổi:

| Phiên bản | Ngày | Người thực hiện | Mô tả thay đổi |
|-----------|------|-----------------|----------------|
| 1.0 | YYYY-MM-DD | [Tên BA] | Tạo mới |
| 1.1 | YYYY-MM-DD | [Tên BA] | Cập nhật section X |

---

## 2. SRS — Software Requirements Specification

### 2.1 Cấu trúc file SRS chuẩn

```
SRS_[TênDựÁn]_[Module].md
├── 1. Giới thiệu
│   ├── 1.1 Mục đích tài liệu
│   ├── 1.2 Phạm vi hệ thống
│   ├── 1.3 Định nghĩa & từ viết tắt
│   ├── 1.4 Tài liệu tham chiếu
│   └── 1.5 Tổng quan tài liệu
├── 2. Mô tả tổng quan hệ thống
│   ├── 2.1 Bối cảnh hệ thống
│   ├── 2.2 Chức năng tổng quát
│   ├── 2.3 Người dùng & vai trò
│   ├── 2.4 Ràng buộc tổng thể
│   └── 2.5 Giả định & phụ thuộc
├── 3. Yêu cầu chức năng (Functional Requirements)
│   ├── 3.x [Tên module/feature]
│   │   ├── Mô tả
│   │   ├── Luồng chính (Happy path)
│   │   ├── Luồng ngoại lệ
│   │   └── Quy tắc nghiệp vụ
├── 4. Yêu cầu phi chức năng (Non-Functional Requirements)
│   ├── 4.1 Hiệu năng (Performance)
│   ├── 4.2 Bảo mật (Security)
│   ├── 4.3 Khả dụng (Availability)
│   ├── 4.4 Khả năng mở rộng (Scalability)
│   ├── 4.5 Khả năng bảo trì (Maintainability)
│   └── 4.6 Trải nghiệm người dùng (Usability)
├── 5. Yêu cầu dữ liệu
│   ├── 5.1 Mô hình dữ liệu (ERD/Data Dictionary)
│   └── 5.2 Quy tắc dữ liệu & validation
├── 6. Yêu cầu giao diện
│   ├── 6.1 Giao diện người dùng (UI)
│   ├── 6.2 Giao diện hệ thống (API/Integration)
│   └── 6.3 Giao diện phần cứng (nếu có)
└── 7. Phụ lục
    ├── Wireframe / Mockup
    ├── Sơ đồ luồng (Flowchart / Sequence Diagram)
    └── Ma trận truy vết yêu cầu (RTM)
```

### 2.2 Quy tắc viết Yêu cầu chức năng

**Định danh yêu cầu:**
```
FR-[MODULE]-[STT]
Ví dụ: FR-LOGIN-001, FR-CART-015
```

**Mẫu viết một yêu cầu chức năng:**

```markdown
#### FR-[MODULE]-[STT]: [Tên ngắn gọn]

**Mô tả:** [Hệ thống] phải/nên [hành động] khi [điều kiện].

**Actor:** [Người dùng / Hệ thống liên quan]

**Tiền điều kiện:**
- [ ] [Điều kiện 1]
- [ ] [Điều kiện 2]

**Luồng chính:**
1. Người dùng [hành động]
2. Hệ thống [phản hồi]
3. ...

**Luồng ngoại lệ:**
- **E1 - [Tên lỗi]:** Nếu [điều kiện], hệ thống hiển thị [thông báo lỗi].
- **E2 - [Tên lỗi]:** ...

**Hậu điều kiện:**
- [ ] [Kết quả mong đợi sau khi hoàn thành]

**Quy tắc nghiệp vụ:**
- BR-001: [Quy tắc]
- BR-002: [Quy tắc]

**Độ ưu tiên:** Must Have / Should Have / Could Have / Won't Have (MoSCoW)
```

### 2.3 Quy tắc viết Yêu cầu phi chức năng

**Định danh:** `NFR-[LOẠI]-[STT]`

**Phải có con số cụ thể — KHÔNG viết mơ hồ:**

| Sai | Đúng |
|-----|------|
| Hệ thống phải nhanh | Thời gian phản hồi API ≤ 500ms ở P95 với 1000 concurrent users |
| Hệ thống phải bảo mật | Mật khẩu phải được hash bằng bcrypt với cost factor ≥ 12 |
| Hệ thống phải ổn định | Uptime ≥ 99.9% (downtime ≤ 8.7h/năm) |

### 2.4 Data Dictionary — Từ điển dữ liệu

```markdown
#### Bảng: [tên_bảng]

| Trường | Kiểu dữ liệu | Bắt buộc | Mô tả | Ràng buộc |
|--------|-------------|----------|-------|-----------|
| id | UUID | Có | Khóa chính | PK, auto-generate |
| email | VARCHAR(255) | Có | Email người dùng | UNIQUE, format email |
| status | ENUM | Có | Trạng thái tài khoản | active/inactive/banned |
| created_at | TIMESTAMP | Có | Thời gian tạo | UTC, auto-set |
```

---

## 3. Đặc tả người dùng (User Specification)

### 3.1 Cấu trúc file đặc tả người dùng

```
UserSpec_[TênDựÁn]_[Module].md
├── 1. Thông tin tài liệu
├── 2. Danh sách vai trò người dùng (User Roles)
├── 3. Persona người dùng
├── 4. User Stories
├── 5. Use Case tổng quan
├── 6. Chi tiết Use Case
└── 7. Ma trận quyền hạn (Permission Matrix)
```

### 3.2 Mẫu Persona người dùng

```markdown
### Persona: [Tên đại diện]

**Ảnh đại diện:** [Mô tả hoặc link ảnh]

| Thông tin | Chi tiết |
|-----------|---------|
| Tên | Nguyễn Văn A |
| Tuổi | 32 |
| Vai trò | Nhân viên kế toán |
| Kinh nghiệm công nghệ | Trung bình |
| Thiết bị sử dụng | Máy tính bàn, đôi khi dùng điện thoại |

**Mục tiêu:** [Người dùng này muốn đạt được gì khi dùng hệ thống]

**Điểm đau (Pain Points):**
- [Vấn đề 1 họ đang gặp phải]
- [Vấn đề 2]

**Kỳ vọng:**
- [Điều họ mong đợi từ hệ thống]

**Tần suất sử dụng:** Hàng ngày / Hàng tuần / Hàng tháng
```

### 3.3 Mẫu User Story

**Định danh:** `US-[STT]`

**Định dạng chuẩn:**

```markdown
#### US-[STT]: [Tên ngắn]

**Là một** [vai trò người dùng],
**Tôi muốn** [hành động / tính năng],
**Để** [mục tiêu / lợi ích nghiệp vụ].

**Tiêu chí chấp nhận (Acceptance Criteria):**
- [ ] AC1: Khi [điều kiện], thì [kết quả mong đợi]
- [ ] AC2: Khi [điều kiện], thì [kết quả mong đợi]
- [ ] AC3: ...

**Định nghĩa hoàn thành (Definition of Done):**
- [ ] Code đã được review
- [ ] Unit test coverage ≥ 80%
- [ ] Test case đã pass
- [ ] Tài liệu đã cập nhật

**Story Points:** [1 / 2 / 3 / 5 / 8 / 13]
**Độ ưu tiên:** [Critical / High / Medium / Low]
**Liên kết FR:** [FR-MODULE-001, FR-MODULE-002]
```

### 3.4 Mẫu Use Case chi tiết

```markdown
### UC-[STT]: [Tên Use Case]

| Thuộc tính | Giá trị |
|-----------|---------|
| **ID** | UC-[STT] |
| **Tên** | [Tên đầy đủ] |
| **Actor chính** | [Tên vai trò] |
| **Actor phụ** | [Hệ thống / người dùng liên quan] |
| **Tiền điều kiện** | [Điều kiện phải đúng trước khi UC bắt đầu] |
| **Hậu điều kiện** | [Trạng thái hệ thống sau khi UC kết thúc] |
| **Tần suất** | [Hàng ngày / Hàng tuần / ...] |

**Luồng chính:**

| Bước | Actor | Hành động |
|------|-------|-----------|
| 1 | Người dùng | Truy cập trang đăng nhập |
| 2 | Hệ thống | Hiển thị form đăng nhập |
| 3 | Người dùng | Nhập email và mật khẩu |
| 4 | Hệ thống | Xác thực thông tin |
| 5 | Hệ thống | Chuyển hướng đến trang chủ |

**Luồng thay thế:**

- **A1 (Bước 4) — Tài khoản không tồn tại:** Hệ thống hiển thị thông báo "Email hoặc mật khẩu không đúng". Quay lại bước 1.
- **A2 (Bước 4) — Sai mật khẩu 5 lần liên tiếp:** Hệ thống khóa tài khoản 30 phút và gửi email thông báo.

**Use Case mở rộng / phụ thuộc:**
- [include] UC-002: Xác thực 2 bước (2FA)
- [extend] UC-010: Quên mật khẩu
```

### 3.5 Ma trận quyền hạn (Permission Matrix)

```markdown
### Ma trận quyền hạn

| Chức năng | Admin | Manager | Staff | Guest |
|-----------|:-----:|:-------:|:-----:|:-----:|
| Xem danh sách | ✓ | ✓ | ✓ | ✗ |
| Tạo mới | ✓ | ✓ | ✓ | ✗ |
| Chỉnh sửa | ✓ | ✓ | Của mình | ✗ |
| Xóa | ✓ | ✓ | ✗ | ✗ |
| Phê duyệt | ✓ | ✓ | ✗ | ✗ |
| Xuất báo cáo | ✓ | ✓ | ✗ | ✗ |
| Quản lý người dùng | ✓ | ✗ | ✗ | ✗ |

**Ghi chú:**
- ✓ = Có quyền đầy đủ
- ✗ = Không có quyền
- "Của mình" = Chỉ có quyền trên dữ liệu của chính họ
```

---

## 4. Test Case

### 4.1 Cấu trúc file Test Case

```
TestCase_[TênDựÁn]_[Module].md
├── 1. Thông tin tài liệu
├── 2. Phạm vi kiểm thử
├── 3. Môi trường kiểm thử
├── 4. Dữ liệu kiểm thử (Test Data)
├── 5. Test Suite
│   ├── TS-[STT]: [Tên nhóm]
│   │   ├── TC-[STT]: [Test case]
│   │   └── ...
└── 6. Báo cáo kết quả (Test Result Summary)
```

### 4.2 Định danh Test Case

```
TC-[MODULE]-[LOẠI]-[STT]

Loại:
  POS = Positive (Happy path)
  NEG = Negative (Error case)
  BND = Boundary (Giá trị biên)
  PER = Performance
  SEC = Security

Ví dụ:
  TC-LOGIN-POS-001  → Test đăng nhập thành công
  TC-LOGIN-NEG-003  → Test sai mật khẩu
  TC-PRICE-BND-001  → Test giá trị giá = 0
```

### 4.3 Mẫu Test Case chi tiết

```markdown
#### TC-[MODULE]-[LOẠI]-[STT]: [Tên test case]

| Thuộc tính | Giá trị |
|-----------|---------|
| **ID** | TC-LOGIN-POS-001 |
| **Tên** | Đăng nhập thành công với email và mật khẩu hợp lệ |
| **Liên kết** | FR-LOGIN-001, US-001 |
| **Độ ưu tiên** | Critical |
| **Loại** | Functional / Positive |
| **Môi trường** | Staging |
| **Người tạo** | [Tên] |
| **Ngày tạo** | YYYY-MM-DD |

**Tiền điều kiện:**
- Hệ thống đang hoạt động bình thường
- Tài khoản test@example.com đã được tạo với mật khẩu Test@123
- Người dùng chưa đăng nhập

**Dữ liệu đầu vào (Test Data):**

| Trường | Giá trị |
|--------|---------|
| Email | test@example.com |
| Password | Test@123 |

**Các bước thực hiện:**

| Bước | Hành động | Dữ liệu đầu vào | Kết quả mong đợi |
|------|-----------|-----------------|------------------|
| 1 | Truy cập URL đăng nhập | https://app.example.com/login | Trang đăng nhập hiển thị đúng |
| 2 | Nhập email | test@example.com | Field email hiển thị giá trị nhập |
| 3 | Nhập mật khẩu | Test@123 | Field password hiển thị dấu *** |
| 4 | Click nút "Đăng nhập" | — | Loading indicator xuất hiện |
| 5 | Chờ phản hồi | — | Chuyển hướng đến /dashboard |

**Kết quả mong đợi:**
- Người dùng được chuyển đến trang dashboard
- Hiển thị tên người dùng ở góc trên phải
- Token JWT được lưu vào localStorage
- Session cookie được set với httpOnly flag

**Kết quả thực tế:** [Điền sau khi chạy test]

**Trạng thái:** Pass / Fail / Blocked / Skipped

**Ghi chú / Bug ID:** [Nếu Fail, ghi link bug ticket]
```

### 4.4 Checklist thiết kế Test Case

Khi thiết kế test case cho một chức năng, phải bao phủ đủ các loại:

```
□ Happy Path (Luồng chính thành công)
□ Negative Cases (Input sai, thiếu, không hợp lệ)
□ Boundary Values (Giá trị biên: min, max, min-1, max+1)
□ Permission Cases (Đúng quyền / Sai quyền / Không có quyền)
□ State-Based Cases (Trạng thái hệ thống khác nhau)
□ Concurrency Cases (Thao tác đồng thời nếu có)
□ UI Validation (Thông báo lỗi, placeholder, format)
□ Integration Cases (Luồng liên quan hệ thống khác)
```

### 4.5 Bảng Test Data chuẩn cho Boundary Testing

```markdown
#### Ví dụ: Field "Tuổi" — quy tắc: 18 ≤ tuổi ≤ 65

| TC ID | Giá trị nhập | Mong đợi | Loại |
|-------|-------------|----------|------|
| TC-AGE-BND-001 | 17 | Lỗi: "Tuổi phải từ 18 đến 65" | BND - dưới min |
| TC-AGE-BND-002 | 18 | Thành công | BND - bằng min |
| TC-AGE-BND-003 | 19 | Thành công | BND - trên min |
| TC-AGE-BND-004 | 40 | Thành công | Giá trị trung bình |
| TC-AGE-BND-005 | 64 | Thành công | BND - dưới max |
| TC-AGE-BND-006 | 65 | Thành công | BND - bằng max |
| TC-AGE-BND-007 | 66 | Lỗi: "Tuổi phải từ 18 đến 65" | BND - trên max |
| TC-AGE-BND-008 | 0 | Lỗi | NEG - zero |
| TC-AGE-BND-009 | -1 | Lỗi | NEG - âm |
| TC-AGE-BND-010 | abc | Lỗi: "Vui lòng nhập số" | NEG - không phải số |
| TC-AGE-BND-011 | (trống) | Lỗi: "Trường này là bắt buộc" | NEG - rỗng |
```

### 4.6 Template Test Result Summary

```markdown
### Báo cáo kết quả kiểm thử

| Thông tin | Chi tiết |
|-----------|---------|
| **Module** | [Tên module] |
| **Ngày thực hiện** | YYYY-MM-DD |
| **Người thực hiện** | [Tên tester] |
| **Build/Version** | v1.2.3 |
| **Môi trường** | Staging |

**Tổng kết:**

| Tổng TC | Pass | Fail | Blocked | Skipped | Tỷ lệ Pass |
|---------|------|------|---------|---------|-----------|
| 50 | 44 | 4 | 1 | 1 | 88% |

**Danh sách lỗi phát hiện:**

| Bug ID | TC ID | Mô tả lỗi | Mức độ | Trạng thái |
|--------|-------|-----------|--------|-----------|
| BUG-123 | TC-LOGIN-NEG-003 | Không hiển thị thông báo lỗi khi sai mật khẩu | High | Open |

**Kết luận:** [Pass / Fail / Cần kiểm thử lại]
```

---

## 5. Quy tắc ngôn ngữ và định dạng

### 5.1 Quy tắc viết yêu cầu

**Động từ bắt buộc (theo RFC 2119):**

| Từ | Ý nghĩa | Khi dùng |
|----|---------|---------|
| **Phải / Must / Shall** | Bắt buộc tuyệt đối | Yêu cầu thiết yếu |
| **Không được / Must Not** | Cấm tuyệt đối | Ràng buộc cứng |
| **Nên / Should** | Khuyến nghị mạnh | Best practice |
| **Không nên / Should Not** | Không khuyến nghị | Nên tránh |
| **Có thể / May / Can** | Tùy chọn | Tính năng optional |

**KHÔNG dùng các từ mơ hồ:**
- ~~nhanh, chậm, nhiều, ít, thường xuyên, phù hợp, thân thiện, dễ dùng~~
- Thay bằng: con số cụ thể, điều kiện đo lường được

### 5.2 Quy tắc định dạng Markdown

```markdown
# Cấp 1: Tên tài liệu (chỉ dùng 1 lần)
## Cấp 2: Chương lớn (1. Giới thiệu, 2. Yêu cầu...)
### Cấp 3: Mục (1.1 Mục đích, 3.1 Module Login...)
#### Cấp 4: Yêu cầu / Use Case / Test Case cụ thể

- Dùng bảng Markdown cho dữ liệu có cấu trúc
- Dùng code block (```) cho ví dụ kỹ thuật, API, SQL
- Dùng checkbox [ ] cho danh sách cần xác nhận
- Dùng **bold** cho thuật ngữ quan trọng lần đầu xuất hiện
- Dùng > blockquote cho ghi chú / cảnh báo quan trọng
```

### 5.3 Quy tắc đặt ID và truy vết

```
Cấu trúc truy vết dọc:
  BusinessGoal → User Story → FR → Use Case → Test Case

Ví dụ:
  BG-001 (Tăng tỷ lệ chuyển đổi)
    └── US-003 (Thanh toán nhanh bằng ví điện tử)
          └── FR-PAY-001 (Tích hợp VNPay)
                └── UC-PAY-001 (Thanh toán qua VNPay)
                      └── TC-PAY-POS-001 (Thanh toán thành công)
                      └── TC-PAY-NEG-001 (Thanh toán thất bại - hết tiền)
```

---

## 6. Quy trình review tài liệu

### 6.1 Checklist review SRS

```
□ Mỗi yêu cầu có ID duy nhất
□ Không có yêu cầu mâu thuẫn nhau
□ Yêu cầu phi chức năng có số liệu cụ thể
□ Luồng ngoại lệ đã xử lý đủ
□ Từ điển dữ liệu đầy đủ
□ Mockup/wireframe đã đính kèm
□ Ma trận truy vết (RTM) đã tạo
□ Đã review với stakeholder
□ Đã có sign-off từ Product Owner
```

### 6.2 Checklist review User Specification

```
□ Persona đại diện đủ cho các nhóm người dùng thực tế
□ Mỗi User Story có Acceptance Criteria rõ ràng
□ Use Case bao phủ hết các chức năng trong phạm vi
□ Ma trận quyền hạn đã review với stakeholder
□ Không có Use Case mồ côi (không liên kết FR)
```

### 6.3 Checklist review Test Case

```
□ Test case bao phủ 100% FR được giao
□ Có đủ positive và negative cases
□ Boundary testing cho mọi field có giới hạn giá trị
□ Test data đã chuẩn bị sẵn
□ Test case có thể chạy độc lập (không phụ thuộc thứ tự)
□ Kết quả mong đợi đủ cụ thể để phán định Pass/Fail
□ Test case liên kết đúng FR / User Story
```

### 6.4 Vòng đời tài liệu

```
Draft → Internal Review → Stakeholder Review → Approved → Baselined
                                                              ↓
                                                    Change Request
                                                              ↓
                                                    Impact Analysis
                                                              ↓
                                                    Update & Re-approve
```

> **Quy tắc vàng:** Không có thay đổi yêu cầu nào được thực thi mà không qua Change Request chính thức khi tài liệu đã ở trạng thái Baselined.

---

*Tài liệu này được duy trì bởi BA Team. Mọi đề xuất cập nhật gửi qua Pull Request.*
=======
# Bộ Kỹ Năng Phân Tích & Viết Tài Liệu (BA/PO Skills)

Tài liệu này tổng hợp các kỹ năng cốt lõi cần thiết trong việc thu thập yêu cầu, phân tích nghiệp vụ và chuyển hóa thông tin thành các tài liệu tiêu chuẩn trong quá trình phát triển phần mềm.

## 1. Kỹ năng làm Tài liệu đặc tả (SRS - Software Requirements Specification)
Tài liệu đặc tả là cầu nối giữa nghiệp vụ và đội ngũ kỹ thuật. Kỹ năng yêu cầu:
- **Tư duy hệ thống:** Hiểu rõ bức tranh tổng thể, nắm bắt được cách các thành phần trong hệ thống tương tác với nhau.
- **Phân tích yêu cầu (Requirement Analysis):** Đào sâu vào yêu cầu của khách hàng để làm rõ những điểm chưa logic, các trường hợp ngoại lệ (edge cases).
- **Trình bày cấu trúc, rõ ràng:** Sử dụng ngôn từ mạch lạc, không gây hiểu lầm. Biết cách phân chia các chức năng lớn thành nhiều module nhỏ.
- **Biểu diễn luồng nghiệp vụ (Modeling):** Sử dụng thành thạo các biểu đồ luồng dữ liệu, UML, BPMN, Flowchart, Sequence Diagram (ví dụ: vẽ sơ đồ Mermaid, Draw.io) để mô tả logic trực quan.
- **Chi tiết hóa dữ liệu:** Mô tả chính xác các quy tắc (Business rules) và ràng buộc dữ liệu (data types, validation rules, mandatory fields).

## 2. Kỹ năng viết Tài liệu Test case
Test case giúp định hướng quá trình đảm bảo chất lượng hệ thống (QA/QC). Kỹ năng yêu cầu:
- **Tư duy phản biện và bao quát:** Luôn đặt câu hỏi "Chuyện gì xảy ra nếu...?". Suy nghĩ bao phủ cả hai luồng: Positive flow (Luồng chuẩn) và Negative flow (Luồng lỗi/bất thường).
- **Đọc hiểu sâu đặc tả (SRS):** Từ tài liệu đặc tả, bóc tách ra được tất cả các điều kiện để thiết kế kịch bản test.
- **Viết ngắn gọn, dễ hiểu:** Các bước thực hiện (Steps to reproduce), Dữ liệu kiểm thử (Test data) và Kết quả mong muốn (Expected result) cần được viết rõ ràng, rành mạch để bất kỳ tester hay developer nào đọc cũng thao tác lại được.
- **Kỹ thuật thiết kế test case:** Áp dụng các kỹ thuật như phân tích giá trị biên (Boundary Value Analysis), phân vùng tương đương (Equivalence Partitioning), bảng quyết định (Decision Table) để tối ưu hóa số lượng test case mà vẫn đảm bảo độ phủ (test coverage).

## 3. Kỹ năng viết User Story
User story là công cụ quan trọng trong môi trường Agile/Scrum để truyền tải giá trị đến người dùng. Kỹ năng yêu cầu:
- **Tập trung vào người dùng cuối (User-centric):** Luôn viết story từ góc nhìn của user, thể hiện được giá trị thực tế mà chức năng mang lại thay vì mô tả công nghệ.
- **Nắm vững format tiêu chuẩn:** Sử dụng cấu trúc *As a [type of user], I want [some goal] so that [some reason/value].*
- **Xác định Tiêu chí nghiệm thu (Acceptance Criteria):** Mô tả cụ thể, đo lường được các điều kiện mà story cần đạt được để được coi là hoàn thành ("Done"). Khuyến khích sử dụng cấu trúc Gherkin: *Given / When / Then*.
- **Biết cách chia nhỏ (Splitting stories):** Đánh giá được kích cỡ của một story (Story points) và biết cách chia một Epic lớn thành những User stories nhỏ hơn, đủ để thực hiện trong phạm vi một Sprint ngắn.
- **Giao tiếp và thương lượng:** User Story chỉ là điểm bắt đầu cho một cuộc thảo luận. Cần có kỹ năng giao tiếp với đội phát triển để làm rõ (refinement) các yêu cầu kỹ thuật đằng sau.

## 4. Kỹ năng Tóm tắt họp (Meeting Summarization / Meeting Minutes)
Kỹ năng ghi chú và tổng hợp lại thông tin quan trọng sau các cuộc họp lấy yêu cầu hoặc thảo luận giải pháp. Kỹ năng yêu cầu:
- **Lắng nghe và chắt lọc thông tin (Active Listening):** Tách biệt được đâu là phần "thảo luận lan man" và đâu là "quyết định then chốt". Ghi chú nhanh các ý chính ngay trong lúc họp.
- **Kỹ năng đặt câu hỏi làm rõ (Clarification):** Khi trong cuộc họp có những điểm chưa thống nhất hoặc mơ hồ, phải có khả năng đặt câu hỏi khéo léo để chốt vấn đề ngay tại chỗ, tránh mang sự hiểu lầm vào biên bản họp.
- **Phân loại và cấu trúc thông tin:** Biên bản tóm tắt cần có bố cục rõ ràng:
  - *Thông tin chung:* Người tham gia, thời gian, chủ đề.
  - *Quyết định đã được chốt (Decisions made):* Rất quan trọng để làm cơ sở triển khai.
  - *Các vấn đề còn tồn đọng (Open issues):* Những mục chưa chốt được, cần confirm thêm.
  - *Hành động tiếp theo (Action items):* Chỉ định rõ "Ai làm việc gì?" (Assignee) và "Bao giờ xong?" (Deadline).
- **Diễn đạt súc tích và khách quan:** Văn phong chuyên nghiệp, cô đọng (dùng gạch đầu dòng), khách quan (tuyệt đối không đưa cảm xúc hay ý kiến cá nhân vào tóm tắt họp nếu không có).
