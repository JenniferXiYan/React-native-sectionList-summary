# React-native-sectionList-summary
#### React native 之 SectionList 组件
#### 1. 问题1. 数据渲染格式
+ issue：TypeError: Cannot read property 'length' of undefined
         This error is located at:in VirtualizedSectionList (at SectionList.js:332)
+ reason：数据结构和sectionList组件内置所需的数据结构不一致
+ resolove： 更改数据结构例如 `let array = [{data:['apple','banana','box']}]`

#### 2. 问题2. key值得唯一性
+ issue：Invariant Violation: A VirtualizedList contains a cell which itself contains
         more than one VirtualizedList of the same orientation as the parent list. 
         You must pass a unique list Key prop to each sibling list
+ reason：意思是在父元素和子元素都用sectionList组件循环列表时，父列表包含了相同的列表, 需要向每个兄弟列表传递唯一的key值
+ resolve：组要加一个属性(listKey)去证明sectionList的唯一性例如，
```script
<SectionList
      listKey={'MDRT'}
      style={{ flex: 1, flexDirection: 'row' }}
      sections={dataArray}
      keyExtractor={(item, index) => index.toString()}
      renderItem={this.renderItem}
 />
