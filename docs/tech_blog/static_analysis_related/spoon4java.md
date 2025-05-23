# 使用 Spoon 分析 Java 项目

Spoon 是一个用于 Java 静态分析与变换的框架。

## 快速示例

```java
Launcher launcher = new Launcher();
launcher.addInputResource("src/main/java");
launcher.run();
```
应用场景
	•	抽象语法树（AST）分析
	•	Java 代码的重写与重构

---

### 📄 `docs/tech_blog/LLM_related/ollama4application.md`

```markdown
# 使用 Ollama 构建本地 LLM 应用

Ollama 提供本地运行 LLaMA 系列模型的能力，适合开发私有 LLM 应用。

## 安装与运行

```bash
ollama run llama3
```

示例应用：问答系统

构建本地知识库问答系统，结合 embedding + Ollama 推理。

---

