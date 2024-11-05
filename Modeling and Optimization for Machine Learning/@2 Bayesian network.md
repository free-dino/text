Representation: Học về : 
1 các kĩ thuật phổ biến và hiệu quả cho việc tham số hóa phân bố xác suất chỉ sử dụng 1 vài tham số
2 nhận thấy rằng models có thể biểu diễn một cách tinh tế qua DAGs
3 Suy luận từ DAG


Chain rule: 
$$
p(x_1, x_2, \cdots , x_n) = p(x_1)p(x_2|x_1)\cdots p(x_n|x_{n-1},\cdots , x_2, x_1)
$$
Compact Bayesian network: là phân bố sao cho mỗi nhân tử bên phải phụ thuộc vào số ít các biến tổ tiên $x_{A_i}$:
$$
p(x_i|x_{i-1}, \cdots , x_1) = p(x_i|x_{A_i})
$$
