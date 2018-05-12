# JAVA8
[Stream](#stream)
- [generate 100 random distinct int](#generate-100-random-distinct-int)

## Stream
### generate 100 random distinct int
[back](#java8)
  ```Java

  public class test {
      // define a supplier
      private class randomS implements Supplier<Integer> {
          @Override
          public Integer get() {
              return new Random().nextInt(100);
          }
      }

      @Test
      public void test() {
          Integer[] i = {0};
          // generate Stream
          Stream.generate(new randomS())
                  // no repeating
                  .distinct()
                  // limit quantity
                  .limit(100)
                  // give a sort
  //                .sorted((a, b) -> a < b ? 1 : (a.equals(b)) ? 0 : -1)
                  // terminal ： print out 
                  .forEach(t -> {
                      i[0]++;
                      System.out.print(t + ",,," + (i[0]) + "\n");
                  });

                  //Another way
  //        IntStream.generate(() -> (int) (System.nanoTime() % 100))
  //                .distinct()
  //                .limit(10)
  //                .forEach(System.out::println);
      }
  }
  ```
