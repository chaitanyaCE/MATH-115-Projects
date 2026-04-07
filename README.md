# 📐 MATH-115 Projects

> Computational exercises and labs from **MATH 115 - Linear Algebra for Engineering** at the University of Waterloo.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SageMath](https://img.shields.io/badge/SageMath-4B8BBE?style=for-the-badge&logo=python&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![University of Waterloo](https://img.shields.io/badge/University%20of%20Waterloo-FFB900?style=for-the-badge&logo=university&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

---

## 📋 Table of Contents

- [About](#-about)
- [Course Overview](#-course-overview)
- [Project Structure](#-project-structure)
- [Exercises](#-exercises)
  - [Exercise 03 — Polynomial Interpolation](#exercise-03--polynomial-interpolation)
  - [Exercise 04 — Plane Projections & Linear Transformations](#exercise-04--plane-projections--linear-transformations)
- [How to Run](#-how-to-run)
- [Technologies Used](#-technologies-used)
- [License](#-license)

---

## 🎯 About

This repository contains **Jupyter Notebook** exercises from **MATH 115: Linear Algebra for Engineering**, a core course for engineering students at the University of Waterloo. These notebooks combine **mathematical theory** with **computational implementation** using **SageMath** (a Python-based mathematical software system), allowing for hands-on exploration of linear algebra concepts through code.

Each notebook serves as an **interactive lab** where theoretical concepts are applied to solve real problems — from polynomial interpolation to 3D graphics projections.

---

## 📚 Course Overview

**MATH 115** is a foundational linear algebra course designed specifically for engineering students. The course covers[web:7][web:8][web:11]:

- ✅ **Complex numbers** and complex polynomials
- ✅ **Vector geometry** — vectors in ℝⁿ, lines, planes, dot/cross products
- ✅ **Systems of linear equations** — solving via matrices and row operations
- ✅ **Matrix algebra** — operations, inverses, determinants
- ✅ **Vector spaces** — spanning sets, linear independence, bases, subspaces
- ✅ **Linear transformations** — projections, reflections, rotations
- ✅ **Eigenvalues and eigenvectors** — diagonalization and applications
- ✅ **Orthogonal diagonalization** and Gram-Schmidt process

This course emphasizes both **theoretical understanding** and **computational methods**, bridging abstract linear algebra with practical engineering applications.

---

## 🗂️ Project Structure
```bash
MATH-115-Projects/
├── exercise03.ipynb # Polynomial Interpolation (Vandermonde matrices, curve fitting)
├── exercise04.ipynb # Plane Projections & Linear Transformations (3D graphics)
└── README.md
```


---

## 📝 Exercises

### Exercise 03 — Polynomial Interpolation 📈
**File:** [`exercise03.ipynb`](./exercise03.ipynb)

A comprehensive exploration of **polynomial interpolation** using linear algebra and matrix methods. This notebook demonstrates how to find a polynomial that passes exactly through a given set of points by solving a system of linear equations.

**Key Topics Covered:**
- **Vandermonde matrices** — constructing the coefficient matrix from x-values
- **Augmented matrices** — setting up the system Ax = b for interpolation
- **Row reduction** — solving for polynomial coefficients a₀, a₁, ..., aₙ
- **Matrix inversion** — computing the coefficient vector v = A⁻¹b
- **Dynamic matrix construction** — programmatically building Vandermonde matrices for large datasets
- **Visualization** — plotting data points alongside interpolated polynomial curves

**Three Progressive Questions:**
| Question | Description |
|----------|-------------|
| **Q1** | Interpolate 3 points (1,2), (3,5), (5,3) by manually constructing the augmented matrix, row-reducing to find coefficients, and adjusting a polynomial function to pass through all points |
| **Q2** | Interpolate 4 points (-1,3), (2,1), (5,2), (6,-1) using matrix inversion (v = A⁻¹b) to automatically compute coefficients, then build and plot the polynomial |
| **Q3** | Interpolate **21 points** requiring a degree-20 polynomial — programmatically construct the Vandermonde matrix using Python loops, solve for all 21 coefficients, and visualize the resulting curve |

**Skills Developed:**
- SageMath/Python syntax for mathematical computing
- Matrix construction and manipulation
- Understanding the relationship between polynomial coefficients and linear systems
- Visualizing mathematical functions with `plot()` and `show()`

---

### Exercise 04 — Plane Projections & Linear Transformations 🎮
**File:** [`exercise04.ipynb`](./exercise04.ipynb)

An interactive lab exploring how **linear transformations** are used to project 3D points and objects onto 2D planes — the mathematical foundation behind **computer graphics, rendering, and 3D visualization**.

**Key Topics Covered:**
- **Plane projection formula** — T(x) = x − projₙ(x) = x − (x·n / ||n||²)n
- **Standard matrices for projections** — deriving the 3×3 matrix that projects onto any plane
- **Coordinate plane projections** — projecting onto xy, xz, and yz planes
- **Arbitrary plane projections** — projecting onto tilted planes (e.g., x + z = 0)
- **Orthonormal bases** — constructing a stable viewing basis using the "world up" convention
- **Cross products** — computing the "right" and "up" view directions
- **Coordinate extraction** — using dot products to find 2D screen coordinates from 3D projected points
- **Camera roll problem** — understanding why consistent basis selection matters for predictable views

**Progressive Parts:**

**Part 1: Standard Matrix of Projection**
- Implement `plane_projection(x, n)` function using the projection formula
- Derive the standard matrix for projection onto any plane with normal n
- Complete `std_matrix_for_plane_proj(n)` function to generate 3×3 projection matrices
- Calculate projections onto the xy plane and analyze the resulting matrix

**Part 2: Multi-Plane Projections of a 3D Object**
- Define a 3D object with 5 vertices and 8 edges (a square pyramid)
- Project the object onto the **xy plane** — dropping the z-component
- Project onto the **xz plane** — dropping the y-component
- Project onto the **yz plane** — dropping the x-component
- Visualize each projection as a 2D shape using `plot_shape_2d()`
- Understand how coordinate plane projections correspond to "dropping" components

**Part 3: Projection onto an Arbitrary (Tilted) Plane**
- Project the 3D object onto the plane **x + z = 0** (normal n = [1, 0, 1])
- Solve the **"camera roll" problem** by defining WORLD_UP = [0, 0, 1]
- Construct an **orthonormal basis** for the tilted plane:
  - **b₁** (right direction) = WORLD_UP × n (normalized)
  - **b₂** (up direction) = n × b₁ (normalized)
- Extract 2D screen coordinates using dot products: (p·b₁, p·b₂)
- Plot the final 2D view as if "staring down" the plane's normal

**Six Progressive Questions:**
| Question | Description |
|----------|-------------|
| **Q1** | Project point (3,4,1) onto plane 2x + 3y − z = 0 using the `plane_projection` function |
| **Q2** | Calculate the standard matrix for projection onto the xy plane |
| **Q3** | Analyze the rank and invertibility of the xy-plane projection matrix |
| **Q4** | Find the y-value of a projected point whose z-value is 32 on the tilted plane |
| **Q5** | Express a projected point in terms of the orthonormal basis (find coordinates c₁, c₂) |
| **Q6** | Estimate the largest coordinate value along the b₂ basis vector from the final plot |

**Real-World Connection:**
This exercise mirrors how **cameras and 3D rendering engines** work — taking a 3D scene and projecting it onto a 2D image plane. The techniques covered here are foundational to computer graphics, game engines, and visualization software.

---

## ⚙️ How to Run

These notebooks are written in **Python** using **SageMath**, a free open-source mathematics software system.

### Option 1: SageMathCell (Online — No Installation Required)

The easiest way to run these notebooks is using the online SageMath environment:

1. Visit [https://sagecell.sagemath.org/](https://sagecell.sagemath.org/)
2. Copy the code from each cell in the `.ipynb` file
3. Paste and click **Evaluate**

### Option 2: CoCalc (Online Jupyter with SageMath)

1. Visit [https://cocalc.com/](https://cocalc.com/)
2. Create a new **SageMath Jupyter Notebook** project
3. Upload the `.ipynb` files
4. Run cells interactively

### Option 3: Local SageMath Installation

```bash
# Install SageMath (Linux/macOS)
# Ubuntu/Debian
sudo apt install sagemath

# macOS (with Homebrew)
brew install sagemath

# Run SageMath Jupyter
sage -n jupyter
```

Then open the notebook files in the Jupyter interface.

### Option 4: GitHub Preview

Simply click on any `.ipynb` file in this repository on GitHub to view the rendered notebook with all markdown, equations, code, and outputs.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| **Python** | Programming language for all code |
| **SageMath** | Mathematical software system (built on Python) |
| **Jupyter Notebook** | Interactive computing environment |
| **SageMath Vectors & Matrices** | Linear algebra data structures |
| **SageMath Plotting** | Visualization of functions and 2D/3D shapes |
| **Git** | Version control |
| **GitHub** | Code hosting and notebook rendering |

---

## 📚 Learning Progression

The exercises in this repository build upon each other:
```bash
Exercise 03 → Polynomial Interpolation
↓
Matrices as tools for solving systems
↓
Exercise 04 → Linear Transformations & Projections
↓
Applying matrix methods to 3D graphics
```


**Exercise 03** focuses on using matrices to **solve systems of equations** (finding polynomial coefficients).

**Exercise 04** extends this by treating matrices as **linear transformations** that act on vectors — specifically, projection transformations in 3D space.

Together, these notebooks demonstrate the **dual nature of matrices** in linear algebra: both as tools for computation and as representations of geometric transformations.

---

## 📄 License

This project is for **educational purposes only**. The notebooks are provided as a learning resource.

- ✅ Feel free to study the code to understand linear algebra concepts
- ✅ Use it as a reference for your own computational math projects
- ❌ Do **not** submit this work as your own in any academic setting
- ❌ Do **not** distribute modified versions without attribution

---

## 🙏 Acknowledgments

- **University of Waterloo** — For the excellent MATH 115 curriculum
- **MATH 115 Instructors & TAs** — For designing these insightful computational exercises
- **SageMath Developers** — For providing a powerful, free mathematical computing platform
- **Course Materials** — Exercise specifications provided by the MATH 115 course team

---

<div align="center">

**Built with 🧮 by [chaitanyaCE](https://github.com/chaitanyaCE)**

*University of Waterloo | Computer Engineering*

📧 Open to collaboration and feedback!

</div>
