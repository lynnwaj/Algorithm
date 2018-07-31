# Algorithm
//Algorithm
//Binary tree:
/**
There are three different types of depth-first traversals, 

- PreOrder traversal - visit the parent first and then left and right children;

                                        先父母，再左孩子，再右孩子

- InOrder traversal - visit the left child, then the parent and the right child;

                                       先左孩子，再父母，再右孩子

- PostOrder traversal - visit left child, then the right child and then the parent;

                                       先左孩子，再右孩子，再父母
 **/
    /**
     * 递归先序遍历
     * */
    public void preOrderRecursion(TreeNode node){
        if(node==null) //如果结点为空则返回
            return;
        visit(node);//访问根节点
        preOrderRecursion(node.left);//访问左孩子
        preOrderRecursion(node.right);//访问右孩子
    }
        /**
     * 非递归先序遍历二叉树,利用栈来
     * */
   class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> result=new ArrayList<Integer>();
        Stack<TreeNode> stack=new Stack<TreeNode>();
        while(root!=null||!stack.empty()){
            if(root!=null){
                result.add(root.val);
                stack.push(root);
                root=root.left;
            }   
            else{
                root=stack.pop();
                root=root.right;
            }
        }
    return result;
    }
}
    参考链接另外的方法：
    https://blog.csdn.net/linhuanmars/article/details/21428647
    
    /**
     * 递归中序遍历 recursive
     * */
    public void inOrderRecursion(TreeNode node){
        if(node==null) //如果结点为空则返回
            return;
        inOrderRecursion(node.left);//访问左孩子
        visit(node);//访问根节点
        inOrderRecursion(node.right);//访问右孩子
    }
     /**
     * 非递归中序遍历 iterative
     * */
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> result=new ArrayList<Integer>();
        Stack<TreeNode> stack=new Stack<TreeNode>();
        while(root!=null||!stack.empty()){
            if(root!=null){
                stack.push(root); //记录parent node
                root=root.left;
            }
            else{
                root=stack.pop(); //回到parent node
                result.add(root.val);//把parent node值记录到最后结果中
                root=root.right; 
            }
        }
        return result;
    }
}
参考链接另外的方法：
https://blog.csdn.net/linhuanmars/article/details/20187257

  /**
     * 递归后序遍历
     * */
    public void postOrderRecursion(TreeNode node){
        if(node==null) //如果结点为空则返回
            return;
        postOrderRecursion(node.left);//访问左孩子
        postOrderRecursion(node.right);//访问右孩子
        visit(node);//访问根节点
    }
/**
     * 非递归后序遍历
     * */
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        LinkedList<Integer> result=new LinkedList<Integer>();
        Stack<TreeNode> stack=new Stack<TreeNode>();
        while(root!=null||!stack.empty()){
            if(root!=null){
                stack.push(root);
                result.addFirst(root.val); //倒序记录值
                root=root.right; 
            }
            else{
                root=stack.pop();
                root=root.left;
            }
        }
    return result;
    }
}

参考链接另外的方法：
https://blog.csdn.net/linhuanmars/article/details/20187257
