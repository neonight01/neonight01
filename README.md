def is_symmetric(tree):
    """
    >>> is_symmetric((1, (2, None, None), (2, None, None)))
    True

    >>> is_symmetric((1, (2, (3, None, None), (4, None, None)), (2, (4, None, None), (3, None, None))))
    True

    >>> is_symmetric((1, (2, (3, None, None), (4, None, None)), (2, (3, None, None), (4, None, None))))
    False

    >>> is_symmetric((1,))
    True
    
    >>> is_symmetric((1, (2, (3, None, None), (4, None, None)), (2, (4, None, None), (3, None, None))))
    True

    >>> is_symmetric((1, (2, (3, None, None), (4, None, None)), (2, (3, None, None), (4, None, None))))
    False
    """
    def is_mirror(t1, t2):  # 定义一个递归函数 is_mirror，用于检查两个子树是否对称
        if t1 is None and t2 is None:  # 如果两个子树都为空，则它们是对称的
            return True
        if t1 is None or t2 is None:  # 如果其中一个子树为空，另一个不为空，则它们不对称
            return False
        if t1[0] != t2[0]:  # 如果两个子树的根节点值不相等，则它们不对称
            return False
        return is_mirror(t1[1], t2[2]) and is_mirror(t1[2], t2[1])  # 递归检查左子树和右子树是否对称

    if tree is None:  # 如果树为空，则它是对称的
        return True
    if len(tree) < 2:  # 如果树的长度小于2，则它是对称的（单节点树或空树）
        return True
    return is_mirror(tree[1], tree[2])  # 检查树的左子树和右子树是否对称

if __name__ == "__main__":
    import doctest
    doctest.testmod()
print("软工1班", 2315304321, "周潇潇")
