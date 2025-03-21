# **Setup Python with Poetry - GitHub Action** 🚀  

This GitHub Action **sets up Python with Poetry**, ensuring that the poetry binaries in .local/ and the dependencies are both cached for faster builds. It is designed for **projects using Poetry** as a dependency manager and helps simplify & speed up workflows by caching **both Poetry binaries and dependencies**.

There is an additional checkout step at the start to further declutter the caller workflow.

---

## **📌 Features**
- ✅ **Checkout to the caller github repo**
- ✅ **Cache hit poetry binary (.local) or install it**
- ✅ **Installs Python** (any version)  
- ✅ **Caches poetry dependencies** using `poetry.lock`
- ✅ **Ensures the Poetry virtual environment is properly configured to the right python**  
- ✅ **Supports all OS environments** (`ubuntu-latest`, `macos-latest`, `windows-latest`)  

---

## **📥 Inputs**
| Name              | Description                                    | Required | Default |
|------------------|--------------------------------|----------|---------|
| `python-version` | The Python version to install |  No   | latest from the setup-python action    |
| `poetry-version` | The Poetry version to install |  No   | latest release from pypi    | 

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
      # - uses: actions/checkout@v4  # No need anymore
      
      - name: Setup Python & Poetry
        uses: aydin-ab/setup-python-poetry-action@v1.1.0  # ✅ Use the GitHub Action
        with:
          python-version: "3.11" # optional
          poetry-verison: "2.1" # optional

      - name: Verify Installation
        run: poetry run python --version
```

---

## **🛠 How It Works**
1. **Checkout to the github repo**
2. **Set python/poetry version if not provided as inputs**
3. **Installs Poetry** or load binaries (at ~/.local) from cache if not already available.
4. **Sets up Python** (using `actions/setup-python`).
5. **Configures the Poetry's version of Python** (`poetry env use <version>`).
6. **Install Poetry dependencies** or load dependencies from cache if not already available. (cached by `actions/setup-python`)


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

