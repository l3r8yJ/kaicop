**KaiCop** stands for [KaiCode](https://www.kaicode.org/2024.html) and [Cop](https://en.wikipedia.org/wiki/Cop).

To roughly estimate code quality in a large number of projects,
we need to have some metric that is not tied to the programming language and its paradigm.
We can't rely on any specific rules, because the rules of writing quality code in procedural
style and functional style will be completely different.
To solve this problem, KaiCop proposes the idea of comparing code _consistency_ within a project.
This metric will not be tied to the language, paradigm, etc.

### Example:

*Disclaimer – this example just showing way of caclucating, real measurement using a lot more parameters rather than style of method arguments. For each project set of rules will be different.*

We're having 10 methods in the project.

```java
public static void doSmth1(int first, int second) {
    // code
}


public static void doSmth2(
    int first, int second
) {
    // code
}

public static void doSmth3(
    int first,
    int second
) {
    // code
}

public static void doSmth4(
    int first, int second) {
    // code
}
```

7 out of 10 written like in style of `doSmth1`.
One written like `doSmth2`, one written like `doSmth3`, one written like `doSmth4`. Now we can build a histogram like this one

![histogram-1.png](assets/histogram.png)

We have another project which histogram looks like this

![Screenshot20240519at134233.png](assets/histogram-2.png)

Now we can say, that in first case quality of code much higher then in second one. Code in first project was written more consistenly. In term of code quality for set of absolutely different projects we can't stand on **spiceific rules**. The code will be more readable and maintainable just by being consistent; with one style, with set of desing rules(that are defined in some place)[](https://) which will restrict doing wrong design desicions. If we take a look at our example. We can say that perfect project will have only the one style of passing aruments and doesn't metter wich one it will be. Like `doSmth1` or `doSmth3`, or something else. Only one thing is important here – consitency. When we have a close to`100%` hit of some case, it's says that project have:

1. Linting or auto checkstyle check built into CI
2. Good code reveiw process

Or both of them.

### How to define "consistency"

To define *consistency* of the project we can scan it's code base. During the scan process we need to determine a several approaches, desing principles and etc. that were used. When we have a set of rules for speciefic project appears the opportunity to count how code was distributed grouping by this rules. If destribution looks like second example, we can say that code inconsistent and code quality is low.
