# THTTNT_BUOI4_NGUYENBUINHATANH
THTTNT_BUOI4
Nguyễn Bùi Nhật Anh
mssv 2033230019
<br>
THUẬT TOÁN TÔ MÀU
<BR>
1.1.	Kiến thức cần nhớ
-	Ràng buộc là một quan hệ trên một tập các biến
-	Ràng buộc có thể được biểu diễn bằng:
•	Một biểu thức (toán học/logic)
•	Một bảng liệt kê các phép gán giá trị phù hợp cho các biến
-	Bài toán thỏa mãn ràng buộc:
•	Một tập hữu hạn các biến X
•	Miền giá trị cho mỗi biến D
•	Một tập hữu hạn các ràng buộc
Một lời giải thỏa mãn ràng buộc là một phép gán đầy đủ các giá trị của các biến sao cho thỏa mãn tất các ràng buộc.
-	Thuật toán tô màu tối ưu trên đồ thị
Ràng buộc: 2 đỉnh kề nhau không tô cùng màu
Lặp lại các bước sau cho đến khi nào tô màu hết các đỉnh
Bước 1: Chọn đỉnh có bậc lớn nhất tô màu i.
Bước 2: Hạ bậc: 
Đỉnh đã tô màu: bậc = 0
Những đỉnh có liên hệ: bậc := bậc – 1
Bước 3: Đánh dấu các đỉnh liên hệ và cấm tô màu i.
<br>
1.2.	Giới thiệu bài tập mẫu
Bài mẫu. Cài đặt thuật toán tô màu đồ thị có 6 đỉnh, như sau:
Ma trận kề của đồ thị:
<br>
0	1	1	0	1	0
 	<br>
1	0	1	1	0	1
 	<br>
1	1	0	1	1	0
 	<br>
0	1	1	0	0	1
 	<br>
1	0	1	0	0	1
 	<br>
0	1	0	1	1	0
 	<br>
<br>
THUẬT TUÁN NGƯỜI GIAO HÀNG
<BR>
Bài toán người bán hàng (tiếng Anh: travelling salesman problem - TSP) là một bài toán NP-khó thuộc thể loại tối ưu rời rạc hay tổ hợp được nghiên cứu trong vận trù học hoặc lý thuyết khoa học máy tính. Bài toán được phát biểu như sau. Cho trước một danh sách các thành phố và khoảng cách giữa chúng, tìm chu trình ngắn nhất thăm mỗi thành phố đúng một lần.

Bài toán được nêu ra lần đầu tiên năm 1930 và là một trong những bài toán được nghiên cứu sâu nhất trong tối ưu hóa. Nó thường được dùng làm thước đo cho nhiều phương pháp tối ưu hóa. Mặc dù bài toán rất khó giải trong trường hợp tổng quát, có nhiều phương pháp giải chính xác cũng như heuristic đã được tìm ra để giải quyết một số trường hợp có tới hàng chục nghìn thành phố.

Ngay trong hình thức phát biểu đơn giản nhất, bài toán TSP đã có nhiều ứng dụng trong lập kế hoạch, hậu cần, cũng như thiết kế vi mạch.

Trong lý thuyết độ phức tạp tính toán, phiên bản quyết định của TSP (cho trước độ dài L, xác định xem có tồn tại hay không một chu trình đi qua mỗi đỉnh đúng một lần và có độ dài nhỏ hơn L) thuộc lớp NP-đầy đủ. Do đó, có nhiều khả năng là thời gian xấu nhất của bất kì thuật toán nào cho TSP đều tăng theo cấp số nhân với số thành phố.

TSP có một vài ứng dụng thậm chí trong dạng thức nguyên thủy của nó như lập kế hoạch, logistic, và sản xuất các microchip. Thay đổi đi chút ít nó xuất hiện như một bài toán con trong rất nhiều lĩnh vực như việc phân tích gen trong sinh học. Trong những ứng dụng này, khái niệm thành phố có thể thay đổi thành khách hàng, các điểm hàn trên bảng mạch, các mảnh DNA trong gen, và khái niệm khoảng cách có thể biểu diễn bởi thời gian du lịch hay giá thành, hay giống như sự so sánh giữa các mảnh DNA với nhau. Trong nhiều ứng dụng, các hạn chế truyền thống như giới hạn tài nguyên hay giới hạn thời gian thậm chí còn làm cho bài toán trở nên khó hơn.
1. Mô tả bài toán TSP
Cho một tập n thành phố và chi phí đi lại giữa từng cặp thành phố.
Yêu cầu tìm một chu trình:
Xuất phát từ một thành phố
Đi qua tất cả các thành phố khác đúng một lần
Trở về lại điểm xuất phát
Với tổng chi phí là nhỏ nhất
2. Các thuật toán giải TSP
TSP là bài toán NP-hard, nên có nhiều hướng tiếp cận:
A. Thuật toán vét cạn (Brute Force)
Liệt kê tất cả các hoán vị của n thành phố → O(n!)
B. Quy hoạch động – Held–Karp (Dynamic Programming)
Giảm độ phức tạp từ O(n!) xuống O(n² · 2ⁿ)
→ Chính xác 100%, thường dùng cho n ≤ 20.
C. Thuật toán tham lam (Greedy / Nearest Neighbor)
Chọn thành phố gần nhất tiếp theo
→ Nhanh nhưng không tối ưu.
D. Heuristic / Metaheuristic
Genetic Algorithm (GA)
Simulated Annealing
Ant Colony Optimization (ACO)
→ Dùng cho n lớn.
3. Mô tả chi tiết THUẬT TOÁN QUY HOẠCH ĐỘNG (Held–Karp)
Đây là thuật toán kinh điển để giải TSP chính xác cho n nhỏ.
Ý tưởng chính
Ta lưu trữ:
dp[S][i] = chi phí nhỏ nhất để đi từ điểm xuất phát, qua tập thành phố S, và kết thúc tại thành phố i.
Trong đó:
S là tập con của các thành phố (mã hóa bằng bitmask)
i là điểm kết thúc
Công thức quy hoạch động
dp[{i}][i] = cost(start → i)
dp[S][i] = min(dp[S - {i}][j] + cost[j][i])  
           với mọi j ∈ S, j ≠ i
Kết quả cuối cùng:
answer = min(dp[AllCities][i] + cost[i][start])
Độ phức tạp
Thời gian: O(n² · 2ⁿ)
Bộ nhớ: O(n · 2ⁿ)
4. Thuật toán chi tiết như sau
Bước 1: Biểu diễn dữ liệu
Có n thành phố
Ma trận chi phí cost[n][n]
Bước 2: Xác định điểm xuất phát
Thường chọn thành phố 0.
Bước 3: Khởi tạo bảng dp
Sử dụng bitmask để biểu diễn tập S.
Kích thước bảng: dp[1 << n][n]
Bước 4: Duyệt tất cả tập con S
Với mỗi tập S, xét thành phố cuối i.
Bước 5: Cập nhật công thức
Chọn thành phố j trước i sao cho chi phí tổng nhỏ nhất.
Bước 6: Tính chu trình tối ưu
Khi tất cả thành phố đã được thăm, quay về điểm xuất phát.
5. Ví dụ minh họa
Cho 4 thành phố và ma trận chi phí:
	0	1	2	3
0	-	10	15	20
1	10	-	35	25
2	15	35	-	30
3	20	25	30	-
Held–Karp sẽ xét tất cả tập con:
{0}
{0,1}
{0,2}
{0,1,2}
Cho đến khi tìm được chu trình tối ưu:

→ Ví dụ kết quả: 0 → 1 → 3 → 2 → 0
<BR>

