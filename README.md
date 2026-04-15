[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23573958&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student ID:** AI20K-2A202600318
**Student Email:** hieutrantrung297@gmail.com
**Name:** Trần Trung Hiếu

---

## Mo ta

Bai lab Day 10 xay dung mot ETL Pipeline tu dong xu ly du lieu san pham tu file JSON.
Pipeline thuc hien 4 buoc: Extract (doc JSON), Validate (loc du lieu khong hop le), Transform (tinh gia giam 10%, chuan hoa category, them timestamp), va Load (luu ra CSV).
Ngoai ra, bai lab thi nghiem tac dong cua du lieu rac (garbage data) den ket qua cua AI agent, chung minh nguyen tac "Quality Data > Quality Prompt".

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Tao garbage data truoc
python generate_garbage.py

# Chay agent voi clean data va garbage data de so sanh
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Tong so records trong raw_data.json:** 5
- **Records hop le sau validation:** 3 (Laptop, Chair, Monitor)
- **Records bi loai:** 2 (Mystery Box co price=-10, Phone co category rong)
- **Output file:** processed_data.csv voi cac cot: id, product, price, category, discounted_price, processed_at
- **Stress Test:** Clean data → agent tra loi dung (Laptop $1200); Garbage data → agent tra loi sai (Nuclear Reactor $999999)
