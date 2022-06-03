<table>
    <tr>
        <th colspan=2>Git Command 基础</th>
    </tr>
    <tr>
        <th>Command</th>
        <th>Usage</th>
    </tr>
    <tr>
        <td>git config --global user.name "Tony"</td>
        <td>配置name</td>
    </tr>
    <tr>
        <td>git config --global user.email "tony@gmail.com"</td>
        <td>配置email</td>
    </tr>
    <tr>
        <td>git init</td>
        <td>创建仓库Repository</td>
    </tr>
    <tr>
        <td>git add build.gradle</td>
        <td>添加指定文件或者文件夹</td>
    </tr>
    <tr>
        <td>git add .</td>
        <td>添加所有文件</td>
    </tr>
    <tr>
        <td>git commit -m "First conmmit"</td>
        <td>添加提交描述性信息，并完成提交</td>
    </tr>
</table>

- **.gitignore忽略文件**


- **查看修改内容**

```git
git  status
```

```git
git diff
```

- **撤销未提交的修改**

```git
git checkout
```

```git
git reset
```

- **查看提交记录**

```git
git log
```