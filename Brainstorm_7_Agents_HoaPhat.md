# Brainstorm Nội dung Khảo sát Chi tiết – 7 Agent AI
**Khách hàng:** Hòa Phát Dung Quất (HPDQ)  
**Phạm vi:** Bộ phận Mua hàng & Phòng Nguyên liệu & Phòng Toàn Môi trường – Phase 2  
**Mục đích tài liệu:** Chuẩn bị câu hỏi & nội dung cần làm rõ trong buổi khảo sát chi tiết

---

## Agent 1 – Tổng hợp, Đánh giá Nhà cung cấp (NCC) / Nhà thầu
**Phòng ban liên quan:** Phòng Vật tư 4 (chị Linh Trang)

### Luồng dự kiến
Upload hồ sơ NCC → OCR trích xuất → Truy vấn SAP → Quét Internet → Chấm điểm → Xuất báo cáo

### Câu hỏi cần làm rõ
- **Đầu vào:**
  - Hồ sơ năng lực + ĐKKD thường là định dạng gì? (PDF scan, Word, ảnh chụp?) – ảnh hưởng đến chất lượng OCR
  - NCC nước ngoài chiếm tỷ lệ bao nhiêu? Ngôn ngữ chủ yếu? (Anh, Hoa, Nhật, Hàn?)
  - Hiện tại HP tự khai thác thông tin internet thủ công hay không có bước này?
- **Tiêu chí chấm điểm:**
  - Bảng tiêu chí hiện tại có bao nhiêu mục? Điểm tối đa mỗi mục là bao nhiêu?
  - Tiêu chí nào là cứng (điểm 0 nếu vi phạm) vs mềm (điểm theo thang)?
  - Ai phê duyệt kết quả chấm điểm cuối cùng?
- **SAP:**
  - Có thể cấp API/kết nối trực tiếp để lấy lịch sử giao dịch, hay chỉ xuất file?
  - Dữ liệu lịch sử cần tra cứu bao xa? (1 năm, 3 năm?)
- **Đầu ra:**
  - Báo cáo xuất ra file Word/Excel hay PDF? Cần chữ ký số không?
  - Kết quả có cần lưu vào hệ thống nào không (SAP, SharePoint, portal nội bộ)?

### Ý tưởng mở rộng
- Blacklist nội bộ (HP tự xây dựng) vs blacklist công khai (cổng thuế, tòa án)
- Tự động gửi email yêu cầu bổ sung hồ sơ nếu thiếu thông tin
- Dashboard tổng quan trạng thái NCC (đang đánh giá / đã phê duyệt / bị loại)

---

## Agent 2 – So sánh Báo giá
**Phòng ban liên quan:** Phòng Vật tư (biểu mẫu chung – chị Linh Trang)

### Luồng dự kiến
Upload nhiều báo giá → Nhận diện & trích xuất → Tra lịch sử giá SAP → Quy đổi tiền tệ/đơn vị → Điền form so sánh

### Câu hỏi cần làm rõ
- **Đầu vào:**
  - Một lần so sánh thường có bao nhiêu báo giá từ bao nhiêu NCC? (3–5 hay 10+?)
  - Báo giá phức tạp nhất thường gặp là loại nào? (nhiều trang, nhiều loại hàng, nhiều tiền tệ cùng lúc?)
  - Có trường hợp báo giá bằng hình ảnh chụp điện thoại không?
- **Chuẩn hóa dữ liệu:**
  - Các đơn vị tính thường gặp: kg, tấn, m3, lít, cái, bộ? Có quy tắc quy đổi chuẩn không?
  - Tỷ giá quy đổi: lấy theo ngày nào? (ngày nhận báo giá, ngày so sánh, tỷ giá ngân hàng nào?)
  - Có mặt hàng nào cùng tên nhưng khác spec (đặc tính kỹ thuật) không? Cần phân biệt không?
- **Biểu mẫu so sánh:**
  - Biểu mẫu hiện tại có bao nhiêu cột/trường cần điền?
  - Cột nào người dùng vẫn cần tự nhập (nhận xét chủ quan, điều kiện thanh toán...)?
