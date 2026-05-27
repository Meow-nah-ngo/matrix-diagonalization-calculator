Assignment #2 CSS114
Eigenvalue / Eigenvector / Diagonalization Program

โปรแกรมนี้ใช้สำหรับคำนวณเกี่ยวกับเมทริกซ์ ได้แก่

- Eigenvalue
- Eigenvector
- Diagonal Matrix
- ตรวจสอบว่า Matrix สามารถทำ Diagonalization ได้หรือไม่

รองรับเมทริกซ์ขนาด

- 2x2
- 3x3

หลักการทางคณิตศาสตร์
1. Eigenvalue

หาได้จากสมการ

    det(A−λI)=0

โดย

- A คือ Matrix ตั้งต้น
- λ คือ Eigenvalue
- I คือ Identity Matrix

เมื่อแก้สมการแล้วจะได้ค่า Eigenvalue

2. Eigenvector

หาได้จาก

    (A−λI)x=0

โดย

- λ คือ Eigenvalue ที่หาได้
- x คือ Eigenvector

3. Diagonalization

Matrix จะสามารถแปลงเป็นเมทริกซ์ทแยงมุมได้เมื่อ

มี Eigenvector อิสระครบจำนวนมิติของ Matrix

เช่น

- Matrix 2x2 ต้องมี Eigenvector อิสระ 2 ตัว
- Matrix 3x3 ต้องมี Eigenvector อิสระ 3 ตัว

สูตรที่ใช้คือ

    D = P^{-1} A P

โดย

- P คือ Matrix ของ Eigenvectors
- P^{-1} คือ Inverse ของ P
- D คือ Diagonal Matrix

การทำงานของโปรแกรม
1. Import Library

    import numpy as np

ใช้ numpy สำหรับ

- คำนวณเมทริกซ์
- หา eigenvalue
- หา eigenvector
- หา inverse matrix

ฟังก์ชันในโปรแกรม
2. ฟังก์ชันรับ Matrix

    def input_matrix(n):

หน้าที่

- รับค่าจากผู้ใช้
- สร้าง Matrix ขนาด n x n

การทำงาน

    matrix = []

สร้าง list ว่างสำหรับเก็บข้อมูล

    for i in range(n):

วนรับข้อมูลทีละแถว

    row = list(map(float, input().split()))

รับข้อมูลจาก keyboard แล้วแปลงเป็น float

ตัวอย่าง

    1 2

จะกลายเป็น

    [1.0, 2.0]

    return np.array(matrix)

แปลง list เป็น numpy array

3. ฟังก์ชันหา Eigenvalue

    def find_eigenvalues(A):

ใช้

    np.linalg.eigvals(A)

เพื่อหา Eigenvalue ของ Matrix

ตัวอย่าง

    eigenvalues = np.linalg.eigvals(A)

จะได้ค่า λ ทั้งหมด

    print(round(val, 4))

ปัดทศนิยม 4 ตำแหน่ง

4. ฟังก์ชันหา Eigenvector

    def find_eigenvectors(A):

ใช้

    np.linalg.eig(A)

ซึ่งจะคืนค่า

- eigenvalues
- eigenvectors

พร้อมกัน

การเข้าถึง Eigenvector

    eigenvectors[:, i]

หมายถึง

ดึง column ที่ i
เพราะ numpy เก็บ eigenvector เป็น column

5. ฟังก์ชัน Diagonalization

    def diagonalize_matrix(A):

หา Eigenvalue และ Eigenvector

    eigenvalues, eigenvectors = np.linalg.eig(A)

ตรวจสอบจำนวน Eigenvector อิสระ

    rank = np.linalg.matrix_rank(eigenvectors)

ถ้า rank เท่ากับขนาด matrix

แสดงว่ามี eigenvector อิสระครบ

กรณี diagonalizable ได้

สร้าง Matrix P

    P = eigenvectors

โดย

แต่ละ column คือ eigenvector

หา Inverse ของ P

    P_inv = np.linalg.inv(P)

คำนวณ Diagonal Matrix

    D = P_inv @ A @ P

เครื่องหมาย

- @ คือ matrix multiplication

กรณี diagonalizable ไม่ได้

ถ้า rank ไม่ครบ

    print("Matrix นี้ไม่สามารถแปลงเป็นเมทริกซ์ทแยงมุมได้")

เพราะมี eigenvector อิสระไม่พอ

6. Main Program

เลือกขนาด Matrix

    size = int(input())

เลือก

- 2
- 3

รับ Matrix

    A = input_matrix(size)

Menu

    while True:

วนเมนูจนกว่าจะกดออก

เมนู

1. หา Eigenvalue
2. หา Eigenvector
3. หา Diagonal Matrix
4. ออกโปรแกรม

ตัวอย่าง Test Case
กรณี diagonalizable ได้

Input

    2 1
    0 3

ผลลัพธ์

- มี eigenvalue ต่างกัน
- มี eigenvector อิสระครบ
- diagonalization ได้

กรณี diagonalizable ไม่ได้

Input

    1 1
    0 1

ผลลัพธ์

- eigenvalue ซ้ำ
- eigenvector ไม่ครบ
- diagonalization ไม่ได้

สรุป

โปรแกรมนี้สามารถ

- ✅ รับ Matrix 2x2 และ 3x3
- ✅ หา Eigenvalue
- ✅ หา Eigenvector
- ✅ ตรวจสอบ Diagonalization
- ✅ แสดง P, P⁻¹ และ D
- ✅ ใช้สูตร D=P⁻¹ A P ในการแปลงเป็นเมทริกซ์ทแยงมุม