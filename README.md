<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bói Toán 12 Con Giáp - Tử Vi Tổng Hợp</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700;900&display=swap" rel="stylesheet">
    <style>
        /* Thiết lập font Playfair Display cho toàn bộ body */
        body {
            font-family: 'Playfair Display', serif; /* Áp dụng font thư pháp cho toàn bộ văn bản */
            background: linear-gradient(135deg, #8B4513 0%, #B8860B 50%, #DAA520 100%); /* Nền vàng nâu đậm sang trọng */
            min-height: 100vh;
            color: #FFFFFF;
            position: relative;
            overflow: hidden; 
        }
        
        /* Hiệu ứng "Vàng ròng bay" cho nền (tăng cường) */
        body::before {
            content: '';
            position: fixed;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" opacity="0.1"><circle cx="20" cy="20" r="8" fill="%23FFEB3B" /><circle cx="80" cy="30" r="5" fill="%23FFEE58" /><circle cx="50" cy="70" r="10" fill="%23FFD700" /><circle cx="10" cy="90" r="6" fill="%23FFC700" /><circle cx="90" cy="10" r="12" fill="%23FDD835" /></svg>');
            background-size: 100px 100px;
            animation: goldFly 90s linear infinite; /* Chạy nhanh hơn */
            z-index: -2;
            opacity: 0.4; /* Sáng hơn */
            filter: blur(1.5px); /* Mờ hơn để tạo chiều sâu */
        }

        @keyframes goldFly {
            0% { transform: translate(0, 0) rotate(0deg); }
            100% { transform: translate(-300px, -300px) rotate(360deg); } /* Dịch chuyển nhiều hơn */
        }

        /* KHỐI HIỆU ỨNG CON GIÁP BAY LUNG TUNG (Tăng Cường) */
        #background-zodiac-effect {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            overflow: hidden;
            z-index: -1;
        }

        .zodiac-flying-item {
            position: absolute;
            font-size: 3.5rem; /* Kích thước lớn hơn */
            color: #FFD700; /* Màu vàng kim */
            opacity: 0.4; /* Rõ ràng hơn */
            animation-iteration-count: infinite;
            animation-timing-function: ease-in-out; /* Chuyển động mượt mà hơn */
            text-shadow: 0 0 15px rgba(255, 255, 255, 0.8), 0 0 5px #FF8C00; /* Hiệu ứng phát sáng mạnh */
        }

        /* Các keyframes cho hiệu ứng bay lung tung (lớn hơn và nhanh hơn) */
        @keyframes flyX {
            from { transform: translateX(0); }
            to { transform: translateX(var(--translate-x-to)); }
        }
        @keyframes flyY {
            from { transform: translateY(0); }
            to { transform: translateY(var(--translate-y-to)); }
        }
        @keyframes rotateZ {
            from { transform: rotate(0deg); }
            to { transform: rotate(var(--rotate-to)); }
        }
        
        /* Style cho nút chính (Lung linh) */
        #fortuneButton {
            background-color: #FFD700; /* Vàng kim */
            color: #8B0000; /* Chữ đỏ đô trên nền vàng */
            font-weight: 900;
            transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
            box-shadow: 0 8px 25px rgba(255, 215, 0, 0.9), 0 0 5px #FFFFFF; /* Bóng sáng mạnh mẽ */
            letter-spacing: 3px;
            border: 4px solid #B8860B; /* Viền vàng đậm */
            text-transform: uppercase;
        }
        #fortuneButton:hover {
            background-color: #FFC700;
            box-shadow: 0 12px 30px rgba(255, 215, 0, 1), 0 0 10px #FFFFFF;
            transform: translateY(-5px) scale(1.05); /* Hiệu ứng 3D nổi */
        }

        /* Màu chữ và khối nội dung (Nổi bật) */
        h1, h2, h3 {
            color: #8B0000; /* Tiêu đề Đỏ Đô */
            font-weight: 900;
            text-shadow: 1px 1px 2px rgba(255, 255, 255, 0.8); /* Thêm bóng trắng cho tiêu đề */
        }
        p, label {
            color: #4A3C1F; /* Chữ thường màu nâu đậm */
        }

        /* Điều chỉnh màu nền của các khối chính */
        .bg-white\/80 { 
            background-color: rgba(255, 250, 205, 0.95); /* Gần như trắng tinh để nổi bật */
            border: 3px solid #FFD700;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3); /* Bóng sâu */
        } 
        .bg-white\/95 { 
            background-color: rgba(255, 255, 255, 0.98); 
            border: 5px solid #FFC700; 
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.5); /* Bóng cực sâu */
        }

        /* Màu sắc cho nội dung */
        .text-red-600 { color: #CD5C5C; } 
        .text-red-700 { color: #8B0000; } 
        .text-green-700 { color: #006400; }
        .text-blue-700 { color: #191970; }
        .text-yellow-800 { color: #B8860B; } 
    </style>
</head>
<body class="p-4 sm:p-8">

    <!-- KHỐI CHỨA CÁC CON GIÁP BAY -->
    <div id="background-zodiac-effect"></div>

    <div class="max-w-4xl mx-auto relative z-10">

        <!-- TIÊU ĐỀ -->
        <div class="text-center mb-10 p-4 bg-white/80 backdrop-blur-sm rounded-xl shadow-lg border-b-4 border-yellow-500">
            <h1 class="text-5xl mb-3 tracking-tight">
                <span class="text-6xl">🌟</span> LỤC THẬP HOA GIÁP & TỬ VI TRỌN ĐỜI <span class="text-6xl">🌟</span>
            </h1>
            <p class="text-xl font-medium">Bói toán tổng hợp theo Ngày, Tháng và Năm sinh</p>
            <p class="text-sm text-red-500 mt-2">Phạm vi dữ liệu: Năm sinh từ 1945 đến 2025.</p>
        </div>

        <!-- KHỐI NHẬP LIỆU -->
        <div id="inputBlock" class="bg-white/90 p-6 sm:p-8 rounded-xl shadow-2xl border-t-4 border-yellow-500 mb-10">
            <h2 class="text-3xl font-bold mb-6">NHẬP THÔNG TIN CHIÊM TINH</h2>
            <form id="fortuneForm" class="space-y-4">
                <div>
                    <label for="nameInput" class="block text-sm font-medium">Tên của bạn:</label>
                    <input type="text" id="nameInput" placeholder="Ví dụ: Nguyễn Văn A" required
                           class="mt-1 block w-full px-4 py-2 border rounded-lg shadow-sm focus:ring-yellow-500 focus:border-yellow-500">
                </div>

                <div class="grid grid-cols-3 gap-4">
                    <div>
                        <label for="dayInput" class="block text-sm font-medium">Ngày sinh (*):</label>
                        <input type="number" id="dayInput" min="1" max="31" placeholder="1-31" required
                               class="mt-1 block w-full px-4 py-2 border rounded-lg shadow-sm focus:ring-yellow-500 focus:border-yellow-500">
                    </div>
                    <div>
                        <label for="monthInput" class="block text-sm font-medium">Tháng sinh (*):</label>
                        <input type="number" id="monthInput" min="1" max="12" placeholder="1-12" required
                               class="mt-1 block w-full px-4 py-2 border rounded-lg shadow-sm focus:ring-yellow-500 focus:border-yellow-500">
                    </div>
                    <div>
                        <label for="yearInput" class="block text-sm font-medium">Năm sinh (*):</label>
                        <input type="number" id="yearInput" min="1945" max="2025" placeholder="1945 - 2025" required
                               class="mt-1 block w-full px-4 py-2 border rounded-lg shadow-sm focus:ring-yellow-500 focus:border-yellow-500">
                    </div>
                </div>

                <button type="submit" id="fortuneButton"
                        class="w-full py-3 mt-6 text-xl rounded-lg shadow-md focus:outline-none focus:ring-4 focus:ring-yellow-300 uppercase">
                    Tìm Hiểu Vận Mệnh Của Tôi
                </button>
            </form>
        </div>

        <!-- KHỐI KẾT QUẢ -->
        <div id="resultContainer" class="mt-12 hidden">
            <h2 class="text-4xl font-extrabold text-center mb-6">📜 BẢN LUẬN GIẢI TỔNG HỢP 📜</h2>
            <div id="resultContent" class="bg-white/95 p-6 sm:p-10 rounded-xl shadow-2xl border-t-8 border-yellow-600">
                <!-- Nội dung kết quả được chèn vào đây bởi JS -->
            </div>
        </div>
    </div>
    
    <!-- MESSAGE BOX (CUSTOM ALERT) -->
    <div id="messageBox" class="fixed top-5 right-5 p-4 rounded-lg text-white font-semibold shadow-xl hidden" style="z-index: 1000;"></div>

    <script>
        // --- CƠ SỞ DỮ LIỆU TĨNH (STATIC DATA) ---
        const ZODIAC_NAMES = ['Tý', 'Sửu', 'Dần', 'Mão', 'Thìn', 'Tỵ', 'Ngọ', 'Mùi', 'Thân', 'Dậu', 'Tuất', 'Hợi'];
        const ZODIAC_EMOJIS = ['🐀', '🐂', '🐅', '🐇', '🐉', '🐍', '🐎', '🐐', '🐒', '🐓', '🐕', '🐖'];
        const CAN_NAMES = ['Giáp', 'Ất', 'Bính', 'Đinh', 'Mậu', 'Kỷ', 'Canh', 'Tân', 'Nhâm', 'Quý'];
        
        // Mệnh Ngũ Hành của 10 Thiên Can
        const NGU_HANH = {
            'Giáp': { Hanh: 'Mộc', Mau: 'Xanh lục', ChiTiet: 'Mệnh đại lâm mộc (Cây lớn trong rừng). Người có mệnh Mộc thường năng động, có tinh thần cầu tiến, thích giúp đỡ người khác và có tính cách cương trực.' },
            'Ất': { Hanh: 'Mộc', Mau: 'Xanh lục', ChiTiet: 'Mệnh đại lâm mộc (Cây lớn trong rừng). Người có mệnh Mộc thường năng động, có tinh thần cầu tiến, thích giúp đỡ người khác và có tính cách cương trực.' },
            'Bính': { Hanh: 'Hỏa', Mau: 'Đỏ, tím', ChiTiet: 'Mệnh lư trung hỏa (Lửa trong lò). Người có mệnh Hỏa thường đam mê, nhiệt huyết, sống có mục tiêu rõ ràng và luôn chủ động trong mọi việc.' },
            'Đinh': { Hanh: 'Hỏa', Mau: 'Đỏ, tím', ChiTiet: 'Mệnh lư trung hỏa (Lửa trong lò). Người có mệnh Hỏa thường đam mê, nhiệt huyết, sống có mục tiêu rõ ràng và luôn chủ động trong mọi việc.' },
            'Mậu': { Hanh: 'Thổ', Mau: 'Vàng, nâu', ChiTiet: 'Mệnh đại trạch thổ (Đất nền nhà lớn). Người có mệnh Thổ thường có tính cách trầm ổn, đáng tin cậy, sống thực tế và biết giữ lời hứa.' },
            'Kỷ': { Hanh: 'Thổ', Mau: 'Vàng, nâu', ChiTiet: 'Mệnh đại trạch thổ (Đất nền nhà lớn). Người có mệnh Thổ thường có tính cách trầm ổn, đáng tin cậy, sống thực tế và biết giữ lời hứa.' },
            'Canh': { Hanh: 'Kim', Mau: 'Trắng, bạc', ChiTiet: 'Mệnh bạch lạp kim (Vàng trong nến). Người có mệnh Kim thường sắc sảo, kiên định, có khả năng tổ chức tốt và thích sự rõ ràng, công bằng.' },
            'Tân': { Hanh: 'Kim', Mau: 'Trắng, bạc', ChiTiet: 'Mệnh bạch lạp kim (Vàng trong nến). Người có mệnh Kim thường sắc sảo, kiên định, có khả năng tổ chức tốt và thích sự rõ ràng, công bằng.' },
            'Nhâm': { Hanh: 'Thủy', Mau: 'Đen, xanh đậm', ChiTiet: 'Mệnh đại hải thủy (Nước biển lớn). Người có mệnh Thủy thường linh hoạt, thông minh, có trực giác nhạy bén và biết cách đối nhân xử thế.' },
            'Quý': { Hanh: 'Thủy', Mau: 'Đen, xanh đậm', ChiTiet: 'Mệnh đại hải thủy (Nước biển lớn). Người có mệnh Thủy thường linh hoạt, thông minh, có trực giác nhạy bén và biết cách đối nhân xử thế.' }
        };

        // Mô tả vận hạn chung chi tiết cho từng Địa Chi (Năm sinh)
        const YEAR_FORTUNES = {
            'Tý': { Title: "Tuổi Chuột - Thông minh và Nhanh nhẹn", Detail: "Người tuổi Tý luôn nổi bật với trí tuệ sắc bén, khả năng thích nghi và sự khéo léo trong giao tiếp. Vận hạn thường thịnh vượng về tiền bạc, nhưng cần cẩn trọng trong các mối quan hệ xã hội phức tạp." },
            'Sửu': { Title: "Tuổi Trâu - Kiên cường và Đáng tin", Detail: "Sửu là biểu tượng của sự chăm chỉ, kiên nhẫn và bền bỉ. Vận mệnh của họ là 'chậm mà chắc', thành công đến từ sự tích lũy và nỗ lực không ngừng. Điểm yếu là tính cách đôi khi quá cố chấp." },
            'Dần': { Title: "Tuổi Hổ - Dũng mãnh và Lãnh đạo", Detail: "Người tuổi Dần là những người sinh ra để làm lãnh đạo, họ mạnh mẽ, dũng cảm và tràn đầy nhiệt huyết. Sự nghiệp thường thăng tiến nhanh chóng. Tuy nhiên, tính cách nóng nảy có thể dẫn đến thất bại." },
            'Mão': { Title: "Tuổi Mèo - Hiền hòa và Tinh tế", Detail: "Mão là con giáp hiền lành, nhân hậu, có tài năng về nghệ thuật và giao tiếp khéo léo. Vận hạn ít sóng gió, thích hợp với môi trường làm việc sáng tạo. Cần chú ý rèn luyện ý chí, tránh bị người khác lợi dụng." },
            'Thìn': { Title: "Tuổi Rồng - Quyền quý và Tham vọng", Detail: "Thìn là con giáp tượng trưng cho quyền lực, may mắn và sự cao quý. Vận trình thường có quý nhân phù trợ, dễ dàng gặt hái thành công vang dội. Họ cần đề phòng sự kiêu ngạo." },
            'Tỵ': { Title: "Tuổi Rắn - Sâu sắc và Khôn ngoan", Detail: "Tỵ là con giáp thông minh, sâu sắc, có trực giác phi thường. Vận mệnh ổn định, tài lộc thường đến từ sự đầu tư cẩn thận. Họ cần học cách mở lòng hơn, tránh cô lập bản thân quá mức." },
            'Ngọ': { Title: "Tuổi Ngựa - Năng động và Phóng khoáng", Detail: "Người tuổi Ngọ yêu thích tự do, đam mê khám phá và luôn tràn đầy năng lượng tích cực. Vận trình thường thay đổi liên tục, có nhiều cơ hội đi xa. Tuy nhiên, tính cách quá vội vàng có thể khiến họ bỏ lỡ chi tiết quan trọng." },
            'Mùi': { Title: "Tuổi Dê - Dịu dàng và Sáng tạo", Detail: "Mùi là con giáp nhân hậu, dịu dàng, có tâm hồn nghệ sĩ. Vận hạn thường bình yên, được người thân yêu thương, che chở. Cần rèn luyện lòng can đảm để tự mình vượt qua khó khăn." },
            'Thân': { Title: "Tuổi Khỉ - Lanh lợi và Linh hoạt", Detail: "Người tuổi Thân thông minh, hoạt bát, có tài ứng biến nhanh nhạy. Vận trình phát triển mạnh mẽ trong lĩnh vực cần sự linh hoạt. Cần cẩn thận trong việc quản lý tài chính, tránh xa những trò may rủi." },
            'Dậu': { Title: "Tuổi Gà - Tỉ mỉ và Chính trực", Detail: "Dậu là con giáp chăm chỉ, ngăn nắp, luôn theo đuổi sự hoàn hảo. Vận hạn có uy tín lớn, dễ thành công trong nghề nghiệp đòi hỏi sự chính xác. Cần học cách mềm dẻo hơn trong lời nói để duy trì hòa khí." },
            'Tuất': { Title: "Tuổi Chó - Trung thành và Trách nhiệm", Detail: "Người tuổi Tuất là biểu tượng của sự trung thành, chân thật và sống có trách nhiệm. Vận mệnh ổn định, thích hợp với các nghề nghiệp liên quan đến pháp luật. Họ cần tránh lo nghĩ quá nhiều." },
            'Hợi': { Title: "Tuổi Heo - Hạnh phúc và May mắn", Detail: "Hợi là con giáp tượng trưng cho sự may mắn, phúc lộc và cuộc sống an nhàn. Vận trình ít phải lo toan về vật chất, thường được quý nhân phù trợ. Tuy nhiên, cần tránh sự lười biếng và xa hoa quá mức." }
        };
        
        // Mô tả vận hạn chung chi tiết cho từng Tháng Sinh
        const MONTH_FORTUNES = {
            1: "Sinh vào tháng Giêng (Dần): Đây là tháng của khởi đầu, người sinh vào tháng này có tính cách mạnh mẽ, đầy tham vọng và có tố chất lãnh đạo bẩm sinh. Vận mệnh thường gặp nhiều may mắn trong sự nghiệp.",
            2: "Sinh vào tháng Hai (Mão): Người tháng 2 có tài năng nghệ thuật, tinh tế và nhạy cảm. Họ khéo léo trong giao tiếp, dễ được người khác yêu mến. Vận trình tình cảm thuận lợi.",
            3: "Sinh vào tháng Ba (Thìn): Có ý chí mạnh mẽ, thông minh xuất chúng và dũng cảm. Người này có vận khí tốt, dễ đạt được thành tựu lớn. Cần đề phòng tính cách kiêu ngạo.",
            4: "Sinh vào tháng Tư (Tỵ): Trầm tĩnh, có trực giác mạnh và khả năng phân tích sâu sắc. Họ thích hợp làm công việc cần sự suy nghĩ, nghiên cứu. Vận mệnh ổn định, tài lộc đến từ sự cẩn trọng.",
            5: "Sinh vào tháng Năm (Ngọ): Nhiệt tình, cởi mở, có tinh thần lạc quan và yêu thích sự tự do. Họ là người có tài kinh doanh. Vận trình năng động, nhưng cần tránh hành động bốc đồng.",
            6: "Sinh vào tháng Sáu (Mùi): Dịu dàng, nhân hậu, có đời sống nội tâm phong phú. Người này có duyên với gia đạo, thường có cuộc sống hôn nhân và gia đình viên mãn.",
            7: "Sinh vào tháng Bảy (Thân): Lanh lợi, nhanh nhẹn, có nhiều tài lẻ và khả năng ứng biến linh hoạt. Họ có vận may trong học tập và khám phá, nhưng cần tránh xa những cám dỗ phù phiếm.",
            8: "Sinh vào tháng Tám (Dậu): Chính trực, tỉ mỉ, có khả năng tổ chức và quản lý xuất sắc. Họ có uy tín trong công việc, dễ dàng thăng tiến. Cần tránh tính cách quá cầu toàn.",
            9: "Sinh vào tháng Chín (Tuất): Trung thực, đáng tin cậy, sống có trách nhiệm cao. Vận mệnh ổn định, được mọi người kính trọng. Sự nghiệp vững chắc nhưng ít đột phá lớn.",
            10: "Sinh vào tháng Mười (Hợi): Hào sảng, phóng khoáng, có tâm hồn thiện lương. Họ có vận lộc về tài chính, nhưng cần học cách quản lý tiền bạc để tránh lãng phí.",
            11: "Sinh vào tháng Mười Một (Tý): Tài trí hơn người, có óc kinh doanh nhạy bén. Vận mệnh giàu sang, nhưng cần cẩn trọng trong các quyết định lớn liên quan đến đầu tư.",
            12: "Sinh vào tháng Mười Hai (Sửu): Kiên nhẫn, bền bỉ, có khả năng chịu đựng. Họ là người làm việc có kế hoạch, thành công đến muộn nhưng vô cùng vững vàng và bền lâu."
        };
        
        // Mô tả tính cách theo Ngày sinh (dữ liệu đơn giản, tượng trưng)
        const DAY_FORTUNES = {
            'odd': "Người sinh vào ngày Lẻ (1, 3, 5...) thường mang tính Dương, có xu hướng hoạt bát, mạnh mẽ, hướng ngoại và quyết đoán. Bạn thích tự mình dẫn dắt và ít khi chịu khuất phục trước khó khăn.",
            'even': "Người sinh vào ngày Chẵn (2, 4, 6...) thường mang tính Âm, có xu hướng trầm tĩnh, nội tâm, cẩn thận và chu đáo. Bạn là người đáng tin cậy, sống tình cảm và coi trọng sự ổn định."
        };


        // --- CHỨC NĂNG (FUNCTIONS) ---

        /**
         * Hiển thị thông báo (thay thế cho alert())
         * @param {string} message - Nội dung thông báo
         * @param {string} type - 'error' hoặc 'success'
         */
        function showMessage(message, type) {
            const msgBox = document.getElementById('messageBox');
            msgBox.textContent = message;
            msgBox.className = 'fixed top-5 right-5 p-4 rounded-lg text-white font-semibold shadow-xl transition-opacity duration-300 z-50';

            if (type === 'error') {
                msgBox.classList.add('bg-red-700'); /* Màu đỏ đậm cho lỗi */
            } else {
                msgBox.classList.add('bg-green-700'); /* Màu xanh đậm cho thành công */
            }
            
            msgBox.classList.remove('hidden');
            setTimeout(() => {
                msgBox.classList.add('opacity-0');
                setTimeout(() => msgBox.classList.add('hidden'), 300);
            }, 5000);
            msgBox.classList.remove('opacity-0');
        }

        /**
         * Tính toán Can Chi và Con Giáp của năm sinh
         * @param {number} year - Năm sinh
         * @returns {object} { zodiacName, canChiName, animalName, fortuneText }
         */
        function getZodiacInfo(year) {
            const baseYear = 1924; // Giáp Tý
            const offset = year - baseYear;
            
            // 1. Tính Địa Chi (Con Giáp) - Chu kỳ 12
            const diaChiIndex = (offset % 12 + 12) % 12; 
            const animalName = ZODIAC_NAMES[diaChiIndex];
            const animalEmoji = ZODIAC_EMOJIS[diaChiIndex];
            
            // 2. Tính Thiên Can - Chu kỳ 10
            const thienCanIndex = (offset % 10 + 10) % 10;
            const canName = CAN_NAMES[thienCanIndex];
            
            // 3. Kết hợp
            const canChiName = `${canName} ${animalName}`;
            
            // 4. Mệnh Ngũ Hành
            const nguHanhInfo = NGU_HANH[canName];
            
            // 5. Vận hạn chung theo năm sinh
            const yearFortune = YEAR_FORTUNES[animalName];

            return {
                zodiacName: animalName,
                zodiacEmoji: animalEmoji,
                canChiName: canChiName,
                nguHanh: nguHanhInfo,
                yearFortune: yearFortune
            };
        }

        /**
         * Hàm chính để xem vận hạn và hiển thị kết quả
         */
        function getFortuneAndDisplay(event) {
            event.preventDefault();

            const name = document.getElementById('nameInput').value.trim();
            const dayStr = document.getElementById('dayInput').value.trim();
            const monthStr = document.getElementById('monthInput').value.trim();
            const yearStr = document.getElementById('yearInput').value.trim();
            
            const day = parseInt(dayStr, 10);
            const month = parseInt(monthStr, 10);
            const year = parseInt(yearStr, 10);
            
            // 1. Kiểm tra đầu vào
            if (!name || !dayStr || !monthStr || !yearStr) {
                 showMessage("Vui lòng nhập đầy đủ Tên, Ngày, Tháng và Năm sinh.", 'error');
                return;
            }

            // 2. Kiểm tra năm sinh hợp lệ (1945 - 2025)
            if (year < 1945 || year > 2025) {
                showMessage(`Chúng tôi không có dữ liệu về các năm: ${year}. Vui lòng nhập năm trong khoảng 1945 - 2025.`, 'error');
                return;
            }
            
            // 3. Kiểm tra ngày/tháng sinh hợp lệ
            if (month < 1 || month > 12) {
                showMessage("Tháng sinh không hợp lệ. Vui lòng nhập tháng từ 1 đến 12.", 'error');
                return;
            }
            if (day < 1 || day > 31) {
                showMessage("Ngày sinh không hợp lệ. Vui lòng nhập ngày từ 1 đến 31.", 'error');
                return;
            }


            // 4. Lấy thông tin Can Chi, Ngũ Hành, Vận hạn Năm/Tháng/Ngày
            const { canChiName, nguHanh, yearFortune, zodiacEmoji, zodiacName } = getZodiacInfo(year);
            const monthFortune = MONTH_FORTUNES[month];
            const dayType = day % 2 === 0 ? 'even' : 'odd';
            const dayFortune = DAY_FORTUNES[dayType];
            
            const greeting = `Xin chào ${name}, người sinh năm ${year} tuổi <span class="text-red-700 font-bold">${canChiName}</span>. Sau đây là luận giải chi tiết về vận mệnh, tính cách và vận hạn tổng hợp dựa trên ngày sinh dương lịch ${day}/${month}/${year} của bạn.`;
            
            // 5. Tạo nội dung kết quả TỔNG HỢP HTML
            const resultHtml = `
                <div class="space-y-8">
                    <div class="p-4 bg-yellow-50 rounded-xl border-l-4 border-yellow-500 shadow-inner">
                        <p class="text-xl font-semibold">${greeting}</p>
                    </div>

                    <div class="border-b pb-4">
                        <h3 class="text-2xl font-extrabold text-red-700 mb-2">${zodiacEmoji} ${yearFortune.Title.toUpperCase()} - VẬN HẠN THEO NĂM</h3>
                        <p class="text-xl font-bold mb-3">Tuổi chính: <span class="text-red-600">${canChiName}</span> | Mệnh: <span class="text-red-700">${nguHanh.Hanh}</span></p>
                        
                        <h4 class="font-bold text-lg mt-4">Đặc điểm Ngũ Hành (${nguHanh.Hanh}):</h4>
                        <p class="text-base leading-relaxed">${nguHanh.ChiTiet} Màu sắc tương sinh: ${nguHanh.Mau}.</p>
                        
                        <h4 class="font-bold text-lg mt-4">Chi tiết Vận hạn Tuổi ${zodiacName}:</h4>
                        <p class="text-base italic leading-relaxed">${yearFortune.Detail}</p>
                    </div>

                    <div class="border-b pb-4">
                        <h3 class="text-2xl font-extrabold text-green-700 mb-2">🗓️ THÁNG SINH ${month} - TÍNH CÁCH VÀ MAY MẮN</h3>
                        <p class="text-base leading-relaxed">${monthFortune}</p>
                    </div>

                    <div class="border-b pb-4">
                        <h3 class="text-2xl font-extrabold text-blue-700 mb-2">⭐ NGÀY SINH ${day} (${dayType === 'odd' ? 'LẺ' : 'CHẴN'}) - XU HƯỚNG CÁ NHÂN</h3>
                        <p class="text-base leading-relaxed">${dayFortune}</p>
                    </div>

                    <div class="pt-4 text-center border-t border-gray-200 mt-6 bg-gray-50 p-4 rounded-lg">
                        <p class="text-lg font-semibold mb-2">Để có được luận giải chi tiết và đầy đủ hơn về lá số tử vi cá nhân, sự nghiệp và tình duyên trong năm tới,</p>
                        <p class="text-xl text-yellow-800 font-extrabold">hãy tiếp tục khám phá vận trình với các Thầy Bói chuyên môn!</p>
                        <p class="text-sm italic mt-2">Chúc bạn một ngày an lành và vạn sự như ý.</p>
                    </div>
                </div>
            `;

            // 6. Hiển thị kết quả
            document.getElementById('resultContent').innerHTML = resultHtml;
            document.getElementById('resultContainer').classList.remove('hidden');
            
            document.getElementById('resultContainer').scrollIntoView({ behavior: 'smooth' });
        }
        
        /**
         * Khởi tạo trang và tạo hiệu ứng con giáp bay lung tung (Cải tiến)
         */
        function initializePage() {
            // 1. Gắn sự kiện cho Form
            document.getElementById('fortuneForm').addEventListener('submit', getFortuneAndDisplay);
            
            // 2. Tạo hiệu ứng con giáp bay lung tung
            const bgZodiacEffect = document.getElementById('background-zodiac-effect');
            const numberOfZodiacs = 40; // Tăng số lượng con giáp bay
            
            for (let i = 0; i < numberOfZodiacs; i++) {
                const randomEmoji = ZODIAC_EMOJIS[Math.floor(Math.random() * ZODIAC_EMOJIS.length)];
                const zodiacElement = document.createElement('div');
                zodiacElement.className = 'zodiac-flying-item';
                zodiacElement.textContent = randomEmoji;
                
                // Vị trí xuất phát ngẫu nhiên
                const startX = Math.random() * window.innerWidth;
                const startY = Math.random() * window.innerHeight;
                zodiacElement.style.left = `${startX}px`;
                zodiacElement.style.top = `${startY}px`;

                // Kích thước ngẫu nhiên
                const randomSize = 2.5 + Math.random() * 4; // 2.5rem to 6.5rem
                zodiacElement.style.fontSize = `${randomSize}rem`;

                // Độ mờ ngẫu nhiên
                const randomOpacity = 0.2 + Math.random() * 0.3; // 20% to 50%
                zodiacElement.style.opacity = randomOpacity;

                // Thời gian animation ngẫu nhiên (nhanh hơn)
                const randomDuration = 20 + Math.random() * 30; // 20s to 50s
                zodiacElement.style.animationDuration = `${randomDuration}s, ${randomDuration * 1.5}s, ${randomDuration * 0.5}s`;

                // Thời gian delay ngẫu nhiên
                const randomDelay = -Math.random() * randomDuration; // Dùng delay âm để animation bắt đầu ngay lập tức
                zodiacElement.style.animationDelay = `${randomDelay}s`;


                // Hướng và khoảng cách bay ngẫu nhiên (LỚN HƠN)
                // Đảm bảo chúng di chuyển vượt ra khỏi màn hình
                const translateXTo = (Math.random() - 0.5) * window.innerWidth * 4; 
                const translateYTo = (Math.random() - 0.5) * window.innerHeight * 4; 
                const rotateTo = (Math.random() - 0.5) * 1080; // Quay 5-6 vòng

                // Gán biến CSS để sử dụng trong keyframes
                zodiacElement.style.setProperty('--translate-x-to', `${translateXTo}px`);
                zodiacElement.style.setProperty('--translate-y-to', `${translateYTo}px`);
                zodiacElement.style.setProperty('--rotate-to', `${rotateTo}deg`);

                // Áp dụng animation (với delay khác nhau cho mỗi animation)
                zodiacElement.style.animationName = `flyX, flyY, rotateZ`;
                
                bgZodiacEffect.appendChild(zodiacElement);
            }
        }

        // Bắt đầu khởi tạo khi trang tải xong
        window.onload = initializePage;

    </script>

</body>
</html>
