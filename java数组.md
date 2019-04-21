### 无序数组
```java
package mynoorderarray;

/**
 * @ProjectName: MyArray
 * @Package: mynoorderarray
 * @ClassName: NoOrderArray
 * @Author: wss
 * @Description: ${description}
 * @Date: 2019/4/21 12:43
 * @Version: 1.0
 */
public class NoOrderArray {
    public int[] items;       //数组
    public int len;             //数组长度
    public NoOrderArray(){
        items = new int[50];
    }
    public NoOrderArray(int var){
        items = new int[var];
    }
    
    /**
     * @Method 添加元素（数组末尾）
     * @Author wss
     * @Version  1.0
     * @Description 
     * @param item
     * @Return 
     * @Exception 
     * @Date 2019/4/21 12:48
     */
    public void insert(int item){
        items[len] = item;
        len++;
    }

    /**
     * @Method 遍历数组
     * @Author wss
     * @Version  1.0
     * @Description
     * @param
     * @Return
     * @Exception
     * @Date 2019/4/21 12:49
     */
    public void display(){
        System.out.println("[");
        for(int i = 0 ; i < len ; i++){
            System.out.println(items[i]);
        }
        System.out.println("]");
    }

    /**
     * @Method 查找某个元素的位置
     * @Author wss
     * @Version  1.0
     * @Description
     * @param
     * @Return
     * @Exception
     * @Date 2019/4/21 13:15
     */
    public int find(int var){
        int i;
        for(i = 0 ; i < len ; i++){
            if(var == items[i]){
                break;
            }
        }
        return i;
    }

    /**
     * @Method 获取某个位置的元素
     * @Author wss
     * @Version  1.0
     * @Description
     * @param
     * @Return
     * @Exception
     * @Date 2019/4/21 13:20
     */
    public int get(int var){
        if (var > len){
            throw new ArrayIndexOutOfBoundsException();
        }else{
            return items[var];
        }
    }
    
    /**
     * @Method 删除某个位置的元素
     * @Author wss
     * @Version  1.0
     * @Description 
     * @param
     * @Return 
     * @Exception 
     * @Date 2019/4/21 13:24
     */
    public void delete(int var){
        if(var > len){
            throw new ArrayIndexOutOfBoundsException();
        }else{
            for(int i = var ; i < len ; i++){
                items[i] = items[i+1];
            }
        }
        len--;
    }

    /**
     * @Method 修改某个位置的元素
     * @Author wss
     * @Version  1.0
     * @Description
     * @param
     * @Return
     * @Exception
     * @Date 2019/4/21 13:26
     */
    public void update(int var,int value){
        if(var > len){
            throw new ArrayIndexOutOfBoundsException();
        }else{
            items[var] = value;
        }
    }
}

```
------------------------ 
### 无序数组
```java
package orderarray;
import mynoorderarray.NoOrderArray;
/**
 * @ProjectName: MyArray
 * @Package: orderarray
 * @ClassName: OrderArray
 * @Author: wss
 * @Description: ${description}
 * @Date: 2019/4/21 13:26
 * @Version: 1.0
 */
public class OrderArray extends NoOrderArray{
    /**
     * @Method 向有序数组添加元素
     * @Author wss
     * @Version  1.0
     * @Description 
     * @param
     * @Return 
     * @Exception 
     * @Date 2019/4/21 13:30
     */
    public void insert(int value){
        int i;
        for(i = 0 ; i < len ; i++){
            if(items[i] > value){
                break;
            }
        }
        for (int j = len;j>i;j--){
            items[j] = items[j-1];
        }
        items[i] = value;
        len++;
    }
}

```
------------------------
### 二分查找（前提有序数组）
```java
package binarysearch;

import orderarray.OrderArray;

/**
 * @ProjectName: MyArray
 * @Package: binarysearch
 * @ClassName: BinarySearch
 * @Author: wss
 * @Description: ${description}
 * @Date: 2019/4/21 13:39
 * @Version: 1.0
 */
public class BinarySearch extends OrderArray {
    public int binarySearch(int var){
        int min = 0;
        int max = len;
        int middle;
        while(true){
            middle = (min + max)/2;
            if(items[middle] == var){
                return middle;
            }else if(items[middle] < var){
                min = middle+1;
            }else if(items[middle] > var){
                max = middle - 1;
            }
        }
    }
}

```


