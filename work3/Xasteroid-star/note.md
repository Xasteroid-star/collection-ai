#task1
```
df = pd.read_csv(fp, dtype=str, encoding='utf-8', low_memory=False,header=0)
```
dtype=str - 数据类型指定，防止某些列被错误解析为数值类型,例如身份证号等
low_memory=False - 内存优化设置，默认为 True，会分块读取以节省内存，
设为 False 会一次性读取整个文件到内存，适用于内存充足的情况
header


```dotnetcli
# 在数据框或系列的 sum() 函数中
df.sum(axis=1, skipna=True)  # 默认参数
df[download_cols].sum(skipna=False)  # 可以显式设置
```
skipna 参数在 pandas 的 sum() 函数中，它控制是否跳过 NaN（空值）进行计算。

```
daily_counts = df.groupby('_发布时间_raw_').size().rename('发布数量')
```
df.groupby('_发布时间_raw_').size()
分组：按 _发布时间_raw_ 列（日期）分组

统计：使用 .size() 计算每组有多少行


对于reset_index() 后：
将 Series 转换为 DataFrame
Series → 单列数据（只有值）

DataFrame → 多列数据（索引变成列+值）


```dotnetcli
plt.subplots(2, 1, figsize=(12, 10))
```

(2, 1) - 子图布局
第一个数字 2：行数（垂直方向）

第二个数字 1：列数（水平方向）
figsize=(12, 10) - 图形尺寸
12：图形的宽度（英寸）

10：图形的高度（英寸）

```dotnetcli
plt.annotate(f'发布高峰: {max_month}月', xy=(max_month-1, max_val), 
             xytext=(max_month, max_val + 5),
             arrowprops=dict(facecolor='red', shrink=0.05),
             fontsize=12, color='red')

```
xy=(max_month-1, max_val)：箭头指向的位置（x坐标减1是因为条形图索引从0开始）

xytext=(max_month, max_val + 5)：文本显示的位置

arrowprops=dict(facecolor='red', shrink=0.05)：设置箭头属性（红色，缩短5%）

显示文本"发布高峰: X月"，红色，字号12


```dotnetcli
# 计算 Pearson 相关系数
correlation = df['标题长度'].corr(df['_下载次数_'])
```
df['标题长度']：DataFrame中的标题长度列

df['_下载次数_']：DataFrame中的下载次数列

.corr()：Pandas的相关系数计算方法，默认就是Pearson相关系数

将计算结果赋值给变量correlation



```
plt.tight_layout(rect=[0, 0.03, 1, 0.95])
```
tight_layout()：自动调整子图间的间距，防止重叠

rect：指定子图区域在图形中的位置和大小

```
data_matrix.argmax()
```
返回扁平化后的索引位置

np.unravel_index(扁平索引, 形状)
将扁平索引转换回多维索引

np.unravel_index(99, (10, 10)) → (9, 9)

