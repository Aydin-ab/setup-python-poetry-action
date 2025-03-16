# Setup Python with Poetry - GitHub Action

This action sets up Python with Poetry, ensuring that dependencies are cached for faster builds.

## 🚀 Usage

```yaml
jobs:
  setup:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Python & Poetry
        uses: your-username/setup-python-poetry@v1
        with:
          python-version: "3.11"
```

## 🛠 Features
- Installs Python (any version)
- Installs Poetry
- Uses cached dependencies (via `poetry.lock`)
- Ensures the Poetry virtual environment is set correctly

## 🎯 Inputs
| Name            | Description             | Required |
|----------------|-------------------------|----------|
| `python-version` | Python version (e.g. `"3.11"`) | ✅ Yes |

## ⚖️ License
This project is licensed under the MIT License.
