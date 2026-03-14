---
title: "Tản mạn về ANOVA một nhân tố"
date: 2026-03-14
draft: false
cover:
    image: /img/coverImg/lovely3.jpg
    alt: An image of lovely flowers
series: ["ISLP"]
tags: ["statistics", "machine learning"]
---

Bài viết này giải thích ngắn gọn về ANOVA (phân tích phương sai một nhân tố - Analysis of variance). Bài viết dựa trên video giải thích về ANOVA: [Statistics 101: ANOVA, A Visual Introduction](https://youtu.be/0Vj2V2qRU10?si=cCbleiHNv3rjqqFY) và phần phân tích phương sai một nhân tố trong giáo trình `"Thống kê và ứng dụng"` của thầy `Đặng Hùng Thắng`

---
### ANOVA được sử dụng khi nào?
Ta sử dụng ANOVA cho bài toán so sánh nhiều giá trị trung bình của nhiều tập hợp chính có phân phối chuẩn. Cụ thể, ta có $k$ đại lượng ngẫu nhiên $X_1, X_2, ..., X_k$ trong đó $X_i \sim N(\mu_i, \sigma_i^2)$. Cả $\mu_i$ và $\sigma_i$ ta đều chưa biết nhưng ta giả thiết rằng $\sigma_1 = \sigma_2 = ... = \sigma_k$. Chúng ta muốn kiểm định xem các giá trị trung bình $\mu_i$ có bằng nhau không:
$$
    H_0: \mu_1 = \mu_2 = ... = \mu_k
$$

Trong thống kê vấn đề trên thường được xem xét dưới góc độ sau: Ta quan tâm tới một nhân tố $X$ và nhân tố này có thể xem xét ở $k$ mức độ khác nhau. Kí hiệu $X_i$ là hiệu quả của việc tác động nhân tổ $X$ ở mức $i$ đối với cá thể, khi đó $\mu_i$ chính là hiệu quả trung bình của nhân tố $X$ ở mức $i$. Chúng ta muốn biết khi cho nhân tố $X$ ở các mức khác nhau thì điều đó có ảnh hưởng hay không tới hiệu quả trung bình.

Ví dụ: Chúng ta muốn nghiên cứu ảnh hưởng của giống
tới năng suất cây trổng. Nhân tố ở đây là giống,  các loại giống khác nhau là các mức của nhân tố. Hiệu quả của giống lên năng suất cây trổng được đo bằng sản lượng. $X_i$ chính là sản lượng của giống $i$ và $\mu_i$ là sản lượng trung bình
của giống $i$. Nếu $\mu_1 = \mu_2 = .. = \mu_k$ nghĩa là sản lượng hay năng suất của các giống này là như nhau.
### ANOVA được tính và sử dụng như thế nào?
Bảng ANOVA:
| Source of variance | Sum of squares | Degree of freedom | Mean of squares | $F_0$ |
|-----|-----|-----|-----|-----|
|Between|$SS_B$|$k - 1$|$MS_B$|$\frac{MS_B}{MS_W}$|
|Within|$SS_W$|$n - k$|$MS_W$||
|Total|$SS_T$|$n-1$|||

Trong đó:
$$
    SS_B = \sum_{i=1}^{k}n_i(\bar{x_i} - \bar{x})^2 \quad \text{(tổng phương sai giữa các nhóm với nhau)}\\
    SS_W = \sum_{i=1}^{k}\sum_{j=1}^{n_i}(x_{ij} - \bar{x_i})^2 \quad \text{(tổng phương sai trong từng nhóm)}\\
    SS_T = \sum_{i=1}^{k}\sum_{j=1}^{n_i}(x_{ij} - \bar{x})^2 \quad \text{(tổng phương sai)}
$$
Còn các giá trị $MS_B = SS_B/(k-1)$, $MS_
W = SS_W/(n-k)$ lần lượt là trung bình bình phương tương ứng. 

Ta có thể chứng minh được rằng $SS_T = SS_B + SS_W$, chứng mình này khá đơn giản và bạn đọc có thể tìm hiểu trong giáo trình. 

Từ bảng ANOVA, ta tính được $F_0$ và đại lượng này tuân theo phân phối $Fisher$ với bậc tự do $(k-1, n-k)$. Khi kiểm định giả thiết, ta sẽ bác bỏ $H_0$ nếu xác suất thu được $F_0$ với điều kiện $H_0$ đúng là rất nhỏ,  hay $F_0$ nằm trong phần màu xanh (miền bác bỏ) ở hình dưới đây, còn về mặt toán học, ta bác bỏ nếu $F_0 > F_\alpha(k-1, n-k)$.

![Phân phối Fisher và mức ý nghĩa $\alpha$](https://online.stat.psu.edu/stat415/sites/stat415/files//lesson32/Lesson32_Drawing03.gif)
Nguồn ảnh: https://online.stat.psu.edu/stat415/lesson/4/4.2

### Hình dung về ANOVA
Cách tính và hiểu về ANOVA như trên rất hợp lý tuy nhiên lại hơi thuần túy toán học. Nhưng có một cách giải thích khác mà mình nghĩ có vẻ dễ tiếp cận hơn và đễ hình dung hơn như sau:

$F_0 = MS_B/MS_E$ do đó, về bản chất nó chính là tỉ số của sự phân tán giữa giá trị trung bình của các nhóm so với độ phân tán của dữ liệu trong các nhóm:
$$
F_0 = \frac{\text{Variance between}}{\text{Variance within}}
$$

Ta bác bỏ $H_0$ khi:
- $F_0$ đủ lớn: $F_0 = \frac{\text{large}}{\text{small}}$ nghĩa là có ít nhất 1 giá trị trung bình của một nhóm là *outlier* so với các nhóm khác (tách xa so với các nhóm khác) và phương sai của các nhóm là rất nhỏ.

Ta tạm thời chấp nhận $H_0$ khi:
 *  $F_0 = \frac{\text{small}}{\text{small}} \approx 1$, các giá trị trung bình của các nhóm gần nhau và phương sai của từng nhóm cũng rất nhỏ, chưa thể đưa ra kết luận.
- $F_0 = \frac{\text{small}}{\text{large}}$, các giá trị trung bình gần nhau nhưng phương sai của từng nhóm là lớn, chưa thể đưa ra kết luận.

Dưới đây là hình minh họa cho các trường hợp
![intuitive anova](/img/statistics/anova.png)

Bạn đọc nếu muốn hiểu thêm về cách giải thích này, có thể xem video youtube [Statistics 101: ANOVA, A Visual Introduction](https://youtu.be/0Vj2V2qRU10?si=cCbleiHNv3rjqqFY), còn nếu muốn tìm hiểu về mặt toán có thể đọc tại `"Thống kê và ứng dụng"` của thầy `Đặng Hùng Thắng` phần phân tích phương sai một nhân tố.

### Câu hỏi: Tại sao lại là Fisher?
Đúng vậy, ở phần trên mọi thứ đều rất hợp lý, tuy nhiên câu hỏi đặt ra là, tại sao $F_0$ lại có phân phối $Fisher$? Để trả lời câu hỏi này, bạn đọc có thể tìm hiểu thêm về phân phối chuẩn, phân chối $chi-square$, phân phối $Fisher$ và mối quan hệ giữa chúng.

--- 
Bài viết được viết theo ý hiểu của mình nên có thể còn nhiều thiếu sót, mình rất vui nếu được nhận góp ý từ bạn đọc để bài viết hoàn thiện và trở nên tốt hơn. Chúc bạn một ngày tốt lành ☘️

Email của mình : uyennguyen.nbu@gmail.com