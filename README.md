## Tiny Benchmark: 一个基于JUnit5下对Java类进行性能压力测试的工具
## 设计目的
 - 提供一个简便的在UnitTest阶段对实装Class和Method进行性能压力测试时工具。
 - 输出性能压力测试的分析结果。
 - 使用@Benchmark注解简单绑定一个已有的TestCase。

##Usage

###1. Simple Run
```bash
mvn test
```


###2. Simple benchmark a exited test case
```java
import net.tiny.benchmark.Benchmark;

public class SampleTest {

    @Benchmark(warmup=10, measure=1000, trace=true)
    public void testTask() throws Exception {
        //Here is your test code
    }
}
```

###3. Benchmark your all your test cases
```java
import net.tiny.benchmark.Benchmark;

@Benchmark
public class SampleTest {
    @Test
    public void testTask() throws Exception {
        //Here is your test code
    }
}
```

###4. Include benchmark in your code
```java
import net.tiny.benchmark.Benchmarker;

public class SampleTest {

    public void testTask() throws Exception {
        Benchmarker bench = new Benchmarker();
        bench.start(10000L, 1000L);
        while (bench.loop()) {
            //Here is your test code
            bench.trace(System.out);
        }
        bench.stop(System.out);
    }
}
```

```bash
Summary ETA:66ms 459889ns MIPS:0.241 0.004ms/per min:51.520K/s max:395.396K/s avg:237.786K/s mean:197.736K/s count:10000 lost:4ms 665661ns
```


##More Detail, See The Samples

---
Email   : wuweibg@gmail.com
