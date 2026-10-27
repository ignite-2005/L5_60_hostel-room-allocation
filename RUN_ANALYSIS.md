# Running Lab 5 Analysis

The repository's GitHub Actions workflow runs the tools in a hosted Ubuntu environment.

To run locally, install Python 3.11 or newer and then run:

```bash
python -m pip install flask pyyaml pylint bandit flake8
```

Generate reports for the original source snapshot and the fixed source:

```bash
python -m pylint reports/before/hostel_allocation.py > reports/before/pylint_report.txt 2>&1
python -m bandit -r reports/before/hostel_allocation.py > reports/before/bandit_report.txt 2>&1
python -m flake8 reports/before/hostel_allocation.py > reports/before/flake8_report.txt 2>&1

python -m pylint hostel_allocation.py > reports/after/pylint_report.txt 2>&1
python -m bandit -r hostel_allocation.py > reports/after/bandit_report.txt 2>&1
python -m flake8 hostel_allocation.py > reports/after/flake8_report.txt 2>&1
```

To get actual reports without installing tools locally, open the repository's **Actions** tab, select the latest **Lab 5 Static Analysis** run, and download the `lab5-static-analysis-reports` artifact. It contains before-and-after reports for all three tools.

The authoring environment used to prepare these changes had no package-index network access, so local tool results are not fabricated or represented as completed runs. Check the uploaded CI reports for the final Pylint score and any remaining findings.
