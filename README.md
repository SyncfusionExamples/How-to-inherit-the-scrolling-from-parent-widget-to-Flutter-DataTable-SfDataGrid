# How to inherit the scrolling from parent widget to Flutter DataTable (SfDataGrid)?

In this article, we will show you how to inherit the scrolling from parent widget to [Flutter DataTable](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget with all the necessary properties. To do this, wrap [SingleChildScrollView](https://api.flutter.dev/flutter/widgets/SingleChildScrollView-class.html) around SfDataGrid as its parent. Then, enable [SfDataGrid.shrinkWrapRows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/shrinkWrapRows.html) to set the height of the datagrid based on the available number of rows. However, note that when using shrinkWrapRows, all rows are constructed during the initial loading to calculate the height of the DataGrid. This approach helps eliminate the inner scroll and enables scrolling through its parent SingleChildScrollView.

```dart
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SingleChildScrollView(
        child: Column(
          children: [
            Container(
              height: 200,
              color: Colors.green,
              child: const Center(
                child: Text(
                  'Container widget 1',
                  style: TextStyle(
                    color: Colors.white,
                    fontSize: 20,
                  ),
                ),
              ),
            ),
            SfDataGrid(
              shrinkWrapRows: true,
              source: employeeDataSource,
              columnWidthMode: ColumnWidthMode.fill,
              columns: getColumns
            ),
          ],
        ),
      ),
    );
  }
```
You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-inherit-the-scrolling-from-parent-widget-to-Flutter-DataTable-SfDataGrid).