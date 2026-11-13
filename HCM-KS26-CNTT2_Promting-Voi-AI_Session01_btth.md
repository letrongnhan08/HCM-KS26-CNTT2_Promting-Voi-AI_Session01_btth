# BTTH: Cẩm nang sử dụng AI hiệu quả cho tân sinh viên

## **Sơ đồ các bước xâu chuỗi prompt (Prompt Chaining):**
Bước 1: Cách AI đoán từ (LLM hoạt động thế nào)
|
v
Bước 2: 3 cách nhận diện ảo giác của AI
|
v
Bước 3: Ứng dụng khung CREATE để viết prompt chuẩn

##  **Nội dung các prompt thành phần:**
Prompt 1: Phần bản chất LLM (Cách AI đoán từ):
"hãy đóng vai là một chuyên gia giáo dục, viết một đoạn ngắn, dễ hiểu cho sinh viên năm nhất giải thích cách LLM hoạt động. không dùng kiến thức chuyên môn gây khó hiểu cho sinh viên năm nhất và giải thích cơ chế dự đoán từ tiếp theo của AI (next-token prediction) dựa trên xác suất và ngữ cảnh.

Prompt 2: Phần nhận diện ảo giác
Dựa vào Prompt 1 .Đưa ra và phân tích 3 cách nhận diện ảo giác của AI cụ thể trong lập trình khi AI đưa ra  thông tin, cú pháp code không có thật.

Prompt 3: Cấu trúc prompt mẫu tối ưu bằng khung CREATE
Giới thiệu cấu trúc prompt chuẩn CREATE ngắn gọn,dễ hiểu cho sinh viên năm nhất hiểu các thành phần: Context (Bối cảnh), Request (Yêu cầu cốt lõi), Explanation (Giải thích & Ràng buộc), Action (Hành động), Tone (Giọng điệu văn phong), Extras (Định dạng đầu ra & Bổ sung). Kèm theo đó là 1 ví dụ prompt

## **Cuốn cẩm nang kết quả hoàn chỉnh xuất ra từ AI:**
Phần 1: Cách AI đoán từ (LLM hoạt động thế nào):
LLM (Large Language Model) -> hoạt động dựa trên cơ chế Next-Token Prediction (Dự đoán từ tiếp theo) -> LLM sẽ tính toán xác suất để chọn ra từ/mảnh ký tự có khả năng xuất hiện tiếp theo cao nhất. 
|
v
Ví dụ con chó đang ở ngoài [....] AI sẽ tính toán từ có xác suất xuất hiện cao kèm ngữ cảnh dựa trên hàng tỷ văn bản đã học (ví dụ: "sân" 90%, "đường" 70%, "đồng ruộng" 0%) và cơ chế xác xuất từ thì nó sẽ chọn ngẫu nhiên từ ngữ và từ nào có xác xuất cao nhất ,AI sẽ ưu tiên sử dụng chọn từ có xác xuất cao nhiều hơn.

Phần 2:3 cách nhận diện ảo giác của AI
Cách 1:Kỹ thuật Kiểm tra Chéo (Cross-check) Giữa AI A và AI B và con người, sử dụng hai AI để đối chiếu phản biện nếu thông tin có mâu thuẫn ví dụ AI A nói sai thì sử dụng AI B để đối chiếu và cần con người để kiểm chứng,đánh giá thông tin của 2 AI ,  giúp tránh được ảo giác AI.

Cách 2: Khi AI nói một thông tin không có thật, bịa ra thì phải hỏi thông tin này ở đâu, từ nguồn chính thống nào. Nếu đó do AI tự bịa ra, nó sẽ lúng túng và thừa nhận ngay.

Cách 3: Khi AI nếu không có số liệu trên mạng,không có file đính kèm RAG Grounding, nó buộc phải tự đoán mò dựa trên trí nhớ cũ , Dễ bị ảo giác , thì phải nhận diện qua một số thuật ngữ lạ và câu trả lời không logic ,lan man thì phải cần đánh giá ,yêu cầu AI giải thích lại văn bản nó bịa ra ví dụ "văn bản này có đúng không, tôi thấy một số điểm này còn chưa được" Thì AI nó sẽ xem lại và đổi ý. Để không còn ảo giác AI sử dụng RAG Grounding để AI chỉ đọc trong file này, và bắt buộc AI nếu không tìm thấy dữ liệu của file đó thì hãy trả lời 'Không rõ', tuyệt đối không đoán"

Phần 3: Cấu trúc prompt mẫu tối ưu bằng khung CREATE cho sinh viên năm nhất sử dụng AI

- Context (Bối cảnh & Vai trò): Định vị  vai trò chuyên gia cho AI và cung cấp bối cảnh thực tế. Ví dụ: "Bạn là chuyên gia hướng dẫn cho sinh viên năm nhất"

- Request (Yêu cầu cốt lõi): Sử dụng AI để làm gì ví dụ (trích xuất dữ liệu từ file word này,rồi đưa vào,tạo một file markdown với thông tin lấy từ file word )

- Explanation (Giải thích & Ràng buộc): Đặt ra ranh giới và quy tắc cấm. Ví dụ:"nếu không tìm thấy thông tin trong file thì hãy trả lời 'Không rõ', tuyệt đối không đoán"

- Action (Các bước hành động): Liệt kê trình tự các bước AI phải làm. Ví dụ:(bước 1: nêu các hướng dẫn cho sinh viên năm nhất , bước 2: các bước lập trình prompt cho AI kèmcó các comment ở mục chú thích

- Tone (Giọng điệu văn phong): Quy định thái độ và cảm xúc của bài viết. Ví dụ: "Văn phong chân thành, chuyên nghiệp

- Extras (Định dạng đầu ra & Bổ sung):Mô tả định dạng kết quả mong muốn. Ví dụ: "Xuất bản dưới dạng mẫu markdown có các câu hỏi trắc nghiệm ôn tập kiến thức