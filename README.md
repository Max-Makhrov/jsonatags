# jsonatags

Jsonatags is a library that enables the use of the [Jsonata.js](https://github.com/jsonata-js/jsonata) library in Google Apps Script. API docs are available [here](https://docs.jsonata.org/overview.html).

## Add the library to your project

To add the library to your project:

1.  Click "Add a library" in the Libraries section of the left pane in the Apps Script IDE.
2.  Enter the project key (`1jH4Denh3jCoqRxDV8V2VLxG2xVzkoe4B57Jg0D66RpG1MMgjFZEeG6Kd`) in the "Script ID" field, and click "Look up".
3.  Select the highest version number, and choose `Jsonata` as the identifier. (Do not turn on Development Mode unless you know what you are doing. The development version may not work)
4.  Press "Add". You can now use the Jsonata library in your code.

## Usage

```javascript
// try live here
// https://try.jsonata.org/

function test() {
  var json = {
    "Account": {
      "Account Name": "Firefly",
      "Order": [
        {
          "OrderID": "order103",
          "Product": [
            {
              "Product Name": "Bowler Hat",
              "ProductID": 858383,
              "SKU": "0406654608",
              "Description": {
                "Colour": "Purple",
                "Width": 300,
                "Height": 200,
                "Depth": 210,
                "Weight": 0.75
              },
              "Price": 34.45,
              "Quantity": 2
            },
            {
              "Product Name": "Trilby hat",
              "ProductID": 858236,
              "SKU": "0406634348",
              "Description": {
                "Colour": "Orange",
                "Width": 300,
                "Height": 200,
                "Depth": 210,
                "Weight": 0.6
              },
              "Price": 21.67,
              "Quantity": 1
            }
          ]
        },
        {
          "OrderID": "order104",
          "Product": [
            {
              "Product Name": "Bowler Hat",
              "ProductID": 858383,
              "SKU": "040657863",
              "Description": {
                "Colour": "Purple",
                "Width": 300,
                "Height": 200,
                "Depth": 210,
                "Weight": 0.75
              },
              "Price": 34.45,
              "Quantity": 4
            },
            {
              "ProductID": 345664,
              "SKU": "0406654603",
              "Product Name": "Cloak",
              "Description": {
                "Colour": "Black",
                "Width": 30,
                "Height": 20,
                "Depth": 210,
                "Weight": 2
              },
              "Price": 107.99,
              "Quantity": 1
            }
          ]
        }
      ]
    }
  }

  var request = '$sum(Account.Order.Product.(Price * Quantity))';
  var result = Jsonata.jsonata(request).evaluate(json);
  console.log(result);

}
```

## Library versions

V1. Copied the version 1.8.6 of the original library and adapted it for `google-apps-script`

V2. Commented lines 523-532, starting from `if (!arrayOK) {`. This resolved the issue with the usage of the [`join` function](https://docs.jsonata.org/string-functions#join).

## License

MIT
