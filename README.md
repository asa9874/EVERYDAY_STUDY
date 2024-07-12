<h1>공부 85일차</h1>


<h2>📌Python</h2>
카카오톡 단어 분석 프로그램제작</p>
matplotlib을 추가하여 막대 그래프로 통계볼수있도록 하였다. </p> 

![image](https://github.com/user-attachments/assets/9962751c-587d-4e0d-ab59-461fccb00aa9)

```python
def drawgraph(human, data):
    num_people = len(human)
    num_cols = 2  # 2열로 그래프를 나타내기 위한 설정
    num_rows = (num_people + num_cols - 1) // num_cols  # 적절한 행 개수 계산
    fig, axes = plt.subplots(nrows=num_rows, ncols=num_cols, figsize=(12, 4 * num_rows))

    if num_people == 1:
        axes = [axes]  # 하나의 사람일 경우를 처리

    for i, human_name in enumerate(human):
        row = i // num_cols
        col = i % num_cols

        keys = list(data[human_name].keys())
        values = list(data[human_name].values())
        keys_int = [int(key) for key in keys]

        bars = axes[row, col].bar(keys_int, values, color='skyblue')
        axes[row, col].set_xticks(keys_int)
        axes[row, col].set_ylabel('개수')
        axes[row, col].set_title(f'{human_name}')
        axes[row, col].tick_params(axis='x', rotation=45)  # x 축 눈금 라벨 회전 설정

        # 각 막대 위에 개수 표시
        for bar in bars:
            yval = bar.get_height()
            axes[row, col].annotate(f'{yval}', xy=(bar.get_x() + bar.get_width() / 2, yval),
                                    xytext=(0, 3), textcoords='offset points',
                                    ha='center', va='bottom')
        axes[row, col].set_ylim(top=max(values) * 1.1)
```

<h2>내일 목표</h2>
AWS 공부,JPA 공부