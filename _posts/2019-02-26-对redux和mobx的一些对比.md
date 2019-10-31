---
layout:     post
title:      对redux和mobx的一些对比
date:       2019-02-26
author:     cuizhu
header-img: img/post-bg-keybord.jpg
catalog: true
tags:
    -h5兼容性问题
---

# 正文
  mobx和redux两个库都有使用过，在店家的时候前期用的mobx，后来由于项目的业务迭代越来越多。越来越复杂，页面中存在很多父组件的store里的属性被子组件，甚至孙子组件等深层嵌套的组件更改，大大的提高了bug率，降低了维护性，往往一个属性不知道在哪个组件里就被更改了。并且Mobx的属性可以在直接修改和负责，不好追踪。所以后面都迁移到了redux。并制定了开发规范。

  Mobx 和 Redux 的目标都是管理好应用状态，但是最根本的区别在于对数据的处理方式不同。

  Redux 认为，数据的一致性很重要，为了保持数据的一致性，要求Store 中的数据尽量范式化，也就是减少一切不必要的冗余，为了限制对数据的修改，要求 Store 中数据是不可改的（Immutable），只能通过 action 触发 reducer 来更新 Store。

  Mobx 也认为数据的一致性很重要，但是它认为解决问题的根本方法不是让数据范式化，而是不要给机会让数据变得不一致。所以，Mobx 鼓励数据干脆就“反范式化”，有冗余没问题，只要所有数据之间保持联动，改了一处，对应依赖这处的数据自动更新，那就不会发生数据不一致的问题。

  值得一提的是，虽然 Mobx 最初的一个卖点就是直接修改数据，但是实践中大家还是发现这样无组织无纪律不好，所以后来 Mobx 还是提供了 action 的概念。和 Redux 的 action 有点不同，Mobx 中的 action 其实就是一个函数，不需要做 dispatch，调用就修改对应数据。


  总结一下 Redux 和 Mobx 的区别，包括这些方面：

    1、Redux 鼓励一个应用只用一个 Store，Mobx 鼓励使用多个 Store；

    2、Redux 使用“拉”的方式使用数据，这一点和 React是一致的，但 Mobx 使用“推”的方式使用数据，和 RxJS 这样的工具走得更近；

    3、Redux 鼓励数据范式化，减少冗余，Mobx 容许数据冗余，但同样能保持数据一致。


  然后，被问起最多的问题就来了：我应该选用 Mobx 还是 Redux 呢？

  问：你的应用是小而且简单，还是大而且复杂？

  如果是前者，选择 Mobx；如果是后者，选择 Redux。

  问：你想要快速开发应用，还是想要长期维护这个应用？

  如果是前者，选择 Mobx；如果是后者，选择 Redux。

  我们真的必须使用 Mobx 和 Redux 吗

  当然不是！

  首先我们要明白，Redux 和 Mobx 都是一个特定时期的产物，在 React 没有提供更好的状态管理方法之前，Redux 能够帮助使用 React 的开发者一把，Mobx 也能提供一种全新的状态管理理念。

  不过，React 是在持续发展的，光是 Context API 的改进，几乎就可以取代 react-redux 和 mobx-react 的作用。实际上，react-redux 和 mobx-react 两者的实现都依赖于 React 的 Context 功能。

  以 Redux 为例，它相较于 React Context 还有哪些特点呢？

  Redux 有更清晰的数据流转过程，配合 Redux Devtools 的确方便 Debug，代价就是我们必须要写啰嗦的 action 和 reducer。如果我们觉得应用并不需要 Redux 这样的增强功能，那完全就可以直接使用 React 的 Context。