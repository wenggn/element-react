## Dialog 对话框
在保留当前页面状态的情况下，告知用户并承载相关操作。

### 基本用法

Dialog 弹出一个对话框，适合需要定制性更大的场景。

:::demo 需要设置`v-model`属性，它接收`Boolean`，当为`true`时显示 Dialog。Dialog 分为两个部分：`body`和`footer`，`footer`需要具名为`footer`的`slot`。`title`属性用于定义标题，它是可选的，默认值为空。本例通过显式改变`v-model`的值来打开 Dialog，此外我们还为 Dialog 实例提供了`open`和`close`方法，可以通过调用它们来打开/关闭 Dialog。

```html
<Button type="text" onClick={ () => this.setState({ dialogVisible1: true }) }>点击打开 Dialog</Button>
<Dialog
  title="提示"
  size="tiny"
  visible={ this.state.dialogVisible1 }
  onCancel={ () => this.setState({ dialogVisible1: false }) }
  lockScroll={ false }
>
  <Dialog.Body>
    <span>这是一段信息</span>
  </Dialog.Body>
  <Dialog.Footer className="dialog-footer">
    <Button onClick={ () => this.setState({ dialogVisible1: false }) }>取 消</Button>
    <Button type="primary" onClick={ () => this.setState({ dialogVisible1: false }) }>确 定</Button>
  </Dialog.Footer>
</Dialog>
```
:::

### 自定义内容

Dialog 组件的内容可以是任意的，甚至可以是表格或表单，下面是应用了 Element Table 和 Form 组件的两个样例。

:::demo
```html
<Button type="text" onClick={ () => this.setState({ dialogVisible2: true }) } type="text">打开嵌套表格的 Dialog</Button>
<Dialog title="收货地址"
        visible={ this.state.dialogVisible2 }
        onCancel={ () => this.setState({ dialogVisible2: false }) }
>
  <Dialog.Body>
    TODO: 待 Table 实现
    <el-table data="gridData">
      <el-table-column property="date" label="日期" width="150"></el-table-column>
      <el-table-column property="name" label="姓名" width="200"></el-table-column>
      <el-table-column property="address" label="地址"></el-table-column>
    </el-table>
  </Dialog.Body>
</Dialog>

<Button type="text" onClick={ () => this.setState({ dialogVisible3: true }) } type="text">打开嵌套表单的 Dialog</Button>
<Dialog title="收货地址"
        visible={ this.state.dialogVisible3 }
        onCancel={ () => this.setState({ dialogVisible3: false }) }
>
  <Dialog.Body>
    TODO: 待 Form 实现
    <el-form model="form">
      <el-form-item label="活动名称" label-width="formLabelWidth">
        <el-input v-model="form.name" auto-complete="off"></el-input>
      </el-form-item>
      <el-form-item label="活动区域" label-width="formLabelWidth">
        <el-select v-model="form.region" placeholder="请选择活动区域">
          <el-option label="区域一" value="shanghai"></el-option>
          <el-option label="区域二" value="beijing"></el-option>
        </el-select>
      </el-form-item>
    </el-form>
  </Dialog.Body>

  <Dialog.Footer className="dialog-footer">
    <Button onClick={ () => this.handleDialogClose(3) }>取 消</Button>
    <Button type="primary" onClick={ () => this.handleDialogClose(3) }>确 定</Button>
  </Dialog.Footer>
</Dialog>
```
:::

### Attributes
| 参数      | 说明          | 类型      | 可选值                           | 默认值  |
|---------- |-------------- |---------- |--------------------------------  |-------- |
| title     | Dialog 的标题 | string    | —                               | —      |
| size      | Dialog 的大小 | string    | tiny/small/large/full | small |
| top       | Dialog CSS 中的 top 值（仅在 size 不为 full 时有效） | string    | —                       | 15%     |
| modal     | 是否需要遮罩层   | boolean   | — | true |
| lock-scroll | 是否在 Dialog 出现时将 body 滚动锁定 | boolean | — | true |
| custom-class      | Dialog 的自定义类名 | string    | — | — |
| close-on-click-modal | 是否可以通过点击 modal 关闭 Dialog | boolean    | — | true |
| close-on-press-escape | 是否可以通过按下 ESC 关闭 Dialog | boolean    | — | true |

### Slot
| name | 说明 |
|------|--------|
| — | Dialog 的内容 |
| footer | Dialog 按钮操作区的内容 |

### 方法
每个 `el-dialog` 实例都暴露了如下方法，用于在不显式改变 `v-model` 值的情况下打开 / 关闭实例：
| 方法名 | 说明 |
|------|--------|
| open | 打开当前实例 |
| close | 关闭当前实例 |

### Events
| 事件名称      | 说明    | 回调参数      |
|---------- |-------- |---------- |
| close  | Dialog 关闭的回调 | — |
| open  | Dialog 打开的回调 | — |