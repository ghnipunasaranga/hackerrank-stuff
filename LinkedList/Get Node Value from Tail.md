## Problem

Given a pointer to the head of a linked list and a specific position, determine the data value at that position. Count backwards from the tail node. 

### Lagging pointer method can be used in this case

    static int getNode(SinglyLinkedListNode head, int positionFromTail) {

        SinglyLinkedListNode current = head;
        SinglyLinkedListNode laggingPointer = head;
        int laggingPointerIndex = 0;

        while (current != null) {

            if (laggingPointerIndex++ > positionFromTail) {
                laggingPointer = laggingPointer.next;
            }
            current = current.next;
        }

        return laggingPointer.data;
    }
    
There is a small trick. Check the `if (laggingPointerIndex++ > positionFromTail)` condition. It is not equal or greater than. Check the while loop condition. When the whole while loop is done, `current` value vill be null. If we use equals as well, and if positionFromTail equals zero, `laggingPointer` will also become null. We do not want that. We want the value, so let's advance `laggingPointer` a one iteration later.
