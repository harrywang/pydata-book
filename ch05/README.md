## This is the note for chapter 5
The following shows how to construct a Series and a DataFrame

    import pandas as pd
    from pandas import Series, DataFrame
    series = Series([4, 7, -5, 3])
    data = {'state': ['Ohio', 'Ohio', 'Ohio', 'Nevada', 'Nevada'],
            'year': [2000, 2001, 2002, 2001, 2002],
            'pop': [1.5, 1.7, 3.6, 2.4, 2.9]}
    frame = DataFrame(data)

To iterate through a dictionary, no matter what the varible names are, the first is the key and the second is the value (in 3.x, iteritems() has been replaced with simply items()):

    for foo, bar in dict.iteritems():
        print foo, bar

Useful command:

View first/last five:

    frame.head()
    frame.tail()

better histogram example:

    data = DataFrame({'q1':['a','a','c','d','g'],
                      'q2':['b','c','e','h','f'],
                      'q3':['a','h','f','g','b']})

        q1 q2 q3
    0  a  b  a
    1  a  c  h
    2  c  e  f
    3  d  h  g
    4  g  f  b

    histogram = data.apply(pd.value_counts).fillna(0)

        q1  q2  q3
    a   2   0   1
    b   0   1   1
    c   1   1   0
    d   1   0   0
    e   0   1   0
    f   0   1   1
    g   1   0   1
    h   0   1   1

Missing values

    from numpy import nan as NA

it does not matter which key is first, the following two commands are the same:

    frame.swaplevel('key1', 'key2')
    frame.swaplevel('key2', 'key1')

The term panel data refers to multi-dimensional data frequently involving measurements over time:

    person  year  income  weight
    1       2001  1300    150
    1       2002  1500    140
    2       2001  1400    200
    3       2001  2000    250

The above is an unbalanced panel because not each person is measured every year.

Series.ix: A primarily label-location based indexer, with integer position fallback.
