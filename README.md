###WHAT:
Run examples to compare runtimes between 3.8 and 3.9 in a push button fashion.

Currently this is set up for the following three neural networks from the [examples repo](http://github.com/deeplearning4j/dl4j-0.4-examples)

* MLPMnistSingleLayerExample
* LenetMnistExample
* GravesLSTMCharModellingExample

Note that these examples have been modified to run only for one epoch.

###HOW:
* Clone this repo
* `cd runtimes_3p8_3p9`
* `./RUN_me list_of_examples`


###WHAT ELSE?
* What does this script do?
  * It uses mvn to kick off these examples. The examples are all kicked off in parallel and run in the background. Once they are all complete the script parses stdout for runtimes and prints comparisons.

* How can you add more examples to this list?
  * Add the files to both the golden_run and the revised_run directory. The contents of these two directories are exactly the same except for the pom.
  * Calculate relevant runtime from within the code and print out in the following format. **Note, that this is the format the script parses for and without this it won't be able to extract runtime.**
`System.out.printf("INFO_PRINT: RUNTIME: %d\n",runtime);`
  * Add the path to the example to "list_of_examples"

* How do I run only one of the examples?
  * Delete all the other examples in "list_of_examples"
  *` ./RUN_me list_of_examples`

* What if I want to run less than one epoch - say a couple of iterations?
Sure. Obviously, make sure changes made are reflected in both the golden_run and revised_run dir. The contents of these two directories should be exactly the same except
 for the pom.

* How long will this take to run?
Depending on what you are running and on what you are running.
The prompt will return when all the runs have completed. It will print out something that looks like this:

```
WAITING FOR RUNS TO COMPLETE.........
= * = * = * = * = * = * = * = * = * = * = * = *= * = * = * = * = * = * = * = * = * = * = * = * * = * = * = * = * = *
                                       MLPMnistSingleLayerExample
= * = * = * = * = * = * = * = * = * = * = * = *= * = * = * = * = * = * = * = * = * = * = * = * * = * = * = * = * = *
MLPMnistSingleLayerExample runs 31% faster in the snapshot
```
