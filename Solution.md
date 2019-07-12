Trying to solve the problem in-place may not work. The trick is to have a global variable to track the maximum path

Like:

global max_path = 0

def recursive_travel(node):
    # Do somthing
    update max_path
    # Do something else
    # Return resul
  

TOP-DOWN DFS vs BOTTOM-UP DFS

The second important is using post-order , not pre-order. For example in following tree:

      1    --> L0
     /
    1      --> L1
   /
  1        --> L2


How do we know there are 3 Node(1) ? With preorder , we need to pass a "count" variable to track, like:
  
def pre_order_count(node, 1)
--> def pre_order_count(node.left, 2)
    --> def pre_order_count(node.left.left, 3)
        --> No where to go, then return 3
Complicated, isn't it ?

Instead, with do it with bottom-up manner, the (1, L2) in L2 will return 1, then (1, L1) in L1 recognize its child node has the same value, then take the value return by (1, L2) which is 1 and add 1 (mean itself) and return 2. Similarly to (1, L0) then finally we have 3

Code

def post_order_count(node)
    child_count = post_order_count(child_node)
    if child_node.val == node.val then return child_count + 1
