# How to make Conda work with PyCharm

My favorite IDE is [PyCharm](https://www.jetbrains.com/pycharm/). And recently, my favorite package manager has become [Conda](https://store.continuum.io/cshop/anaconda/) So I was pleased to discover that __PyCharm__, __Conda__ *and* __pip__ can be happily coexist together in blissful harmony. Here's how and why.

## The short answer

Just manage Conda __from the command line__. PyCharm will automatically notice changes once they happen, just like it does with __pip__.

## The long answer

Create a new Conda environment:

	conda create --name foo pandas bokeh

This environment lives under 

	conda_root/envs/foo

Your python interpreter is 

	conda_root/envs/foo/bin/pythonX.X

And your all your site-packages are in 

	conda_root/envs/foo/lib/pythonX.X/site-packages

This is same directory structure as in a pip virtual environment. PyCharm sees no difference. Now to activate your new environment from PyCharm go to *file > settings > project > interpreter*, select *Add local* in the project interpreter field (the little gear wheel) and hunt down your python interpreter. Congratulations! You now have a Conda environment with Pandas and Bokeh!

Now install more packages, for example:

	conda install scikit-learn

OK... go back to your interpreter in settings. Magically, PyCharm now sees SciKit-Learn!

And __the reverse is also true__, i.e. when you pip install another package in PyCharm, Conda will automatically notice. If you do 

	pip install requests`

and then list the Conda packages in your current environment with 

	conda list

you will see that Conda now includes Requests. Indeed, the third column indicates the package was installed with pip.

## Conclusion

This is good news for PyCharm fans like myself who are sometimes having trouble with pip installations. Alas, this tends to happen when a package has lots of non-python dependencies. Conda spares you these head-aches by shipping all dependencies pre-compiled. Now you can have the best of all worlds... Cool.
