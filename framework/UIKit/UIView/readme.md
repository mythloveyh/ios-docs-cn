# UIView

### 简介

视图基类

<br>
***
<br>


### API

**`- initWithFrame:`**

说明：初始化方法

<br>


**`backgroundColor`**

说明：背景色，默认值为nil，即透明背景。

<br>


**`hidden`**

说明：布尔值，表示视图是否隐藏，默认值为NO。

<br>


**`alpha`**

说明：视图的alpha值

<br>


**`opaque`**

说明：布尔值，表示视图是否是不透明的，默认值为YES。

<br>


**`tintColor`**

说明：它定义了一个非默认的着色颜色值，它会影响到以该视图为根视图的整个视图层级。

注意：

* 默认情况下，一个视图的`tintColor`为nil，这意味着视图将使用父视图的`tintColor`值。

* 当我们指定了一个视图的`tintColor`后，这个色值会自动传播到以当前视图为根视图的视图层级中的所有子视图上。

* 如果系统在视图层级中没有找到一个非默认的`tintColor`值，则会使用系统定义的颜色值。

<br>


**`tintAdjustmentMode`**

说明：枚举值，它定义了tint color的调整模式。

注意：当你查询该属性值时，如果系统无法在子视图层级中找到一个非缺省值，返回`UIViewTintAdjustmentModeNormal`。

<br>


**`clipsToBounds`**

说明：布尔值，表示是否将子视图限制在视图的边界内。

<br>


**`clearsContextBeforeDrawing`**

说明：布尔值，表示在视图重画之前是否先清理视图以前的内容，默认值为YES。

注意：如果视图的`opaque`属性值设置为YES，则`backgroundColor`的属性值就不能为nil，否则可能发生错误。

<br>


**`maskView`**

说明：一个可选的视图，它的alpha通道用来遮盖一个视图的内容。

注意：从iOS 8.0开始可用

<br>


**`+ layerClass`**

说明：返回用于创建核心动画层实例的类

<br>


**`layer`**

说明：只读，返回视图的核心动画层。

注意：

* 该属性的值永远不会是nil

* 当前layer的代理对象就是当前视图，所以不要将当前视图设置为另一个CALayer对象的代理，也不要改变当前layer的代理对象。

<br>


**`userInteractionEnabled`**

说明：布尔值，表示是否忽略用户事件并从事件队列移除，默认值为YES（表示不忽略）。

注意：在动画期间，无论该属性的值是什么，所有视图的用户交互都会被暂时禁用。你可以在配置动画时，通过设置`UIViewAnimationOptionAllowUserInteraction`选项来禁止该行为。

<br>


**`multipleTouchEnabled`**

说明：布尔值，表示是否视图是否支持多点触摸事件，默认值为NO。

注意：如果你只想让当前视图多点触摸事件，可以在将设置该属性为YES的同时，将`exclusiveTouch`设置为YES。

<br>


**`exclusiveTouch`**

说明：布尔值，表示是否只允许当前视图处理触摸事件，默认值为NO。

注意：将该属性值设置为YES后，当前视图会阻止触摸事件转发到同一窗口中的其他视图。

<br>


**`frame`**

说明：它用来描述当前视图在其父视图坐标系统中的位置和尺寸

注意：

* 如果你想在`frame`属性改变时自调用视图的`drawRect:`方法，就将`contentMode`的属性值设置为`UIViewContentModeRedraw`。

<br>


**`bounds`**

说明：它用来描述当前视图在自己坐标系统中的位置和尺寸，默认的原点是`(0,0)`，尺寸则和`frame`的尺寸一致。

<br>


**`center`**

说明：当前视图`frame`的中心点

注意：

* 中心点是在父视图的坐标系统中指定的

* 设置该属性会改变相应地`frame`属性的值

<br>


**`transform`**

说明：指定应用于当前视图的变换，变换的原点即为当前视图的`center`属性值，或当前视图layer的`anchorPoint`属性（如果该属性值发生了改变），默认值为`CGAffineTransformIdentity`。

<br>


**`superview`**

说明：只读，返回当前视图的父视图，如果没有父视图，则返回nil。

<br>


**`subviews`**

说明：只读，返回当前视图的直接子视图。

<br>


**`window`**

说明：只读，返回当前视图所在的窗口对象，如果没有，则返回nil。

<br>


**`- addSubview:`**

说明：添加一个视图到当前视图子视图列表的末尾

