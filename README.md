Recover-Binary-Search-Tree
==========================


/**
 * Definition for binary tree
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public void recoverTree(TreeNode root) {
        // Start typing your Java solution below
        // DO NOT write main() function
        ArrayList<TreeNode> list = new ArrayList<TreeNode>();
        recoverTreeHelper(root, list);

        int index1 = -1, index2 = -1;
        
        for(int j = 0; j < list.size()-1;j++){
            
            if(list.get(j).val > list.get(j+1).val){
                index1 = j;
                 break;
            }
            
           
        }
        
          for(int i= list.size()-1; i >=0; i--){
            
            if(list.get(i).val< list.get(i-1).val){
                index2 = i;
                break;
            }
            
            
        }
        
       
        int temp = list.get(index1).val;
        list.get(index1).val = list.get(index2).val;
        list.get(index2).val = temp;
    }
    public void recoverTreeHelper(TreeNode root, ArrayList<TreeNode> list){
        if(root == null) return;
        recoverTreeHelper(root.left, list);
        list.add(root);
        recoverTreeHelper(root.right, list);
    }
}
