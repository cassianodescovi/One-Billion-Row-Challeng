# One Billion Rows: Data Processing Challenge with Python

## Introduction
The aim of this project is to demonstrate how to efficiently process a massive data file containing 1 billion rows (~14GB), specifically to calculate statistics (including aggregation and sorting, which are heavyweight operations) using Python.

This challenge was inspired by The One Billion Row Challenge (https://github.com/gunnarmorling/1brc), originally proposed for Java.

The data file consists of temperature measurements from various weather stations. Each record follows the format `<string: station name>;<double: measurement>`, with the temperature presented to one decimal place precision.

Here are ten example lines from the file:

| Station            | Temperature |
|--------------------|-------------|
| Nsanje             | -45.5       |
| Tirorā             | -76.1       |
| Boumia             | 15.7        |
| Leskovac           | 42.5        |
| Baharampur         | -68.0       |
| South Londonderry  | 23.7        |
| Balingoan          | -56.8       |
| Haa                | 44.0        |
| Stuhr              | -30.7       |
| Nyurba             | -63.3       |



The challenge is to develop a Python program capable of reading this file and calculating the minimum, average (rounded to one decimal place), and maximum temperature for each station, displaying the results in a table sorted by station name (example table below).

| station      | min_temperature | mean_temperature | max_temperature |
|--------------|-----------------|------------------|-----------------|
| Abha         | -31.1           | 18.0             | 66.5            |
| Abidjan      | -25.9           | 26.0             | 74.6            |
| ...          | ...             | ...              | ...             |

## Results
Tests were performed on a laptop equipped with an i7 processor and 16GB of RAM. Implementations utilized purely Python approaches, Pandas, and DuckDB. Runtime results for processing the 1 billion row file are presented below:

| Implementation  | Time        |
|-----------------|-------------|
| Bash + awk      | 25 minutes  |
| Python          | 20 minutes  |
| Python + Pandas | 263 seconds |
| Python + Duckdb | 14.98 seconds |

## Conclusion
This challenge has clearly highlighted the effectiveness of various Python libraries in handling large volumes of data. Traditional methods like Bash (25 minutes), pure Python (20 minutes), and even Pandas (263 seconds) required a range of tactics to implement "batch" processing, whereas libraries like DuckDB prove to be exceptionally efficient, requiring fewer lines of code due to its inherent ability to distribute data in "streaming batches" more efficiently. DuckDB stood out, achieving the shortest execution time thanks to its execution strategy and data processing capabilities.

These results emphasize the importance of selecting the right tool for large-scale data analysis, demonstrating that Python, with the right libraries, is a powerful choice for tackling big data challenges.

DuckDB also wins with 1 million rows, proving to be the best option.

## How to Run
To execute this project and reproduce the results:

- Clone this repository
- Set the Python version using `pyenv local 3.12.1`
- Run `poetry env use 3.12.1`, `poetry install --no-root`, and `poetry lock --no-update`
- Execute the command `python src/create_measurements.py` to generate the test file
- Be patient and go make a coffee; it will take about 10 minutes to generate the file
- Make sure to install the specified versions of libraries
- Run the scripts `python src/using_python.py`, `python src/using_pandas.py`, and `python src/using_duckdb.py` through a terminal or development environment that supports Python.

This project highlights the versatility of the Python ecosystem for data processing tasks, offering valuable lessons on tool choice for large-scale analyses.

