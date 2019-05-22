#include <iostream>
#include <vector>
#include <queue>
#include <stack>
using namespace std;

int main() {
    int n,i,u,v;
    
    // Tree Representation using vector
    cin >> n;
    vector<int>tree[n+1];
    for(i=1;i<=n-1;i++)
    {
        cin >> u >> v;
        tree[u].push_back(v);
    }
    
    // BFS in a TREE
    queue<int> qu;
    qu.push(1);
    while(!qu.empty())
    {
        int temp = qu.front();
        qu.pop();
        for(i=0;i<tree[temp].size();i++)
        {
            qu.push(tree[temp][i]);
            cout << tree[temp][i] << " ";
        }
    }
    cout << "\n";
    
    // DFS in a tree
    stack<int> st;
    st.push(1);
    int vis[n+1];
    while(!st.empty())
    {
        int temp = st.top();
        if(tree[temp].size() == 0)
        {
            st.pop();
            cout << temp << " ";
        }
        for(i=0;i<tree[temp].size();i++)
        {   
            if(vis[temp] != 1)
                st.push(tree[temp][i]);
            else
            {
                cout << temp << " ";
                st.pop();
                break;
            }
        }
        vis[temp] = 1;
    }
    
}
