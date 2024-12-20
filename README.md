# Data-Binding

## Factory function

factory function là kỹ thuật UI5, với factory function bạn có thể kiểm tra thuộc tính item trong dữ liệu quyết định UI control nào sẽ tạo ra.

ví dụ :

```js
<List
  id="productList"
  items="{
      path: '/Products',
      factory: '.productListFactory'
    }"
></List>
```

sẽ lấy đc từng item của product
`productListFactory` : dùng getProperty() sẽ lấy được giá trị của `Discontinued` và `UnitsInStock`

- `true` : tạo một `StandardListItem` và gán một số thông tin
- `false` : tạo một `ObjectListItem`
  - Tiếp tục kiểm tra `UnitsInStock` <1 nếu đúng thêm addAttribute

## onItemSelected()

`event.getSource()` sẽ được item nào vừa được trigger vào
`getBindingContext("products")` sẽ lấy được dữ liệu của item mà control đó đang hiển thị.
`getPath()`: sẽ lấy được đường dẫn của context đang trỏ đến
`this.byId("productDetailsPanel")` trả về control UI có ID đó
`bindElement()` : sau khi cung cấp đường dẫn sPath và model `products` bindElement sẽ hiển thị item được trigger

## formatStockValue()

Tạo 1 `new Currency()` để định dạng tiền tệ

Tính toán giá trị và định dạng thành chuỗi nhờ method `formatValue`:

```js
return oCurrency.formatValue([fUnitPrice * iStockLevel, sCurrCode], "string");
```
