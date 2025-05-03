# Project-2

# Table of Data
|Thread<br>Count|Wall Clock<br>Time|User Time|System Time|Speedup|
|:--:|--:|--:|--:|:--:|
|1|14.61|13.91| 0.52|1.00|
|2| 8.24|15.34| 0.53| 1.77|
|3| 5.79|15.75| 0.67| 2.52|
|4| 4.56|15.75| 0.87| 3.20|
|5| 3.76|15.68| 0.87| 3.89|
|6| 3.38|16.29| 1.11| 4.32|
|7| 2.93|16.35| 0.97| 4.99|
|8| 2.80|16.86| 1.30| 5.22|
|16| 2.07|18.38| 2.96| 7.06|
|24| 1.92|18.71| 7.15| 7.61|
|32| 1.91|18.42|11.50| 7.65|
|40| 1.95|17.64|17.29| 7.49|
|48| 1.98|17.35|19.47| 7.38|
|56| 1.88|17.23|26.38| 7.77|
|64| 1.95|17.12|25.81| 7.49|
|72| 1.90|17.11|32.25| 7.69|
|80| 1.97|17.57|18.11| 7.42|

# Speed-up vs. Number of Threads
![Speed-up vs  Number of Threads](https://github.com/user-attachments/assets/129aa174-0e56-4d5a-927e-76a94ee7054a)

# Question 1
Q. Notice that there is a maximum speed-up factor, but not necessarily using the most threads. Make a guess (i.e., write a short paragraph) as to why you think more threads aren't necessary better. Here's a hint: think about a group of people waiting to go through a turnstile (like at BART or Disney World). Are more people able to go through it just because there are more people?


A. More threads are not necessarily better because all the threads still need to share resources. In terms of the analogy, a lot of people does not increase the amount of people able to go through because there is a limited amount of a resource, in this case, it is space. So, to some point, if there are enough resources to supply every thread with some left over, increasing the number of threads will increase the speed; however, once there are more threads than there are resources to supply those threads, they end up clogging up the system and slowing it down.

# Question 2
Q. Do you think it's possible to get "perfect scaling" — meaning that the $(1-p)$ terms is zero?


A. I do not think it is possible to get "perfect scaling" because some part every program must be sequential since it is impossible to make everything run in parallel.

# Question 3
$$ speedup = \frac{1}{1 - 0.99699 + \frac{0.99699}{16}} \approx 15.31$$

# Question 4
Q. In reviewing the graph of speed-ups to number of threads, note that we get pretty linear (when you plot the dots, they're pretty close to being a line) speed-up. What's the slope of that line? (Pick two values, like for one and seven threads, and do the rise-over-run thing you learned in Algebra). Does that linear trend continue as we add more threads? What do you think causes the curve to "flatten out" when we use large thread counts?


A. Taking the values of 1.00 for 1 thread and 4.99 for 7 threads we get that the slope of the line is 0.665. As we add more threads, the linear trend does not continue; instead, the curve flattens out. I think the curve flattens out when we use large thread counts because of Amdahl's Law, which tells us that some part of the program is unable to be parallelized no matter how many threads we give the program; therefore, speed-up is not increased with an increase in threads once we get to that bottleneck.
