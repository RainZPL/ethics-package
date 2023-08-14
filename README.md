# ethics-package
a Python Package that includes normative ethics principles functions to deal with deciding the best action and allocating resources

# How did we create
After creating the algorithms for ethical principles for solving __Deciding the Best Action__ and __Allocating Resources__, we gave each principle algorithm a defined function, which returns the best result computed for specific principle and other reference outputs. For example, Utilitarianism, which solves Deciding the Best Action, returns the best behaviour and the maximum utility/happiness value. To create the Python Package, we created a `class` called `Principle`, and we put each principle function into this `class`. Each `self` parameter in this `class` is taken from the input of the users, who enter relevant parameters (e.g. number of users, preferences, number of resources, principle factors, etc.) based on their subjective judgement and pass them to `self` function. The code below shows the base class of the class hierarchy:
```python
def __init__(self, preference=None, happiness=None, contribution=None, luck=None, resources=None, resources_num=0, users=0)
```
Then the `Users` function in the Principle `class` stores each `self` data and integrates it into a large `list dict`. When the user calls which principle function in which scenario, `Users` and `self` are used by specific principle function call to calculate and generate the final result.


# How to Import and Use
If others want to use our ethics principles Python Package, they first need to import it:
```python
from ethics import ethics_test
```
If used to solve the __Deciding the Best Action__ scenario, creating parameters for the `number of users`, `preferences`, and `principle factor values` is necessary. The `number of users` parameter is of type `int`; the `preference` parameter is a `list`, which contains the preferred behaviours of all users; and the `principle factor values` parameter is `list dict`, which contains the factor values of all users for each of the preferred behaviours, e.g. if there are a total of two users, with preferences London and Bristol, and the requirement is to take into account the factor of Happiness, then the possible factor value is `happiness=({'London': 5, 'Bristol': 6}, {'London': 7, 'Bristol': 4})`. After creating these variables, pass them into the `self` function, then call the `Users` function to aggregate the data for each principle factor, and finally call specific principle functions to get results. Code below is an example of calling the functions for __Deciding the Best Action__:
```python
    output = principle.Principle(preference, happiness, contribution, luck, None, 0, num_user)

    users = output.Users()
    
    utilitarianism_Output = output.Utilitarianism(users)
    
    prioritarianism_Output = output.Prioritarianism(users)
    
    desertbased_proportionalism_Output = output.DesertBased_Proportionalism(users)
    
    libertarian_proportionalism_Output = output.Libertarian_Proportionalism(users)
```

In addition, when used to solve the __Allocating Resources__ scenario, creating parameters for the `number of users`, `resource names`, `number of resources` and `principle factor values` is necessary. The `number of users` parameter is of type `int`; the `resource name` is `string`; the `number of resources` is `int`; and the `principle factor values` parameter is of type `list`, which contains the values of all users' principle factors about either the resource or themselves, e.g., if there are two users in total, and it is requested that the factor of Happiness be considered, it might be `happiness=(6, 7)`. The subsequent calling package functions process is made in the same way as described in the Deciding the Best Action instructions, except that the principle functions for __Allocating Resources__ are different. Code below is an example of calling principle functions for this scenario:
```python
    output = principle.Principle(None, happiness, contribution, 0, resource, resource_num, num_user)

    users = output.Users()

    utilitarianism = output.utilitarianism_allocate(users)
    
    libertarian_proportionalism = output.libertarian_allocating(users)
```
