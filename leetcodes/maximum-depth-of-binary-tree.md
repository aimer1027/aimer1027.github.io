Maximum Depth of Binary Tree My Submissions Question

Total Accepted: 102492 Total Submissions: 221648 Difficulty: Easy
Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

Subscribe to see which companies asked this question

source code
````c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
       
       int left , right ;
       
       left  = 0 ;
       right = 0 ;
       
       if(root == NULL)
            return 0 ;
            
       if(root->left != NULL)
          left = maxDepth(root->left) ;
       if(root->right != NULL)
          right = maxDepth(root->right) ;
        
        return 1+ (left >= right? left : right) ;    
    }
};
````