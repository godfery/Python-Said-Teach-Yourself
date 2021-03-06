# 一棵树的前序遍历
 下面我们有Node类来表示树结构，然后优雅的实现深度遍历

 注意需要Python版本高于3.3
## 代码
    class Node:
        def __init__(self, value):
            self._value = value
            self._children = []
        
        # 控制print显示
        def __repr__(self):
            return 'Node({!r})'.format(self._value)

        # 增加子节点
        def add_child(self, node):
            self._children.append(node)

        # 实现迭代方法
        def __iter__(self):
            return iter(self._children)

        def depth_first(self):
            yield self
            for c in self:
                yield from c.depth_first()
    # Example
    if __name__ == '__main__':
        root = Node(0)
        child1 = Node(1)
        child2 = Node(2）
        root.add_child(child1)
        root.add_child(child2)
        child1.add_child(Node(3))
        child1.add_child(Node(4))
        child2.add_child(Node(5))

        for ch in root.depth_first():
            print(ch)
        # Outputs Node(0), Node(1), Node(3), Node(4), Node(2), Node(5)

depth_first方法先返回本身，然后对self中的_children进行迭代。
##以上示例代码来源于Python Cookbook(第三版)