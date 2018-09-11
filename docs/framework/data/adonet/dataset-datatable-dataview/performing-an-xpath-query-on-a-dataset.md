---
title: Wykonywanie zapytania XPath w zestawie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: a1718429360d79c4628e9948eb1b052c3ac01964
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270382"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Wykonywanie zapytania XPath w zestawie danych
Relacja między zsynchronizowany <xref:System.Data.DataSet> i <xref:System.Xml.XmlDataDocument> pozwala korzystać z XML usług, takich jak zapytania XML Path Language (XPath), do których dostęp **XmlDataDocument** i mogą wykonywać niektóre funkcje bardzo ułatwia niż dostęp do **DataSet** bezpośrednio. Na przykład, zamiast używać **wybierz** metody <xref:System.Data.DataTable> do nawigowanie po relacjach z innymi tabelami w **zestawu danych**, można wykonać zapytania XPath na **XmlDataDocument**  , jest zsynchronizowany z **DataSet**, aby uzyskać listę elementów XML w formie <xref:System.Xml.XmlNodeList>. Węzły w **XmlNodeList**, rzutowania jako <xref:System.Xml.XmlElement> węzłów, może być następnie przekazywany do **GetRowFromElement** metody **XmlDataDocument**, aby zwrócić dopasowania <xref:System.Data.DataRow> odwołania do wierszy w tabeli zsynchronizowane **zestawu danych**.  
  
 Na przykład poniższy przykładowy kod wykonuje zapytanie XPath "podwójnym". **DataSet** jest wypełniany trzy tabele: **klientów**, **zamówienia**, i **OrderDetails**. W tym przykładzie najpierw tworzenie relacji nadrzędny podrzędny między **klientów** i **zamówienia** tabel oraz między **zamówienia** i **OrderDetails** tabel. Zapytania XPath następnie odbywa się do zwrócenia **XmlNodeList** z **klientów** węzły w przypadku, gdy podwójnym **OrderDetails** węzeł ma **ProductID**węzła z wartością 43. W zasadzie próbka używa zapytanie XPath do określenia, którzy mają uporządkowane produktu, który ma **ProductID** 43.  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],   
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);   
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Synchronizacja elementów DataSet i XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
