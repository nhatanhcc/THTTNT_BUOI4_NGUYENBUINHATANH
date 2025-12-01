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

