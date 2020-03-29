[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

Exercise 3.1 Something like the class size paradox appears if you survey children and ask how many children are in their family. Families with many children are more likely to appear in your sample, and families with no children have no chance to be in the sample.
1) Use the NSFG respondent variable NUMKDHH to construct the actual distribution for the number of children under 18 in the household.
2) Now compute the biased distribution we would see if we surveyed the children and asked them how many children under 18 (including themselves) are in their household.
3) Plot the actual and biased distributions, and compute their means

Part 1: 
kids_under_18 = resp['numkdhh']
kids_under_18_pmf = thinkstats2.Pmf(kids_under_18, label='actual')

Part 2:
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
    
    new_pmf.Normalize()
    return new_pmf

biased_pmf = BiasPmf(kids_under_18_pmf, label='observed')

thinkplot.PrePlot(2)
thinkplot.Pmfs([kids_under_18_pmf, biased_pmf])
thinkplot.Show(xlabel='children per family', ylabel='PMF')

Part 3:
print('mean', kids_under_18_pmf.Mean())
print('mean', biased_pmf.Mean())
