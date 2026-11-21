> **Mock - OPPE**
# Problem 4
Write a Java program that takes as input 4 Shop objects and the list of Shop objects
with attributes shop name, and number of items sold nsold. The program should add
each customer name as key and number of items as value to the map object. After
adding all objects to the map, display the shop name which has sold maximum number
of items as shown in the test cases. Complete the program as specified below:

Class Shop that has the following members:
- String name, int nsold as private instance variable
- Constructor to initialize the name and nsold
- Accessor methods to all instance variables
. Class MapTest has the following members:
- You should define method public static void printShopName(ArrayList<Shop>
sList) that does the following:
* Iterates over array sList such that in each iteration, add each customer
name as key and number of items as value to the map object.
* Print the shop name which has sold maximum number of items.
- main method has the following functionality
* Creates a list of 4 Shop objects.
* Invokes method printShopName(list) to print the shop name which has
sold maximum number of items.

> **Solution**

```
import java.util .*;

class Shop {
    private String name;
    private int nsold;

    public Shop(String s, int ns) {
        this.name = s;
        this.nsold = ns;
    }

    public String getName() {
        return name;
    }

    public int getItemSold() {
        return nsold;
    }
}

public class MapTest {
    public static void printShopName(ArrayList<Shop> sList) {

        Map<String, Integer> m = new LinkedHashMap<String, Integer>();
        String shop = "";
        int sold = 0;

        // iterate through sList and add each
        // shop object to map "m"
        for (int i = 0; i < sList.size(); i++) {
            String name = sList.get(i).getName();
            int items = sList.get(i).getItemSold();

            if (m.containsKey(name)) {
                m.put(name, m.get(name) + items);
            }
            else {
                m.put(name, items);
            }
        }

        // Find shop with maximum items sold
        for (Map.Entry<String, Integer> entry : m.entrySet()) {
            if (entry.getValue() > sold) {
                sold = entry.getValue();
                shop = entry.getKey();
            }
        }

        System.out.println(shop + " : " + sold);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<Shop> list = new ArrayList<Shop>();

        for (int i = 0; i < 4; i++) {
            list.add(new Shop(sc.next(), sc.nextInt()));
        }

        printShopName(list);
    }
}
```