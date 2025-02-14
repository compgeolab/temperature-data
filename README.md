# Global monthly average temperature data

Download and create a subset of global monthly average temperature data for
different countries from [Berkeley Earth](https://berkeleyearth.org). This can
be used as sample data for introduction to programming and data science
classes.

## Download the data

Get the latest version of the dataset as a zip file:


| File | MD5 checksum |
|:-----|:----|
| [`temperature-data.zip`](https://github.com/compgeolab/temperature-data/releases/download/2025-02-11/temperature-data.zip) | `d102212049af1695b686c94ae1eea233` |

The zip file contains CSVs with the monthly average temperature in degrees
Celsius, one for each country. See the [README.md](data/processed/README.md)
for more information.

You can download and unpack this arquive in Python using the [Pooch](https://www.fatiando.org/pooch) library:

```python
import pooch

# Copy the URL and MD5 from above.
paths_to_each_file = pooch.retrieve(
    url="https://github.com/compgeolab/temperature-data/releases/download/2025-02-11/temperature-data.zip",
    known_hash="md5:d102212049af1695b686c94ae1eea233",
    processor=pooch.Unzip(),
)

# paths_to_each_file is a list with the path to each file in the archive
# The paths can be passed to pandas directly.
import pandas as pd

# Grab the second one because the README.md will be the first.
data = pandas.read_csv(sorted(paths_to_each_file)[1], comment="#")
```

## License

The processed temperature data are made available under the
[Creative Commons Attribution-NonCommercial 4.0 International license](https://creativecommons.org/licenses/by-nc/4.0/)
(CC-BY-NC).
Please credit the original authors of the data (Berkeley Earth) as well as
Leonardo Uieda when using this work.
Please include links to https://www.berkeleyearth.org and
https://github.com/compgeolab/temperature-data.

The Python source code is licensed under the MIT license.
