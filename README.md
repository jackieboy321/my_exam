这是根据公司现有模拟考试系统改写的程序
首发版本主要功能：
1. 从题库中随机选择200题组成一份试卷（150选择题+50是非题）。
2. 运行程序开始考试，会先要求你输入一个考试ID。可以随意输入，没有字符限制，但输入后请牢记自己的ID。因为这会影响到程序后续的功能。
3. 程序会自动统计每个ID做错的题目（根据不同ID分别统计），并自动生成一个JSON文件用来记录每个ID每次考试的错题。这个JSON文件不要删除。
4. 程序会累计统计每个ID的历史错题，并且根据同一道题目的错误次数动态调整错题权重。接着在你每开始一次新的考试时，程序都会先从JSON文件中读取此ID的历史错题，计算权重，然后增加选中这些历史错题的概率。（前提是你每次考试都使用相同的考试ID）
5. 每次考试后，程序会生成2个TXT文本文件，一个是“错题.txt”，用来显示你此次考试的错题，并显示正确答案。另外一个是“错题类似.txt”，由于题库中存在大量描述非常接近、但答案不同的题目，为了对这些题目进行着重记忆，所以提供了这个功能。程序会把你每道做错的题目跟题库中的所有题目去进行比对，字符相似度达到80%以上的题目会被列为类似题目，与你的错题一起显示在“错题类似.txt”中。

后续v0.02版本将会改进：
1. 目前程序为了测试运行稳定性、方便纠错，只做了命令行窗口运行（CMD窗口运行）的方式，没有图形界面，需要手动输入选择题的'A''B''C''D'答案序号、或者是非题的'对'或'错'。
2. 由于原题库中存在极少部分带有图片内容的题目，因此在目前CMD命令行运行的环境下，此类带有图片的题目无法显示图片内容。
3. 增加简单的图形界面，使得可以使用鼠标选择答案，而不必键盘输入答案。