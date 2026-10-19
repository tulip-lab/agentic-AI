# 专题大纲与课程安排

[项目首页](README.md) | [课程介绍](description.md) | [学习目标](learning-outcomes.md) | [专题大纲与安排](syllabus.md) | [实践与工具](lab-map.md) | [学习建议与成果](assessment-map.md)

本系列共 **10 学时，五场专题，合计 450 分钟**，结合原理讲解、案例分析、应用演示与实践。

| 专题 | 主题 |
| --- | --- |
| S01 | 生成式 AI 与智能体：基础、能力边界与商科应用 |
| S02 | AI Engineering：从提示词到智能体系统 |
| S03 | AI赋能课程建设与教学资源开发 |
| S04 | AI赋能作业设计、预批改与教学评价 |
| S05 | AI赋能科研、论文协作与学术评审 |

S01–S05 是本系列的专题编号；M01–M08 是 FLIP 共享技术模块编号。每个专题可结合多个技术模块。下列参考材料中的链接可直接查阅；不带链接的名称用于说明专题实践方向。

## S01 生成式 AI 与智能体：基础、能力边界与商科应用

从生成式 AI 与大语言模型出发，介绍智能体如何结合工具、上下文和反馈完成任务，比较单模型、单智能体和多智能体协作的特点。联系商科教学与科研任务，讨论从文本生成到实际行动的变化，以及可靠性、权限与教师判断的重要性。

**主要内容**：大语言模型与智能体；工具调用与 Agent loop；多模态能力；多智能体协作；幻觉与能力边界；商科应用情境。

