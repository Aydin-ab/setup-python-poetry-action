# **Setup Python with Poetry - GitHub Action** 🚀  

This GitHub Action **sets up Python with Poetry**, ensuring that dependencies are cached for faster builds. It is designed for **projects using Poetry** as a dependency manager and helps simplify & speed up workflows by caching **both Poetry binaries and dependencies**.

---

## **📌 Features**
✅ **Installs Python** (any version)  
✅ **Installs Poetry** if not found  
✅ **Caches dependencies** using `poetry.lock`  
✅ **Ensures the Poetry virtual environment is properly configured**  
✅ **Supports all OS environments** (`ubuntu-latest`, `macos-latest`, `windows-latest`)  

---

## **📥 Inputs**
| Name              | Description                                    | Required | Default |
|------------------|--------------------------------|----------|---------|
| `python-version` | The Python version to install | ✅ Yes   | None    |

---

## **📤 Outputs**
This action **does not return any outputs**, but it ensures that **Python and Poetry** are correctly installed and ready for subsequent workflow steps.

---

## **🔑 Secrets**
This action **does not require any secrets**.

---

## **🌍 Environment Variables**
This action **does not require any environment variables**.

---

## **📖 Example Usage**
### **🔹 Basic Usage**
This workflow **installs Python 3.11, sets up Poetry, and installs dependencies**:

```yaml
jobs:
  setup:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4  # ✅ Check out repository
      
      - name: Setup Python & Poetry
        uses: your-username/setup-python-poetry@v1  # ✅ Use the GitHub Action
        with:
          python-version: "3.11"

      - name: Verify Installation
        run: poetry run python --version
```

---

## **🛠 How It Works**
1. **Installs Poetry** if not already available.
2. **Sets up Python** (using `actions/setup-python`).
3. **Caches Poetry dependencies** to avoid redundant installations.
4. **Configures the Poetry's version of Python** (`poetry env use <version>`).
5. **Installs project dependencies** using `poetry install`.

---

## **📦 How to Use with a Cached Virtual Environment**
If you want to **cache the virtual environment (`.venv`)** for faster builds:

```yaml
jobs:
  setup:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Restore Cached Virtual Environment
        uses: actions/cache@v4
        with:
          path: .venv
          key: venv-${{ runner.os }}-${{ hashFiles('poetry.lock') }}

      - name: Setup Python & Poetry
        uses: your-username/setup-python-poetry@v1
        with:
          python-version: "3.11"

      - name: Run Tests
        run: poetry run pytest
```

---

## **📝 License**
This project is licensed under the **MIT License**.

---

## **💡 Best Practices**
- **Pin a version of the action** in your workflows to ensure stability.

---

## **📢 Contributing**
- **Found an issue?** Open an [issue](https://github.com/your-username/setup-python-poetry/issues).
- **Want to improve it?** Submit a pull request!

