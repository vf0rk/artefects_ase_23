## Description

We have proposed a new repair technique named REPATT, which incorporates a two-level pattern mining process for enabling effective patch generation (i.e., token and expression levels). To evaluate the performance of REPATT, we have conducted an extensive study over the widely-used Defects4J benchmark by comparing it with eight state-of-the-art APR approaches. The results show that our approach complements existing approaches by repairing 15 unique bugs compared with the latest deep learning-based method and 19 unique bugs compared with traditional repair methods when providing the perfect fault localization. In addition, when the perfect fault localization is unknown in real practice, REPATT significantly outperforms the baseline approaches by achieving much higher patch precision, i.e., 81.1%. The results demonstrate the effectiveness of our approach for practical use.

## Project Structure

```
.
├── d4j-info                    #Information about D4j, such as failing tests 
├── expriment_without_skip.zip  #Experiment logs of RQ2
├── lib                         #Essential java libaraies 
├── res                         #Log4j settings
├── repatt.jar                  #Executable Jar File of RePatt
├── sbfl_result.zip             #Experiment of our tool in SBFL scenario
├── src                         #Source code, based on SimFix
├── standard_experiment_log.zip #Experiment logs of RQ1
├── test                        #Unit tests
├── token_freq_2_log.zip        #Experiment logs of RQ3
└── token_freq_5_log.zip        #Experiment logs of RQ3 
```



## Reproducibility

The most Easy way to run the artefacts is using our docker images

`docker pull veweew/ase_23_artefacts`

After successfully launching the docker container, the path to the executable artifacts is `/artefacts`.

To check out the buggy projects, you must place them in the `d4j` folder. The path should be formatted as `/d4j/project/project_id_buggy`, with all directory names in lowercase. Three sample projects, Codec 3, JacksonDatbind 96, and CLi 5, have already been checked out in the docker image.

To execute the program, simply run `./test.sh`, and the fix process will begin.

The command to run Repatt is as follows:

```
java -Xmx10240m -jar repatt.jar --proj_home=/artefacts --proj_name=jacksondatabind --bug_id=96
```

------

If you wish to configure the environment by yourself, you should follow these steps:

1. Install JDK 8.
2. Install the Defects4j Framework.
3. Configure your environment variables by adding `JAVA_TOOL_OPTIONS=-Dfile.encoding=UTF8` and `DEFECTS4J_HOME=/path_to_d4j`.
4. Run the program with arguments, as mentioned above.
