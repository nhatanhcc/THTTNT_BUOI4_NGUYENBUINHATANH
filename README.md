# THTTNT_BUOI4_NGUYENBUINHATANH
THTTNT_BUOI4
Nguyễn Bùi Nhật Anh
mssv 2033230019
<br>
THUẬT TOÁN TÔ MÀU
<BR>
giải thích cách hoạt động của bài 1
Bài 1: Phát triển code bài tập mẫu để đọc file ma trận kề dạng txt bất kỳ và in kết quả tô màu ra màn hình.

**Hàm read_adj_matrix(file_path)**

        matrix = []
        for line in lines:
            row = [int(x) for x in line.strip().split()]
            if row:
                matrix.append(row)

        N = len(matrix)
        if not matrix or N != len(matrix[0]):
            raise ValueError("Ma trận không hợp lệ hoặc không phải ma trận vuông.")

        return matrix

    except FileNotFoundError:
        print(f"LỖI: Không tìm thấy tệp tin tại đường dẫn {file_path}")
        print("Vui lòng tải tệp tin này lên môi trường Colab (ở thanh menu bên trái).")
        return None
    except ValueError as e:
        print(f"LỖI DỮ LIỆU: {e}")
        return None
------------------------------------------------------------------

**Hàm greedy_graph_coloring(G_matrix)**
def greedy_graph_coloring(G_matrix):
    """Thực hiện thuật toán tô màu tham lam (sắp xếp theo bậc giảm dần)."""
    N = len(G_matrix)
    node = [chr(65 + i) for i in range(N)]
    t_ = {node[i]: i for i in range(N)}
    # Tính bậc của mỗi đỉnh
    degree = [sum(G_matrix[i]) for i in range(N)]

    available_colors = ["Red", "Blue", "Yellow", "Green", "Cyan", "Magenta", "Orange", "Purple"]
    colorDict = {n: available_colors[:] for n in node}

    # Sắp xếp đỉnh theo bậc giảm dần (Chiến lược Tham Lam)
    degree_indexed = [(degree[i], i) for i in range(N)]
    sorted_indices = [idx for deg, idx in sorted(degree_indexed, key=lambda x: x[0], reverse=True)]
    sortedNode = [node[i] for i in sorted_indices]

    theSolution = {}
    for n in sortedNode:

        if not colorDict[n]:
            theSolution[n] = "Black"
            continue
            
        # 1. Chọn màu hợp lệ nhỏ nhất
        setTheColor = colorDict[n][0]
        theSolution[n] = setTheColor
        
        adjacentNode_index = G_matrix[t_[n]]

        # 2. Cập nhật danh sách màu khả dụng cho các đỉnh kề
        for j in range(N):
            if adjacentNode_index[j] == 1 and (setTheColor in colorDict[node[j]]):
                # Loại bỏ màu vừa dùng khỏi danh sách khả dụng của đỉnh kề j
                colorDict[node[j]].remove(setTheColor)

    return theSolution, node
    -------------------------------------------------
 
    <br>
**Hàm draw_colored_graph(G_matrix, coloring_result, node_names)**
<br>
def draw_colored_graph(G_matrix, coloring_result, node_names):
    """Vẽ đồ thị và tô màu các đỉnh dựa trên kết quả."""

    # 1. Xây dựng đồ thị NetworkX
    G = nx.Graph()
    G.add_nodes_from(node_names)

    N = len(G_matrix)
    for i in range(N):
        for j in range(i + 1, N):
            if G_matrix[i][j] == 1:
                G.add_edge(node_names[i], node_names[j])

    # 2. Ánh xạ tên màu sang mã HEX
    color_map_hex = {
        'Red': '#FF0000', 'Blue': '#0000FF', 'Yellow': '#FFFF00', 'Green': '#008000',
        'Cyan': '#00FFFF', 'Magenta': '#FF00FF', 'Orange': '#FFA500', 'Purple': '#800080',
        'Black': '#000000'
    }

    # 3. Chuẩn bị màu cho các đỉnh
    node_colors = [color_map_hex.get(coloring_result.get(node), '#808080') for node in G.nodes()]

    # 4. Tính toán bố cục và vẽ đồ thị
    pos = nx.spring_layout(G, seed=42)
    plt.figure(figsize=(10, 7))
    nx.draw(G, pos,
            with_labels=True,
            node_color=node_colors, # Sử dụng danh sách màu đã tô
            node_size=2500,
            font_size=12,
            font_color='black',
            font_weight='bold',
            edge_color='gray',
            width=2)

    plt.title("Đồ Thị Đã Tô Màu (Thuật Toán Tham Lam)", size=16)
    plt.show()
    --------------------------------------------------------
    Bước	Dòng Mã Chính	Giải Thích Chi Tiết