- **Đầu ra:**
  - Sau khi có bảng so sánh, quy trình phê duyệt tiếp theo là gì?

### Ý tưởng mở rộng
- Gợi ý NCC tốt nhất theo từng tiêu chí (giá rẻ nhất, thời gian giao hàng tốt nhất, lịch sử đánh giá tốt nhất)
- Cảnh báo nếu giá báo cao hơn lịch sử trung bình X%
- Hỗ trợ template báo giá gửi cho NCC để chuẩn hóa format đầu vào

---

## Agent 3 – Báo cáo Tình hình Mua Nguyên liệu (Theo dõi Chất lượng)
**Phòng ban liên quan:** Phòng Quản lý Chất lượng / Phòng Nguyên liệu (chị Quỳnh Trang, chị Nga)

### Luồng dự kiến
Nhập liệu kết quả KT lên Becamis → Agent thu thập định kỳ → Phân tích chuỗi thời gian → Vẽ biểu đồ xu hướng → Cảnh báo nếu có xu hướng xấu → Gửi báo cáo qua Email/Teams

### Câu hỏi cần làm rõ
- **Nguồn dữ liệu:**
  - Becamis lưu trữ theo từng bản ghi riêng lẻ hay theo file đính kèm?
  - Có thể cấp quyền API để agent tự động truy vấn, hay chỉ xuất file Excel định kỳ?
  - Dữ liệu Becamis có thống nhất cấu trúc giữa các lô hàng không?
- **Chỉ tiêu kỹ thuật:**
  - Hiện có bao nhiêu chỉ tiêu theo dõi? Chỉ tiêu nào quan trọng nhất?
  - Định nghĩa "xu hướng chất lượng xấu đi": giảm liên tiếp X lần, hay lệch khỏi ngưỡng Y%, hay thuật toán phức tạp hơn?
  - Mỗi chỉ tiêu có giá trị ngưỡng (threshold) riêng không?
- **Báo cáo:**
  - Báo cáo cần xuất theo tần suất nào: tuần / tháng / quý / on-demand?
  - Cần phân tách theo nhà cung cấp, theo mặt hàng, theo nhà máy, hay tổng hợp?
  - Biểu đồ xu hướng hiện tại HP đang dùng loại nào? (line chart, control chart, waterfall?)
- **Cảnh báo:**
  - Gửi cảnh báo cho ai? (trưởng phòng, nhân viên phụ trách NCC, ban giám đốc?)
  - Ngưỡng cảnh báo: có khác nhau theo từng NCC không (NCC nội vs NCC ngoại)?

### Ý tưởng mở rộng
- Tự động tạo Action Items đề xuất xử lý khi chất lượng xấu (yêu cầu giải trình NCC, tạm ngừng đặt hàng)
- Tích hợp với Agent 1: cập nhật điểm đánh giá NCC dựa trên kết quả chất lượng thực tế

---

## Agent 4 – Theo dõi Hàng Tồn kho
**Phòng ban liên quan:** Phòng Nguyên liệu (chị Quỳnh Trang, chị Nga, anh Văn)

### Luồng dự kiến
Nhà máy gửi Excel tồn kho hàng tuần + Dữ liệu SAP → Tổng hợp & đối chiếu định mức → Dashboard cân đối → Cảnh báo Real-time/Daily qua Email/Teams

### Câu hỏi cần làm rõ
- **Nguồn dữ liệu:**
  - Hiện có bao nhiêu nhà máy gửi báo cáo? Format Excel có đồng nhất không?
  - Nhà máy gửi vào thứ mấy, giờ nào hàng tuần?
  - SAP tổng kho có cập nhật theo ngày không hay chỉ cuối tháng?
  - Tình trạng lệch số liệu giữa Excel nhà máy và SAP xảy ra thường xuyên không? Xử lý thế nào?
