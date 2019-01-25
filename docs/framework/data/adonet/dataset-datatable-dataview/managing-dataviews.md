---
title: Zarządzanie elementami DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: 847829f6b131a33cc5ff1ca77b10f7e756da920f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497082"
---
# <a name="managing-dataviews"></a><span data-ttu-id="c211c-102">Zarządzanie elementami DataView</span><span class="sxs-lookup"><span data-stu-id="c211c-102">Managing DataViews</span></span>
<span data-ttu-id="c211c-103">Możesz użyć <xref:System.Data.DataViewManager> do zarządzania ustawieniami widoku dla wszystkich tabel w <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="c211c-103">You can use a <xref:System.Data.DataViewManager> to manage view settings for all the tables in a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="c211c-104">Jeśli masz formant, który chcesz powiązać z wieloma tabelami, takie jak siatki która nawiguje relacji **DataViewManager** jest idealnym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="c211c-104">If you have a control that you want to bind to multiple tables, such as a grid that navigates relationships, a **DataViewManager** is ideal.</span></span>  
  
 <span data-ttu-id="c211c-105">**DataViewManager** zawiera zbiór <xref:System.Data.DataViewSetting> obiekty, które są używane do ustawienia widoku tabel w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c211c-105">The **DataViewManager** contains a collection of <xref:System.Data.DataViewSetting> objects that are used to set the view setting of the tables in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c211c-106"><xref:System.Data.DataViewSettingCollection> Zawiera jeden <xref:System.Data.DataViewSetting> obiektu dla każdej tabeli w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="c211c-106">The <xref:System.Data.DataViewSettingCollection> contains one <xref:System.Data.DataViewSetting> object for each table in a **DataSet**.</span></span> <span data-ttu-id="c211c-107">Można określić wartość domyślną **ApplyDefaultSort**, **sortowania**, **RowFilter**, i **Element RowStateFilter** właściwości tej tabeli przez za pomocą jego **DataViewSetting**.</span><span class="sxs-lookup"><span data-stu-id="c211c-107">You can set the default **ApplyDefaultSort**, **Sort**, **RowFilter**, and **RowStateFilter** properties of the referenced table by using its **DataViewSetting**.</span></span> <span data-ttu-id="c211c-108">Możesz odwoływać się do **DataViewSetting** dla konkretnej tabeli przez nazwę lub numer porządkowy odwołanie lub przekazywaniem odwołań do tego obiektu w określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c211c-108">You can reference the **DataViewSetting** for a particular table by name or ordinal reference, or by passing a reference to that specific table object.</span></span> <span data-ttu-id="c211c-109">Możesz uzyskać dostęp kolekcję **DataViewSetting** obiekty w **DataViewManager** przy użyciu **DataViewSettings** właściwości.</span><span class="sxs-lookup"><span data-stu-id="c211c-109">You can access the collection of **DataViewSetting** objects in a **DataViewManager** by using the **DataViewSettings** property.</span></span>  
  
 <span data-ttu-id="c211c-110">Poniższy kod przykładowy wypełnienia **zestawu danych** z programem SQL Server **Northwind** bazy danych tabel **klientów**, **zamówienia**i  **Szczegóły zamówienia**, tworzy relacje między tabelami, używa **DataViewManager** do ustawiania domyślnych **DataView** ustawienia i powiązań **DataGrid**  do **DataViewManager**.</span><span class="sxs-lookup"><span data-stu-id="c211c-110">The following code example fills a **DataSet** with the SQL Server **Northwind** database tables **Customers**, **Orders**, and **Order Details**, creates the relationships between the tables, uses a **DataViewManager** to set default **DataView** settings, and binds a **DataGrid** to the **DataViewManager**.</span></span> <span data-ttu-id="c211c-111">W przykładzie ustawiono domyślną **DataView** ustawienia dla wszystkich tabel w **DataSet** Aby posortować według klucza podstawowego tabeli (**ApplyDefaultSort**  =  **true**), a następnie zmienia kolejność sortowania **klientów** tabeli, aby posortować według **CompanyName**.</span><span class="sxs-lookup"><span data-stu-id="c211c-111">The example sets the default **DataView** settings for all tables in the **DataSet** to sort by the primary key of the table (**ApplyDefaultSort** = **true**), and then modifies the sort order of the **Customers** table to sort by **CompanyName**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c211c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c211c-112">See also</span></span>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataViewManager>
- <xref:System.Data.DataViewSetting>
- <xref:System.Data.DataViewSettingCollection>
- [<span data-ttu-id="c211c-113">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="c211c-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [<span data-ttu-id="c211c-114">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="c211c-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