1. Xây dựng Đồ thị	G = nx.Graph() / G.add_edge(...)	Tạo đối tượng đồ thị và thêm các cạnh dựa trên ma trận kề G_matrix.
2. Ánh xạ Màu	color_map_hex = {...}	Định nghĩa mã màu HEX tiêu chuẩn, cần thiết để NetworkX/Matplotlib hiển thị màu chính xác.
3. Vẽ Đồ thị	pos = nx.spring_layout(...)	Tính toán vị trí sắp xếp các đỉnh bằng thuật toán bố trí lực (Spring Layout) để hình vẽ cân đối.
4. Hiển thị	nx.draw(G, ..., node_color=node_colors)	Vẽ đồ thị, sử dụng danh sách node_colors để tô màu cho từng đỉnh theo kết quả của thuật toán.
<br>
**Bài 2: Phát triển code bài tập mẫu thành các chương trình con sao cho phù hợp.**
<br>
**Hàm read_adj_matrix(file_path)**
<br>
def read_adj_matrix(file_path):
    """Đọc ma trận kề từ tệp tin văn bản."""
    try:
        with open(file_path, 'r') as f:
            lines = f.readlines()
        # ... (xử lý dòng) ...
        N = len(matrix)
        if not matrix or N != len(matrix[0]):
            raise ValueError("Ma trận không hợp lệ hoặc không phải ma trận vuông.")
        return matrix
    # ... (xử lý lỗi) ...
    ------------------------------------------
    Mục đích: Đọc và phân tích cú pháp Ma trận Kề (Adjacency Matrix) từ một tệp văn bản.

Xử lý Dữ liệu: Hàm lặp qua từng dòng, loại bỏ khoảng trắng thừa (strip()), tách các phần tử (split()), và chuyển chúng thành số nguyên (int).

Xác thực: Kiểm tra để đảm bảo dữ liệu đầu vào là một ma trận vuông (số hàng bằng số cột), điều kiện cần cho ma trận kề của đồ thị.

Xử lý Lỗi: Sử dụng try-except để bắt các lỗi phổ biến như FileNotFoundError (không tìm thấy tệp) hoặc ValueError (dữ liệu không hợp lệ).
<br>
**Hàm greedy_graph_coloring(G_matrix)**
<br>
def greedy_graph_coloring(G_matrix):
    """Thực hiện thuật toán tô màu tham lam (sắp xếp theo bậc giảm dần)."""
    N = len(G_matrix)
    node = [chr(65 + i) for i in range(N)]
    # ... (Tính bậc và Sắp xếp) ...
    degree = [sum(G_matrix[i]) for i in range(N)]
    # ... (Khởi tạo colors và colorDict) ...
    sortedNode = [node[i] for i in sorted_indices] # Đỉnh đã sắp xếp

    theSolution = {}
    for n in sortedNode:
        
        # 1. Chọn màu hợp lệ nhỏ nhất
        setTheColor = colorDict[n][0] 
        theSolution[n] = setTheColor

        adjacentNode_index = G_matrix[t_[n]]

        # 2. Cập nhật danh sách màu khả dụng cho các đỉnh kề
        for j in range(N):
            if adjacentNode_index[j] == 1 and (setTheColor in colorDict[node[j]]):
                colorDict[node[j]].remove(setTheColor)

    return theSolution, node
--------------------------------------------------
Tính Bậc và Sắp xếp: Tính bậc của mỗi đỉnh (sum(G_matrix[i])) và tạo danh sách sortedNode bằng cách sắp xếp các đỉnh theo bậc giảm dần.Khởi tạo Màu: Mỗi đỉnh được gán một danh sách available_colors đầy đủ ban đầu (colorDict).Quy tắc Tô màu (Vòng lặp Tham lam):Lặp qua các đỉnh theo thứ tự đã sắp xếp.Chọn Màu: Chọn màu đầu tiên (colorDict[n][0]) còn khả dụng cho đỉnh hiện tại $n$. Đây là nguyên tắc tham lam: luôn chọn màu "tốt nhất" (đầu tiên) hiện tại.Cập nhật Đỉnh kề: Sau khi đỉnh $n$ được tô màu, hàm lặp qua tất cả các đỉnh $j$ kề với $n$. Màu vừa dùng (setTheColor) sẽ bị loại bỏ khỏi danh sách màu khả dụng của đỉnh $j$, đảm bảo quy tắc tô màu đồ thị (các đỉnh kề nhau phải khác màu) được duy trì.
<br>
**Hàm draw_colored_graph(G_matrix, coloring_result, node_names)**
<br>
def draw_colored_graph(G_matrix, coloring_result, node_names):
    """Vẽ đồ thị và tô màu các đỉnh dựa trên kết quả."""

    G = nx.Graph()
    # 1. Thêm đỉnh và cạnh vào đồ thị NetworkX
    # ...
    
    # 2. Ánh xạ tên màu sang mã HEX
    color_map_hex = {
        'Red': '#FF0000', 'Blue': '#0000FF', 'Yellow': '#FFFF00', 'Green': '#008000',
        # ... (các màu khác) ...
    }

    node_colors = [color_map_hex.get(coloring_result.get(node), '#808080') for node in G.nodes()]
    
    # 3. Tính toán bố cục và vẽ
    pos = nx.spring_layout(G, seed=42)

    plt.figure(figsize=(10, 7))
    nx.draw(G, pos,
            with_labels=True,
            node_color=node_colors, # Dùng danh sách màu đã chuẩn bị
            # ... (tham số hình vẽ) ...
            )

    plt.title("Đồ Thị Đã Tô Màu (Thuật Toán Tham Lam)", size=16)
    plt.show()
    <br>
    --------------------------------------------------------------------------
    Xây dựng Đồ thị: Tạo đối tượng nx.Graph() và thêm các đỉnh (add_nodes_from) và cạnh (add_edge) dựa trên ma trận kề G_matrix.

