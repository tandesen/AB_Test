## **$\textcolor{brown}{Business\ Goal}$**
就像 Instruction 里面说的，通过增加新功能，我们期望：
 * 增善学生体验，减少因为时间不够而中途退出 free trial 的学生数量。使 coaches 得到更好的分配，有更充足的时间和精力服务可能完成课程的学生。
 * 不会过多减少那些通过 free trial 并且最终完成课程的人数，不会大幅减少平台盈利。


## **$\textcolor{brown}{Metric\ Choice}$**
## **$\textcolor{grey}{Invariant\ Metrices}$**
 * **Number of cookies:** 这个是分组的依据，实验组与对照组除了新增功能的不同，其余应该保持统一，包括样本量，即这里的 cookies 。
 * **Number of clicks:** 点击 "Start free trial" 按钮的人数，这个是发生在 free trial trigger 之前的，所以实验组与对照组应保持统一，以防其他因素或者改变影响了实验效果。
 * **Click-through-probability:** `点击 "Start free trial" 按钮的人数`比上`浏览主页的人数`。这个指标比上面的更好，考虑到了分母即两组的 cookies 基数。但我还不知道实际需要这个和上面的指标都考虑么？只考虑这个点击率和两组基数 cookies 就可以了？因为看起来点击率和基数确定了，上一个指标就也确定了。或许也不用考虑这么多，都看一下就完事了。


## **$\textcolor{grey}{Evaluation\ Metrices}$**
 * **Number of user-ids:** 实验组里面这个数值应该会减少，但这不是一个比较好的指标，我们更倾向于选择比率类的指标。
 * **Gross conversion:** 这正是我们想要衡量的指标，分子是决定参加 free trial 计划的人数，在看到了我们的 trigger 之后仍然选择参加 free trial 的人数，分母是点击了 "Start free trial" 的人数，注意这里的点击是在我们的 trigger 出现之前。
 * **Retention:** 这不是一个好指标因为需要的时间太长了，分子需要至少 14 天以后才能收集到信息，我们整个实验就要拖得很长，还要去除掉前面14天的数据，做 cohort analysis 等等。如果要测的话我们会期望这个指标减少，因为 trigger 赶走了一些心不诚的人，剩下注册了的会更倾向于 pass 14-day boundary 。
 * **Net conversion:** 这个指标跟上面一个指标一样，都存在数据收集时间过长的问题。如果要计算这个指标的话，期待在实验组会减少，因为部分人被 trigger 后选择不 enroll 。

还有一些指标我觉得 instruction 里面没写出来的，因为 business goal 里面提到了 coach 相关的事情，我们做了实验也期望可以使 coach 资源得到更合理且高效的分配。我现在能想到的指标包括互动率，比如平均每人每天与 coach 交流的次数或者时长，但这个指标可能非常的稳定，出现了变化极大程度上会是由于我们实验设置上的问题而不是真的由于我们的新功能，要具体的看一下。还有一个指标是 coach 这方面两组平均每天上线时长或者与学生交流次数，指标存在的问题也跟前面一个一样。  

指标产生怎样的变化我才会上线新功能？  
我会选择 **Gross conversion** 和 **Net conversion** 两个 Evaluation Metric 指标。前两个指标里面选择点击率而不是点击量指标，后两个选择 **Net conversion** 因为这个指标穿越的漏斗指标层级之间包括了我们的 trigger，但是后面这两个指标还是存在计算时间过长的问题。如果我们有足够的时间的话，我们期望这两个指标在实验组都要上涨。


## **$\textcolor{brown}{Measuring\ Variability}$**
对于指标 **Gross conversion**，我们用 Enrollments per day (660) 除以 Unique cookies to click "Start free trial" per day (3200)，算得 0.20625。Variability 是 $\sqrt(p(1-p)*(2/N))$，这里 p 是 0.20625，N 是单组的样本量。因为我们分组用的是 cookies，计算指标的时候只能用 cookies 或者 event_based clicks。对于指标 **Net conversion**，我们用 "Probability of payment, given click"，数值是 0.1093125，variability 的计算方式与上面一个指标相同。因为我们要追踪用户，计算指标时候要用 cookies 而不是 event_based clicks，而且两个指标都是去重的点击率，可以用正态分布模拟，所以不用计算 empirical variance。


## **$\textcolor{brown}{Sizing}$**
我们选择的两个 evaluation metrices 之间有很大的相关性，可用 bonferroni correction 来进行修正，即选择 $\frac{\alpha}{2}=0.025$ 来作为每个 metric 的 alpha 值。通过样本量计算网站得到两个指标需要的样本量结果如下：


![lll](sample_size_gross_conversion.PNG)

![lll](sample_size_net_conversion.PNG)


所以我们最后取 35013 样本量即可。


## **$\textcolor{grey}{Duration\ and\ Exposure}$**
如果我们要测量 **Net conversion** 指标的话，我们就需要很长时间的实验，至少要14天以上，才能测得有效数据进行计算。实验周期可以选4周。但这太久了，就像 Instruction 里面说的。所以不然就不去算 **Net conversion** 这个指标，想一想其他的指标来代替。我问了 Udacity 的 chatgpt，回答如下：  
```
对于你的情况，如果你希望在几周内进行短期的A/B实验并测量指标数据，可以考虑以下替代指标：

活跃用户比例：该指标可以通过计算每个实验组中的活跃用户数量与总用户数量的比例来衡量。
活跃用户可以定义为在一定时间范围内与产品进行交互的用户。这个指标可以更快地反映用户对产品的兴趣和参与度。

转化率：转化率是指用户从一个阶段转移到下一个阶段的比例。
例如，你可以关注用户从注册到完成某项操作（如购买、订阅等）的转化率。这个指标可以帮助你了解用户在关键行为上的表现。

平均访问时长：这个指标可以衡量用户在产品上的停留时间。
通过比较实验组和对照组的平均访问时长，你可以了解到用户对不同版本的产品的使用习惯和偏好。

这些替代指标可以在较短的时间内收集数据，并提供有关用户体验的有用信息。
当然，选择适合你实验目标的指标时，要确保它与你的研究问题和产品目标相一致。你可以根据实际情况选择一个或多个指标来评估实验结果。
```

对于实验时长和周期的考虑，还要看用户群体。是上班族？那实验周期就一定要包括周末，因为上班族一般周末学习的时间比较多。是学生党？那就要看实验的时间是不是学生放假的时候？考试周？等等。  


## **$\textcolor{brown}{Analysis}$**
