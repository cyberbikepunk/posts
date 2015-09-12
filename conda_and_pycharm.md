#How to make Conda work with PyCharm

My favorite IDE is [PyCharm](https://www.jetbrains.com/pycharm/). And recently, my favorite package manager has become [Conda](https://store.continuum.io/cshop/anaconda/). So I was *very* pleased to discover that __PyCharm__, __Conda__ and  and __pip__ can be happily coexist together in blissful harmony. Here's the how and the why.

##The short answer
Just manage Conda __from the command line__. PyCharm will automatically notice changes once they happen, just like it does with __pip__.

##The long answer
Create a new Conda environment:

```conda create --name foo pandas bokeh```

This environment lives under `conda_root/envs/foo`. Your python interpreter is `conda_root/envs/foo/bin/pythonX.X` and your all your site-packages are in `conda_root/envs/foo/lib/pythonX.X/site-packages`. This is same directory structure as in a pip virtual environement. PyCharm sees no difference.

Now to activate your new environment from PyCharm go to *file > settings > project > interpreter*, select *Add local* in the project interpreter field (the little gear wheel) and hunt down your python interpreter. Congratulations! You now have a Conda environment with pandas and bokeh!

Now install more packages:

```conda install scikit-learn```

OK... go back to your interpreter in settings. Magically, PyCharm now sees scikit-learn!

And __the reverse is also true__, i.e. when you pip install another package in PyCharm, Conda will automatically notice. Say you've installed requests. Now list the Conda packages in your current environment:

```conda list```

The list now includes requests and Conda has correctly detected (3rd column) that it was installed with pip.

## Conclusion
This is definitely good news for PyCharm fans like myself who were sometimes having pip installation problems when packages were not pure python. Now you can have the best of both worlds!
