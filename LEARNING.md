# 井字棋：Java 入门学习指南

这份指南为学习副本补充；原仓库：https://github.com/LazoVelko/Tic-Tac-Toe 。原作者的玩法和 AI 介绍见 README.md。

## 适合学习的范围
先学习棋盘、输入检查、轮流落子和胜负判断。项目中的 Alpha-Beta AI 属于进阶内容，可以暂时当作已提供的功能调用。

需要先了解 Java 的类、对象和 enum；二维数组、循环、if、方法和 Scanner 都能直接用到。

## 在 Mac 上运行控制台版
需要 JDK。在仓库根目录执行：
```bash
mkdir -p out
javac -d out TicTacToe/TicTacToe/*.java TicTacToe/ArtificialIntelligence/*.java
java -cp out TicTacToe.Console
```
输入 0 到 8 选择格子，编号从左到右、从上到下排列；中心是 4。这一版本默认玩家与 AI 对战。

说明：已检查源码目录、包名和入口方法；当前教学环境没有 javac，未在这里实际编译或运行。

## 推荐阅读顺序
1. `TicTacToe/TicTacToe/Console.java` 的 main 和 play：程序从哪里开始，为什么不断循环。
2. `getPlayerMove()`：Scanner 读取数字，检查范围和格子是否为空。
3. `TicTacToe/TicTacToe/Board.java` 的 initialize 和 reset：创建棋盘并清空状态。
4. `move(int index)`：index % 3 得到列，index / 3 得到行。
5. `checkRow/checkColumn/checkDiagonal...`：判断三格是否相同。
6. `getTurn/getWinner/isGameOver`：如何把棋盘状态交给界面使用。
7. 最后再学习 ArtificialIntelligence 目录的递归搜索。

注意：某些原始注释与实现不一致。下标转换以代码为准，例如 index = 4 的行、列均为 1；即从 0 开始计数的中心格。

## 三个由易到难的练习
1. 修改提示文字，让玩家更清楚该输入 0–8。
2. 给 getPlayerMove 加上 InputMismatchException 处理；输入字母时提示错误并清理输入，程序继续运行。这里能练习你在 CSC1003 学过的 Scanner 和异常。
3. 将 Console 的 playMove 改成双方都调用 getPlayerMove，做控制台双人对战；轮换由 Board 处理。

## 完成后检查
- 输入 a 不崩溃；输入 -1 或 9 不落子。
- 已有棋子的格子不能再次落子。
- 行、列、两条对角线获胜都能被识别。
- 棋盘填满且无人获胜时判为平局。
- 重开后棋盘、步数、轮次恢复初始状态。

先把双人版规则理解清楚，再研究 AI 为什么能选择下一步。
