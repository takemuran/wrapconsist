# wrapconsist

**检查接口响应包装格式是否前后一致。**

`wrapconsist` —— 比对多条响应的外层结构，标出包装字段缺失或类型变化

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`wrapconsist.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install takemuran-wrapconsist
```

装完直接用命令名调用：

```bash
wrapconsist --help
```

也可以不用安装，直接把 `wrapconsist.py` 拷走用——它只依赖标准库。

## 为什么需要它

外层包装是接口契约，改动会让所有调用方一起坏

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 响应包装一致性 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python wrapconsist.py --file input.txt
python wrapconsist.py --text "示例内容"
python wrapconsist.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 一致性靠字面差异判定，语义等价但写法不同会误报。
- 不解析跨文档的引用关系。

## 跑测试

```bash
python test_wrapconsist.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/takemuran/wrapconsist>

---

## 关于作者

takemuran 做响应包装一致性相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://takemuran.github.io>
- 仓库：<https://github.com/takemuran/wrapconsist>

## 许可

MIT，见 [LICENSE](LICENSE)。
