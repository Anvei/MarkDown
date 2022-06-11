## 六大基本布局

#### LinearLayout线性布局

<table>
    <tr>
        <td>orientation</td>
    </tr>
    <tr>
        <td>id</td>
    </tr>
    <tr>
        <td>layout_width</td>
    </tr>
    <tr>
        <td>layout_height</td>
    </tr>
    </tr>
        <td>layout_weight</td>
    </tr>
    <tr>
        <td>layout_gravity</td>
    </tr>
    <tr>
        <td>gravity</td>
    </tr>
    </tr>
        <td>background</td>
    </tr>
    </tr>
        <td>divider</td>
        <td>为LinearLayout设置分割线图片</td>
    </tr>
    </tr>
        <td>showDividers</td>
        <td>设置分割线位置,none、begining、end、middle(每两个child之间)</td>
    </tr>
    </tr>
        <td>dividerPadding</td>
        <td>设置分割线的padding</td>
    </tr>
</table>

#### RelativaLayout相对布局

<table>
    <tr>
        <th rowspan=2>基本属性</th>
        <td>gravity</td>
        <td>设置容器内组件的对齐方式</td>
    </tr>
    <tr>
        <td>ignoreGravity</td>
        <td>设置为true的组件，将不受gravity属性影响</td>
    </tr>
    <tr>
        <th rowspan=4>根据父容器定位</th>
        <td>layout_alignParentLeft</td>
        <td>左对齐,left、right、top、bottom</td>
    </tr>
    <tr>
        <td>layout_centerVertical</td>
        <td>水平居中</td>
    </tr>
    <tr>
        <td>layout_centerHorizontal</td>
        <td>垂直居中</td>
    </tr>
    <tr>
        <td>centerInParent</td>
        <td>居中</td>
    </tr>
    <tr>
        <th rowspan=3>根据兄弟容器定位</th>
        <td>layout_toLeftOf</td>
        <td>参考组件的左边,left、right</td>
    </tr>
    <tr>
        <td>layout_above</td>
        <td>参考组件的上方,above、below</td>
    </tr>
    <tr>
        <td>layout_alignTop</td>
        <td>对齐参考组件的上边界,top、bottom、left、right</td>
    </tr>
    <tr>
        <th rowspan=3>Magin偏移</th>
        <td>layout_margin</td>
        <td>设置上下左右的偏移量</td>
    </tr>
    <tr>
        <td>layout_marginLeft</td>
        <td>设置组件左边的偏移量,left、right、top、bottom、start、end</td>
    </tr>
    <tr>
        <td>layout_marginVertical</td>
        <td>设置组件上下的偏移量,vertical、horizontal</td>
    </tr>
    <tr>
        <th rowspan=3>Padding填充</th>
        <td>padding</td>
        <td>设置上下左右内边距</td>
    </tr>
    <tr>   
        <td>paddingLeft</td>
        <td>设置左侧内边距,left、right、bottom、top</td>
    </tr>
    <tr>
        <td>paddingVertical</td>
        <td>设置上下内边距,vertical、horizontal</td>
    </tr>
</table>

#### FrameLayout帧布局

<table>
    <tr>
        <td>foreground</td>
        <td>设置改帧布局容器的前景图像</td>
    </tr>
    <tr>
        <td>foregroundGravity</td>
        <td>设置前景图像显示的位置</td>
    </tr>
</table>

#### GridLayout网格布局

<table>
    <tr>
        <td>orientation</td>
        <td>设置排列方式</td>
    </tr>
    <tr>
        <td>layout_gravity</td>
        <td>设置对齐方式</td>
    </tr>
    <tr>
        <td>rowCount</td>
        <td>设置行数</td>
    </tr>
    <tr>
        <td>columnCount</td>
        <td>设置列数</td>
    </tr>
    <tr>
        <td>layout_row</td>
        <td>第几行</td>
    </tr>
    <tr>
        <td>layout_column</td>
        <td>第几列</td>
    </tr>
    <tr>
        <td>layout_rowSpan</td>
        <td>横跨多少行</td>
    </tr>
    <tr>
        <td>layout_columnSpan</td>
        <td>横跨多少列</td>
    </tr>
</table>

#### TableLayout表格布局

<table>
    <tr>
        <td>collapseColumns</td>
        <td>设置需要被隐藏的列的序号</td>
    </tr>
    <tr>
        <td>shrinkColumns</td>
        <td>设置允许被收缩的列的列序号</td>
    </tr>
    <tr>
        <td>stretchColumns</td>
        <td>设置运行被拉伸的列的列序号</td>
    </tr>
</table>

#### AbsoluteLayout绝对布局

<table>
    <tr>
        <td>android:layout_width</td>
        <td>组件宽度,单位都是dp</td>
    </tr>
    <tr>
        <td>android:layout_height</td>
        <td>组件高度</td>
    </tr>
    <tr>
        <td>android:layout_x</td>
        <td>设置组件x坐标,单位都是dp</td>
    </tr>
    <tr>
        <td>android:layout_y</td>
        <td>设置组件y坐标</td>
    </tr>
</table>