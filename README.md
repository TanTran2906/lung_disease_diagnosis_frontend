# HỆ THỐNG CHẨN ĐOÁN BỆNH PHỔI

## Giới thiệu

Ứng dụng web dành cho chẩn đoán bệnh lý hô hấp. Hệ thống tích hợp các phương pháp xử lý ngôn ngữ tự nhiên, phân tích hình ảnh y tế, bầu chọn đa số, tìm kiếm được cải tiến bằng kỹ thuật sinh tạo (RAG), và giải pháp tối ưu hóa MaxSAT để đưa ra quyết định chẩn đoán chính xác.

Ứng dụng hỗ trợ phân tích các bệnh lý phổi phổ biến bao gồm bình thường, COPD, COVID-19, hen suyễn, lao phổi, phổi phì đại, suy hô hấp, tràn dịch màng phổi, tràn khí, xẹp phổi, viêm phổi và các bệnh lý khác.

## Công nghệ sử dụng

Ứng dụng được xây dựng sử dụng các công nghệ:

- Vite: Công cụ xây dựng ứng dụng web có hiệu suất cao
- React: Thư viện JavaScript để xây dựng giao diện người dùng
- JavaScript ES6+: Ngôn ngữ lập trình độc lập nền tảng
- Node.js: Môi trường thực thi JavaScript phía máy chủ

## Cấu trúc dự án

```
frontend/
  index.html                 - Tệp HTML chính
  package.json               - Cấu hình phụ thuộc và lệnh dự án
  vite.config.js             - Cấu hình Vite cho xây dựng và phát triển

  public/                    - Thư mục tài nguyên tĩnh
    icons/                   - Tệp biểu tượng ứng dụng
    samples/                 - Dữ liệu mẫu cho kiểm thử
      images/                - Hình ảnh y tế mẫu
      texts/                 - Báo cáo văn bản DICOM mẫu
        - Các tệp bệnh lý: Bình Thường, COPD, COVID, Hen, Lao, Phổi Phì Đại,
          Suy Hô Hấp, Tràn Dịch, Tràn Khí, Xẹp Phổi, Viêm Phổi, Ứng Hủy
        - Mỗi bệnh lý có 3 mẫu khác nhau

  src/                       - Mã nguồn ứng dụng
    main.jsx                 - Điểm vào chính ứng dụng React
    App.jsx                  - Thành phần gốc ứng dụng
    App.css                  - Kiểu CSS ứng dụng
    reset.css                - Kiểu CSS đặt lại mặc định trình duyệt

    api/                     - Module gọi API và xử lý dữ liệu từ máy chủ

    assets/                  - Tài nguyên ứng dụng (ảnh, phông chữ, v.v.)

    components/              - Thành phần React tái sử dụng
      DiagnosisMarkdown.jsx  - Thành phần hiển thị chẩn đoán dạng Markdown
      VotingExplanationTooltip.jsx - Gợi ý công cụ giải thích cơ chế bỏ phiếu

    features/                - Redux store và logic trạng thái toàn cục
      store.js               - Cấu hình Redux store

    hooks/                   - React hooks tùy chỉnh

    layouts/                 - Bố cục chính ứng dụng
      MainLayout.jsx         - Bố cục khung chính

    pages/                   - Trang ứng dụng chính
      HomePage.jsx           - Trang chủ ứng dụng
      ImagePage.jsx          - Trang phân tích hình ảnh y tế
      TextPage.jsx           - Trang phân tích văn bản báo cáo
      MultimodalPage.jsx     - Trang phân tích kết hợp hình ảnh và văn bản
      RAGPage.jsx            - Trang tìm kiếm nâng cao với RAG
      MaxSATPage.jsx         - Trang giải quyết vấn đề tối ưu hóa MaxSAT
      VotingPage.jsx         - Trang bầu chọn đa số

    routes/                  - Cấu hình định tuyến ứng dụng
      index.jsx              - Định nghĩa các tuyến đường

    styles/                  - Kiểu CSS toàn cục

    utils/                   - Hàm tiện ích và cấu hình
      keywordGroups.js       - Nhóm từ khóa y tế theo danh mục
      labelMapping.js        - Ánh xạ nhãn bệnh lý sang mã định danh
      maxSatTestCases.js     - Các trường hợp kiểm thử cho MaxSAT solver
```

