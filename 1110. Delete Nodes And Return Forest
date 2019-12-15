//https://leetcode.com/problems/delete-nodes-and-return-forest/
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
struct ParentNodePair {
    TreeNode* parent;
    TreeNode* node;
};

class Solution {
private:
    void bfs(TreeNode* curr, stack<ParentNodePair>& marked, const unordered_set<int>& toDelete) {
        if (curr == nullptr)
            return;
        
        TreeNode* parent = nullptr;
        queue<ParentNodePair> q;
        q.push({parent, curr});
        
        while (!q.empty()) {
            auto front = q.front(); q.pop();
            
            if (front.node == nullptr)
                continue;
            
            if (toDelete.find(front.node->val) != toDelete.end())
                marked.push(front);
            
            q.push({front.node, front.node->left});
            q.push({front.node, front.node->right});
        }
    }
public:
    vector<TreeNode*> delNodes(TreeNode* root, const vector<int>& to_delete) {
        unordered_set<int> toDelete;
        for (const auto& elem : to_delete) {
            toDelete.insert(elem);
        }
        
        stack<ParentNodePair> marked;
        bfs(root, marked, toDelete);
        
        vector<TreeNode*> result;
        bool deletedRoot = false;
        while(!marked.empty()) {
            auto top = marked.top(); marked.pop();
            
            if (top.node == root) {
                deletedRoot = true;
            }
            
            if (top.parent != nullptr) {
                if (top.parent->left == top.node) {
                    top.parent->left = nullptr;
                } else {
                    top.parent->right = nullptr;
                }
            }
            
            if (top.node->left != nullptr)
                result.push_back(top.node->left);
            if (top.node->right != nullptr)
                result.push_back(top.node->right);
        }
        
        if (!deletedRoot) {
            result.push_back(root);
        }
        
        return result;
    }
};
