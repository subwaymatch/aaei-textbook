# Jupyter Notebooks

Jupyter Notebooks are an open-source web application that allows you to create and share documents that contain live code, equations, visualizations, and narrative text. They are widely used in data science, machine learning, and scientific computing for data cleaning and transformation, numerical simulation, statistical modeling, data visualization, and machine learning.

The name "Jupyter" is a combination of "**Ju**lia", "**Py**thon", and "**R**", which are three programming languages commonly used in data science. The name also pays homage to Galileo's notebooks, as Jupiter is the largest planet in our solar system and was named after the Roman god Jupiter.

```{image} images/jupyter-name-origin.jpg
:alt: Where does the name Jupyter come from?
:align: center
```

&nbsp;

---

## 🚀 Why Use Jupyter Notebooks?

- **Interactive Coding**: You can write and execute code in small chunks (cells), making it easier to test and debug.
- **Rich Media**: You can include images, videos, and interactive visualizations alongside your code.
- **Documentation**: You can use Markdown to create well-documented notebooks that explain your code and findings.
- **Reproducibility**: Notebooks can be shared and rerun by others, ensuring that your analyses can be reproduced.
- **Integration**: Jupyter supports many programming languages, including Python, R, and Julia.

---

## 💻 Running Jupyter Notebooks using Google Colab

There are multiple ways to run Jupyter Notebooks. For this course, we recommend using Google Colab, which is a free cloud-based service that allows you to run Jupyter Notebooks without any local installation. You can access it at [colab.research.google.com](https://colab.research.google.com/). It provides free access to GPUs and TPUs, making it suitable for machine learning tasks.

:::{warning} Use Google Colab for This Course!
Unless you're already familiar with Jupyter Notebook environments, we strongly recommend using **Google Colab** for this course. It simplifies the setup process and allows you to focus on learning Python and data analytics without worrying about local installations and configurations.
:::

Follow these steps to get started with Google Colab:

First, go to [colab.research.google.com](https://colab.research.google.com/). If you're not signed in, you'll see a screen like this: Click on the "Sign In" button at the top right corner.

```{image} images/colab/click-on-sign-in-button.png
:alt: Click on the Sign In Button
:align: center
```

Once you're signed in, go back to the Colab homepage at [colab.research.google.com](https://colab.research.google.com/). Click on the "New Notebook" button.

```{image} images/colab/click-on-new-notebook.png
:alt: Click on the New Notebook Button
:align: center
```

This will create a new Jupyter Notebook in Google Colab with a blank code cell ready for you to start coding.

```{image} images/colab/new-notebook-screen.png
:alt: New Notebook Screen
:align: center
```

Let's test it out by running a simple block of code. Copy the following code into the code cell and click on the "Run" button (the play icon) or press `Shift + Enter` on your keyboard.

```python
import pandas as pd

my_series = pd.Series([10, 20, 30, 40])
print(my_series)
```

```{image} images/colab/run-code-cell.png
:alt: Run Code Cell
:align: center
```

You can also add a "Text Cell" to include explanations or notes. Move your cursor to the area below your code cell. This will display the buttons to add a new cell. Click on the "+ Text" button to add a new text cell.

```{image} images/colab/hover-to-add-new-cell.png
:alt: Hover to Add New Cell
:align: center
```

The "Text Cell" uses Markdown syntax, which allows you to format your text. You can write headings, lists, links, and more. Although we won't cover Markdown in detail here, you can refer to the [Markdown Guide](https://www.markdownguide.org/basic-syntax/) for more information.

```{image} images/colab/text-cell-example.png
:alt: Text Cell Example
:align: center
```

Note that you can add more code cells and text cells as needed by using the "+ Code" and "+ Text" buttons. Let's add another code cell below the text cell by clicking on the "+ Code" button. The Jupyter Notebook environment has a "memory" that retains the state of your variables and imports across different code cells. For example, you can reuse the `my_series` variable defined in the first code cell in this new code cell. Copy the following code into the new code cell and run it.

```python
# multiply each element and print the result
print(my_series * 2)
```

```{image} images/colab/add-another-code-cell.png
:alt: Add Another Code Cell
:align: center
```

This will output:

```plaintext
0    20
1    40
2    60
3    80
dtype: int64
```

We won't worry about the details of these code blocks just yet. Finally, you can run all the code cells in your notebook by using the "Run All" button.

```{image} images/colab/run-all-button.png
:alt: Run All Button
:align: center
```

For now, that's a brief introduction to using Jupyter Notebooks with Google Colab.

---

### 📦 Other Installation Options for Running Jupyter Notebooks

If you prefer to run Jupyter Notebooks locally on your machine, here are some options:

1. **JupyterLab Desktop App**: JupyterLab is the next-generation user interface for Jupyter Notebooks. It provides a more flexible and powerful environment for working with notebooks, code, and data. You can download the JupyterLab desktop app from [here](https://github.com/jupyterlab/jupyterlab-desktop/releases).

2. **Anaconda Distribution (Local Installation via Anaconda)**: Anaconda is a popular distribution of Python and R for scientific computing and data science. It comes with Jupyter Notebooks pre-installed. You can download Anaconda from [here](https://www.anaconda.com/products/distribution).

3. **JupyterLab (Local Installation via `pip`)**: JupyterLab is the next-generation user interface for Jupyter Notebooks. It provides a more flexible and powerful environment for working with notebooks, code, and data. You can install it using pip:

   ```bash
   pip install jupyterlab
   ```

   Then, you can start JupyterLab by running:

   ```bash
   jupyter lab
   ```

4. **Visual Studio Code (VS Code)**: VS Code is a popular code editor that supports Jupyter Notebooks through an extension. You can install the "Jupyter" extension from the VS Code marketplace. More information can be found [here](https://code.visualstudio.com/docs/datascience/jupyter-notebooks).

---

## 🔄 Jupyter's Read-Eval-Print Loop (REPL)

```{image} images/jupyter-repl.jpg
:alt: Read-Eval-Print Loop (REPL)
:align: center
```

&nbsp;

The Jupyter Notebook interface operates as a Read-Eval-Print Loop (REPL). REPL is the fundamental loop behind interactive programming environments. It consists of three main steps:

1. **Read**: The system takes in user input (e.g., `print(3 + 20)`).
2. **Eval**: The input is evaluated by the interpreter. In this case, it executes the expression `3 + 20`.
3. **Print**: The result of evaluation (`23`) is printed back to the user.

This is why when you open a Python shell, you can type a command, see the result immediately, and continue typing more commands interactively — it's the REPL cycle at work.

```{image} images/how-jupyter-runs-your-code.jpg
:alt: How does Jupyter Notebooks Run Code?
:align: center
```

&nbsp;

The underlying process for a Jupyter Notebook environment is REPL-based — just separated into a client (browser interface) and a backend (kernel).

1. **JupyterLab in Browser**: A user runs a code cell inside the Jupyter Notebook (`.ipynb`).
2. **Input**: The content of the cell (e.g., `print(3 + 20)`) is sent to the backend.
3. **Python Kernel**: The kernel executes the code, just like the "Eval" step in REPL.
4. **Output**: The kernel sends the result (`23`) back to JupyterLab, which displays it under the code cell.

### 🧠 Maintaining State with the Kernel

The kernel maintains the state of the notebook, including variables, functions, and imports. This means that you can run code cells in any order, and the state will persist until you restart the kernel or close the notebook.
