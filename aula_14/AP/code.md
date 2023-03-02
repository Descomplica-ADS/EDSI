**R e s p o s t a - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -**

*JAVA:*
```java
import javax.swing.JOptionPane;

public class BinaryTree {
    private Node root;

    private class Node {
        double element;
        Node left, right;

        public Node(double element) {
            this.element = element;
            this.left = null;
            this.right = null;
        }
    }
    public BinaryTree() {
        this.root = null;
    }

    public void showRoot() {
        if (root != null) System.out.println("A raiz é: " + root.element);
        else System.out.println("A árvore está vazia");
    }

    public double search(double element) {
        Node found = searchRec(element);
        if (found == null) {
            System.out.println("Elemento não encontrado na árvore");
            return Double.NaN;
        }
        return found.element;
    }
    private Node searchRec(double element) {
        Node current = root;
        while (current != null && current.element != element) {
            if (element < current.element) {
                current = current.left;
            } else {
                current = current.right;
            }
        }
        return current;
    }

    public void insert(double element) {
        root = insertRec(root, element);
    }
    private Node insertRec(Node root, double element) {
        if (root == null) {
            root = new Node(element);
            return root;
        }

        if (element < root.element) {
            root.left = insertRec(root.left, element);
        } else if (element > root.element) {
            root.right = insertRec(root.right, element);
        }

        return root;
    }

    public void remove(double element) {
        root = removeRec(root, element);
    }
    private Node removeRec(Node root, double element) {
        if (root == null) return root;

        if (element < root.element) {
            root.left = removeRec(root.left, element);
        } else if (element > root.element) {
            root.right = removeRec(root.right, element);
        } else {
            if (root.left == null) {
                return root.right;
            } else if (root.right == null) {
                return root.left;
            }

            root.element = minValue(root.right);
            root.right = removeRec(root.right, root.element);
        }

        return root;
    }
    private double minValue(Node root) {
        double minv = root.element;
        while (root.left != null) {
            minv = root.left.element;
            root = root.left;
        }
        return minv;
    }

    public void inorderTraversal() {
        inorderTraversalRec(root);
    }
    private void inorderTraversalRec(Node root) {
        if (root != null) {
            inorderTraversalRec(root.left);
            System.out.print(root.element + " ");
            inorderTraversalRec(root.right);
        }
    }

    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();
        int nInputs = 5;

        for (int i = 1; i <= nInputs; i++) {
            String input = JOptionPane.showInputDialog("Digite o " + i + "°/" + nInputs +" número decimal:");
            double value = Double.parseDouble(input);
            tree.insert(value);
        }

        System.out.print("Árvore binária de busca em ordem: ");
        tree.inorderTraversal();

        System.exit(0);
    }
}
```