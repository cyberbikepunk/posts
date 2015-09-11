Having switched to The (Ana)Conda package manager lately, I was pleased to discover that PyCharm and Conda __and pip__ can work together in blissful harmony. Here's the how and the why.

##The short answer
Just manage Conda __from the command line__. PyCharm will automatically notice changes once they happen, just like it does with __pip__.

##The long answer
Create a new Conda environment:

```conda create --name foo pandas bokeh
```

This environment lives under `conda_root/envs/foo`. Your python interpreter is `conda_root/envs/foo/bin/pythonX.X` and your all your site-packages are in `conda_root/envs/foo/lib/pythonX.X/site-packages`. This is same directory structure as in a pip virtual environement. PyCharm sees no difference.

Now to activate your new environment from PyCharm go to *file > settings > project > interpreter*, select *Add local* in the project interpreter field (the little gear wheel) and hunt down your python interpreter. Congratulations! You now have a Conda environment with pandas and bokeh!

Now install more packages:

```conda install scikit-learn
```

OK... go back to your interpreter in settings. Magically, PyCharm now sees scikit-learn!

And __the reverse is also true__, i.e. when you pip install another package in PyCharm, Conda will automatically notice. Say you've installed requests. Now list the Conda packages in your current environment:

```conda list
```

The list now includes requests and Conda has correctly detected (3rd column) that it was installed with pip.

## Conclusion
This is definitely good news for people like myself who are sometimes having pip installation problems when packages are not pure python. 
