[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

Exercise 2.4 Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. Compute Cohen’s d to quantify the difference between the groups. How does it compare to the difference in
pregnancy length?

hist = thinkstats2.Hist(live.totalwgt_lb, label='totalwgt_lb')
thinkplot.Hist(hist)
thinkplot.Show(xlabel='pounds', ylabel='frequency')

for pounds, freq in hist.Smallest(10):
    print(pounds, freq)

for pounds, freq in hist.Largest(10):
    print(pounds, freq)

mean = live.totalwgt_lb.mean()
std = live.totalwgt_lb.std()

mean, std

first_baby = live[live.birthord == 1]
other_babies = live[live.birthord != 1]

first_baby_hist = thinkstats2.Hist(first_baby.totalwgt_lb, label = 'first baby')
other_babies_hist = thinkstats2.Hist(other_babies.totalwgt_lb, label = 'other babies')

width = 0.25
thinkplot.PrePlot(2)
thinkplot.Hist(first_baby_hist, align='right', width=width)
thinkplot.Hist(other_babies_hist, align='left', width=width)
thinkplot.Show(xlabel='pounds', ylabel='frequency', xlim=[1,16])

CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
-0.088672927072602

Comments: Given Cohen's d of approx. -0.089, my interpretation is that the difference in means of newborn weights for first babies vs. other babies is very small (and first babies are ever-so-slightly less heavy).  Cohen's d for pregnancy lengths in first babies vs. other babies was 0.029, an even smaller difference 