- **Định mức:**
  - Định mức tiêu hao do Phòng Công nghệ cấp, cập nhật bao lâu một lần?
  - Định mức có thay đổi theo mùa/theo đơn hàng không?
  - Ngưỡng cảnh báo: tồn kho < X ngày tiêu hao, hay tiêu hao tuần tăng > Y% so định mức?
- **Dashboard:**
  - HP muốn xem dashboard trên nền tảng nào? (PowerBI, web app nội bộ, Excel?)
  - Ai cần xem dashboard? Phân quyền theo phòng ban không?
- **Cảnh báo:**
  - Cảnh báo gửi ngay khi phát hiện hay tổng hợp cuối ngày/tuần?
  - Cần phân loại mức độ cảnh báo (warning, critical)?

### Ý tưởng mở rộng
- Dự báo tồn kho theo kế hoạch sản xuất (nếu có dữ liệu kế hoạch)
- Tự động tạo đề nghị đặt hàng (Purchase Request) khi tồn kho về ngưỡng tối thiểu
- Kết nối với Agent 2: khi cần đặt hàng thêm → tự động trigger quy trình so sánh báo giá

---

## Agent 5 – Phân tích Môi trường
**Phòng ban liên quan:** Phòng Toàn Môi trường (chị Diễm My, anh Sang)

### Luồng dự kiến
Thu thập dữ liệu quan trắc (real-time / file PDF) → Đối chiếu với ngưỡng pháp lý & nội bộ → Cảnh báo nếu vượt ngưỡng → Tổng hợp báo cáo nội bộ + báo cáo cơ quan nhà nước

### Câu hỏi cần làm rõ
- **Nguồn dữ liệu quan trắc:**
  - Phần mềm quan trắc thuê bên ngoài là phần mềm nào? Có cung cấp API không, hay chỉ xuất PDF?
  - Dữ liệu cập nhật mỗi 5 phút – agent cần xử lý real-time hay chỉ cần batch theo giờ/ngày?
  - Có bao nhiêu điểm/trạm quan trắc? Bao nhiêu chỉ số môi trường cần theo dõi?
- **Quy định pháp lý:**
  - Văn bản pháp luật (DTM, QCVN...) lưu ở đâu? File PDF nội bộ hay link tới cổng chính phủ?
  - Ngưỡng pháp lý có thay đổi định kỳ không? Quy trình cập nhật ngưỡng mới?
  - Bên cạnh quy định pháp luật, HP có quy định nội bộ chặt hơn không?
- **Báo cáo nội bộ:**
  - Biểu mẫu báo cáo nội bộ hiện tại (ví dụ bia 05234...) đang fill thủ công thế nào? Tần suất?
  - Ai ký duyệt báo cáo nội bộ?
- **Báo cáo cơ quan nhà nước:**
  - Nộp qua cổng dịch vụ công nào? (cổng Sở TNMT, Bộ TNMT, địa phương?)
  - Tần suất nộp định kỳ và deadline nộp đột xuất khi có sự cố?
  - Agent hỗ trợ đến bước nào: tổng hợp dữ liệu ra file, hay tự động upload lên cổng?
- **Cảnh báo:**
  - Cảnh báo chỉ cần gửi qua Teams/Email hay cần ghi log vào hệ thống?
  - Cần cảnh báo nhiều cấp độ không? (gần ngưỡng / vượt ngưỡng / nguy hiểm)

### Ý tưởng mở rộng
- Chatbot hỏi đáp nội bộ về quy định pháp luật môi trường (tra cứu nhanh ngưỡng cho phép)
- Tự động phát sinh ticket xử lý sự cố khi phát hiện vượt ngưỡng
- Lịch sử dữ liệu quan trắc → phân tích xu hướng theo mùa / theo thời điểm sản xuất

---

## Agent 6 – Theo dõi Chất lượng Công nghiệp (Chất thải)
**Phòng ban liên quan:** Phòng Toàn Môi trường (chị Diễm My) – liên quan chất thải công nghiệp

### Luồng dự kiến
Nhà máy scan giấy tờ chứng từ chất thải → Upload lên kho dữ liệu tập trung → Agent OCR & trích xuất → Lưu vào cơ sở dữ liệu mềm → Báo cáo tổng hợp + Cảnh báo