**技术模块**：[M01 智能体基础](https://github.com/tulip-lab/agentic-AI/blob/develop/M01-Foundations/README.md)；[M06 多智能体与安全](https://github.com/tulip-lab/agentic-AI/blob/develop/M06-Multi-Agent-Safety/README.md)。

**Lab 参考**：[M01B 生成式 AI 与智能体基础](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M01-Foundations/Jupyter/M01B-GenAI-Fundamentals.ipynb)；[M01C 工具调用与 API](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M01-Foundations/Jupyter/M01C-LLMs-FunctionCalling-APIs.ipynb)。

**专题实践**：围绕 Data Privacy 情境，比较单模型、单智能体与多角色审核的结果、权限和证据。

## S02 AI Engineering：从提示词到智能体系统

介绍如何把教学与科研需求转化为清晰任务，组织上下文与知识来源，并通过工具、可复用技能和质量控制提升工作流的可用性。理解提示词、检索、记忆、工具接口与执行机制各自承担的责任，学习用可检查的输出要求评价系统。

**主要内容**：Prompt Engineering；Context Engineering；检索增强生成（RAG）；工具与 MCP；Skills；Harness 与智能体评价。

**技术模块**：[M02 提示词与 RAG](https://github.com/tulip-lab/agentic-AI/blob/develop/M02-Prompt-RAG/README.md)；[M03 上下文与编排](https://github.com/tulip-lab/agentic-AI/blob/develop/M03-Context-Orchestration/README.md)；[M08 智能体工程](https://github.com/tulip-lab/agentic-AI/blob/develop/M08-Agent-Engineering/README.md)。

**Lab 参考**：[M02A 提示词基础](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M02-Prompt-RAG/Jupyter/M02A-Prompt-Foundations.ipynb)；[M02B 提示词工程与受控改进](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M02-Prompt-RAG/Jupyter/M02B-Prompt-Engineering-Control-Loop.ipynb)；[M08E 工作流质量控制](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M08-Agent-Engineering/Jupyter/M08E-Agent-Hooks-WorkflowGuards.ipynb)。

**专题实践**：以 Data Privacy 资料建立任务规范与 Teaching Skill，比较 Prompt—Context—Skill—Harness 的责任与停止条件。

## S03 AI赋能课程建设与教学资源开发

围绕课程学习目标，探讨 AI 如何支持大纲、教学活动、讲义、课件与练习的设计，以及课程知识助手如何利用已有资料支持教学。以 Data Privacy 课程为案例，讨论隐私泄露、数据泄密与差分隐私的不同边界，核查生成内容的准确性、资料来源与教学适切性，并讨论向商科课程的迁移。

**主要内容**：课程目标与教学活动对齐；课程知识助手；讲义与练习设计；Slidev 课件；教学内容审核与来源核查。

**技术模块**：[M03 上下文与编排](https://github.com/tulip-lab/agentic-AI/blob/develop/M03-Context-Orchestration/README.md)；[M05 知识与状态智能体](https://github.com/tulip-lab/agentic-AI/blob/develop/M05-Knowledge-Agents/README.md)；[M08 智能体工程](https://github.com/tulip-lab/agentic-AI/blob/develop/M08-Agent-Engineering/README.md)。

**Lab 参考**：[M03C Flowise 课程资料检索](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M03-Context-Orchestration/Flowise/M03C-Flowise-RAG-Public-Unit-Docs.md)；[M05B 课程知识助手](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M05-Knowledge-Agents/Jupyter/M05B-RAG-CourseMaterials-Assistant.ipynb)；[课程资源贯通实践（L1/L2）](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M05-Knowledge-Agents/Applications/course-rag)。

**专题实践**：Data Privacy 课程案例（隐私泄露、数据泄密与差分隐私）；Course Design Skill；Lecture Planning Skill；Slidev 教学资源生成。

## S04 AI赋能作业设计、预批改与教学评价

探讨 AI 如何支持作业说明、评价标准和反馈设计，介绍多角色审核在改进作业质量与评价一致性中的作用。结合工作流与多智能体方法，分析从作业设计、审核到预批改的过程，重视证据、公平性和教师的最终判断。

**主要内容**：Assignment Design；Rubrics；作业发布与审核流程；预批改反馈；多智能体审核；评分一致性与人工负责。

**技术模块**：[M03 上下文与编排](https://github.com/tulip-lab/agentic-AI/blob/develop/M03-Context-Orchestration/README.md)；[M06 多智能体与安全](https://github.com/tulip-lab/agentic-AI/blob/develop/M06-Multi-Agent-Safety/README.md)；[M08 智能体工程](https://github.com/tulip-lab/agentic-AI/blob/develop/M08-Agent-Engineering/README.md)。

**Lab 参考**：[M03D Flowise AgentFlow 与安全工具](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M03-Context-Orchestration/Flowise/M03D-Flowise-AgentFlow-Safe-Tools.md)；[M06A 多智能体协作](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M06-Multi-Agent-Safety/Jupyter/M06A-MultiAgent-Collaboration.ipynb)；[M08A 评价方法](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M08-Agent-Engineering/Jupyter/M08A-HuggingFace-Evaluation.ipynb)。

**专题实践**：以同一 Data Privacy 情境设计 Assignment Design Skill、Rubric、合成作业预批改与多角色审核。

## S05 AI赋能科研、论文协作与学术评审

围绕研究问题、文献证据和学术表达，探讨智能体在研究规划、论文写作与模拟同行评审中的应用。分析研究主张与证据的关系，讨论多角色评审、意见汇总和分歧处理，以及协作效果、成本与可复现性的评价。

**主要内容**：文献与证据整理；研究计划；学术写作协作；模拟 Peer Review 与 Meta-Review；可复现性；质量与效率评价。

**技术模块**：[M04 智能体编程与工具](https://github.com/tulip-lab/agentic-AI/blob/develop/M04-Agent-Programming/README.md)；[M05 知识与状态智能体](https://github.com/tulip-lab/agentic-AI/blob/develop/M05-Knowledge-Agents/README.md)；[M06 多智能体与安全](https://github.com/tulip-lab/agentic-AI/blob/develop/M06-Multi-Agent-Safety/README.md)；[M08 智能体工程](https://github.com/tulip-lab/agentic-AI/blob/develop/M08-Agent-Engineering/README.md)。

**Lab 参考**：[M04D 研究与写作智能体](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M04-Agent-Programming/Jupyter/M04D-LeadResearch-WritingAgent.ipynb)；[M05A 检索与证据基础](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M05-Knowledge-Agents/Jupyter/M05A-Basic-RAG-System.ipynb)；[M06A 多智能体协作](https://github.com/tulip-lab/agentic-AI-lab/blob/develop/M06-Multi-Agent-Safety/Jupyter/M06A-MultiAgent-Collaboration.ipynb)。

**专题实践**：围绕 Data Privacy 的合成研究问题，制作证据表、研究计划、模拟同行评审与 Meta-Review。

贯穿案例的[Data Privacy L1–L3 实验](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M06-Multi-Agent-Safety/Applications/data-privacy)可按需要用于 S01、S02 和 S05；S03 的[课程资源贯通实践](https://github.com/tulip-lab/agentic-AI-lab/tree/develop/M05-Knowledge-Agents/Applications/course-rag)提供教学资源设计路线。工具选择与实践建议见[实践与工具](lab-map.md)。
