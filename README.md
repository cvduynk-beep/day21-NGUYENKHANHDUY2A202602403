# Lab 21 – Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Nguyễn Khánh Duy
- MSSV / mã học viên: 2A202602403
- Lớp: Track 1 (K4B)
- Ngành đã chọn: HR / tuyển dụng

---

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | Phân biệt đối xử và bất bình đẳng cơ hội việc làm (Bias & Discrimination); Tước đoạt sinh kế và cơ hội nghề nghiệp của các nhóm yếu thế hoặc thiểu số (Opportunity loss); Phán xét sai lệch về phẩm chất, năng lực ứng viên qua các chỉ số ngụy khoa học (Dignity loss); Xâm phạm dữ liệu cá nhân, hồ sơ sức khỏe và đời tư của người lao động (Privacy violation). |
| Mức độ high-stakes | **Cao (High)**. Tuyển dụng và việc làm là yếu tố quyết định trực tiếp đến thu nhập, bảo trợ xã hội và sinh kế lâu dài của mỗi cá nhân. Quyết định loại hồ sơ bởi AI có tác động mang tính dây chuyền; nếu hệ thống mắc lỗi thiên kiến hệ thống, hàng chục ngàn ứng viên có thể bị tước đoạt cơ hội tiếp cận thị trường lao động mà không hề có cơ hội giải trình hay khiếu nại. |
| Dữ liệu nhạy cảm có thể được sử dụng | Dữ liệu nhân khẩu học (giới tính, độ tuổi, chủng tộc, quốc tịch); Dữ liệu sinh trắc học và hình ảnh (khuôn mặt, giọng nói, biểu cảm vi mô); Dữ liệu lịch sử y tế và tình trạng khuyết tật; Dữ liệu hành vi và tính cách qua các bài test tâm lý; Lịch sử mức lương quá khứ và thông tin lý lịch tư pháp. |
| Nhu cầu human review | **Cao (High)**. Cần có chuyên viên nhân sự (HR Specialist) và hội đồng tuyển dụng độc lập kiểm tra và giám sát ở hai thời điểm then chốt: (1) Trước khi gửi thư từ chối ứng viên sơ loại – nhằm đảm bảo không có ứng viên tiềm năng bị loại oan do lỗi thuật toán (False Negative); (2) Kiểm toán định kỳ (Algorithmic Auditing) đối với tỷ lệ vượt qua vòng lọc theo từng nhóm nhân khẩu học để phát hiện kịp thời hiện tượng bất bình đẳng tác động (Disparate Impact). |

---

### 2. Case study 1 – Amazon AI Recruitment Engine (Hệ thống AI sàng lọc hồ sơ tuyển dụng Amazon)

#### Brief Case
- **Tổ chức / sản phẩm AI:** Tập đoàn Amazon (nhóm nghiên cứu phát triển Machine Learning tại Edinburgh, Scotland).
- **Thời gian, địa điểm / bối cảnh:** Phát triển từ năm 2014 đến 2017; điều tra nội bộ phát hiện lỗi và truyền thông quốc tế công bố vào tháng 10/2018; trụ sở tại Seattle, Mỹ và văn phòng Edinburgh, Anh.
- **AI được dùng để làm gì:** Tự động quét, phân tích nội dung hàng trăm ngàn hồ sơ ứng viên (CV/Resume) gửi về công ty và chấm điểm xếp hạng từ 1 đến 5 sao, nhằm tự động đề xuất top 5 ứng viên xuất sắc nhất cho các vị trí kỹ sư phần mềm (Software Development Engineer).
- **Vấn đề hoặc sự kiện đáng chú ý:** Hệ thống phát sinh thiên kiến giới tính nghiêm trọng chống lại phụ nữ. Do được huấn luyện trên dữ liệu hồ sơ tuyển dụng trong quá khứ 10 năm của Amazon (giai đoạn ngành công nghệ do nam giới thống trị áp đảo), mô hình tự học và suy luận rằng ứng viên nam được ưu tiên hơn. Hệ thống tự động phạt điểm các hồ sơ có chứa từ *"women's"* (ví dụ: *"women's chess club captain"*, *"Society of Women Engineers"*) và hạ điểm ứng viên tốt nghiệp từ các trường đại học nữ sinh.
- **Số liệu có nguồn:** 
  - Mô hình được huấn luyện trên kho dữ liệu hồ sơ xin việc tích lũy trong **10 năm** (2004–2014) tại Amazon.
  - Tỷ lệ nhân sự công nghệ của Amazon thời điểm 2014 phản ánh chênh lệch giới tính sâu sắc với **hơn 60% nam giới toàn cầu** và **hơn 70% ở các vị trí kỹ thuật cấp cao**.
  - Đội ngũ kỹ sư đã cố gắng tạo quy tắc trung hòa giới tính cho hơn **500 thuật ngữ cụ thể**, nhưng thuật toán vẫn tự động tìm ra các từ khóa thay thế (proxies) gián tiếp trừng phạt hồ sơ phụ nữ.
  - Đầu năm **2017**, lãnh đạo Amazon đã chính thức quyết định khai tử và giải thể hoàn toàn dự án tuyển dụng này.
