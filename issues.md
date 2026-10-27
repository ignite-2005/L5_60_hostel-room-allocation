# Issues Found and Fixes

Line numbers refer to the original `hostel_allocation.py` before changes.

| Issue | Type | Line(s) | Description | Fix Approach |
|---|---|---:|---|---|
| Unsafe YAML loading | High / Security | 19 | `yaml.load(..., Loader=yaml.Loader)` can construct arbitrary Python objects from untrusted YAML. | Replaced with `yaml.safe_load` and validated the configuration structure. |
| Hard-coded database password | High / Security | 65 | A password literal is embedded in source code. | Removed the literal; the demo reads configuration from environment variables and does not print a secret. |
| Remote logging listener | High / Security | 71 | Starting a remote logging configuration listener can expose a dangerous network control surface. | Removed the remote listener functionality. |
| Flask debug mode enabled | High / Security | 81 | Debug mode should not be enabled by default in a deployed application. | Changed the portal to run with `debug=False`. |
| HTML injection risk | Medium / Security | 76–78 | Query-string input was concatenated directly into HTML. | Escaped user-controlled text with `html.escape`. |
| Mutable default argument | Bug / Maintainability | 27 | `preferred=[]` shares one mutable list between calls. | Changed the default to `None` and creates a local list per call. |
| Capacity comparison incorrect | Bug | 31 | Using `>` allowed a room to exceed its stated capacity. | Changed the check to `>=` before assigning a bed. |
| Gender compatibility not checked | Bug | 27–34 | A student could be allocated to a room in a block intended for another gender. | Skips rooms whose configured gender does not match the student. |
| Vacating left stale occupancy | Bug | 39–43 | Removing an allocation did not remove the student from the room's occupant list. | Removes the student from both allocation and occupancy records. |
| Duplicate allocation | Bug | 27–35 | A student could be allocated more than once. | Returns the existing room if the student already has an allocation. |
| Unused imports and naming/style issues | Style | 1–5 and throughout | Unused imports, camelCase names, long lines, and inconsistent formatting reduce readability. | Removed unused imports, adopted snake_case names, and formatted the file consistently. |
| Unconditional execution on import | Maintainability | 99 | Importing the module ran the demonstration immediately. | Added the `if __name__ == "__main__"` guard. |
