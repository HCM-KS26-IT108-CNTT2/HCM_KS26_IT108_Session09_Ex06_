---


---

<h1 id="🌱-smart-farm-hệ-thống-trang-trại-thông-minh-iot--ai">🌱 Smart-Farm: Hệ thống Trang trại Thông minh IoT + AI</h1>
<p><strong>Smart-Farm</strong> là hệ thống <em>giám sát và tưới tiêu tự động</em> chạy trên chip SoC, kết hợp <strong>cảm biến IoT</strong> với <strong>mô hình AI</strong> để tối ưu nước và năng suất cây trồng.</p>
<blockquote>
<p><strong>Dành cho nhà đầu tư:</strong> hệ thống biến <em>dữ liệu thô</em> thành <em>quyết định tự động</em> theo luồng DIKW.</p>
</blockquote>
<h2 id="🖼️-sơ-đồ-hệ-thống-ipo">🖼️ Sơ đồ hệ thống (IPO)</h2>
<p><img src="https://raw.githubusercontent.com/nhom-smartfarm/smart-farm/main/images/ipo-diagram.png" alt="Sơ đồ IPO hệ thống Smart-Farm: Input cảm biến, Process CPU/RAM + AI, Output bơm tưới"></p>

<table>
<thead>
<tr>
<th align="center">Input</th>
<th align="center">Process</th>
<th align="center">Output</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">Nhiệt độ, độ ẩm, ánh sáng</td>
<td align="center">CPU + RAM + mô hình AI</td>
<td align="center">Bơm, quạt, đèn, cảnh báo</td>
</tr>
</tbody>
</table><h2 id="🔄-luồng-dữ-liệu-dikw">🔄 Luồng dữ liệu DIKW</h2>

<table>
<thead>
<tr>
<th align="left">Tầng</th>
<th align="left">Ví dụ</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><strong>Data</strong></td>
<td align="left"><code>35.2</code></td>
</tr>
<tr>
<td align="left"><strong>Information</strong></td>
<td align="left">Nhiệt độ 35.2°C, vượt ngưỡng 32°C</td>
</tr>
<tr>
<td align="left"><strong>Knowledge</strong></td>
<td align="left">Nóng và đất khô, cây thiếu nước</td>
</tr>
<tr>
<td align="left"><strong>Wisdom</strong></td>
<td align="left">Tưới 10 phút vào sáng sớm</td>
</tr>
</tbody>
</table><h2 id="⚙️-hạ-tầng-chu-kỳ-fetch–decode–execute">⚙️ Hạ tầng: Chu kỳ Fetch–Decode–Execute</h2>
<p>Khi cảm biến gửi giá trị nhiệt độ, CPU xử lý theo 3 bước:</p>
<blockquote>
<p><strong>1. Fetch (Nạp lệnh):</strong> CPU lấy lệnh tiếp theo (ví dụ <code>ĐỌC_NHIỆT_ĐỘ</code>) từ <strong>RAM</strong> thông qua bộ đếm chương trình (PC).</p>
<p><strong>2. Decode (Giải mã):</strong> Bộ điều khiển (Control Unit) giải mã lệnh để biết cần <em>đọc cổng cảm biến</em> và <em>so sánh với ngưỡng</em>.</p>
<p><strong>3. Execute (Thực thi):</strong> ALU so sánh <code>35.2 &gt; 32</code>. Nếu đúng, CPU ghi kết quả vào RAM và gửi tín hiệu bật bơm ra cổng output.</p>
</blockquote>
<h2 id="🚀-hướng-dẫn-cài-đặt">🚀 Hướng dẫn Cài đặt</h2>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token comment"># 1. Tải mã nguồn</span>
<span class="token function">git</span> clone https://github.com/nhom-smartfarm/smart-farm.git
<span class="token function">cd</span> smart-farm

<span class="token comment"># 2. Tạo môi trường ảo và cài thư viện</span>
python3 -m venv venv
<span class="token function">source</span> venv/bin/activate
pip <span class="token function">install</span> -r requirements.txt

<span class="token comment"># 3. Chạy hệ thống</span>
python3 main.py
</code></pre>
<h2 id="✅-tính-năng">✅ Tính năng</h2>
<ul>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Đọc dữ liệu nhiệt độ, độ ẩm, ánh sáng</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Lưu dữ liệu và hiển thị biểu đồ</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" checked="true" disabled=""> Tự động bật/tắt bơm theo ngưỡng</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Dự đoán nhu cầu tưới bằng AI</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Cảnh báo qua Telegram / email</li>
</ul>
<h2 id="📚-bảng-thư-viện">📚 Bảng thư viện</h2>

<table>
<thead>
<tr>
<th align="left">Thư viện</th>
<th align="left">Mục đích</th>
<th align="center">Phiên bản</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><code>paho-mqtt</code></td>
<td align="left">Truyền dữ liệu cảm biến qua MQTT</td>
<td align="center">1.6.1</td>
</tr>
<tr>
<td align="left"><code>RPi.GPIO</code></td>
<td align="left">Điều khiển chân GPIO (bơm, quạt)</td>
<td align="center">0.7.1</td>
</tr>
<tr>
<td align="left"><code>pandas</code></td>
<td align="left">Xử lý và lưu dữ liệu</td>
<td align="center">2.2</td>
</tr>
<tr>
<td align="left"><code>scikit-learn</code></td>
<td align="left">Mô hình AI dự đoán nhu cầu tưới</td>
<td align="center">1.4</td>
</tr>
</tbody>
</table><h2 id="💾-tính-toán-dung-lượng-lưu-trữ-cảm-biến-1-năm">💾 Tính toán dung lượng lưu trữ cảm biến (1 năm)</h2>
<p><strong>Giả định:</strong> mỗi mẫu 8 byte (4 byte thời gian + 4 byte giá trị), đo mỗi 1 phút.</p>
<p><strong>Công thức:</strong> <code>Dung lượng = Số cảm biến × 525.600 mẫu/năm × 8 byte</code></p>

<table>
<thead>
<tr>
<th align="left">Loại cảm biến</th>
<th align="center">Số lượng</th>
<th align="right">Mẫu/năm (tổng)</th>
<th align="right">Dung lượng/năm</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">Nhiệt độ</td>
<td align="center">10</td>
<td align="right">5.256.000</td>
<td align="right">42,0 MB</td>
</tr>
<tr>
<td align="left">Độ ẩm không khí</td>
<td align="center">10</td>
<td align="right">5.256.000</td>
<td align="right">42,0 MB</td>
</tr>
<tr>
<td align="left">Độ ẩm đất</td>
<td align="center">20</td>
<td align="right">10.512.000</td>
<td align="right">84,1 MB</td>
</tr>
<tr>
<td align="left">Ánh sáng</td>
<td align="center">5</td>
<td align="right">2.628.000</td>
<td align="right">21,0 MB</td>
</tr>
<tr>
<td align="left"><strong>Tổng</strong></td>
<td align="center"><strong>45</strong></td>
<td align="right"><strong>23.652.000</strong></td>
<td align="right"><strong>≈ 189,2 MB</strong></td>
</tr>
</tbody>
</table><blockquote>
<p><em>Ghi chú:</em> đây là dữ liệu thô. Khi lưu vào cơ sở dữ liệu (có chỉ mục), dung lượng thực tế khoảng gấp 2 lần, tức <strong>dưới 0,5 GB/năm</strong>, thẻ nhớ 32 GB là dư dùng.</p>
</blockquote>

