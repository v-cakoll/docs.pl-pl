---
title: Wykonywanie zapytania XPath w elemencie DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 5e9a00ab78a57c3c1686d7c87ed8b45d9b2649af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150834"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Wykonywanie zapytania XPath w elemencie DataSet
Relacja <xref:System.Data.DataSet> między zsynchronizowanym i <xref:System.Xml.XmlDataDocument> umożliwia korzystanie z usług XML, takich jak xml path language (XPath), które uzyskują dostęp do **XmlDataDocument** i można wykonywać pewne funkcje wygodniej niż dostęp do **DataSet** bezpośrednio. Na przykład zamiast używać **Select** metody Select <xref:System.Data.DataTable> a do nawigowania relacji do innych tabel w **zestawie danych,** można wykonać kwerendę XPath na **XmlDataDocument,** który jest zsynchronizowany z **Zestawem danych**, aby uzyskać listę elementów XML w postaci <xref:System.Xml.XmlNodeList>pliku . Węzły w **XmlNodeList**, <xref:System.Xml.XmlElement> rzutowane jako węzły, mogą być następnie przekazywane do **Metody GetRowFromElement** dokumentu <xref:System.Data.DataRow> **XmlDataDocument**, aby zwrócić pasujące odwołania do wierszy tabeli w zsynchronizowanym zestawie **danych**.  
  
 Na przykład poniższy przykład kodu wykonuje kwerendę XPath "wnuk". Zestaw **danych** jest wypełniony trzema tabelami: **Klienci,** **Zamówienia**i **Szczegóły zamówienia.** W przykładzie relacja nadrzędny podrzędny jest najpierw tworzony między **klientami** i **zamówienia** tabel oraz między **zamówieniami** i **OrderDetails** tabel. Następnie wykonuje się kwerendę XPath w celu zwrócenia **XmlNodeList** węzłów **klientów,** w których węzeł **OrderDetails** wnuka ma węzeł **ProductID** o wartości 43. W istocie przykład używa XPath kwerendy, aby ustalić, którzy klienci zamówili produkt, który ma **ProductID** 43.  
  
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

- [Synchronizacja elementów DataSet i XmlDataDocument](dataset-and-xmldatadocument-synchronization.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