Chuẩn bị Màu: Chuyển đổi tên màu từ kết quả tô màu (coloring_result) sang mã HEX (vì Matplotlib sử dụng mã HEX để vẽ màu sắc chính xác).

Vẽ:

Sử dụng nx.spring_layout để tính toán vị trí hiển thị của các đỉnh sao cho đồ thị dễ nhìn.

Hàm nx.draw sử dụng danh sách node_colors để tô màu cho từng đỉnh, trực quan hóa kết quả tô màu của thuật toán.
<br>
**Bài 3: Cài đặt thuật toán người bán hàng và ứng dụng tìm chu trình qua n thành phố mỗi thành phố qua 1 lần với chi phí tối thiểu.**
<br>
**Hàm held_karp_tsp(cost_matrix)**

<br>
def held_karp_tsp(cost_matrix):
    N = len(cost_matrix)
    DP = [[INF] * N for _ in range(1 << N)] # Khởi tạo bảng DP
    DP[1][0] = 0 # Trạng thái cơ sở: Đã thăm đỉnh 0, dừng tại 0, chi phí = 0
    
    # ... (Vòng lặp chính) ...

    # Tính chi phí cuối cùng để quay về đỉnh 0
    final_mask = (1 << N) - 1
    min_cost = INF
    
    for j in range(1, N):
        min_cost = min(min_cost, DP[final_mask][j] + cost_matrix[j][0])

    return min_cost
    <br>
    ---------------------------------------------------------
Số lượng thành phố (đỉnh).$DP$ Array: Mảng Quy hoạch động có kích thước $(2^N) \times N$.$1 \ll N$ ($2^N$): Tổng số trạng thái $mask$ có thể có (tập hợp con của các đỉnh).$N$: Số lượng đỉnh cuối cùng có thể.Trạng thái cơ sở:DP[1][0] = 0. Mask 1 (binary 00...01) chỉ ra rằng chỉ có đỉnh 0 được thăm. Đỉnh cuối cùng là 0. Chi phí là 0.
<br>
**Vòng Lặp Chính (Quy hoạch động)**
<br>
for mask in range(1, 1 << N):
        for j in range(N):
            if not (mask & (1 << j)): # Đảm bảo đỉnh j có trong tập hợp mask
                continue
            
            prev_mask = mask ^ (1 << j) # Tập hợp các đỉnh đã thăm TRƯỚC khi đến j
            
            if prev_mask == 0:
                continue

            for i in range(N):
                if prev_mask & (1 << i): # Đảm bảo đỉnh i có trong prev_mask (i là đỉnh trước j)
                    
                    if DP[prev_mask][i] != INF and cost_matrix[i][j] != INF:
                        new_cost = DP[prev_mask][i] + cost_matrix[i][j]
                        DP[mask][j] = min(DP[mask][j], new_cost)
        <br>
        ----------------------------------------------------------
        Lặp qua $mask$: Lặp qua tất cả các tập hợp đỉnh đã thăm, từ tập nhỏ đến tập lớn.Lặp qua $j$: Đỉnh hiện tại mà đường đi kết thúc ($j$ phải thuộc $mask$).Xác định $i$: Đỉnh ngay trước $j$ trong đường đi (ký hiệu là $i$).prev_mask = mask ^ (1 << j): Tạo mặt nạ mới bằng cách loại bỏ đỉnh $j$ khỏi $mask$.Vòng lặp trong cùng lặp qua tất cả các đỉnh $i$ thuộc prev_mask.Công thức Chuyển đổi Trạng thái (DP Transition):$$DP[mask][j] = \min_{i \in prev\_mask} \left( DP[prev\_mask][i] + \text{cost}[i][j] \right)$$Điều này có nghĩa là, chi phí tối thiểu để đi qua tập đỉnh $mask$ và kết thúc tại $j$ bằng chi phí tối thiểu để đi qua tập đỉnh $prev\_mask$ và kết thúc tại $i$, cộng thêm chi phí đi từ $i$ đến $j$.
