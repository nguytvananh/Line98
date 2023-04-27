# Line98 Algorithm
# Nguyen Thi Van Anh 20200035

Part 1: Tạo bảng bi ban đầu 

generateMatrix(): Khởi tạo bảng ô vuông 9*9 ô trống là 1 mảng 2 chiều a[9,9] có 81 phần tử gán giá trị ban đầu a[i,j]= 0. 
Màu bi: có 7 màu bi có nhãn số; màu bi là giá trị của a[i;j]
Đặt viên bi đầu tiên vào 1 vị trí k ngẫu nhiên (từ 0 đến 80). Ta gán viên bi ở vị trí k màu ngẫu nhiên trong 7 màu bi. Việc này lặp lại 5 lần để khởi tạo bảng ban đầu có 5 viên.
Thuật toán chuyển đổi từ k sang a[i,j]: Duyệt tuần tự từ trên xuống, trái sang đếm số ô trống a[i,j]= 0, bỏ qua ô đã có bi. Duyệt đến khi đếm đủ k thì dừng lại. Vị trí dừng lại chính là vị trí hàng i cột j cần tìm

Function addNextColor: thêm vào ma trận a 3 viên bi ở 3 vị trí ngẫu nhiên chuẩn bị hiện lên. 
Màu bi: vẫn là 7 màu bi nhưng gán = giá trị âm (từ -1 --> -7) để phân biệt với bi đã hiện lên trên bảng

Function countEmpty: đếm số phần tử trống là số phần tử a[i;j] có giá trị <= 0 

Part 2: Tìm đường đi ngắn nhất 
Tìm đường đi ngắn nhất từ a[i1;j1] tới a[i2;j2]
Quy định: Đường đi bao gồm dãy liên tiếp các ô trống kề cạnh.
Thuật toán: Breadth First Search 
- Tập V: 81 đỉnh 
- Tập E: 2 ô trống kề nhau tạo ra 1 cạnh nối 
Các bước thuật toán:
- Khởi tạo queue; đưa ô (i2 ,j2) vào queue.
- Lặp lại các việc sau đến khi queue cạn:
{
    + Lấy ra 1 ô trong queue.
    + Xét 4 ô xung quanh:
    {
        Nếu ô xung quanh trống thì:
        {
            Thêm ô đó vào queue.
            Truy hồi đường đi ô đi trước.
            Nếu ô đi trước chính là (i1, j1) thì chấm dứt vòng lặp.
        }
    }
}
