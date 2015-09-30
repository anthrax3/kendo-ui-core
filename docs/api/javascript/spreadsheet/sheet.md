---
title: Sheet
page_title: Configuration, methods and events of Kendo UI Spreadsheet Sheet Instance object
---

# kendo.spreadsheet.Sheet

Represents a sheet instance in the [Kendo UI Spreadsheet](/api/javascript/ui/spreadsheet) widget. Inherits from [Observable](/api/javascript/observable).

## Methods

### clearFilter

Clears the filters for the passed column index. If an array is passed, `clearFilter` will clear the filter for each column index.

#### Parameters

##### indexes `Number|Array`

The column index(es)

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.range("A1:B2").values([
            [1, 2],
            [2, 3]
        ]).filter({
            column: 1,
            filter: new kendo.spreadsheet.ValueFilter({
                values: [2]
            })
        }); // the filter will hide the second row

        sheet.clearFilter(1); // the clear filter will remove the applied filter for the second column.
    </script>
```

### columnWidth

Gets or sets the width of the column at the given index.

#### Parameters

##### index `Number`

The zero-based index of the column

##### width `Number` *optional*

If passed, the method will set the width of the column at the passed index.

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.columnWidth(1, 100);
    </script>
```

### deleteColumn

Deletes the contents of the column at the provided index and shifts the remaining contents of the sheet to the left.

#### Parameters

##### index `Number`

The zero-based index of the column

##### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.range("A1:B2").values([ [1, 2], [2, 3] ]);

        sheet.deleteColumn(0);
    </script>
```
### deleteRow

Deletes the contents of the row at the provided index and shifts the remaining contents of the sheet up.

#### Parameters

##### index `Number`

The zero-based index of the row

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.range("A1:B2").values([ [1, 2], [2, 3] ]);

        sheet.deleteRow(0);
    </script>
```

### fromJSON

Loads the widget state and sheet data from JSON.

The schema follows the same structure as the [widget configuration](/api/javascript/ui/spreadsheet#configuration).

> An official JSON schema will be published once the component goes out of Beta.

#### Parameters

##### data `Object`

The object to load data from.  This should be **the deserialized object**, not the JSON string.

#### Example - Load spreadsheet from JSON

    <div id="spreadsheet"></div>
    <script>
        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");
        spreadsheet.fromJSON({
            sheets: [{
                name: "Food Order",
                mergedCells: [
                    "A1:G1"
                ],
                rows: [{
                    height: 70,
                    cells: [{
                        value: "My Company", fontSize: 32, textAlign: "center"
                    }]
                }]
            }]
        });
    </script>

### frozenColumns

Gets or sets the amount of frozen columns displayed by the sheet.

#### Parameters

##### count `Number` *optional*

The amount of columns to be frozen. Pass `0` to remove the frozen pane.

#### Returns

`Number` The current frozen columns. By default, returns `0`.

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.frozenColumns(5);
    </script>
```

### frozenRows

Gets or sets the amount of frozen rows displayed by the sheet.

#### Parameters

##### count `Number` *optional*

The amount of columns to be frozen. Pass `0` to remove the frozen pane.

#### Returns

`Number` The current frozen rows. By default, returns `0`.

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.frozenRows(5);
    </script>
```

### hideColumn

Hides the column at the provided index.

#### Parameters

##### index `Number`

The zero-based index of the column

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.range("A1:B2").values([ [1, 2], [2, 3] ]);

        sheet.hideColumn(1);
    </script>
```

### hideRow

Hides the row at the provided index.

#### Parameters

##### index `Number`

The zero-based index of the row

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.range("A1:B2").values([ [1, 2], [2, 3] ]);

        sheet.hideRow(1);
    </script>
```

### insertColumn

Inserts a new, empty column at the provided index. The contents of the spreadsheet (including the ones in the current column index) are shifted to the right.

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.range("A1:B2").values([ [1, 2], [2, 3] ]);

        sheet.insertColumn(1);
    </script>
```

#### Parameters

##### index `Number`

The zero-based index of the column

### insertRow

Inserts a new, empty row at the provided index. The contents of the spreadsheet (including the ones in the current row index) are shifted down.

#### Parameters

##### index `Number`

The zero-based index of the column

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.range("A1:B2").values([ [1, 2], [2, 3] ]);

        sheet.insertRow(1);
    </script>
```

### range

Returns a [Range](/api/javascript/spreadsheet/range) for the given range specification.

#### Parameters

##### ref `String`

[A1](https://msdn.microsoft.com/en-us/library/bb211395.aspx) or [RC notation](http://excelribbon.tips.net/T008803_Understanding_R1C1_References.html) reference of the cells.

#### Returns

`kendo.spreadsheet.Range` a range object, which may be used to manipulate the cell state further.

#### Example
```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        // set contents of the A1:B2 range
        sheet.range("A1:B2").values([ [1, 2], [2, 3] ]);
    </script>
```

### rowHeight

Gets or sets the height of the row at the given index.

#### Parameters

##### index `Number`

The zero-based index of the row

##### width `Number` *optional*

If passed, the method will set the height of the row at the passed index.

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.rowHeight(1, 100);
    </script>
```

### selection

Returns a range with the current active selection.

#### Returns

`kendo.spreadsheet.Range` the selection range.

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.range("A1:B2").select();

        var selection = sheet.selection(); // A1:B2 range
    </script>
```

### toJSON

Stores the widget state and sheet data to JSON format.

The schema follows the same structure as the [widget configuration](/api/javascript/ui/spreadsheet#configuration).

> An official JSON schema will be published once the component goes out of Beta.

#### Example - Store spreadsheet to JSON

    <div id="spreadsheet"></div>
    <pre id="result"></pre>
    <script>
        $("#spreadsheet").kendoSpreadsheet({
            sheets: [{
                name: "Food Order",
                mergedCells: [
                    "A1:G1"
                ],
                rows: [{
                    height: 70,
                    cells: [{
                        value: "My Company", fontSize: 32, textAlign: "center"
                    }]
                }]
            }]
        });

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");
        var data = spreadsheet.toJSON();
        var json = JSON.stringify(data, null, 2);

        $("#spreadsheet").remove();
        $("#result").text(json);
    </script>

### unhideColumn

Shows the hidden column at the provided index. Does not have any effect if the column is already visible.

#### Parameters

##### index `Number`

The zero-based index of the column

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.range("A1:B2").values([ [1, 2], [2, 3] ]);

        sheet.hideColumn(1);
        sheet.unhideColumn(1); // reverts upper call
    </script>
```

### unhideRow

Shows the hidden row at the provided index. Does not have any effect if the row is already visible.

#### Parameters

##### index `Number`

The zero-based index of the row

#### Example

```html
    <div id="spreadsheet"></div>
    <script type="text/javascript" charset="utf-8">

        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.range("A1:B2").values([ [1, 2], [2, 3] ]);

        sheet.hideRow(1);
        sheet.unhideRow(1); // reverts upper call
    </script>
```

## Events

### change

Fires when the configuration or the data of the sheet change.

#### Event Data

##### e.sender `kendo.spreadsheet.Sheet`

The sheet instance.

#### Example - subscribe to the "change" event during initialization

```html
    <input id="dropdownlist" />
    <script>
        $("#spreadsheet").kendoSpreadsheet();

        var spreadsheet = $("#spreadsheet").data("kendoSpreadsheet");

        var sheet = spreadsheet.activeSheet();

        sheet.bind("change", function() {
            console.log("sheet state changed");
        });

        sheet.range("A1:B2").values([ [1, 2], [2, 3] ]);
    </script>
```