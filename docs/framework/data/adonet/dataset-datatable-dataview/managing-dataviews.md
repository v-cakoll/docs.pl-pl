---
title: Zarządzanie elementami DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: 5e85fccddf6359791ea702667a36b44f611815dc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784508"
---
# <a name="managing-dataviews"></a>Zarządzanie elementami DataView
Można użyć <xref:System.Data.DataViewManager> do zarządzania ustawieniami widoku dla wszystkich tabel <xref:System.Data.DataView>w. Jeśli masz kontrolkę, którą chcesz powiązać z wieloma tabelami, na przykład z siatką, która nawiguje relacje, obiekt **DataViewManager** jest idealny.  
  
 Element **DataViewManager** zawiera kolekcję <xref:System.Data.DataViewSetting> obiektów, które są używane do ustawiania ustawienia widoku tabel w <xref:System.Data.DataSet>. Zawiera jeden <xref:System.Data.DataViewSetting> obiekt dla każdej tabeli w **zestawie danych.** <xref:System.Data.DataViewSettingCollection> Można ustawić domyślne właściwości **ApplyDefaultSort**, **sort**, **RowFilter**i **RowStateFilter** tabeli, do których istnieje odwołanie, przy użyciu jej **DataViewSetting**. Można odwołać się do **DataViewSetting** dla konkretnej tabeli według nazwy lub odwołania do liczby porządkowej lub przez przekazanie odwołania do tego konkretnego obiektu tabeli. Można uzyskać dostęp do kolekcji obiektów **DataViewSetting** w elemencie **DataViewManager** przy użyciu właściwości **DataViewSettings** .  
  
 Poniższy przykład kodu wypełnia **zestaw danych** z SQL Server bazy danych **Northwind** tabele **Customers**, **Orders**i **Order Details**, tworzy relacje między tabelami, używa elementu **DataViewManager** do Ustaw domyślne ustawienia **widoku** danych i powiąże element **DataGrid** z elementem **DataViewManager**. Przykład ustawia domyślne ustawienia **DataView** dla wszystkich tabel w **zestawie danych** , aby sortować według klucza podstawowego tabeli (**ApplyDefaultSort** = **true**), a następnie modyfikuje kolejność sortowania tabeli **Customers** na Sortuj według **NazwaFirmy**.  
  
```vb  
' Assumes connection is a valid SqlConnection to Northwind.  
' Create a Connection, DataAdapters, and a DataSet.  
Dim custDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID FROM Orders", connection)  
Dim ordDetDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection)  
  
Dim custDS As DataSet = New DataSet()  
  
' Open the Connection.  
connection.Open()  
  
    ' Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
  
    custDA.Fill(custDS, "Customers")  
    orderDA.Fill(custDS, "Orders")  
    ordDetDA.Fill(custDS, "OrderDetails")  
  
    ' Close the Connection.  
    connection.Close()  
  
    ' Create relationships.  
    custDS.Relations.Add("CustomerOrders", _  
          custDS.Tables("Customers").Columns("CustomerID"), _  
          custDS.Tables("Orders").Columns("CustomerID"))  
  
    custDS.Relations.Add("OrderDetails", _  
          custDS.Tables("Orders").Columns("OrderID"), _  
          custDS.Tables("OrderDetails").Columns("OrderID"))  
  
' Create default DataView settings.  
Dim viewManager As DataViewManager = New DataViewManager(custDS)  
  
Dim viewSetting As DataViewSetting  
For Each viewSetting In viewManager.DataViewSettings  
  viewSetting.ApplyDefaultSort = True  
Next  
  
viewManager.DataViewSettings("Customers").Sort = "CompanyName"  
  
' Bind to a DataGrid.  
Dim grid As System.Windows.Forms.DataGrid = New System.Windows.Forms.DataGrid()  
grid.SetDataBinding(viewManager, "Customers")  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection to Northwind.  
// Create a Connection, DataAdapters, and a DataSet.  
SqlDataAdapter custDA = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderDA = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID FROM Orders", connection);  
SqlDataAdapter ordDetDA = new SqlDataAdapter(  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection);  
  
DataSet custDS = new DataSet();  
  
// Open the Connection.  
connection.Open();  
  
    // Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
  
    custDA.Fill(custDS, "Customers");  
    orderDA.Fill(custDS, "Orders");  
    ordDetDA.Fill(custDS, "OrderDetails");  
  
    // Close the Connection.  
    connection.Close();  
  
    // Create relationships.  
    custDS.Relations.Add("CustomerOrders",  
          custDS.Tables["Customers"].Columns["CustomerID"],  
          custDS.Tables["Orders"].Columns["CustomerID"]);  
  
    custDS.Relations.Add("OrderDetails",  
          custDS.Tables["Orders"].Columns["OrderID"],  
          custDS.Tables["OrderDetails"].Columns["OrderID"]);  
  
// Create default DataView settings.  
DataViewManager viewManager = new DataViewManager(custDS);  
  
foreach (DataViewSetting viewSetting in viewManager.DataViewSettings)  
  viewSetting.ApplyDefaultSort = true;  
  
viewManager.DataViewSettings["Customers"].Sort = "CompanyName";  
  
// Bind to a DataGrid.  
System.Windows.Forms.DataGrid grid = new System.Windows.Forms.DataGrid();  
grid.SetDataBinding(viewManager, "Customers");  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataSet>
- <xref:System.Data.DataViewManager>
- <xref:System.Data.DataViewSetting>
- <xref:System.Data.DataViewSettingCollection>
- [Elementy DataView](dataviews.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
