&emsp;&emsp;本文收集React Native UI、性能等常见问题的最佳实践，文中内容来源于公司内部业务RN改造实践经验，部分来源于业界最佳实践总结，主要目的是防止每个业务方踩同样的坑。

### 首屏渲染
&emsp;&emsp;*** 定义Loading动画，缓解bundle初始化白屏带来的不友好体验 ***

&emsp;&emsp;虚线框内为生命周期第一阶段，这个阶段完成初始化，并第一次渲染组件。左下角虚线框为组件运行和交互阶段，这里可能会再次渲染组件。右下角虚线框为第三阶段，组件这一阶段卸载消亡。对应生命周期方法，我们在初始阶段首先渲染loading视图，并开始拉取数据。获取数据后，通过改变状态（state），触发视图的再次渲染，在屏幕绘制出视图。
  <br><br>
  ![](http://www.alloyteam.com/wp-content/uploads/2016/03/01.png)


### ListView
- Lazy Load
- 下拉刷新