注意：视图只能有一个父视图，如果被添加的视图已经有了父视图且该视图不是接受者，那么该方法会在当前视图成为被添加视图新的父视图前，移除被添加视图原有的父视图。

<br>


**`- bringSubviewToFront:`**

说明：移动指定的子视图，让它出现在其兄弟视图的最顶部。

注意：该方法实际上是将目标子视图移动到`subviews`列表的末尾

<br>


**`- sendSubviewToBack:`**

说明：移动指定的子视图，让它出现在其兄弟视图的最后面。

注意：该方法实际上是将目标子视图移动到`subviews`列表的队首

<br>


**`- removeFromSuperview`**

说明：从当前视图的父视图及当前视图所在的窗口中分离视图，并将其从响应者链中删除。

注意：不要在当前视图的`drawRect:`方法调用该方法

<br>


**`- insertSubview:atIndex:`**

说明：在`subviews`列表的指定位置插入一个子视图

<br>


**`- insertSubview:aboveSubview:`**

说明：在视图层级里另一个视图的上面插入指定视图

<br>


**`- insertSubview:belowSubview:`**

说明：在视图层级里另一个视图的下面插入指定视图

<br>


**`- exchangeSubviewAtIndex:withSubviewAtIndex:`**

说明：将`subviews`列表中指定索引处的两个子视图互换位置

注意：该方法不会改变子视图的父视图，只是互换一下它们在`subviews`数组中的位置。

<br>


**`- isDescendantOfView:`**

说明：返回一个子视图，表示当前视图是否为给定视图的子视图，或是否与给定视图为同一个视图。

<br>


**`autoresizingMask`**

说明：它用于决定当父视图的边界改变时，视图如何重新调整自己的大小，默认值为`UIViewAutoresizingNone`（即视图始终不会调整大小）。

<br>


**`autoresizesSubviews`**

说明：布尔值，表示当前视图的边界发生改变时，是否自动调整其子视图，默认值为YES。

<br>


**`contentMode`**

说明：它用于决定当视图的边界发生改变时，如何对视图的内容进行布局，默认值为`UIViewContentModeScaleToFill`。

<br>


**`- sizeThatFits:`**

说明：要求视图计算并返回最适合其子视图的尺寸

注意：

* 该方法的默认实现返回视图的现有大小

* 该方法不会调整当前视图的大小

<br>


**`- sizeToFit`**

说明：调整并移动视图，使它能包围它的子视图。

注意：

* 当你想要调整当前视图的尺寸时，调用该方法，以便于它使用最合适的尺寸。

* 你不能覆盖该方法，如果你想改变你的视图的默认尺寸信息，覆盖`sizeThatFits:`方法。

<br>


**`- layoutSubviews`**

说明：布局子视图

注意：

* 不要直接调用该方法

* 该方法只会进行位置，视图大小的数字计算，并不会引起屏幕的绘制。(注：来自web的结论，没有亲自验证)

<br>


**`- setNeedsLayout`**

说明：废止视图的当前布局并在下一个布局更新期间触发一个新的布局

注意：

* 当你想调整一个视图的子视图布局时，在应用的主线程中调用那个视图的该方法。

* 这个方法不会强制立即更新，而是等待下一个更新周期，你可以使用它来废止之前多个视图的布局更新。这种行为可以让你将所有的布局更新放到一个更新周期内，这通常会带来更好的性能。

<br>


**`- layoutIfNeeded`**

说明：立即布局子视图

<br>


**`+ requiresConstraintBasedLayout`**

说明：返回布尔值，表示当前视图是否依赖基于约束的布局系统。

<br>


**`translatesAutoresizingMaskIntoConstraints`**

说明：返回布尔值，表示是否需要将视图从Autoresizing（即`autoresizingMask`属性值表示的自动调整模式）转换到基于约束的自动布局。

注意：

* 通过程序创建的视图，该属性的默认值为YES；通过Interface Builder创建的视图，系统自动将该属性设置为NO。

<br>


**`bottomAnchor`**

说明：只读，它是一个表示视图框架底部边缘的布局锚点，可用它创建视图底部边缘的约束。

注意：

* 从iOS 9.0开始可用

<br>


**`centerXAnchor`**

说明：只读，它是一个表示视图框架水平中心的布局锚点，可以用它创建视图水平中心的约束。

注意：

* 从iOS 9.0开始可用

<br>


