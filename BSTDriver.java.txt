import DataStructures.BinarySearchTree;
import java.util.Scanner;

public class BSTDriver
{
    public static void main( String[] args )
    {
        BinarySearchTree bst = new BinarySearchTree( );
        Scanner scanner = new Scanner( System.in );
        int choice = 0;

        System.out.println( "=== Binary Search Tree Driver ===" );

        while( choice != 8 )
        {
            System.out.println( "\nChoose an operation:" );
            System.out.println( "1. Insert an item" );
            System.out.println( "2. Remove an item" );
            System.out.println( "3. Find an item" );
            System.out.println( "4. Find Min" );
            System.out.println( "5. Find Max" );
            System.out.println( "6. Find Kth Smallest" );
            System.out.println( "7. Print Tree (using '*' for levels)" );
            System.out.println( "8. Quit" );
            System.out.print( "Enter your choice: " );

            if( scanner.hasNextInt() )
            {
                choice = scanner.nextInt();
            }
            else
            {
                System.out.println( "Invalid input. Please enter a number." );
                scanner.next();
                continue;
            }

            switch( choice )
            {
                case 1:
                    System.out.print( "Enter integer to insert: " );
                    int insVal = scanner.nextInt();
                    bst.insert( insVal );
                    System.out.println( insVal + " inserted." );
                    break;

                case 2:
                    System.out.print( "Enter integer to remove: " );
                    int remVal = scanner.nextInt();
                    bst.remove( remVal );
                    System.out.println( remVal + " removed (if present)." );
                    break;

                case 3:
                    System.out.print( "Enter integer to find: " );
                    int findVal = scanner.nextInt();
                    Comparable found = bst.find( findVal );
                    if( found != null )
                        System.out.println( "Found: " + found );
                    else
                        System.out.println( findVal + " not found in tree." );
                    break;

                case 4:
                    Comparable min = bst.findMin();
                    if( min != null )
                        System.out.println( "Minimum item: " + min );
                    else
                        System.out.println( "Tree is empty." );
                    break;

                case 5:
                    Comparable max = bst.findMax();
                    if( max != null )
                        System.out.println( "Maximum item: " + max );
                    else
                        System.out.println( "Tree is empty." );
                    break;

                case 6:
                    System.out.print( "Enter k (for kth smallest): " );
                    int k = scanner.nextInt();
                    Comparable kth = bst.findKth( k );
                    if( kth != null )
                        System.out.println( "The " + k + "-th smallest item is: " + kth );
                    else
                        System.out.println( "Invalid rank k or empty tree." );
                    break;

                case 7:
                    System.out.println( "\nCurrent Tree Structure:" );
                    bst.printTree();
                    break;

                case 8:
                    System.out.println( "Exiting program. Goodbye!" );
                    break;

                default:
                    System.out.println( "Invalid choice. Please select between 1 and 8." );
            }
        }
        scanner.close();
    }
}
