# MTF/FTM 嗓音判断小工具
# MTF/FTM Voice Gender Analysis Tool

---

## 原理
## How It Works

> 引自 https://gist.github.com/ypwhs/b6731d3e795ced814311573d26edd21c
> Referenced from https://gist.github.com/ypwhs/b6731d3e795ced814311573d26edd21c

使用决策树（机器学习）的方法判断一段音频信号是男性还是女性，以及男女倾向百分比。
Uses a decision tree (machine learning) approach to determine whether an audio signal is male or female, along with a probability percentage for each.

判断依据为以下声学特征：
The classification is based on the following acoustic features:

| 特征 / Feature | 说明（中文）| Description (English) |
|---|---|---|
| meanfreq | 频率平均值 (kHz) | Mean frequency (kHz) |
| sd | 频率标准差 | Standard deviation of frequency |
| median | 频率中位数 (kHz) | Median frequency (kHz) |
| Q25 | 频率第一四分位数 (kHz) | First quantile of frequency (kHz) |
| Q75 | 频率第三四分位数 (kHz) | Third quantile of frequency (kHz) |
| IQR | 频率四分位数间距 (kHz) | Interquartile range of frequency (kHz) |
| skew | 频谱偏度 | Spectral skewness |
| kurt | 频谱峰度 | Spectral kurtosis |
| sp.ent | 频谱熵 | Spectral entropy |
| sfm | 频谱平坦度 | Spectral flatness measure |
| mode | 频率众数 | Mode frequency |
| centroid | 频谱质心 | Spectral centroid |
| meanfun | 平均基音频率 | Mean fundamental frequency |
| minfun | 最小基音频率 | Minimum fundamental frequency |
| maxfun | 最大基音频率 | Maximum fundamental frequency |
| meandom | 平均主频 | Mean dominant frequency |
| mindom | 最小主频 | Minimum dominant frequency |
| maxdom | 最大主频 | Maximum dominant frequency |
| dfrange | 主频范围 | Range of dominant frequency |
| modindx | 调制指数（累积相邻两帧绝对基频频差除以频率范围）| Modulation index (cumulative absolute difference between adjacent frames' fundamental frequencies divided by frequency range) |

---

## 数据集
## Dataset

> 详见 / See: https://www.kaggle.com/datasets/primaryobjects/voicegender

在笔者写作时，使用 Colab 拟合的数据与原文章相比有所差异。以下为笔者提供的决策树权重与原文章决策树权重的对比：
At the time of writing, the model fitted with Colab differs somewhat from the original article. Below is a comparison between the author's decision tree weights and those from the original article:

**笔者提供的决策树权重 / Author's Decision Tree Weights:**

![Author's decision tree weights](https://github.com/user-attachments/assets/a720b658-d727-4dd6-803a-7295218ca829)

**原文章决策树权重 / Original Article's Decision Tree Weights:**

![Original article's decision tree weights](https://github.com/user-attachments/assets/af22e28d-f945-422d-9e8c-c4077f1583e5)

---

## 使用方法
## Usage

在安装 Python 3 及以上版本的情况下，执行以下命令：
With Python 3 or above installed, run the following commands:

```shell
python -m venv venv
source venv/bin/activate.xxx  # xxx 为对应的系统与终端 / xxx depends on your OS and shell
pip install -r requirements.txt
```

安装完成后，准备好待测试的 MP3 文件，然后运行：
After installation, prepare the MP3 file you want to analyze, then run:

```shell
python main.py xxx.mp3
```

即可得到如下结果：
You will get an output like this:

![Sample output](https://github.com/user-attachments/assets/e19c1d2a-8b50-4c5c-9e32-fd7cc621e434)
