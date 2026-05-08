Nếu tôi đang làm việc trên nhánh feature/nav-bar mà sếp yêu cầu tôi phải sửa gấp một lỗi chính tả ở nhánh main, tôi nên dùng lệnh Git gì để tạm cất code đang làm dở?
1. Tạm dừng mã đang làm
Tại nhánh feature/nav-bar, bạn nhập:
 git stash
(Lệnh này sẽ dọn dẹp công việc thư mục của bạn, code sẽ biến mất và được lưu vào bộ nhớ tạm thời của Git).

2. Chuyển nhánh mainđể sửa lỗi
git checkout main
( Time sẽ sửa lỗi chính, add, commitvà pushnhư bình thường thôi).

3. Quay lại Đặc điểm
Sau khi Lãnh chúa hài lòng, bạn quay lại công việc đang dang nha:
git checkout feature/nav-bar

4. Lấy mã từ "ngăn kéo" ra
Để lấy lại những gì bạn đã lưu trữ lúc đó, hãy sử dụng:
 git stash pop
(Lệnh này sẽ lấy mã ra và đồng thời xóa luôn bản lưu tạm thời trong "ngăn kéo" cho sạch sẽ).

<div id="website-wrapper">
    <header>
        <h1 class="logo">TechBugs News</h1>
        <nav class="menu">
            <ul>
                <a href="#">Trang chủ</a>
                <a href="#">Sản phẩm</a>
                <a href="#">Tuyển dụng</a>
                <a href="#">Liên hệ</a>
            </ul>
        </nav>
    </header>

    <main>
        <section>
            <h3>Bản cập nhật hệ thống V2.0</h3>
            <p>Bởi: Admin - Ngày 21/04/2026</p>
            <p>Hôm nay chúng ta sẽ cập nhật server...</p>
        </section>
    </main>

    <footer>
        <div class="copyright">© 2026 TechBugs Inc.</div>
    </footer>
</div>

Kiểm tra code chuẩn Semantic chưa?