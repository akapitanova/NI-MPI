# Experimental Evaluation of Iterative Methods for Solving Linear Systems  

This repository contains an experimental evaluation of various **iterative methods** for solving linear systems, 
focusing on their convergence properties depending on parameter **gamma (γ)** and **omega (ω)**.  

## 📌 Overview  

### 1️⃣ Jacobi Method
- **Method Definition**:  
  - Uses **Q = D**, where **D** is a diagonal matrix with the same dimensions as **A**, containing the diagonal elements of **A** while other elements are zero.  
- **Results**:  
  - **γ = 10**: Converged in **9 iterations**.  
  - **γ = 2**: Converged but required **987 iterations**.  
  - **γ = 4/5**: **Diverged**.  
- **Observations**:  
  - The closer **γ** approaches **2** from above, the higher the number of iterations required.  
  - If **γ < 2**, the method diverges.  

---

### 2️⃣ Gauss-Seidel Method
- **Method Definition**:  
  - Uses **Q = D + L**, where **L** is the lower triangular part of **A** (below the diagonal).  
- **Results**:  
  - **γ = 10**: Converged in **7 iterations**.  
  - **γ = 2**: Converged in **495 iterations**.  
  - **γ = 4/5**: **Diverged**.  
- **Observations**:  
  - Similar behavior to the **Jacobi Method**, but typically requires fewer iterations.  

---

### 3️⃣ Richardson Method
- **Method Definition**:  
  - Uses **Q = E**, where **E** is the identity matrix.  
- **Results**:  
  - **For all tested γ values (10, 2, 4/5)**: **Diverged**.  
- **Observations**:  
  - The method fails due to **inappropriate matrix dimensions** for convergence.  

---

### 4️⃣ Successive Over-Relaxation (SOR) 
- **Method Definition**:  
  - Uses **Q = (1/ω)D + L**, where **ω** is a relaxation parameter.  
- **Results for γ = 10**:  
  - **ω = 0.1**: **163 iterations**  
  - **ω = 0.5**: **26 iterations**  
  - **ω = 1.2**: **10 iterations**  
  - **ω = 1.5**: **22 iterations**  
- **Results for γ = 2**:  
  - **ω = 0.1**: **9427 iterations**  
  - **ω = 0.5**: **1488 iterations**  
  - **ω = 1.2**: **329 iterations**  
  - **ω = 1.5**: **161 iterations**  
- **Results for γ = 4/5**: **Diverged for all ω values**.  
- **Observations**:  
  - The closer **γ** gets to **2** from above, the higher **ω** helps reduce iterations.  
  - **γ < 2** leads to divergence.  

---

## 🔍 Conclusion  
- Convergence was analyzed using the **spectral radius** of matrix **W**.  
- **An iterative method is convergent if max{|λ| : λ is an eigenvalue of M} < 1**.  
- **Matrix W was computed as**:  
  \[
  W = E - (Q^{-1})A
  \]  
- Results for additional **γ values** are included in the **Jupyter Notebook**.  