**`centerYAnchor`**

说明：只读，它是一个表示视图框架垂直中心的布局锚点，可以用它创建视图垂直中心的约束。

注意：

* 从iOS 9.0开始可用

<br>


**`firstBaselineAnchor`**

说明：只读，它是一个表示视图中顶行文本基线的布局锚点，可用它创建基线约束。

注意：

* 从iOS 9.0开始可用

<br>


**`heightAnchor`**

说明：只读，它是一个用于表示视图高度的布局锚点，可用它创建视图的高度约束。

注意：

* 从iOS 9.0开始可用

<br>


**`lastBaselineAnchor`**

说明：只读，它是一个表示视图中底部文本基线的布局锚点，可用它创建基线约束。

注意：

* 从iOS 9.0开始可用

<br>


**`leadingAnchor`**

说明：只读，它是一个表示视图框架行距的布局锚点，可用它创建视图的行距约束。

注意：

* 从iOS 9.0开始可用

<br>


**`leftAnchor`**

说明：只读，它是一个表示视图框架左边距的布局锚点，可用它创建视图的左边距约束。

注意：

* 从iOS 9.0开始可用

<br>


**`rightAnchor`**

说明：只读，它是一个表示视图框架右边距的布局锚点，可用它创建视图的右边距约束。

注意：

* 从iOS 9.0开始可用

<br>


**`topAnchor`**

说明：只读，它是一个表示视图框架顶边距的布局锚点，可用它创建视图的顶边距约束。

注意：

* 从iOS 9.0开始可用

<br>


**`trailingAnchor`**

说明：只读，它是一个表示视图框架尾随距离的布局锚点，可用它创建视图的尾随距离约束。

注意：

* 从iOS 9.0开始可用

<br>


**`widthAnchor`**

说明：只读，它是一个表示视图宽度的布局锚点，可用它创建视图的宽度约束。

注意：

* 从iOS 9.0开始可用

<br>


**`constraints`**

说明：只读，返回视图持有的布局约束。

<br>


**`- addConstraint:`**

说明：给当前视图或其子视图添加一个布局约束

注意：对于iOS 8.0+，可以通过将约束对象的`active`属性设置为YES来替代该方法，设置为YES后，会自动将约束添加到正确的视图上。

<br>


**`- addConstraints:`**

说明：给当前视图或其子视图添加多个布局约束

注意：对于iOS 8.0+，可用使用`NSLayoutConstraint`的`activateConstraints:`方法来替代该方法，它会自动将约束添加到正确的视图上。

<br>


**`- removeConstraint:`**

说明：从当前视图中移除指定的布局约束

注意：对于iOS 8.0+，可以通过将约束对象的`active`属性设置为NO来替代该方法，设置为NO后，它会将约束从正确的视图上移除。

<br>


**`- removeConstraints:`**

说明：从当前视图或其子视图移除多个布局约束

注意：对于iOS 8.0+，可用使用`NSLayoutConstraint`的`deactivateConstraints:`方法来替代该方法，它会自动将约束从正确的视图上移除。

<br>


**`- addLayoutGuide:`**

说明：给视图添加一个指定的UILayoutGuide对象

注意：

* 该方法会将指定的layoutGuide添加到视图的`layoutGuides`数组的末尾

* 当前视图也被赋值给layoutGuide对象的`owningView`属性

* 从iOS 9.0开始可用

<br>


**`layoutGuides`**

说明：只读，表示当前视图拥有的UILayoutGuide对象

注意：从iOS 9.0开始可用

<br>


**`layoutMarginsGuide`**

说明：只读，它是一个UILayoutGuide对象，表示视图外边距，可以使用这个UILayoutGuide对象的锚点来创建视图的外边距约束。

注意：从iOS 9.0开始可用

<br>


**`readableContentGuide`**

说明：只读，它是一个UILayoutGuide对象，用于表示视图内的一个可读宽度区域。

注意：

* 从iOS 9.0开始可用

<br>


**`- removeLayoutGuide:`**

说明：从视图中删除指定的layoutGuide

注意：

* 该方法会将指定的layoutGuide从视图的`layoutGuides`数组中移除

* 被移除layoutGuide对象的`owningView`属性，其值同时被设置为nil。

* 从iOS 9.0开始可用

<br>


**`- systemLayoutSizeFittingSize:`**

说明：返回满足视图持有之约束的尺寸

<br>


