import java.util.*;

class ListNode {
    int value;
    ListNode next;
    ListNode(int value) {
        this.value = value;
        this.next = null;
    }
}

public class Main {

    public static ListNode createLinkedList(int[] values) {
        if (values.length == 0) return null;
        ListNode head = new ListNode(values[0]);
        ListNode current = head;
        for (int i = 1; i < values.length; i++) {
            current.next = new ListNode(values[i]);
            current = current.next;
        }
        return head;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Read sizes of the three linked lists
        int n = scanner.nextInt();
        int m = scanner.nextInt();
        int k = scanner.nextInt();

        // Read elements of the first linked list
        int[] aValues = new int[n];
        for (int i = 0; i < n; i++) {
            aValues[i] = scanner.nextInt();
        }

        // Read elements of the second linked list
        int[] bValues = new int[m];
        for (int i = 0; i < m; i++) {
            bValues[i] = scanner.nextInt();
        }

        // Read elements of the third linked list
        int[] cValues = new int[k];
        for (int i = 0; i < k; i++) {
            cValues[i] = scanner.nextInt();
        }

        // Read the target sum
        int target = scanner.nextInt();

        // Create linked lists from the input arrays
        ListNode a = createLinkedList(aValues);
        ListNode b = createLinkedList(bValues);
        ListNode c = createLinkedList(cValues);

        // Brute force search for the target sum
        outerLoop:
        for (ListNode nodeA = a; nodeA != null; nodeA = nodeA.next) {
            for (ListNode nodeB = b; nodeB != null; nodeB = nodeB.next) {
                for (ListNode nodeC = c; nodeC != null; nodeC = nodeC.next) {
                    if (nodeA.value + nodeB.value + nodeC.value == target) {
                        System.out.println(nodeA.value + " " + nodeB.value + " " + nodeC.value);
                        break outerLoop;
                    }
                }
            }
        }
    }
}
