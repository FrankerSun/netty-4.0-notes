An ExecutorService that can schedule commands to run after a given
delay, or to execute periodically.
ScheduledExecutorService在ExecutorService提供的功能之上增加了**延迟和定期执行任务**的功能。

```java
/**
 * 创建并执行在给定延迟后启用的一次性操作
 *
 * @param command 要执行的任务 
 * @param delay 从现在开始延迟执行的时间 
 * @param unit 延时参数的时间单位 
 * @return 表示任务等待完成，并且其的ScheduledFuture get()方法将返回 null完成后 
 * @throws RejectedExecutionException 如果任务无法安排执行 
 * @throws NullPointerException 如果命令为空 
 */
public ScheduledFuture<?> schedule(Runnable command,
                                   long delay, TimeUnit unit);

/**
 * 创建并执行在给定延迟后启用的ScheduledFuture。 
 *
 * @param callable 执行的功能 
 * @param delay 从现在开始延迟执行的时间 
 * @param unit 延迟参数的时间单位 
 * @param <V> the 可调用结果的类型 
 * @return一个可用于提取结果或取消的ScheduledFuture 
 * @throws RejectedExecutionException 如果该任务无法安排执行 
 * @throws NullPointerException 如果callable为空 
 */
public <V> ScheduledFuture<V> schedule(Callable<V> callable,
                                       long delay, TimeUnit unit);

/**
 * 创建并执行一个在给定初始延迟后首次启用的定期操作，后续操作具有给定的周期；也就是将在initialDelay后开始执行，然后在 
 * initialDelay+period后执行，接着在initialDelay + 2 * period后执行，依此类推。 
 * 如果任务的执行遇到异常，则后续的执行被抑制。 否则，任务将仅通过取消或终止执行人终止。
 * 如果任务执行时间比其周期长，则后续执行可能会迟到，但不会同时执行。 
 *
 * @param command 要执行的任务 
 * @param initialDelay 首次执行的延迟时间
 * @param period 连续执行之间的周期
 * @param unit initialDelay和period参数的时间单位 
 * @return 一个ScheduledFuture代表待完成的任务，其 get()方法将在取消时抛出异常 
 * @throws RejectedExecutionException 如果任务无法安排执行 
 * @throws NullPointerException 如果命令为空 
 * @throws IllegalArgumentException 如果period小于或等于零 
 */
public ScheduledFuture<?> scheduleAtFixedRate(Runnable command,
                                              long initialDelay,
                                              long period,
                                              TimeUnit unit);

/**
 * 创建并执行一个在给定初始延迟后首次启用的定期操作，随后，在每一次执行终止和下一次执行开始之间都存在给定的延迟。
*  如果任务的执行遇到异常，则后续的执行被抑制。 否则，任务将仅通过取消或终止执行人终止。 
 *
 * @param command 要执行的任务 
 * @param initialDelay 首次执行的延迟时间
 * @param delay 一次执行终止和下一次执行开始之间的延迟
 * @param unit initialDelay和delay参数的时间单位
 * @return 表示挂起任务完成的ScheduledFuture，并且其get()方法在取消后将抛出异常
 * @throws RejectedExecutionException 如果任务不能安排执行 
 * @throws NullPointerException 如果command为null
 * @throws IllegalArgumentException 如果delay小于等于0
 */
public ScheduledFuture<?> scheduleWithFixedDelay(Runnable command,
                                                 long initialDelay,
                                                 long delay,
                                                 TimeUnit unit);
```




>refer
>https://www.jianshu.com/p/a4608ac35277