**`- systemLayoutSizeFittingSize:withHorizontalFittingPriority:verticalFittingPriority:`**

说明：返回满足视图持有之约束的尺寸

注意：

* 从iOS 8.0开始可用

<br>


**`- intrinsicContentSize`**

说明：返回视图的自然大小（只考虑视图本身的属性），默认值为`UIViewNoIntrinsicMetric`。

<br>


**`- invalidateIntrinsicContentSize`**

说明：废止视图的内在内容大小

<br>


**`- contentCompressionResistancePriorityForAxis:`**

说明：返回在指定轴线上缩小视图的优先级

注意：

* 子类不应该覆盖该方法，而应该在创建自定义视图时设置默认值，通常是`NSLayoutPriorityDefaultLow`或`NSLayoutPriorityDefaultHigh`。

<br>


**`- setContentCompressionResistancePriority:forAxis:`**

说明：设置在指定轴线上缩小视图的优先级

注意：

* 子类不应该覆盖该方法

<br>


**`- contentHuggingPriorityForAxis:`**

说明：返回在指定轴线上放大视图的优先级

<br>


**`- setContentHuggingPriority:forAxis:`**

说明：设置在指定轴线上放大视图的优先级

<br>


**`- alignmentRectForFrame:`**

说明：返回给定框架的视图对齐矩形

注意：

* 基于约束的布局系统使用对齐矩形来排列视图

* 该方法的默认实现返回被视图的`alignmentRectInsets`属性修改后的视图框架

<br>


**`- frameForAlignmentRect:`**

说明：返回给定对齐矩形的视图框架

注意：`- alignmentRectForFrame:`与`- frameForAlignmentRect:`总是互逆的

<br>


**`- alignmentRectInsets`**

说明：返回当前视图框架的内边距信息，默认值为`UIEdgeInsetsZero`。

<br>


**`viewForBaselineLayout`**

说明：返回一个符合基线约束的视图，默认实现返回当前视图。

注意：

* 如果你覆盖了该方法，则返回的必须是当前视图的子视图。

* 从iOS 9.0开始，该方法已被废弃。

<br>


**`viewForFirstBaselineLayout`**

说明：只读，返回一个符合首行基线约束的视图，默认实现返回当前视图。

注意：

* 如果你覆盖了该方法，则返回的必须是当前视图的子视图。

* 该方法从iOS 9.0开始可用

<br>


**`viewForLastBaselineLayout`**

说明：只读，返回一个符合尾行基线约束的视图，默认实现返回当前视图。

注意：

* 如果你覆盖了该方法，则返回的必须是当前视图的子视图。

* 该方法从iOS 9.0开始可用

<br>


**`- needsUpdateConstraints`**

说明：返回一个布尔值，表示视图的约束是否需要更新，YES表示需要。

<br>


**`- setNeedsUpdateConstraints`**

说明：控制视图的约束是否需要更新

注意：

* 当你的自定义视图的某个属性发生变更时，可以调用这个来表明视图的约束需要在将来的某个时候更新，之后系统将会调用`updateConstraints`方法。

<br>


**`- updateConstraints`**

说明：更新视图的约束

注意：

* 在约束更新阶段，你不能废止任何约束，也不能唤起布局或绘制。

* 如果你覆盖了该方法，则需要在实现的最后调用父类的实现。

<br>


**`- updateConstraintsIfNeeded`**

说明：更新当前视图及其子视图的约束

注意：

* 当视图触发一个新的布局过程后，系统就会自动调用该方法。

* 子类不应该覆盖该方法

<br>


**`semanticContentAttribute`**

说明：它是一个视图内容的语义化描述，用于决定当切换左右布局时是否应该翻转视图。

注意：从iOS 9.0开始可用

<br>


**`+ userInterfaceLayoutDirectionForSemanticContentAttribute:`**

说明：返回给定语义内容属性的用户界面布局方向（left-to-right or right-to-left）

注意：

* 当创建一个包含子视图的视图时，可以使用该方法来决定子视图是否应该翻转且以适当地顺序布局视图。

* 从iOS 9.0开始可用

<br>


**`layoutMargins`**

说明：布局视图内容时所使用的默认间隔，默认值是(8,8,8,8)。

注意：

* 使用该属性来指定视图和任何子视图边缘之间的间隔，自动布局使用你指定的边距来放置内容。

