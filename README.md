# Python

This is a repository of patterns, anti-patterns, and best practices for Python development.

## Basic Tenants
 - Simplicity over complexity - Make your programs as simple as possible. Avoid creating structure for the sake of structure. 
 - Explicit over implicit - write your code for the reader. Make it easy to understand.
 - Comment often - Add comments that explain what/why you are doing something. You can gennerally assume that the reader can understand code, but if you are doing something more complex, it is good practice to clearly document what you are doing.


## Tips and Tricks

### Psudo Code
 When you are starting a coding project, write out the logic in comments. Create psudo functions with only input and outputs and docstrings defined. This can help you avoid the sunk cost fallacy which can happen when you have spent hours writing out your code and you find you have coded yourself into a corner.

 For example, your psudo code may look like:

 ```python
"""
We need to read a CSV input from the user and find all colunms that contain 
bind varibles. Bind variables are denoted by '${}'
"""

def extract_bind_variables(data: str) -> List[str]|List:
    """
    Use regex to find the bind variables.
    Return a list of them to the user.
    """

    # Extract the values using regex
    # Iterate through the matches
    # Return the list
 
def main(csv_file: Path):
    """
    Open the CSV File and read the data into memory
    Parse the data to find all bind variables
    Print that data
    """

    # Ensure that the csv_file Path passed to us is a real file
    # Open the File

    # Pass the data to the extract bind variables function 
    bind_variables = extract_bind_variables(data)

    #Iterate through the bind variables and print them out to the user
    for variable in bind_variables:
        print(variable)

```

I was able to create this in about 10 minutes. I haven't invested a huge amount of time into it, but I can already tell that this logic will work. I can now spend the time fleshing it out feeling fairly confident that I won't be heading for a wall.


### Verify Inputs
Python is a [duck-typed language](https://towardsdatascience.com/duck-typing-python-7aeac97e11f8#:~:text=Duck%20Typing%20is%20a%20term,care%20about%20whether%20it%20quacks.). That means that you never know what inputs your functions or methods  will be getting passed. It is a good practice to verify your inputs at the beginning of your function or method. Especially in cases where an input not being the right datatype may result in confusing errors.


```python

def map_datasets(table_reference: str, dataset_map: dict) -> str:
    """
    Given a table_reference like 'dataset.table' map the dataset (the first
    element) to the correct dataset using the provided map.
    """

    # Validate inputs
    assert isinstance(table_reference, str), "table_reference must be of type"\
        f" str. You passed in a {type(table_reference)}."

    assert isinstance(dataset_map, dict), "dataset_map must be of type dict. "\
        f"You passed in a {type(dataset_map)}."

    # Extract the dataset from the table reference
    split_table_reference = table_reference.split('.')

    assert len(split_table_reference) == 2, "Malformed table reference. The "\
        "table reference should contain a dataset and table name seperated by"\
        f" a period. E.g 'my_dataset.my_table'. You provided "\
        "'{table_reference}'."


    # Do stuff assuming that your inputs are correct
```

This will give the user of your method clear directions if they pass in something that you do not expect. It will also allow you to code with verified assumptions about the inputs to your method or function
