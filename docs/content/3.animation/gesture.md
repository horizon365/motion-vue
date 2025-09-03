---
title: Gesture
navigation.icon: 'lucide:hand'
---

动作提供了一套手势控制，允许您创建交互式动画。

## 悬停

`运动` 提供了一个 `悬停` 属性，允许您在鼠标悬停时对元素进行动画处理。

<ComponentPreview name="hover" />

### 悬停事件

`hoverStart`

回调函数，当鼠标悬停在元素上时触发。提供触发 `MouseEvent`。

```vue
  <Motion
    @hover-start="(event)=>console.log('hover start', event)"
  />
```

`hoverEnd`

回调函数，当鼠标离开元素时触发。提供触发 `MouseEvent`。

```vue
  <Motion
    @hover-end="(event)=>console.log('hover end', event)"
  />
```

## 按

The `Press` 手势控制允许您在鼠标按下时对元素进行动画处理。

<ComponentPreview name="press" />

### 按鈕事件

`pressStart`

回调函数，当指针开始按下组件时触发。提供触发的事件。

```vue
  <Motion
    @press-start="(event)=>console.log('press start', event)"
  />
```

`按鈕`

回调函数，当指针停止按下组件且指针仍在组件上时触发。提供触发事件 `PointerEvent`。

```vue
  <Motion
    @press="(event)=>console.log('press', event)"
  />
```

`pressCancel`

回调函数，当指针停止按下组件且指针不再位于组件上时触发。提供触发事件 `PointerEvent`。

```vue
  <Motion
    @press-cancel="(event)=>console.log('press cancel', event)"
  />
```

## 关注

焦点手势检测组件何时获得或失去焦点，遵循与 CSS :focus-visible 选择器相同的规则。

您可以使用`@focus`和`@blur`事件，或者使用`focus`属性来在组件获得焦点时进行动画处理。例如：

```vue
<Motion
  focus="{ scale: 1.2 }"
  href="#"
/>
```

## Pan

手势识别在指针按下组件并移动超过 3 像素时触发。当指针释放时，手势识别结束。与拖动不同，平移仅提供事件处理器，没有动画属性。

您可以使用`@pan-start`、`@pan`、`@pan-end`事件来处理平移手势：

<ComponentPreview name="pan" />


## 拖

拖拽`拖拽`手势控制允许您拖动一个元素。

<ComponentPreview name="drag" />

可以使用`whileDrag`在拖动元素时进行动画处理。

<ComponentPreview name="while-drag" />

### 拖动时有限制

<ComponentPreview name="drag-with-constraints" />

### 拖拽属性

::PropsTable
---
data:
- name: drag
  default: "false"
  type: "boolean | 'x' | 'y'"
  description: 启用此元素的拖动功能。默认设置为 `false`。
- name: dragSnapToOrigin
  default: "false"
  type: "boolean"
  description: 如果 `true`，则在拖动结束时将返回到其原始位置。
- name: dragDirectionLock
  default: "false"
  type: "boolean"
  description: 如果 `true`，则将拖动锁定到最初检测到的方向。默认为 `false`。
- name: dragPropagation
  default: "false"
  type: "boolean"
  description: 允许拖动手势传播到子组件。默认设置为 `false`。
- name: dragConstraints
  default: "false"
  type: "false | Partial<BoundingBox> | HTMLElement"
  description: 拖动限制。默认设置为 `false`。
- name: dragElastic
  default: "0.5"
  type: "boolean | number | Partial<BoundingBox>"
  description: 拖动弹性。默认设置为 `0.5`。
- name: dragMomentum
  default: "true"
  type: "boolean"
  description: 在拖动结束时将平移手势的动量应用到组件上。默认设置为 `true`。
- name: dragTransition
  type: "InertiaOptions"
  description: 拖动过渡。默认设置为 `undefined`。
- name: dragListener
  default: "true"
  type: "boolean"
  description: 默认情况下，如果组件上定义了 `drag`，则将自动附加事件监听器，当用户按下时启动拖动。默认设置为 `true`。
- name: dragControls
  type: "DragControls"
  description: 拖动控制对象
- name: onDragStart
  type: "(event: PointerEvent, info: PanInfo) => void"
  description: 当拖动开始时触发的回调函数。提供触发事件 `PointerEvent` 和 `PanInfo`。
- name: onDrag
  type: "(event: PointerEvent, info: PanInfo) => void"
  description: 当拖动时触发的回调函数。提供触发 `PointerEvent` 和 `PanInfo`。
- name: onDragEnd
  type: "(event: PointerEvent, info: PanInfo) => void"
  description: 拖动结束时触发的回调函数。
- name: dragDirectionLock
  type: "(axis: 'x' | 'y') => void"
  description: 当拖动方向锁定到 x 或 y 轴时触发的回调函数。
- name: onDragTransitionEnd
  type: "() => void"
  description: 当拖动惯性/弹跳过渡结束时触发的回调函数。
- name: onMeasureDragConstraints
  type: "(constraints: BoundingBox) => BoundingBox | void"
  description: 如果 `dragConstraints` 设置为 React 引用，则此回调将使用测量的拖动约束调用。
---
::
