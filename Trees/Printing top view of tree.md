## Problem

Given a pointer to the root of a binary tree, print the top view of the binary tree.

The tree as seen from the top the nodes, is called the top view of the tree.

For example :

       1
        \
         2
          \
           5
          /  \
         3    6
          \
           4
Top View : 1->2->5->6

## Solution

Using levelOrder traversal with modifications.

    public static void topView(Node root) {
        Map<Integer, Integer> treeNodes = new TreeMap<>();
        levelOrder(root, treeNodes);

        for(Map.Entry<Integer,Integer> entry : treeNodes.entrySet()) {
            System.out.print(entry.getValue() + " ");
        }
    }

    public static void levelOrder(Node root, Map<Integer, Integer> treeNodes) {

        LinkedList<List<Object>> queue = new LinkedList<>();
        queue.add(Arrays.asList(root, 0)); // Simple queue won't do, 0 is root's horizontal index, left -> rootHIndex - 1, right -> rootHIndex + 1

        while(queue.size() != 0) {
            List<Object> n = queue.poll();

            if (!treeNodes.containsKey((Integer)n.get(1)))
                treeNodes.put((Integer)n.get(1), ((Node)n.get(0)).data);

            if (((Node)n.get(0)).left != null) queue.add(Arrays.asList(((Node)n.get(0)).left, (Integer)n.get(1) - 1));
            if (((Node)n.get(0)).right != null) queue.add(Arrays.asList(((Node)n.get(0)).right, (Integer)n.get(1) + 1));
        }
    }
