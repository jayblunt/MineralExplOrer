
# Example optimizations for Eve - How much Ore do I need

*WORK IN PROGRESS* - this does not give useful results yet.

jupyter-lab notebook to explore optimization for eve ores.
This uses a subset of T1 ship hulls and some pre-generated data for mineral requirements and ore yields and prices. 

The pre-generated data for mineral requirements, ore yields, item info are from [Steve Ronuken](https://www.fuzzwork.co.uk/dump/).
Prices are from [ESI](https://esi.evetech.net/latest/markets/10000002/history) (include the type_id=NNN paramter to get the history for each item).
input_data.py has all the pre-generated data used in the notebook.

## Setup your python environment

You will need python3 (3.8 or better) installed. To make your environment use the following commands:

```shell
$ python3 -mvenv python-env
$ . python-env-bin/activate
$ pip install -U pip wheel setuptools
$ pip install --prefer-binary -r requirements.txt
```

If you get an error for a missing package, then find its name on [pypi](https://pypi.org) and then ```pip install``` it.


## Setup your jupyter-lab environment

```shell
$ jupyter-lab --generate-config
```

## Start jupyter

```shell
$ jupyter-lab
```


## Notes and Misc:

The optimizations are *slow* - they are currently brute-force searching.

Adding in the penalty for solutions that have too few minerals makes the objective function *very slow*.

Decreasing the number of possible inputs (reducing the dimensionality of the problem) makes the process faster (smaller search space).
I originally wanted to include all the required minerals and all the possible ores that yield only those minerals. This was just too slow.
I see why other ore calculators have a minimum number of ores - to keep the process as fast as possible.

I do not find any case where the cost of buying / refining ore is cheaper than the cost of buying the minerals directly.

The refining yield is very important to the cost of solutions - but if you are building at an NPC station then the refining yield is going to be terrible anyway - use a refining implant if possible.

Next up is to look at https://pypi.org/project/pymprog/ - introduced by Ja'e and used in an unmaintained project that is on github. Some input mangling required to get things setup.

Key Takeaway: Minerals are cheaper than Ore. There is a premium on Ore because it is so much more compact than the minerals it yields.


