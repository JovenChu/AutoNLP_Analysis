# AutoNLP_Analysis
The analysis for AutoNLP and use in different data set

1. [AutoNLP 2019](https://www.4paradigm.com/competition/autoNLP2019)：

   * 由第四范式（4Paradigm）举办的自然语言处理竞赛，属于WAIC 2019的其中一个试题。

   * 目的：解决**多类文本分类问题**。

   * 解决挑战：

     *  如何自动预处理不同语言的文本数据？
     * 如何自动处理长文本和短文本？

     - 如何从文本数据中自动提取有用的功能？
     -  如何自动设计有效的神经网络结构？
     - 如何构建和自动选择有效的预训练模型？
     - 如何自动有效地选择合适的机器学习模型和超参数？
     - 如何使解决方案更通用，即如何使其适用于看不见的任务？
     - 如何保持计算和内存成本可以接受？

   * 数据集：这一挑战侧重于从现实世界企业收集的**多类文本分类**问题。数据集由内容文件，标签文件和元文件组成，其中内容文件和标签文件分为列车部件和测试部件：

     - **内容文件（{train，test} .data）**包含实例的内容。内容文件中的每一行代表实例的内容。

     - **标签文件（{train，dataset_name} .solution）**由one-hot格式的实例标签组成。请注意，其每一行对应于内容文件中的相应行号。

     -  **元文件（meta.json）**是一个json文件，由关于数据集的元信息组成，包括语言，列车实例编号，测试实例编号，类别编号。

     - 下图说明了数据集的形式：

       ![image-20190918165147920](https://joven-1252328025.cos.ap-shanghai.myqcloud.com/2019-09-18-085148.png)

   * 评估：数据集上的解的得分计算为**学习曲线下的面积（ALC）**。

     

2. autonlp_starting_kit

   * Download  docker：

     ```shell
     $ cd autonlp_starting_kit/
     $ docker run -it -v "$(pwd):/app/codalab" wahaha909/autonlp:gpu
     ```

     Output:

     ```shell
     docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.39/containers/create: dial unix /var/run/docker.sock: connect: permission denied.
     See 'docker run --help'.
     ```

     The option `-v "$(pwd):/app/codalab"` mounts current directory (`autonlp_starting_kit/`) as `/app/codalab`. If you want to mount other directories on your disk, please replace `$(pwd)` by your own directory.

   * The Docker image：

     ```shell
     $ wahaha909/autonlp:gpu
     ```

   * Usage：

     ```shell
     $ python run_local_test.py -dataset_dir=./AutoDL_sample_data/DEMO -code_dir=./AutoDL_sample_code_submission
     
     $ python run_local_test.py -dataset_dir=./AutoDL_sample_data/output/Reuters -code_dir=./AutoDL_sample_code_submission
     ```

     You can change the argument `dataset_dir` to other datasets (e.g. the five practice datasets we provide). On the other hand, you can also modify the directory containing your other sample code (`model.py`).

   * Result：

     * DEMO：
       * train time：2.68  sec
       * predict time：3.98  sec
       * score：0.763964
     * O1:
       - train time：0.21  sec
       - predict time：0.23  sec
       - score：0.615035
     * IMDB：
       - train time：8.70  sec
       - predict time：9.69  sec
       - score：0.753487
     * 20News：
       - train time：6.55  sec
       - predict time：7.21  sec
       - score：0.808549
     * AGNews：
       - train time：6.04  sec
       - predict time：6.58  sec
       - score：0.854864
     * DBpedia：
       - train time：39.42  sec
       - predict time：42.61  sec
       - score：0.836783
     * Reuters：
       - train time：1.92  sec
       - predict time：2.08  sec
       - score：0.668992