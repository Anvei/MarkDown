## ConstraintLayout约束布局

#### 基本方向约束

横向约束有start、end、left、right, 纵向约束有top、bottom、baseline

1. **app:layout_constraintBottom_toBottomOf**: 底部与指定组件的底部对齐

2. **app:layout_contraintStart_toEndOf**: 起始方向与指定组件的终止方向对齐

3. **app:layout_constraintBaseline_toBaselineOf**: 基线与指定组件的基线对齐

#### 角度约束

1. **app:layout_constraintCircle**: 目标控件id

2. **app:layout_constraintCircleAngle**: 对于目标的角度(0-360)

3. **app:layout_constraintCircleRadius**: 到目标中心的距离
 
#### 百分比偏移

1. **app:layout_constraintHorizontal_bias**: 水平方向的偏移量(0到1之间)

2. **app:layout_constraintVertical_bias**: 垂直方向的偏移量

#### 内边距、外边距、GONE Margin

1. **内边距Padding**

- **android:padding**

- top、bottom、start、end、left、right、vertical、horizontal

2. **外边距Margin**

- **android:layout_margin**

- top、bottom、start、end、left、right、vertical、horizontal

3. **GONE Margin**

当所依赖的view隐藏,该属性就会生效

- **app:layout_goneMarginTop**

- top、bottom、left、right、start、end

#### 控件尺寸

1. **限制尺寸**
 
<table>
    <tr>
        <td>android:maxWidth</td>
        <td>android:minWidth</td>
    </tr>
    <tr>
        <td>android:maxHeight</td>
        <td>android:minHeight</td>
    </tr>
</table>

2. **0dp(MATCH_CONSTRAINT)**

<table>
    <tr>
        <th colspan=2>app:layout_constraintWidth_default</th>
    </tr>
    <tr>
        <th>取值</th>
        <th>说明</th>
    </tr>
    <tr>
        <td>spread</td>
        <td>占用符合约束的所有约束空间</td>
    <tr>
    <tr>
        <td>percent</td>
        <td>按照父布局的百分比设置</td>
    <tr>
        <td>wrap</td>
        <td>匹配内容大小但是不超过约束限制</td>
    </tr>
</table>

- app:layout_constraintWidth_percent="0.5"

- 对wrap_content强制约束

<table>
    <tr>
        <td>app:layout_constraintWidth="true | false"</td>
    </tr>
    <tr>
        <td>app:layout_constraintHeight="true | false"</td>
    </tr>
</table>