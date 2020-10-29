## Two ways are available for revering.

### Iterative

    static SinglyLinkedListNode reverse(SinglyLinkedListNode head) {

         SinglyLinkedListNode prev = null;
         SinglyLinkedListNode current = head;

         while (current != null) {

             SinglyLinkedListNode next = current.next; // Have to make this local variable so that we do not lose next node
             current.next = prev;
             prev = current;
             current = next;
         }

         return prev;
    }
  
### Recursive

    static SinglyLinkedListNode reverse(SinglyLinkedListNode head) {

        if (head.next == null) {
            return head;
        }

        SinglyLinkedListNode reversedHead = reverse(head.next); // Note code after recursive call, bottom-up processing manner

        head.next.next = head;
        head.next = null;
        return reversedHead;
    }
