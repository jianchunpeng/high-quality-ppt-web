# Guided Intake Questions

Use this when the user gives a topic, file, URL, or rough requirement but has not provided a complete presentation brief.

## Principle

Read or skim the material first when available. Ask 3-6 targeted questions tied to the material. Include a recommended default for each important choice.

Do not make the user become a prompt engineer. Your job is to turn their incomplete intent into a useful creative brief.

## Minimum Brief

Capture these fields:

- audience: who will listen
- occasion: meeting, class, roadshow, report, training, keynote, review
- desired outcome: understand, approve, decide, remember, act
- duration: minutes or target slide count
- tone: formal, sharp, warm, dramatic, academic, product-led
- style: preset or reference direction
- source fidelity: faithful summary, persuasive rewrite, bold reinterpretation
- image appetite: none, few key visuals, image-rich
- interaction level: static, light motion, interactive web talk

## Question Patterns

Use questions like these, adapted to the actual material:

- "这份材料主要讲给谁听？领导决策、客户路演、课堂分享，还是项目复盘？我建议先按目标听众决定信息密度。"
- "你希望听众结束后做什么：理解背景、同意方案、批准预算、还是记住一个观点？我建议把这个作为主线。"
- "演讲大概多长？如果没有固定时长，我建议按 10-12 页做，适合 8-15 分钟讲清楚。"
- "内容要忠实压缩原文，还是可以重构成更有说服力的现场表达？我建议专业汇报保留事实，标题和过渡大胆重写。"
- "风格更适合哪种：政务汇报、科技发布会、杂志叙事、瑞士信息设计、教育讲解？根据材料我建议先选一个主风格。"
- "配图要真实资料图、AI 生成图、图表地图，还是混合？我建议只生成关键横版图，其余用图表和版式完成。"
- "需要多少网页现场感：静态翻页、轻量动效，还是点击展开/数据切换/地图交互？我建议 HTML 版至少加入转场和分步揭示。"

## Recommended Default

When the user is unsure, propose:

```text
我建议做成 10-12 页，采用一个主风格，先给你页级大纲、配图计划和动效计划。配图只生成 3-5 张关键横版图，其余用图表、地图和排版承接，这样更稳，也更像正式演讲材料。
```

## Mode Choice

- Use fast mode if the user says "直接做", "你决定", "快点出一版".
- Use guided mode if the topic is clear but audience or style is unclear.
- Use master mode if the deck is image-heavy, high-stakes, public-facing, or the user explicitly wants a polished result.