* 当你的视图的边缘接近其父视图的边缘且`preservesSuperviewLayoutMargins`属性值被设置为YES时，实际的布局边距会增加以阻止内容与父视图边距重叠。

* 如果视图是视图控制器的根视图，则由系统来设置和管理`layoutMargins`：顶部和底部被设置为0，两边的边距取决于当前的size class（可能是16或20点），你也无法修改它们。

* 从iOS 8.0开始可用

<br>


**`preservesSuperviewLayoutMargins`**

说明：布尔值，表明当前视图是否遵守其父视图的边距，默认值为NO。

注意：

* 从iOS 8.0开始可用

<br>


**`- layoutMarginsDidChange`**

说明：通知视图`layoutMargins`发生了变化

注意：

* 该方法的默认实现什么也不做

* 从iOS 8.0开始可用

<br>


**`- drawRect:`**

说明：在传入的矩形范围内绘制视图的图像

注意：

* 该方法的默认实现什么也不做

* 只有使用Core Graphics 和 UIKit来绘制视图内容的子类才需要覆盖该方法

* 当你的视图使用其他方式设置内容时（如显示背景色、直接使用视图的层设置内容），不用覆盖该方法。

* 如果视图被设置成了不透明，你的`drawRect:`方法就必须用不透明的内容填满指定的矩形。

* 如果你直接子类化`UIView`，那么在实现该方法时就不需要调用父类的实现；如果你子类化其他的视图类，则应该在你的实现中调用父类的该方法。

* 不要直接调用该方法，而是通过调用`setNeedsDisplay`或`setNeedsDisplayInRect:`方法来替代。

* 在视图首次显示或视图的可见部分失效时，会自动调用该方法。

<br>


**`- setNeedsDisplay`**

说明：标记视图的边界矩形需要被重绘

注意：

* 调用该方法后，视图并不会立即重绘，而是等到下一个绘制周期，此时所有失效的视图都会被更新。
* 即使多次调用该方法，系统也不会多次执行drawRect方法，而只会执行一次。

<br>


**`- setNeedsDisplayInRect:`**

说明：标记视图的指定矩形区域需要被重绘（即局部重绘）

注意：调用该方法后，会将指定的矩形添加到视图的失效矩形列表中并立即返回，等到下一个绘制周期再重绘，此时所有失效的视图都会被更新。

<br>


**`contentScaleFactor`**

说明：应用到视图的比例因子，比例因子决定了视图内容如何从逻辑坐标空间（单位是点）映射到设备坐标空间（单位是像素），其值通常是1.0或2.0，默认值是屏幕显示的当前视图的比例因子。

<br>


**`- tintColorDidChange`**

说明：当`tintColor`属性发生改变时，系统会调用该方法。

<br>


**`- addGestureRecognizer:`**

说明：给视图附加一个手势识别器

注意：视图会建立一个手势识别器的强引用

<br>


**`- removeGestureRecognizer:`**

说明：从视图分离一个指定的手势识别器

<br>


**`gestureRecognizers`**

说明：返回附加给视图的手势识别器列表，如果视图没有附加手势识别器，则返回一个空数组。

<br>


**`- gestureRecognizerShouldBegin:`**

说明：询问视图是否允许手势识别器继续跟踪触摸事件，默认值为YES。

<br>


**`+ animateWithDuration:delay:options:animations:completion:`**

说明：使用指定的持续时间、延迟、动画选项及完成回调，来动画改变一个或多个视图。

注意：

* 动画期间，视图的用户交互会被暂时禁止，如果你想改变这种行为，在options参数值中包含`UIViewAnimationOptionAllowUserInteraction`即可。

<br>


**`+ animateWithDuration:animations:completion:`**

说明：使用指定的持续时间和完成回调，来动画改变一个或多个视图。

注意：

* 该方法使用`UIViewAnimationOptionCurveEaseInOut`和`UIViewAnimationOptionTransitionNone`动画选项，立即执行指定的动画。

* 动画期间，视图的用户交互会被暂时禁止，如果你想改变这种行为，在options参数值中包含`UIViewAnimationOptionAllowUserInteraction`即可。

例子：

```
// 渐隐并移除视图
[UIView animateWithDuration:0.2 animations:^{
									view.alpha = 0.0;
								} 
								completion:^(BOOL finished){ 
									[view removeFromSuperview]; 
								}];
``` 

<br>


**`+ animateWithDuration:animations:`**

说明：使用指定的持续时间来动画改变一个或多个视图

