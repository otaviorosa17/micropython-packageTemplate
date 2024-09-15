# Package Template

Package Template

(meta) Considerations

1. I believe running through a simple tutorial or a simple example is the most natural way to learn something.
   - but *simple* examples may get complicated as the author knowledge evolves. I'll try not to do this.
2. This example is based on https://github.com/jimmo/micropython-mlx90640 (forked on Sept, 15, 2024)
   - added a working function into `packageTemplate.utils` in order to provide a more useful example

## Objective

Show how to create Micropython packages with explanations (as detailed as possible/manageable)

## Results

### The shortest path (by now)

1. Install, to your micropython device, this package (to test if the instructions are still useful);
2. Run, in you micropython device, a function from the package;
3. Clone/Fork this repository (do not change the repository name);
4. Edit file `utils.py` add your code in it;
5. Commit changes
6. Install, to your micropython device, your package;

#### Install, to your micropython device, this package (to test if the instructions are still useful);

Connect you micropython device to the Internet by ajusting and running the code below:
  
```python
import network, time
staif=network.WLAN(network.STA_IF) 
staif.active(True) 
staif.connect(<YOUR_NET>, <PASSWORDOFYOUR_NET>)
```

Download and install the package by running the code below:
  
```python
import mip
mip.install("github:FNakano/micropython-packageTemplate")
```

Expected result:

![](/Captura%20de%20tela%20de%202024-09-15%2013-17-03.png)

#### Run, in you micropython device, a function from the package;

 Package name is `packageTemplate`. It contains a module named `utils`. This module contains a function named `sayHello(name)`
 
Run the function by running the code below:

```python
import packageTemplate
from packageTemplate import utils
utils.sayHello('Jim') 
```

Expected result:
  
![](./Captura%20de%20tela%20de%202024-09-15%2015-03-11.png)

#### Clone/Fork this repository (do not change the repository name) to your github user or to your local computer;
#### Edit file `utils.py` add your code into it;
#### Commit changes to your repository in Github;
#### Install, to your micropython device, your package;

```python
import mip
mip.install("github:YOUR_GITHUB_USER/micropython-packageTemplate")
```

## Details

- About Python modules/packages (https://docs.python.org/3/tutorial/modules.html)
  - Explains why `__init.py__` is necessary
  - Explains why
  ```python
  import packageTemplate
  from packageTemplate import utils
  utils.sayHello('Jim') 
  ```
  should be like it is
- latest documentation about Micropython mip: https://docs.micropython.org/en/latest/reference/packages.html
- forum posts on Micropython mip: https://github.com/orgs/micropython/discussions/11980
- repository of packages designed to be useful for writing MicroPython applications: https://github.com/micropython/micropython-lib

There is not much documentation on what each entry in `package.json` mean. Perhaps a *by example* approach would be enough. 

```json
{
  "urls": [
    ["packageTemplate/__init__.py", "github:fnakano/micropython-packageTemplate/packageTemplate/__init__.py"],
    ["packageTemplate/utils.py", "github:fnakano/micropython-packageTemplate/packageTemplate/utils.py"]
  ],
  "deps": [
    ["collections-defaultdict", "latest"]
  ],
  "version": "0.1"
}
```

> More sophisticated packages (i.e. with more than one file, or with dependencies) can be downloaded by specifying the path to their package.json.

(Source: https://docs.micropython.org/en/latest/reference/packages.html#installing-packages-with-mip , accessed Sept, 15, 2024)
