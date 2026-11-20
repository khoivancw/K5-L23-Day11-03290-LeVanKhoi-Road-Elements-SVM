# Phiếu QC 1 — Road v1.0

Lô được kiểm: **03269 — Vũ Tiến Vinh**  
Người kiểm: **Lê Văn Khởi**  
Ngày: **20/11/2026** · Guideline: **Road v1.0**  
File được kiểm: **vinh-front.zip**, bản Vinh gửi ban đầu; chưa có manifest.  
Phạm vi: **A01–A06**, 6 ảnh, 0 ảnh thêm.  
Số nhãn đã kiểm: **57 = 33 hình + 24 tag**.

Kiểm bằng cách đối chiếu ảnh, file nhãn và guideline của lab.
Phiếu này ghi nhận bản Vinh ban đầu, không phải bản đã chỉnh sửa trên task 24.

## Tổng hợp theo mã

| Mã | Loại lỗi | Số mục kiểm | Số lỗi ghi nhận | Mức |
| --- | --- | --- | ---: | --- |
| QC1-01 camera | sai thuộc tính / bỏ sót | 6 camera; kiểm đủ 18 tag còn lại | 0 | nặng nếu sai camera |
| QC1-02 đủ L1, R1 | bỏ sót | 6 ảnh; ghi chú A05 không thấy vạch | 0 cộng riêng | nặng |
| QC1-03 position | sai thuộc tính | 12 lane | 2 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi | 12 lane, chưa đo độ lệch theo pixel | 0 ghi nhận | chính |
| QC1-05 vạch đứt, che | sai phạm vi / thuộc tính | 12 lane | 0 ghi nhận | chính |
| QC1-06 style, color, kind | sai thuộc tính | 12 lane | 0 ghi nhận | chính |
| QC1-07 vùng lái | sai phạm vi | 12 drivable, 2 road_curb, 1 crosswalk | 0 ghi nhận | chính |
| QC1-08 đèn, màu | sai thuộc tính / bỏ sót | 4 box đèn ở A06 | 0 ghi nhận | nặng / chính |
| QC1-09 facing, type, group | sai thuộc tính | 4 đèn và 2 biển | 1 | chính |
| QC1-10 đủ biển, hình in | bỏ sót / thừa | 2 biển đã gán; rà thêm trên 6 ảnh | 0 cộng, ghi chú phạm vi | chính |
| QC1-11 fisheye | sai phạm vi | 0, mẫu chỉ có front | không áp dụng | chính |
| QC1-12 file | lỗi file | 1 ZIP mở được | 0 | nhẹ / nặng |

Một nhãn có thể được kiểm ở nhiều mã; mẫu số vẫn là **57**, không cộng cột số mục kiểm.

## Danh sách lỗi

`ZIP#n` là thứ tự hình trong từng ảnh, bắt đầu từ 0, không phải ID trên CVAT.
Tọa độ được kèm theo để xác định hình.

| # | Mã | Ảnh | Nhãn | Mức | Nhận xét và hướng sửa |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-03 | A03 | lane L1, ZIP#1; đầu gần (1276,604) | nặng | Đường bên phải ngoài cùng đang ghi L1. Đổi thành R2 sau khi đối chiếu làn đang đi. |
| 2 | QC1-03 | A03 | lane L1, ZIP#3; đầu gần (701,468) | nặng | Đường sát bên phải làn xe đang đi đang ghi L1. Đổi thành R1. |
| 3 | QC1-09 | A03 | traffic_sign, ZIP#0; box (797,314)–(827,343) | chính | Biển cam công trường đang ghi group=other. Đổi thành warning theo bảng nhóm biển trong guideline. |

Không cộng thêm lỗi thiếu R1 từ cùng lỗi gán nhầm position ở A03.

## Nhận xét theo ảnh

| Ảnh | Nhận xét |
| --- | --- |
| A01 | Không tính lỗi single/double. Biển xanh chỉ dẫn được ghi vào phần ghi chú. |
| A02 | Chưa ghi nhận lỗi rõ khi xem ảnh. |
| A03 | Hai lỗi position và một lỗi group biển. |
| A04 | Có hai lane cho cụm vàng đôi; ghi chú cách biểu diễn, chưa tính lỗi này. |
| A05 | Không thấy vạch sơn rõ; ghi nhận cảnh báo thiếu L1/R1, không tạo lane bằng suy đoán. |
| A06 | Có crosswalk, drivable, 4 đèn và 1 biển. Ghi chú biển ONE WAY và biển cam ngoài các box đã kiểm. |

## Ca mơ hồ

Các mục dưới đây là ghi chú của người kiểm, không cộng thêm vào số lỗi.

| Ảnh | Mục ghi chú | Nhận xét theo guideline |
| --- | --- | --- |
| A01 | Phạm vi gán biển xanh | Nếu ảnh yêu cầu biển thì gán information; chưa cộng lỗi bỏ sót khi chưa rõ phạm vi |
| A04 | Cụm vàng đôi | Ghi kind=double cho cụm vàng đôi; không cộng lỗi về số đường biểu diễn |
| A05 | Không thấy vạch | Không tạo lane từ khoảng trống giữa xe; ghi rõ ảnh không thấy vạch sơn |
| A06 | Biển ONE WAY và biển cam | Nếu thuộc phạm vi gán biển: ONE WAY là mandatory, biển công trường là warning; chưa cộng lỗi bỏ sót |


## Quyết định

- Lỗi nặng: **2**.
- Lỗi chính: **1 / 57 = 1,75%**.
- Lỗi nhẹ: **0**.
- Ca ghi chú: **4**.
- **Đề xuất: Rework — trả sửa**, vì có lỗi nặng về position ở A03.

Phạm vi phiếu chỉ gồm A01–A06. Chưa kiểm fisheye và các ảnh còn lại.

Tham khảo: [Guideline](docs/guideline_road_v1.0.md),
[thang mức lỗi](docs/qc_severity_road_v1.0.md).