### Câu hỏi cần làm rõ
- **Hiện trạng:**
  - Quy trình hiện tại: nhà máy scan → gửi file qua email/Teams cho phòng toàn môi trường → nhập tay lại?
  - Có bao nhiêu loại chứng từ chất thải khác nhau? (manifest, chứng từ vận chuyển, biên bản tiêu hủy...)
  - Có bao nhiêu nhà máy? Mỗi nhà máy thường gửi bao nhiêu file/tháng?
- **Kho dữ liệu tập trung:**
  - HP muốn xây dựng trên nền tảng gì? (SharePoint, portal web mới, Teams channel?)
  - Phân quyền: mỗi nhà máy chỉ xem data của mình, hay xem tổng?
  - Cần gắn metadata gì khi upload? (loại chất thải, ngày, nhà máy, nhà thầu xử lý?)
- **OCR & dữ liệu:**
  - Chứng từ thường có chữ viết tay không? Ảnh hưởng lớn đến độ chính xác OCR
  - Dữ liệu cần trích xuất: khối lượng, loại chất thải, mã chất thải, ngày tháng, nhà thầu?
  - Sau khi trích xuất, cần lưu vào đâu? (Excel, database, kết nối SAP?)
- **Báo cáo & cảnh báo:**
  - Báo cáo tổng hợp chất thải theo chu kỳ nào? (tháng, quý, năm?)
  - Cần đối chiếu với hạn ngạch xử lý chất thải theo giấy phép không?
  - Cảnh báo khi nào? (chứng từ thiếu, khối lượng vượt giấy phép, chưa nhận được chứng từ trong X ngày?)

### Ý tưởng mở rộng
- QR code trên chứng từ để nhà máy scan nhanh và auto-index metadata
- Tra cứu trạng thái xử lý chất thải theo lô (đã xử lý, đang xử lý, chưa xử lý)
- Tích hợp Agent 7: khi lên kế hoạch xuất kho → tự động tạo yêu cầu chứng từ

---

## Agent 7 – Lên Kế hoạch Xuất kho (Chất thải)
**Phòng ban liên quan:** Phòng Toàn Môi trường (anh Hân, anh Sang, chị Diễm My)

### Luồng dự kiến
Đọc kế hoạch khai thác từ Elfit (PDF) + Tồn kho thực tế (Excel) + Danh sách nhà thầu → Gợi ý phân bổ khối lượng cho nhà thầu → Xuất file lệnh rút kho theo biểu mẫu → Xác nhận & cập nhật lũy kế → Theo dõi thực tế vs kế hoạch

### Câu hỏi cần làm rõ
- **Đầu vào – Kế hoạch khai thác:**
  - Elfit là phần mềm gì? Có thể kết nối API không, hay chỉ xuất PDF?
  - Kế hoạch khai thác lưu theo tháng, quý hay năm? Cập nhật bao lâu một lần?
  - Kế hoạch có bao nhiêu loại chất thải? Mỗi loại có ô/ngăn lưu chứa riêng không?
- **Đầu vào – Tồn kho:**
  - Tồn kho hiện tại đang theo dõi trên file Excel cá nhân – file này có template chuẩn không?
  - Ai cập nhật file tồn kho? Tần suất cập nhật?
  - Có thể build portal/kho tập trung để không phụ thuộc file cá nhân không?
- **Đầu vào – Danh sách nhà thầu:**
  - Nhà thầu xử lý chất thải hiện quản lý qua kênh nào? (Excel, Teams, hệ thống hợp đồng?)
  - Mỗi nhà thầu xử lý được loại chất thải nào? Công suất tối đa/tháng?
  - Hợp đồng nhà thầu có tỷ lệ phân bổ cố định không hay linh hoạt theo lô?
