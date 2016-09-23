# Python Pandas Notes

### Common commands -- Data Input & Info

```python
import pandas as pd
df = pd.read_table(fname, sep="\t", dtypes=(float,float))
df.info()
df.describe()
df.head()
print(df.columns())
```
