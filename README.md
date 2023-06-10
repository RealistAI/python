# Python

This is a repository of patterns, anti-patterns, and best practices for Python development.

## Basic Tenants
 - Simplicity over complexity - Make your programs as simple as possible. Avoid creating structure for the sake of structure. 
 - Explicit over implicit - write your code for the reader. Make it easy to understand.


## Tips and Tricks
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

    # Open the File

    # Pass the data to the extract bind variables function 
    bind_variables = extract_bind_variables(data)

    #Iterate through the bind variables and print them out to the user
    for variable in bind_variables:
        print(variable)

```

I was able to create this in about 10 minutes. I haven't invested a huge amount of time into it, but I can already tell that this logic will work. I can now spend the time fleshing it out feeling fairly confident that I won't be heading for a wall.