- **Nguồn:** Báo cáo điều tra độc quyền của Reuters (Tác giả: Jeffrey Dastin, ngày 10/10/2018: *"Amazon scraps secret AI recruiting tool that showed bias against women"* - URL: https://www.reuters.com/article/world/insight-amazon-scraps-secret-ai-recruiting-tool-that-showed-bias-against-women-idUSKCN1MK08G/).
- **Phân biệt bằng chứng và nhận định:**
  - *Điều nguồn xác nhận:* Amazon đã xây dựng công cụ AI từ 2014, công cụ tự động hạ điểm hồ sơ phụ nữ, các kỹ sư không thể khắc phục triệt để thiên kiến, và ban lãnh đạo đã hủy bỏ dự án vào năm 2017.
  - *Điều nhận định/suy luận của tôi:* Dù Amazon tuyên bố công cụ chưa từng được triển khai độc lập hoàn toàn để ra quyết định tuyển dụng cuối cùng, sự tồn tại của nó đã chứng minh rủi ro cốt tử khi sao chép dữ liệu lịch sử chưa qua xử lý công bằng vào mô hình tự động hóa (Data Grounding Fallacy).

#### Harm Map Worksheet
| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Thời điểm thuật toán AI tự động chấm điểm sao (Ranking 1-5 sao) và lập danh sách lọc hồ sơ sơ tuyển chuyển cho nhà tuyển dụng. |
| Stakeholder bị ảnh hưởng | **[Ứng viên nữ nộp hồ sơ kỹ thuật]** bị **[hạ điểm bất công và tước đoạt cơ hội phỏng vấn]** khi **[thuật toán AI tự động phạt điểm các từ khóa liên quan đến phụ nữ]**; **[Doanh nghiệp Amazon]** bị **[tổn hại danh tiếng thương hiệu và rủi ro pháp lý]** khi **[công cụ AI nội bộ phát sinh thiên kiến phân biệt đối xử]**. |
| Failure mode | **Bias / fairness** (Thiên kiến thuật toán do học từ dữ liệu lịch sử mất cân bằng giới tính nghiêm trọng). |
| Layer bắt đầu lỗi | **Grounding / Data layer** (Dữ liệu huấn luyện lịch sử 10 năm bị thiên lệch nam giới được nạp trực tiếp vào hệ thống mà không có cơ chế tiền xử lý và kiểm định tính đại diện công bằng). |
| Harm xảy ra là gì? | **Đã xảy ra trên thực tế thử nghiệm:** Hồ sơ ứng viên nữ bị trừ điểm bất công; **Nguy cơ tiềm ẩn:** Phân biệt đối xử có tính hệ thống trên quy mô hàng ngàn lao động nếu đưa vào vận hành chính thức. |
| Harm lens | **Opportunity loss** (Mất cơ hội việc làm, thu nhập) & **Dignity loss** (Tổn thương phẩm giá khi bị đánh giá thấp vì giới tính). |
| Severity | **High** (Tác động trực tiếp và nghiêm trọng tới quyền tiếp cận cơ hội việc làm công bằng của phụ nữ). |
| Scale | **Lớn (High)** (Hàng ngàn ứng viên thử nghiệm tại Amazon trong giai đoạn 2014–2017; tiềm năng ảnh hưởng hàng trăm ngàn người nếu mở rộng). |
| Probability | **Cao (High)** (Theo điều tra nội bộ, gần như 100% hồ sơ chứa từ khóa liên quan đến nữ giới trong tập thử nghiệm đều bị hạ điểm). |
| Frequency | **Thường xuyên (High)** (Xảy ra tự động trên mọi lượt quét hồ sơ có đặc điểm liên quan đến nữ giới). |
| Vì sao? | Căn cứ đánh giá: Severity ở mức High vì tước đoạt cơ hội kinh tế; Probability và Frequency ở mức High do mô hình ML học trực tiếp từ dữ liệu lịch sử 10 năm nam giới áp đảo (>60%–70%) và tự động tối ưu hóa việc tìm ứng viên tương đồng với quá khứ. Giới hạn bằng chứng: Amazon đã dừng dự án trước khi đưa vào sản xuất đại trà nên hậu quả ở quy mô thử nghiệm nội bộ. |

---

### 3. Case study 2 – HireVue AI Video Facial Assessment (Hệ thống AI phân tích video nét mặt HireVue)

#### Brief Case
- **Tổ chức / sản phẩm AI:** Công ty HireVue Inc. (Hoa Kỳ) – nền tảng phỏng vấn tuyển dụng kỹ thuật số ứng dụng AI.
- **Thời gian, địa điểm / bối cảnh:** 2014 – 2021; triển khai trên quy mô toàn cầu cho hơn 700 tập đoàn đa quốc gia (bao gồm Unilever, Goldman Sachs, Vodafone, Intel).
- **AI được dùng để làm gì:** Thu thập video phỏng vấn tự động của ứng viên, sử dụng thị giác máy tính và phân tích âm thanh để đo lường biểu cảm vi mô trên nét mặt (facial micro-expressions), ánh mắt, ngữ điệu giọng nói và trường từ vựng; từ đó tính toán ra điểm số *"Employability Score"* để xếp hạng năng lực ứng viên.
- **Vấn đề hoặc sự kiện đáng chú ý:** Hệ thống bị giới khoa học và các tổ chức nhân quyền lên án là "ngụy khoa học" (pseudoscientific phrenology), phán xét sai lệch về tính cách và năng lực làm việc dựa trên diện mạo; gây phân biệt đối xử bất công đối với ứng viên khuyết tật (liệt cơ mặt, dị tật phát âm, tự kỷ) và ứng viên thuộc các nền văn hóa thiểu số có thói quen giao tiếp phi ngôn ngữ khác biệt. Tháng 11/2019, Trung tâm Thông tin Quyền riêng tư Điện tử (EPIC) đã chính thức đệ đơn khiếu nại lên Ủy ban Thương mại Liên bang Hoa Kỳ (FTC) yêu cầu điều tra và xử phạt HireVue.
- **Số liệu có nguồn:**
  - Nền tảng HireVue đã phục vụ hơn **700 doanh nghiệp khách hàng** và thực hiện hơn **19 triệu cuộc phỏng vấn** ứng viên tính đến năm 2021.
  - Đơn khiếu nại của tổ chức EPIC đệ trình lên FTC ngày **06/11/2019** dài **42 trang**, cáo buộc hệ thống vi phạm Đạo luật FTC Act (Mục 5) về các hành vi thương mại gian lận và không công bằng.
  - Dưới sức ép pháp lý và kết quả kiểm toán độc lập của hãng kiểm toán thuật toán ORCAA (O’Neil Risk Consulting & Algorithmic Auditing), đầu năm **2021**, HireVue đã buộc phải thông báo chính thức gỡ bỏ 100% tính năng phân tích biểu cảm khuôn mặt khỏi nền tảng.
- **Nguồn:**
  - Đơn khiếu nại của EPIC lên FTC: Electronic Privacy Information Center (EPIC), *"In re HireVue - FTC Complaint on Deceptive and Unfair AI Hiring Practices"* (06/11/2019 - URL: https://epic.org/documents/in-the-matter-of-hirevue-inc/).
  - Báo cáo về quyết định gỡ bỏ tính năng: The Washington Post (Tác giả: Drew Harwell, ngày 31/01/2021: *"Rights group pushes FTC to investigate AI hiring software used by big companies"* - URL: https://www.washingtonpost.com/technology/2021/01/31/hirevue-drops-facial-monitoring/).
- **Phân biệt bằng chứng và nhận định:**
  - *Điều nguồn xác nhận:* HireVue đã phân tích khuôn mặt trên hàng triệu cuộc phỏng vấn thực tế, bị tổ chức bảo vệ quyền riêng tư đệ đơn lên FTC vì thiếu bằng chứng khoa học vững chắc và có nguy cơ phân biệt đối xử, và hãng đã chính thức dừng công nghệ quét nét mặt từ năm 2021.
  - *Điều nhận định/suy luận của tôi:* Việc gán ghép chuyển động cơ mặt với năng lực làm việc là một sai lầm nghiêm trọng về mô hình hóa (Model Layer Failure) do biểu cảm phi ngôn ngữ phụ thuộc rất lớn vào bối cảnh văn hóa, tâm lý và sinh học của từng cá nhân.

#### Harm Map Worksheet
| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Thời điểm hệ thống phân tích tín hiệu video phỏng vấn và xuất điểm xếp hạng Employability Score cho nhà tuyển dụng để quyết định cho qua hay loại ứng viên. |
| Stakeholder bị ảnh hưởng | **[Ứng viên khuyết tật, người tự kỷ và người thuộc văn hóa thiểu số]** bị **[đánh giá thấp và loại khỏi quy trình tuyển dụng]** khi **[AI chấm điểm năng lực dựa trên phân tích nét mặt]**; **[Nhà tuyển dụng]** bị **[đánh mất nhân tài và vướng khiếu nại pháp lý]** khi **[phụ thuộc vào thuật toán ngụy khoa học]**. |
| Failure mode | **Harmful advice / Over-reliance & Bias** (Cung cấp phán đoán sai lệch, phi khoa học về năng lực con người; nhà tuyển dụng tin tưởng mù quáng vào điểm số tự động). |
| Layer bắt đầu lỗi | **Model Layer** (Giả định khoa học của mô hình sai lầm cơ bản khi xem chuyển động cơ mặt là thước đo năng lực lao động; thiếu dữ liệu đại diện cho người khuyết tật và đa dạng thần kinh - neurodiversity). |
| Harm xảy ra là gì? | **Đã xảy ra trên thực tế:** Hàng ngàn ứng viên bị loại khỏi quy trình tuyển dụng bởi thuật toán thiếu minh bạch và không có cơ sở khoa học; **Nguy cơ tiềm ẩn:** Bình thường hóa việc phán xét con người qua diện mạo trong toàn ngành nhân sự. |
| Harm lens | **Opportunity loss** (Mất cơ hội việc làm) & **Dignity loss** (Bị máy móc phán xét nhân cách và phẩm giá dựa trên đặc điểm thể chất bên ngoài). |
| Severity | **High** (Tác động sâu rộng tới quyền bình đẳng tiếp cận việc làm của người khuyết tật và các nhóm thiểu số). |
| Scale | **Rất lớn (Very High)** (Triển khai trên hơn **19 triệu lượt phỏng vấn** của hơn **700 doanh nghiệp** trên toàn cầu). |
| Probability | **Cao (High)** (Rất cao đối với các ứng viên có khiếm khuyết vận động cơ mặt hoặc thuộc các nhóm văn hóa không có thói quen nhìn thẳng vào camera). |
| Frequency | **Thường xuyên (High)** (Xảy ra lặp đi lặp lại trên mọi video phỏng vấn được AI chấm điểm). |
| Vì sao? | Căn cứ đánh giá: Severity và Scale ở mức rất lớn vì hơn 19 triệu cuộc phỏng vấn tại 700 công ty toàn cầu đã áp dụng; Probability và Frequency cao vì hệ thống chạy mặc định trên toàn bộ video nộp vào. Nguồn bằng chứng: Xác nhận qua 42 trang đơn khiếu nại của tổ chức EPIC gửi FTC và kiểm toán của ORCAA buộc HireVue phải xóa bỏ tính năng này năm 2021. |

---

### 4. Case study 3 – Vụ kiện thuật toán sàng lọc Workday AI (Mobley v. Workday, Inc.)

#### Brief Case
- **Tổ chức / sản phẩm AI:** Tập đoàn Workday, Inc. (hệ thống công cụ AI sàng lọc và tuyển dụng nhân tài tích hợp trong Workday Human Capital Management).
- **Thời gian, địa điểm / bối cảnh:** 2023 – 2024; Tòa án Quận Bắc California, Hoa Kỳ (U.S. District Court for the Northern District of California), Thẩm phán liên bang Rita F. Lin thụ lý.
- **AI được dùng để làm gì:** Tự động lọc hồ sơ, xếp hạng và loại bỏ các ứng viên nộp đơn trước khi hồ sơ đến tay chuyên viên tuyển dụng con người của các doanh nghiệp khách hàng sử dụng phần mềm Workday.
- **Vấn đề hoặc sự kiện đáng chú ý:** Nguyên đơn Derek Mobley (một người Mỹ gốc Phi trên 40 tuổi và mắc chứng rối loạn lo âu/trầm cảm) đã nộp hồ sơ vào hơn 100 vị trí tuyển dụng khác nhau tại các công ty lớn sử dụng nền tảng Workday nhưng đều bị từ chối tự động gần như tức thì dù có bằng cấp cử nhân tài chính và dày dặn kinh nghiệm làm việc. Đơn kiện tập thể (Class Action) cáo buộc thuật toán AI của Workday có thiên kiến mang tính hệ thống chống lại người da đen, người trên 40 tuổi và người khuyết tật, vi phạm Đạo luật Dân quyền Title VII, ADEA và ADA.
- **Số liệu có nguồn:**
  - Derek Mobley đã nộp hồ sơ vào **hơn 100 vị trí công việc** tại các tập đoàn lớn sử dụng Workday từ năm 2017 đến 2023 và đều bị từ chối tự động.
  - Vụ kiện đại diện cho **hàng ngàn ứng viên** có hoàn cảnh tương tự trên khắp nước Mỹ.
  - Ngày **12/07/2024**, Thẩm phán Rita F. Lin đã ban hành phán quyết pháp lý mang tính bước ngoặt dài **30 trang**, chính thức bác bỏ yêu cầu hủy vụ kiện của Workday, khẳng định các công ty cung cấp phần mềm AI tuyển dụng có thể bị quy trách nhiệm như một *"Đại lý việc làm"* (Employment Agency) theo Đạo luật Dân quyền liên bang nếu thuật toán của họ thay thế con người quyết định ai bị loại.
- **Nguồn:**
  - Văn bản phán quyết của Tòa án Liên bang: U.S. District Court Northern District of California, Case No. 23-cv-00770-RFL, *Derek Mobley v. Workday, Inc.* (Phán quyết ngày 12/07/2024 - Order Granting in Part and Denying in Part Motion to Dismiss).
  - Bản tin pháp lý quốc tế: Reuters / Bloomberg Law (Tác giả: Patrick Dorrian, ngày 15/07/2024: *"Workday Must Face Landmark Bias Suit Over AI Hiring Software"* - URL: https://news.bloomberglaw.com/daily-labor-report/workday-must-face-landmark-bias-suit-over-ai-hiring-software).
- **Phân biệt bằng chứng và nhận định:**
  - *Điều nguồn xác nhận:* Tòa án liên bang Mỹ đã thụ lý vụ kiện, xác nhận thẩm quyền và trách nhiệm pháp lý trực tiếp của đơn vị cung cấp AI tuyển dụng Workday; nguyên đơn bị từ chối liên tiếp trên 100 lần bởi hệ thống.
  - *Điều nhận định/suy luận của tôi:* Dù vụ kiện đang trong quá trình xét xử tiếp theo về nội dung vi phạm thực tế, phán quyết của tòa án đã xác lập một án lệ pháp lý cực kỳ quan trọng: nhà phát triển AI không thể trốn tránh trách nhiệm đằng sau bức bình phong "thuật toán chỉ là công cụ hỗ trợ".

#### Harm Map Worksheet
| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Thời điểm thuật toán Workday tự động quét hàng triệu hồ sơ ứng viên và đưa ra quyết định từ chối (Rejection) ngay lập tức mà không có sự thẩm định hay phê duyệt của con người. |
| Stakeholder bị ảnh hưởng | **[Ứng viên da màu, người lao động trên 40 tuổi và người khuyết tật]** bị **[từ chối việc làm tự động hàng loạt không rõ nguyên nhân]** khi **[thuật toán Workday loại hồ sơ qua các biến số gián tiếp mà không có con người giám sát]**; **[Doanh nghiệp khách hàng của Workday]** bị **[liên đới trách nhiệm pháp lý trong vụ kiện phân biệt đối xử tập thể]** khi **[triển khai công cụ AI sàng lọc thiếu kiểm toán độc lập]**. |
| Failure mode | **Bias / fairness & Escalation failure** (Thiên kiến cấu trúc theo tuổi tác, chủng tộc, bệnh lý và không có kênh khiếu nại hay chuyển giao cho con người can thiệp khi bị loại tự động). |
| Layer bắt đầu lỗi | **Grounding & Model Layer** (Mô hình sử dụng các biến số gián tiếp - proxies như năm tốt nghiệp đại học, địa điểm, khoảng thời gian ngắt quãng trong CV để gán nhãn loại trừ ứng viên). |
| Harm xảy ra là gì? | **Đã xảy ra trên thực tế:** Hơn 100 lần từ chối việc làm bất công đối với cá nhân nguyên đơn và hàng ngàn ứng viên tiềm năng khác; **Nguy cơ tiềm ẩn:** Tạo rào cản ngăn chặn sự đa dạng và hòa nhập xã hội một cách vô hình. |
| Harm lens | **Opportunity loss** (Tước đoạt cơ hội việc làm, mất thu nhập sinh kế) & **Dignity loss** (Cảm giác bất lực khi đối mặt với hệ thống từ chối hộp đen không thể phản hồi). |
| Severity | **High** (Tác động trực tiếp đến quyền mưu sinh hợp pháp và quyền bình đẳng lao động theo hiến pháp và pháp luật). |
| Scale | **Rất lớn (Very High)** (Hệ thống Workday quản trị hàng chục triệu hồ sơ tuyển dụng mỗi năm cho hàng ngàn tập đoàn lớn trên toàn cầu). |
| Probability | **Cao (High)** (Tỷ lệ bị từ chối tự động đối với các hồ sơ có đặc điểm nhân khẩu học tương tự nguyên đơn là cực kỳ cao, trên 100/100 vị trí). |
| Frequency | **Thường xuyên (High)** (Hệ thống chạy tự động liên tục 24/7 trên toàn bộ các cổng tuyển dụng của khách hàng). |
| Vì sao? | Căn cứ đánh giá: Severity và Scale ở mức rất lớn vì Workday là nền tảng quản trị nhân sự hàng đầu thế giới; Probability và Frequency cao vì hệ thống hoạt động khép kín theo cơ chế hộp đen (Black box), loại tự động trước khi tới tay con người. Nguồn bằng chứng: Phán quyết dài 30 trang của Tòa án Liên bang Mỹ (U.S. District Court, 12/07/2024) khẳng định nhà cung cấp phần mềm AI tuyển dụng phải chịu trách nhiệm như đại lý việc làm. |

---

### 5. Kết luận và Khuyến nghị Responsible AI cho Ngành HR

Từ 3 case study thực tế kinh điển trên, có thể rút ra các bài học cốt tử để phát triển và ứng dụng AI có trách nhiệm (Responsible AI) trong tuyển dụng:
1. **Thiết lập Human-in-the-loop bắt buộc:** Tuyệt đối không để AI đưa ra quyết định từ chối ứng viên một cách tự động (Autonomous Rejection). Mọi quyết định loại hồ sơ phải có sự xem xét và phê duyệt của con người.
2. **Kiểm toán thuật toán độc lập (Algorithmic Auditing):** Doanh nghiệp phải thực hiện kiểm toán định kỳ bởi bên thứ ba đối với tỷ lệ lựa chọn ứng viên theo các nhóm nhân khẩu học (quy tắc 4/5 - Four-Fifths Rule trong luật lao động Mỹ) để phát hiện và ngăn chặn kịp thời Disparate Impact.
3. **Minh bạch và Quyền giải trình (Transparency & Recourse):** Cung cấp cho ứng viên quyền được biết khi nào AI được sử dụng trong quy trình tuyển dụng và cơ chế khiếu nại (Escalation channel) để yêu cầu chuyên viên con người phúc khảo hồ sơ khi có nghi ngờ về tính công bằng.
4. **Loại bỏ các thước đo ngụy khoa học:** Nghiêm cấm ứng dụng các mô hình phán xét cảm xúc, cử động khuôn mặt hay ngôn ngữ cơ thể vào việc đánh giá năng lực nghề nghiệp của người lao động.