## Các tính năng chính

1. Phân tích hình ảnh (Image Page)
    - Tải và xử lý hình ảnh y tế
    - Phân tích đặc trưng hình ảnh
    - Dự đoán bệnh lý dựa trên phân tích hình ảnh

2. Phân tích văn bản (Text Page)
    - Xử lý báo cáo y tế dạng văn bản
    - Trích xuất thông tin chủ yếu từ tài liệu
    - Phân loại bệnh lý từ mô tả văn bản

3. Phân tích Multimodal (Multimodal Page)
    - Kết hợp dữ liệu hình ảnh và văn bản
    - Tích hợp thông tin từ nhiều nguồn
    - Chẩn đoán chính xác cao hơn thông qua đa phương thức

4. Tìm kiếm được cải tiến (RAG Page)
    - Retrieval-Augmented Generation (RAG)
    - Tìm kiếm thông tin liên quan từ cơ sở dữ liệu
    - Tạo ra câu trả lời dựa trên tài liệu tham khảo

5. Bầu chọn đa số (Voting Page)
    - Kết hợp kết quả từ nhiều mô hình
    - Logic bỏ phiếu thông minh để xác định chẩn đoán cuối cùng
    - Độ tin cậy dựa trên sự đồng ý giữa các mô hình

6. Tối ưu hóa MaxSAT (MaxSAT Page)
    - Giải các bài toán thỏa mãn điều kiện tối đa
    - Tìm giải pháp tối ưu với ràng buộc phức tạp
    - Hỗ trợ lý luận logic nâng cao

## Cài đặt

### Yêu cầu hệ thống

- Node.js: Phiên bản 14.x hoặc cao hơn
- npm: Phiên bản 6.x hoặc cao hơn

### Các bước cài đặt

1. Clone hoặc tải xuống dự án:

```
git clone <đường dẫn kho lưu trữ>
cd frontend
```

2. Cài đặt các phụ thuộc:

```
npm install
```

3. Khởi động máy chủ phát triển:

```
npm run dev
```

4. Truy cập ứng dụng thông qua trình duyệt:
   Mở trình duyệt và điều hướng đến http://localhost:5173 (hoặc cổng được chỉ định)

## Các lệnh NPM

Các lệnh chính để phát triển và xây dựng dự án:

- `npm run dev` - Khởi động máy chủ phát triển với reload nóng
- `npm run build` - Xây dựng ứng dụng để triển khai
- `npm run preview` - Xem trước bản dựng cuối cùng cục bộ

## Dữ liệu mẫu

Dự án bao gồm các tệp báo cáo DICOM mẫu trong thư mục `public/samples/texts/`:

Bệnh lý được hỗ trợ (mỗi bệnh có 3 mẫu):

- Bình thường: text*Binhthuong*[1-3].dcm.txt
- COPD: text*COPD*[1-3].dcm.txt
- COVID-19: text*Covid*[1-3].dcm.txt
- Hen suyễn: text*Hen*[1-3].dcm.txt
- Lao phổi: text*Lao*[1-3].dcm.txt
- Phổi phì đại: text*Phuphoi*[1-3].dcm.txt
- Suy hô hấp: text*Suyhohap*[1-3].dcm.txt
- Tràn dịch: text*Trandich*[1-3].dcm.txt
- Tràn khí: text*Trankhi*[1-3].dcm.txt
- Ứng hủy: text*Uphoi*[1-3].dcm.txt
- Viêm phổi: text*Viemphoi*[1-3].dcm.txt
- Xẹp phổi: text*Xepphoi*[1-3].dcm.txt