- **Phân bổ & lên kế hoạch:**
  - Hiện tại việc phân bổ khối lượng cho nhà thầu dựa trên tiêu chí gì? (giá, công suất, lịch sử thực hiện, điều kiện hợp đồng?)
  - Agent chỉ cần "gợi ý" hay có thể "tự động phân bổ" nếu đáp ứng điều kiện?
  - Kế hoạch tháng có thể điều chỉnh giữa chừng không? Cần phê duyệt lại không?
- **Xuất kho & trình ký:**
  - Biểu mẫu lệnh rút kho hiện có: bao nhiêu trường? Ai ký duyệt?
  - Quy trình trình ký có qua Elfit không? Elfit có thể tự động hóa bước ký không?
  - Sau khi có lệnh xuất, nhà thầu vào thu gom → cân khối lượng thực tế → cập nhật vào đâu?
- **Cập nhật lũy kế & báo cáo:**
  - Cần lưu lịch sử theo bao lâu? (1 năm, 5 năm? Liên quan yêu cầu pháp lý?)
  - Báo cáo tổng hợp cuối tháng/quý cần có các cột/chỉ số gì?
  - Có cần báo cáo so sánh kế hoạch vs thực tế không?

### Ý tưởng mở rộng
- Tự động phân bổ tối ưu (optimization) dựa trên hợp đồng, công suất, lịch đến thu gom
- Gửi thông báo cho nhà thầu khi có lệnh xuất kho mới
- Tích hợp với Agent 6: sau khi xuất kho → tự động yêu cầu chứng từ chất thải

---

## Tổng hợp – Câu hỏi chung cho tất cả Agent

| Chủ đề | Câu hỏi |
|--------|---------|
| **Tích hợp hệ thống** | SAP có phiên bản nào? Có policy về việc tích hợp bên ngoài không? |
| **Nền tảng** | HP đang dùng Microsoft 365 (Teams, SharePoint)? Có thể dùng Graph API không? |
| **Phân quyền** | User nào có thể dùng từng agent? Cần phân quyền theo phòng ban/chức vụ không? |
| **Ngôn ngữ tương tác** | Agent giao tiếp hoàn toàn tiếng Việt? Có hỗ trợ tiếng Anh/Trung không? |
| **Lưu trữ dữ liệu** | Dữ liệu do AI xử lý có cần lưu nội bộ (on-premise) không, hay cloud được? |
| **Audit trail** | Cần log lại mọi hành động của agent không? (quan trọng với dữ liệu pháp lý) |
| **Tiếp nhận phản hồi** | Nếu kết quả AI sai, user phản hồi/sửa thế nào? Agent có học từ phản hồi không? |

---

## Những điều cần Hòa Phát chuẩn bị trước buổi khảo sát chi tiết

**Phòng Vật tư / Mua hàng (Agent 1, 2, 3, 4):**
- [ ] File mẫu ĐKKD + Hồ sơ năng lực NCC (2–3 bộ điển hình, gồm 1 NCC nước ngoài)
- [ ] Bảng tiêu chí chấm điểm NCC hiện tại
- [ ] File báo giá mẫu (đặc biệt file phức tạp nhất: nhiều tiền tệ, nhiều đơn vị)
- [ ] File Excel báo cáo tồn kho mẫu từ nhà máy
- [ ] File xuất mẫu từ Becamis (dữ liệu chất lượng nguyên liệu)
- [ ] Định nghĩa "xu hướng chất lượng xấu đi" (rule business)

**Phòng Toàn Môi trường (Agent 5, 6, 7):**
- [ ] Thông tin phần mềm quan trắc (tên phần mềm, khả năng xuất dữ liệu)
- [ ] File PDF mẫu báo cáo quan trắc + biểu mẫu báo cáo nội bộ
- [ ] Ví dụ chứng từ chất thải công nghiệp (manifest, biên bản...)
- [ ] File Excel tồn kho chất thải mẫu + template lệnh rút kho
- [ ] Danh sách nhà thầu và điều kiện hợp đồng mẫu
- [ ] Thông tin về Elfit (phiên bản, khả năng xuất dữ liệu)

---

*Tài liệu này phục vụ chuẩn bị cho buổi khảo sát chi tiết sắp tới tại Hòa Phát Dung Quất*
