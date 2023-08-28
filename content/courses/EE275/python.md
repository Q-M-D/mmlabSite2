---
title: C1. Python Basics
date: '2023-03-02'
type: book
weight: 20
---

<!--more--> <!-- This also prevent a abstract appearing in CoursePage -->

{{< icon name="clock" pack="fas" >}} 15 min

## C1.1. Prerequisite

1. Download and install [Anaconda 3](https://www.anaconda.com/) before class.
    - Anaconda 3 is a Python distribution which will be the compiler for our Python codes;
    - We are going to use it to create virtual environment to ensure everybody in this class is on the same page;
    - The version does not matter if we use virtual environment. I installed *Anaconda3-2022.10-Windows-x86_64.exe* for my Windows machine.
    - For Windows PCs, you can set up a virtual environment following these steps:
        - Open anaconda prompt, or alternatively, you can add anaconda to system path (the Windows environment variable).
            ```
            D:\Programs\anaconda3
            D:\Programs\anaconda3\Scripts
            D:\Programs\anaconda3\Library\bin
            ```
            After doing this, you can call python.exe and pip.exe in your command prompt (cmd.exe)
        - Create a virtual environment python 3.10 under the name "main":
            - `conda create -n main python=3.10`
            - Type `y` to confirm downloading the packages and wait.
        - Activate it
            - `conda activate main`
        - Now, if you run command `pip install`, the packages will be installed for this virtual environment
            - `pip install matplotlib pandas numba control dearpygui`
        - Open file explorer.exe at current directory
            - `explorer.exe .`
        - Create a file named `my_dearpygui_demo.py` and paste the following codes and save
            ```python
            import dearpygui.dearpygui as dpg
            import dearpygui.demo as demo
            dpg.create_context()
            dpg.create_viewport(title='Custom Title', width=600, height=600)
            demo.show_demo()
            dpg.setup_dearpygui()
            dpg.show_viewport()
            dpg.start_dearpygui()
            dpg.destroy_context()
            ```
        - Run python codes
            - `python my_dearpygui_demo.py`
            - Have fun!
        - You can check existing virtual environment by typing: `conda env list`
    - Jupyter notebook/lab
        - Open cmd.exe and type `jupyter lab`. It will fire up jupyter lab in your default browser.
        - I often use jupyter lab to do derivation verification and here is an example (you need to `pip install sympy`):
            ```python
            from sympy import *
            from IPython.display import display, Latex

            # display result without need of print (matlab like)
            from IPython.core.interactiveshell import InteractiveShell; InteractiveShell.ast_node_interactivity = "all"

            # use mathjax
            init_printing(use_latex='mathjax')

            # Define symbols
            t, p, a, b, c, d, e = symbols('t, p, a, b, c, d, e')
            L_σ = Symbol(r'L_\sigma')
            M_σ = Symbol(r'M_\sigma')
            i_alpha = Function(r'i_{\alpha}')(t)
            i_beta  = Function(r'i_{\beta}')(t)
            i_abs = Matrix(2, 1, [i_alpha, i_beta])
            Theta = Function(r'\varTheta')(t)
            Omega = Theta.diff(t)

            # Display stuff
            display(i_abs)
            display(Theta, Omega)
            a=100
            a
            100+a

            # Rotation Matrix
            P = Matrix(2,2,     [ cos(Theta), sin(Theta), \
                                 -sin(Theta), cos(Theta)] )
            P_inv = P.T
            # Full Park transformation (power invariant)
            T = sqrt(2/3)*Matrix(3,3,
                                 [ cos(Theta),  cos(Theta-2*pi/3),  cos(Theta-4*pi/3), 
                                  -sin(Theta), -sin(Theta-2*pi/3), -sin(Theta-4*pi/3),
                                    1/sqrt(2),          1/sqrt(2),          1/sqrt(2)] )
            T_inv = T.T
            # Verify inverse equals transpose
            display(simplify(T*T_inv))
            display(simplify(T_inv*T))

            # Matrix
            Labcσs = Matrix(3,3, [L_σ, M_σ, M_σ, \
                                  M_σ, L_σ, M_σ, \
                                  M_σ, M_σ, L_σ] )
            display(Labcσs)
            Ldqnσs = T * Labcσs * T_inv
            display(simplify(Ldqnσs))

            # LaTeX
            latex(simplify(Ldqnσs))
            ```
        - `ctrl+enter` to execute and stay at current block.
        - `shift+enter` to execute and move to next block.

2. Download and install [Visual Studio Code](https://code.visualstudio.com/download) before class. VS code is a popular editor for programmers.
    - **You need to install extension for Python**
    - We can then take advantage of its super-cool jupyter notebook compatibility.
        - ~~Option 1: to activate a regular jupyter notebook, press `ctrl+shift+p`, type `create: new jupyter notebook`.~~
        - Option 2: use the magic command `#%%` in your regular .py file.
            - `ctrl+enter` to execute and stay at current block.
            - `shift+enter` to execute and move to next block.
    - Alternative editor I very like is [sublime text 4](https://www.sublimetext.com/download)

## C1.2. Outline

1. Numerical simulation essentials
    - Euler method (ode1)
    - Runge Kutta method (ode4)
    - Learn concept of a variable step size solver
    - Solve for some example systems
2. Numba accelerated simulation
3. Separation between simulation framework and motor dynamics

<!-- 数值积分1阶4阶
可视化洛伦兹系统
numba加速
框架和电机模型分开
 -->

## C1.3. My Python Tutorials

[Donwload jupyter notebook .ipynb file here.](https://github.com/horychen/ee275/blob/master/python_tutorial_cjh.ipynb).


## C1.?. Learn Python in one video by Derek Banas (N4mEzFDjqtA)
(need access to Youtube)
{{< youtube N4mEzFDjqtA >}}















## C1.?. Quiz

{{< spoiler text="What is the difference between lists and tuples?" >}}
Lists

- Lists are mutable - they can be changed
- Slower than tuples
- Syntax: `a_list = [1, 2.0, 'Hello world']`

Tuples

- Tuples are immutable - they can't be changed
- Tuples are faster than lists 
- Syntax: `a_tuple = (1, 2.0, 'Hello world')`
{{< /spoiler >}}

{{< spoiler text="Is Python case-sensitive?" >}}
Yes
{{< /spoiler >}}
