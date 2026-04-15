# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600318
**Name:** Trần Trung Hiếu
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Correct answer, clean data with valid prices and categories |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Wrong answer due to extreme outlier in garbage data |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi su dung garbage data, agent tra loi sai vi du lieu dau vao chua nhieu van de chat luong nghiem trong.

Thu nhat, **Duplicate IDs**: garbage data chua hai ban ghi co cung id=1 (Laptop va Banana), khien agent khong biet ban ghi nao la chinh xac, gay nham lan khi tra cuu.

Thu hai, **Wrong data types**: cot price cua "Broken Chair" la chuoi "ten dollars" thay vi so, khien pandas khong the so sanh gia tri chinh xac. Dieu nay dan den ket qua sai khi tinh toan hoac loc du lieu.

Thu ba, **Extreme outliers**: ban ghi "Nuclear Reactor" co gia 999999, rat cao bat thuong. Khi agent tim san pham electronics co gia cao nhat, no tra ve "Nuclear Reactor" thay vi san pham co y nghia thuc te, khien ket qua tro nen vo nghia voi nguoi dung.

Thu tu, **Null values**: ban ghi co id=None, price=0 va category=None gay loi trong qua trinh xu ly, khien agent co the bi crash hoac tra ve ket qua khong chinh xac.

Tat ca nhung van de nay chung to rang du lieu rac gay ra ket qua sai lech nghiem trong, bat ke prompt co tot den dau.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y hoan toan.

Thi nghiem nay chung minh rang du lieu chat luong kem se dan den ket qua sai du AI agent duoc viet tot den dau. Nguyen tac GIGO (Garbage In, Garbage Out) rat ro rang: khi dua garbage data vao, agent tra ve "Nuclear Reactor at $999999" - mot ket qua hoan toan vo nghia. ETL pipeline voi validation chat che la buoc bat buoc de dam bao chat luong du lieu truoc khi dua vao he thong AI.
