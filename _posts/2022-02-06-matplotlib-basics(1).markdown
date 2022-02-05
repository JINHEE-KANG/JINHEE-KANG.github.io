Ustage-week3 ***Data Visualization***

# Matplotlib


Python에서 사용할 수 있는 시각화 라이브러리
- `numpy`와 `scipy`같은 수학적 라이브러리 기반
  - 머신러닝 라이브러리(`sklearn`,`pytorch`,`tensorflow`,`pandas`)와 호환이 좋다
- 범용성이 넓고 가장 기본이 되는 시각화 라이브러리
  - 시각화는 점,선,면으로 구현-->다양한 시각화 방법론을 쉽게 구성함
- 이외에는 `seaborn`,`plotlt`, `bokeh`, `altair` 등이 있다

## Import


```python
import numpy as np
import matplotlib as mpl
```

> `matplotlib`은 1,2차원 벡터에 대한 표현이 좋다. 그래서 `numpy`로 벡터를 사용하기 위해 같이 호출한다.


```python
# version check
import sys

print(f'python version:{sys.version}')
print(f'numpy version:{np.__version__}')
print(f'matplotlib version:{mpl.__version__}')
```

    python version:3.7.12 (default, Jan 15 2022, 18:48:18) 
    [GCC 7.5.0]
    numpy version:1.19.5
    matplotlib version:3.2.2
    


```python
# installation
## pip
#!pip install matplotlib
```

```
💡 터미널 상에서 설치할 때

▶ pip
    python -m pip install -U pip
    python -m pip install -U matplotlib
▶ conda
  - conda install matplotlib
  - conda install -c conda-forge matplotlib
```


```python
import matplotlib.pyplot as plt
```

> `matplotlib`에서 가장 많이 사용하는 `pyplot`모듈

# Plot Basics
1. figure
2. ax


## figure 만들기
☝ `plt.figure()`

`fig`는 그래프를 그릴 큰 틀(팔레트)을 준비한다는 의미


```python
fig = plt.figure()
plt.show()
# %matplotlib inline
```


    <Figure size 432x288 with 0 Axes>


> 틀(팔레트)만 갖춘 상태. 그래프를 그리지 않아서 아무 것도 없다.

```
🔔 plt.show()는 Jupyter notebook이나 Ipython notebook에서는 필요없지만 다른 환경에서는 필요하다.

▶ plt.show()는 그래프를 그려서 보여준다는 의미

 plt.show를 사용하지 않으면 주피터 노트북에서도 마지막 변수만 출력하는 경향이 있다
 plt.show 대신 %matplotlib inline을 사용해도 된다.
```

## ax 만들기
☝ `fig.add_subplot()`

`fig`에 `ax`를 하나 추가한다. `ax`는 그래프 공간을 의미한다.


```python
fig = plt.figure()
ax = fig.add_subplot()
plt.show()
```


    
![png](images/u3_matplotlib_basics(1)_files/u3_matplotlib_basics(1)_16_0.png)
    


## ax 다루기
- 사이즈 조절하기
- 색상 바꾸기
- 여러 개 만들기

### 사이즈 조절하기
☝ `plt.figure(figsize=(w,h))`


```python
fig = plt.figure(figsize=(12,7))
ax = fig.add_subplot()
plt.show()
```


    
![png](images/u3_matplotlib_basics(1)_files/u3_matplotlib_basics(1)_19_0.png)
    


그래프 사이즈는 figsize로 ax의 사이즈를 조절한다. 원래 inch단위이기는 하지만 노트북에서는 정확한 길이보다는 비율이라고 생각하면 된다.

### 색상 바꾸기
☝ `fig.set_facecolor()`



```python
fig = plt.figure(figsize=(7,5))
fig.set_facecolor('yellow') #figure 색상을 yellow로 지정
ax = fig.add_subplot()
plt.show()
```


    
![png](images/u3_matplotlib_basics(1)_files/u3_matplotlib_basics(1)_22_0.png)
    


```
💡 위 코드의 실행결과를 보면 fig와 ax를 더 쉽게 이해할 수 있다.

set_facecolor()를 통해 figure를 yellow 색상으로 채웠고,yellow 색상의 팔레트 위에 (7,5)사이즈의 ax를 그렸다고 보면 된다.

즉, figure라는 틀에 그래프를 그릴 공간 ax를 넣은 것이다.
```

☝ `ax.set_facecolor()`


```python
fig = plt.figure(figsize=(7,5))
ax = fig.add_subplot()
ax.set_facecolor('yellow') #ax 색상을 yellow로 지정
plt.show()
```


    
![png](images/u3_matplotlib_basics(1)_files/u3_matplotlib_basics(1)_25_0.png)
    


### 여러 개 만들기


```python
# (1x2) 공간에 ax 2개 만들기
fig = plt.figure()
ax = fig.add_subplot(1,2,1) #121 사용 가능
ax = fig.add_subplot(1,2,2) #122 사용 가능
plt.show()
```


    
![png](images/u3_matplotlib_basics(1)_files/u3_matplotlib_basics(1)_27_0.png)
    


```
1,2,1은 1(row) x 2(col) 에서 1번째 그래프를 의미한다.
1,2,2는 1(row) x 2(col) 에서 2번째 그래프를 의미한다.
```


```python
# (2x1) 공간에 ax 2개 만들기
fig = plt.figure()
ax = fig.add_subplot(2,1,1) #211 사용 가능
ax = fig.add_subplot(2,1,2) #212 사용 가능
plt.show()
```


    
![png](images/u3_matplotlib_basics(1)_files/u3_matplotlib_basics(1)_29_0.png)
    


```
2,1,1은 2(row) x 1(col) 에서 1번째 그래프를 의미한다.
2,1,2는 2(row) x 1(col) 에서 2번째 그래프를 의미한다.
```


```python
# (2x2) 공간에 ax 4개 만들기
fig = plt.figure(figsize=(7,6))

ax = fig.add_subplot(2,2,1) #121 사용 가능
ax.set_title('ax1')
ax.set_facecolor('yellow')

ax = fig.add_subplot(2,2,2) #122 사용 가능
ax.set_title('ax2')
ax.set_facecolor('lightgreen')

ax = fig.add_subplot(2,2,3) #122 사용 가능
ax.set_title('ax3')
ax.set_facecolor('orange')

ax = fig.add_subplot(2,2,4) #122 사용 가능
ax.set_title('ax4')
ax.set_facecolor('skyblue')

plt.show()
```


    
![png](images/u3_matplotlib_basics(1)_files/u3_matplotlib_basics(1)_31_0.png)
    


```
2,2,1은 2(row) x 2(col) 에서 1번째(1,1) 그래프를 의미한다.
2,2,2은 2(row) x 2(col) 에서 2번째(1,2) 그래프를 의미한다.
2,2,3은 2(row) x 2(col) 에서 3번째(2,1) 그래프를 의미한다.
2,2,4은 2(row) x 2(col) 에서 4번째(2,2) 그래프를 의미한다.
```

☝ `plt.subplots(r,c)`


```python
# (2x2) 공간에 ax 4개 만들기
fig,axes = plt.subplots(2,2,figsize=(7,6))

colors = ['yellow','lightgreen','orange','skyblue']

for idx in range(4): # 0,1,2,3
  title = 'ax'+str(idx+1)
  axes[idx//2][idx%2].set_title(title)
  axes[idx//2][idx%2].set_facecolor(colors[idx])

plt.show()
```


    
![png](images/u3_matplotlib_basics(1)_files/u3_matplotlib_basics(1)_34_0.png)
    