注意：

* 该方法使用`UIViewAnimationOptionCurveEaseInOut`和`UIViewAnimationOptionTransitionNone`动画选项，立即执行指定的动画。

* 动画期间，视图的用户交互会被暂时禁止，如果你想改变这种行为，在options参数值中包含`UIViewAnimationOptionAllowUserInteraction`即可。

<br>


**`+ transitionWithView:duration:options:animations:completion:`**

说明：为指定的视图容器创建一个过渡动画

注意：

* 如果你想加入其他可以做成动画的变化，你必须在options参数值中包含`UIViewAnimationOptionAllowAnimatedContent`。

* 动画期间，视图的用户交互会被暂时禁止，如果你想改变这种行为，在options参数值中包含`UIViewAnimationOptionAllowUserInteraction`即可。

例子：

```
// 为containerView创建一个翻转动画
[UIView transitionWithView:containerView
           duration:0.2
           options:UIViewAnimationOptionTransitionFlipFromLeft
           animations:^{ 
           		[fromView removeFromSuperview]; 
           		[containerView addSubview:toView]; 
           }
           completion:nil];
```

<br>


**`+ transitionFromView:toView:duration:options:completion:`**

说明：使用指定的参数在指定的视图之间创建过渡动画

注意：

* 该方法只有修改视图层次里的视图

* 它不会以任何方式修改应用的视图控制器

* 动画会立即开始，除非另一个动画正在执行中，在这种情况下，它会在另一个动画执行完毕后立即开始。

* 动画期间，视图的用户交互会被暂时禁止，如果你想改变这种行为，在options参数值中包含`UIViewAnimationOptionAllowUserInteraction`即可。

<br>


**`+ animateKeyframesWithDuration:delay:options:animations:completion:`**

作用：为当前视图设置一个基于关键帧的动画

注意：

* 你必须在animations回调中一次或多次地调用`addKeyframeWithRelativeStartTime:relativeDuration:animations:`方法来添加关键帧动画的时间和数据

* 如果没有添加关键帧动画，那么通过该方法创建的动画就会像标准动画一样执行，即在指定的持续时间内，视图从当前值变成一个新值。

<br>


**`+ addKeyframeWithRelativeStartTime:relativeDuration:animations:`**

作用：给一个关键帧动画指定一帧的时间和动画值

<br>


**`+ performSystemAnimation:onViews:options:animations:completion:`**

作用：在一个或多个视图上执行执行的系统动画及可选的并行动画（animations参数定义的动画）

<br>


**`+ animateWithDuration:delay:usingSpringWithDamping:initialSpringVelocity:options:animations:completion:`**

作用：使用一个对应于物理弹簧运动的时间曲线来执行视图动画

<br>


**`+ performWithoutAnimation:`**

作用：禁止一个视图过渡动画

<br>


**`- addMotionEffect:`**

说明：开始应用一个动画效果到视图上

<br>


**`motionEffects`**

说明：视图的动画效果集合

<br>


**`- removeMotionEffect:`**

说明：停止应用一个动画效果到视图

<br>


**`restorationIdentifier`**

说明：一个标识符，用于决定视图是否支持状态恢复，默认值为nil。

注意：

* 仅在实现了`encodeRestorableStateWithCoder:`和`decodeRestorableStateWithCoder:`方法时，才可以给该属性赋值。

* 只设置该属性值，不足以确保该视图被保留并恢复，其所属的视图控制器及该视图控制器的所有父控制器，都必须有一个恢复的标识符。

<br>


**`- encodeRestorableStateWithCoder:`**

说明：编码视图的状态相关信息

<br>


**`- decodeRestorableStateWithCoder:`**

说明：解码视图的状态相关信息

<br>


**`- snapshotViewAfterScreenUpdates:`**

说明：返回一个基于当前视图内容的快照视图

<br>


**`- resizableSnapshotViewFromRect:afterScreenUpdates:withCapInsets:`**

说明：返回一个基于当前视图指定内容的，带有可伸缩内边距的快照视图。

<br>


**`- drawViewHierarchyInRect:afterScreenUpdates:`**

说明：在当前上下文中，将一个快照的完整视图层次结构呈现到可见屏幕上。如果快照是完整的，就返回YES；如果快照丢失了任何视图层级结构中的图像数据，则返回NO。

注意：

* 当你想应用一个图形效果（如模糊）到快照视图时，就使用该方法。

