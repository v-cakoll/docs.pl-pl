---
title: Wykonywanie zapytania XPath w elemencie DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 56d1d11240934036994a14e454cf1a1d8b95226a
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204534"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="e3d82-102">Wykonywanie zapytania XPath w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="e3d82-102">Performing an XPath Query on a DataSet</span></span>
<span data-ttu-id="e3d82-103">Relacja między zsynchronizowaną <xref:System.Data.DataSet> i <xref:System.Xml.XmlDataDocument> umożliwia korzystanie z usług XML, takich jak zapytanie XML Path Language (XPath), które uzyskuje dostęp do **XmlDataDocument** i może działać bardziej wygodnie niż bezpośredni dostęp do **zestawu danych** .</span><span class="sxs-lookup"><span data-stu-id="e3d82-103">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="e3d82-104">Na przykład <xref:System.Data.DataTable> zamiast używać metody **SELECT** elementu do nawigacji relacji do innych tabel w **zestawie danych**, można wykonać zapytanie XPath na **XmlDataDocument** , który jest synchronizowany z **zestawem danych**, aby uzyskać Lista elementów XML w postaci <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="e3d82-104">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="e3d82-105">Węzły w **XmlNodeList**, rzutowania jako <xref:System.Xml.XmlElement> węzły, mogą następnie zostać przesłane do metody **GetRowFromElement** **XmlDataDocument**, aby zwracały pasujące <xref:System.Data.DataRow> odwołania do wierszy tabeli zsynchronizowanych  **Zestaw danych**.</span><span class="sxs-lookup"><span data-stu-id="e3d82-105">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="e3d82-106">Na przykład poniższy kod przykład wykonuje zapytanie XPath "grandchild".</span><span class="sxs-lookup"><span data-stu-id="e3d82-106">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="e3d82-107">**Zestaw danych** jest wypełniony trzema tabelami: **Klienci**, **zamówienia**i **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="e3d82-107">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="e3d82-108">W przykładzie relacja nadrzędny-podrzędny jest najpierw tworzona między tabelami **Customers** i **Orders** oraz między tabelami **Orders** i **OrderDetails** .</span><span class="sxs-lookup"><span data-stu-id="e3d82-108">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="e3d82-109">Następnie zostanie wykonane zapytanie XPath w celu zwrócenia **XmlNodeList** węzłów **klientów** , gdzie węzeł grandchild **OrderDetails** ma węzeł **ProductID** o wartości 43.</span><span class="sxs-lookup"><span data-stu-id="e3d82-109">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="e3d82-110">W zasadzie przykład używa zapytania XPath, aby określić, którzy klienci mają zamówiony produkt o identyfikatorze **ProductID** 43.</span><span class="sxs-lookup"><span data-stu-id="e3d82-110">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3d82-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3d82-111">See also</span></span>

- [<span data-ttu-id="e3d82-112">Synchronizacja elementów DataSet i XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="e3d82-112">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="e3d82-113">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="e3d82-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
