## S: Single-responsibility principle
>A class should have one and only one reason to change, meaning that a class should have only one job/purpose.

>One class should only serve one purpose, this does not imply that each class should have only one method but they should all relate directly to the responsibility of the class. All the methods and properties should all work towards the same goal. When a class serves multiple purposes or responsibility then it should be made into a new class.

So, as an example lets take popular and widely-used example - an online store with orders, products and customers.
```php
class Order
{
    public function calculateTotalSum()
    {
        // TODO: code logic
    }
    public function getItems()
    {
        // TODO: code logic
    }
    public function getItemCount()
    {
        // TODO: code logic
    }
    public function addItem($item)
    {
        // TODO: code logic
    }
    public function deleteItem($item)
    {
        // TODO: code logic
    }

    public function printOrder()
    {
        // TODO: code logic
    }
    public function showOrder()
    {
        // TODO: code logic
    }

    public function load()
    {
        // TODO: code logic
    }
    public function save()
    {
        // TODO: code logic
    }
    public function update()
    {
        // TODO: code logic
    }
    public function delete()
    {
        // TODO: code logic
    }
}
```

Above class violates single responsibility principle. As you can see, this class performs the operation for 3 different types of tasks: work with every order (calculateTotalSum, getItems, getItemsCount, addItem, deleteItem), display order (printOrder, showOrder) and data handeling (load, save, update, delete). To solve this problem is the division of the class into 3 classes, each of which will be to carry out their task:

So finally the refactored code will be described as below :

```php
namespace Order;
class Order
{
    public function calculateTotalSum()
    {
        // TODO: code logic
    }
    public function getItems()
    {
        // TODO: code logic
    }
    public function getItemCount()
    {
        // TODO: code logic
    }
    public function addItem($item)
    {
        // TODO: code logic
    }
    public function deleteItem($item)
    {
        // TODO: code logic
    }
}

namespace Order\Repositories;
class OrderRepository
{
    public function load()
    {
        // TODO: code logic
    }
    public function save()
    {
        // TODO: code logic
    }
    public function update()
    {
        // TODO: code logic
    }
    public function delete()
    {
        // TODO: code logic
    }
}

namespace Order;
class OrderViewer
{
    public function printOrder()
    {
        // TODO: code logic
    }
    public function showOrder()
    {
        // TODO: code logic
    }
}
```
Now each class is engaged in the specific task and for each class there is only one reason to change it.