* 该方法没有`snapshotViewAfterScreenUpdates:`方法块

<br>


**`tag`**

说明：一个整数，你可以用它来标识应用中的视图对象，默认值为0。

<br>


**`- viewWithTag:`**

说明：返回tag值与指定tag值匹配的视图

注意：该方法会搜索指定视图及其所有子视图

<br>


**`- convertPoint:toView:`**

说明：将来自当前视图坐标系统中的一个点转换为指定视图坐标系统中的点

<br>


**`- convertPoint:fromView:`**

说明：将来自指定视图坐标系统中的一个点转换为当前视图坐标系统中的点

<br>


**`- convertRect:toView`**

说明：将来自当前视图坐标系统中的矩形转换为指定视图坐标系统中的矩形

<br>


**`- convertRect:fromView:`**

说明：将来自指定视图坐标系统中的矩形转换为当前视图坐标系统中的矩形

<br>


**`- hitTest:withEvent:`**

说明：从当前视图层级结构中找到一个包含指定点，且处于层级结构最前面的子视图。

注意：

* 该方法会遍历当前视图层级结构，调用每个子视图的`pointInside:withEvent:`方法，如果该方法返回YES，则在子视图的层级结构中采取类似的遍历，直到最前面的视图包含指定的点。

* 你很少需要调用该方法，但你可能需要通过覆盖该方法来隐藏来自子视图的触摸事件。

* 该方法会忽略这些视图：隐藏的视图；禁止用户交互的视图；alpha值小于0.01的视图。

* 在确定命中时，该方法不会考虑视图的内容，因此，即使指定的点是在该视图内容中的透明部分，仍会返回命中的视图。

* 当指定的点在当前视图的边界之外时，即使某个子视图包含该点，也不会视为命中。这种情况通常发生在当前视图的`clipsToBounds`属性值设置为NO，且被命中的子视图超出父视图的边界时。

<br>


**`- pointInside:withEvent:`**

说明：返回一个布尔值，表示当前视图是否包含指定的点，YES表示包含。

<br>


**`- endEditing:`**

说明：返回一个布尔值，表示是否已让视图（或嵌入到视图中的一个文本域）放弃了第一响应者的状态（类似于失去焦点）。

注意：

* 该方法会在当前视图及其子视图中查找处于第一响应者状态的文本域，如果找到了一个文本域，则会要求它放弃第一响应者状态；如果`force`参数被设置为了YES，则会强制被找到的文本域放弃第一响应者状态。

<br>


**`- didAddSubview:`**

说明：告诉视图，子视图已添加。

注意：

* 该方法的默认实现什么也不做

<br>


**`- willRemoveSubview:`**

说明：告诉视图，子视图将要被移除。

注意：

* 该方法的默认实现什么也不做

* 该方法在两种情况下被调用：子视图的父视图发生改变时；子视图从视图层级结构中完全删除时。

<br>


**`- willMoveToSuperview:`**

说明：告诉视图，它的父视图将要变更为指定的父视图。

注意：

* 该方法的默认实现什么也不做

<br>


**`- didMoveToSuperview`**

说明：告诉父视图，它的父视图已经变更。

注意：

* 该方法的默认实现什么也不做

<br>


**`- willMoveToWindow:`**

说明：告诉视图，它的窗口对象将要发生变更。

注意：

* 该方法的默认实现什么也不做

<br>


**`- didMoveToWindow`**

说明：告诉视图，它的窗口对象已经变更。

注意：

* 该方法的默认实现什么也不做


<br>
***
<br>


### 注意

* 如果多次调用`setNeedsDisplay`方法，系统只会执行一次`drawRect`方法。
* 视图被添加到父视图后，并不会马上显示在屏幕上，而是会在执行完`viewWillAppear`方法后、`viewDidAppear`方法前执行绘制.
* 下列属性支持动画：
	* frame
	* bounds
	* center
	* transform
	* alpha
	* backgroundColor
	* contentStretch


<br>
***
<br>


### 参考资源

* [UIView中的updateConstraints、layoutSubviews及drawRect](http://www.jianshu.com/p/438bcf8e3e53)
* [详解UIView的tintColor属性](http://www.cocoachina.com/ios/20150703/12363.html?utm_medium=referral&utm_source=pulsenews)
* [细数AutoLayout以来UIView和UIViewController新增的相关API](http://www.cocoachina.com/ios/20141026/10045.html)
