---
title: Chia sẻ thuật toán hay
tags: [code, algothrym]
classes: wide
---

> Ngồi đọc tài liệu linh tinh thế nào lại va vào mấy blog thuật toán, code củng. Đọc được bài này khá hay share lại cho ae bẹn bà.
**Đề bài:** Tìm số lớn hơn trong 2 số đưa vào. Không được dùng `if/else` hoặc các phép so sánh `= < >`.
> Me: _Méo gì mà khoai thế, không so sánh thì làm thế quái nào được =]]_
**Dưới đây là đáp án, rất hay và logic:**

1. Nếu `a < b: return b`, ngược lại `return a`
2. Nếu `a – b < 0: return b`, ngược lại `return a`
3. Ta nhẩm: 
`b = a – (a – b) = a – 1*(a-b) = a – k*(a-b)` với `k = 1` --- Và:`a = a – 0 = a – 0*(a-b) = a – k*(a-b)` với `k = 0`
4. Kết hợp 2 và 3 ta có:
5. `return a – k*(a-b)`. Nếu `a – b < 0: k = 1`, ngược lại `k = 0`
6. Gọi `c = a-b`. Ta không thể so sánh `c` với `0`, tuy nhiên ta biết rằng `c < 0` nếu `c` là số âm. Số âm có đặc tính gì nhỉ: bit ngoài cùng bên trái của nó sẽ bằng `1`. Bit ngoài cùng bên trái của số dương sẽ bằng `0`. Ồ, đúng là số `k` chúng ta đang tìm còn gì.

Lời giải khá ngắn gọn, nhưng logic để có được lời giải này cũng không phải dạng vừa đâu.

```c
int getMax(int a, int b) {
   int c = a - b;
   int k = (c << 31) & 0x1;
   int max = a - k * c;
   return max;
}
```

Tới đây mình chắc các bạn cũng khá nhức não rồi, mình cũng vậy. Lâu lâu hãy đọc những câu hỏi như thế này để tăng tư duy lập trình nhé. Hẹn gặp lại các bạn ở bài viết sau.