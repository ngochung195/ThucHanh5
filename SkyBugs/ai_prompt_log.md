khái niệm "Fast-forward merge"
1. Cơ chế hoạt động của Fast ForwardKhi bạn thực hiện cấp độ (hợp nhất), Git sẽ không cần tạo một mới "hợp nhất cam kết". Thay vào đó, nó chỉ đưa cái nhãn (con trỏ) của nhánh mainlên phía trước, trỏ thẳng vào cuối cùng của nhánh feature.Ví dụ thực tế:Bạn đang ở main(tại commit A).Bạn phân tách nhánh featurevà tạo thêm cam kết B và C.Trong lúc đó, không ai cam kết gì maincả. mainvẫn đứng yên ở A.Khi bạn git merge featurevào main: Git tìm thấy đường đi từ A đến C là một đường thẳng. Nó chỉ cần lấy tên maintừ A đặt sang C. Xong!
2. Điều kiện để diễn ra nhanh chóngĐể Git có thể sử dụng cơ chế Chuyển tiếp nhanh, lịch sử cam kết phải có dạng tuyến tính (tuyến tính) .Nếu tại thời điểm bạn làm nhánh feature, có ai đó đưa ra một cam kết mới lên main, thì lúc này lịch sử đã bị phân nhánh (chuyển hướng).Khi đó, Git không thể Fast-forward nữa mà phải sử dụng tính năng hợp nhất 3 chiều (tạo ra một cam kết chung).
3. Ưu và điểmĐặc biệtChiƯuLịch sử cam kết cực kỳ sạch sẽ, là một đường thẳng duy nhất, không có các "commerge" gây rối mắt.điểmBạn sẽ mất dấu vết về công việc "nhánh này từng tồn tại". Khi nhìn lại lịch sử, bạn không biết những cam kết đó từng thuộc về một tính năng riêng biệt.
4. Cách kiểm soát Tua nhanhĐôi khi bạn không muốn Git tự động chuyển tiếp nhanh (vì bạn muốn giữ lại dấu vết của tính năng nhánh), bạn có thể sử dụng lệnh:Ép buộc tạo merge commit (ngay cả khi có thể FF): git merge --no-ff feature(Cách này thường được sử dụng trong các dự án chuyên nghiệp để dễ dàng quản lý các tính năng đã cấp).Chỉ cho phép hợp nhất nếu Chuyển tiếp nhanh: git merge --ff-only feature(Nếu không thể FF, Git sẽ báo lỗi và không hợp nhất. Rất an toàn để tránh làm rối lịch sử).

cách xem biểu đồ Git (git log graph)
Tiêu chuẩn lệnh tối đa để xem biểu đồ là kết hợp các tham số --graph, --oneline, và --all.

các cơ:
git log --oneline --graph --all

--graph: Vẽ nhánh bằng các bản văn tự.

--oneline: Gom each commit back thành một dòng cho rút gọn.

--all: Hiển thị tất cả các nhánh (không có cái nào bạn chỉ thấy tại nhánh này).

Lệnh "đầy đủ" để xem chi tiết hơn:
git log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all

Mẹo: Vì lệnh này quá dài, bạn nên tạo một cái "tên viết tắt" (bí danh) để sau này chỉ cần nhập git treexong:
git config --global alias.tree "log --oneline --graph --all"