LESS 是一种 CSS 预编译语言，将 CSS 进行简化和拓展，提升编码效率，降低维护成本。由于书写简便，功能够用，安装方便，中间件支持较多，现为许多团队的内置的 CSS 预编译语言。但由于 LESS 的灵活性，容易导致项目维护的隐形成本上升，因此，需要一些编码方式的约束，用以规范 LESS 文件的书写。

本指南将组件拆分，并填写了详细注释，这些文件分布在 `./less` 文件夹下，是以 `.less` 后缀结尾的文件。(WIP)

#### 采用 Space

采用 Space 而非 Tab 进行缩进。

#### 缩进控制

所有文件，均采用 2 空格缩进。

#### 选择器的继承不超过 3 层

LESS 文件可以很方便的进行继承选择器的书写，例如：

```less
.father {
  .brother {
    color: red;
    a {
      span {
        font-size: 12px;
      }
    }
  }
  .me {
    background-color: #000;
    &:hover {
      background-color: #fff;
    } 
  }
  &:hover {
    background-color: #efefef;
  }
}
```

但我们并不建议继承选择器采用这种方式进行深度嵌套，所以请确保你的 LESS 文件没有超过 3 层的选择器嵌套，例如将上述代码的迁移部分，修改成为：

```less
.father {
  .brother {
    color: red;
    a span {
      font-size: 12px;
    }
  }
}
```

#### 区分属性与继承选择器

使用空行区分属性与继承选择器，而非粘连的写在一起：

```less
.father {
  .brother {
    color: red;

    a span {
      font-size: 12px;
    }
  }
}
```

#### 属性在前，伪类其次，继承选择器最后

为了更好的区分当前选择器的属性，与当前选择器伪类的属性，和子孙选择器所匹配的样式有所不同，请按照上述顺序，来进行样式的书写，比如：

```less
.father {
  font-size: 14px;
  
  &:hover {
    background-color: #efefef;
  }
  &:active {
    background-color: red;
  }
  &.abc {
    background-color: green;
  }

  .brother {
    color: red;
    a span {
      font-size: 12px;
    }
  }
}
```

### MIT license
Copyright (c) 2014 Guo Yu &lt;o.u.turing@gmail.com&gt;

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the &quot;Software&quot;), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED &quot;AS IS&quot;, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
