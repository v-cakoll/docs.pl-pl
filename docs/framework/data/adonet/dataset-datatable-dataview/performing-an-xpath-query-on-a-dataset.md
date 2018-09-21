---
title: Wykonywanie zapytania XPath w zestawie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: a1718429360d79c4628e9948eb1b052c3ac01964
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493041"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="fc3f8-102">Wykonywanie zapytania XPath w zestawie danych</span><span class="sxs-lookup"><span data-stu-id="fc3f8-102">Performing an XPath Query on a DataSet</span></span>
<span data-ttu-id="fc3f8-103">Relacja między zsynchronizowany <xref:System.Data.DataSet> i <xref:System.Xml.XmlDataDocument> pozwala korzystać z XML usług, takich jak zapytania XML Path Language (XPath), do których dostęp **XmlDataDocument** i mogą wykonywać niektóre funkcje bardzo ułatwia niż dostęp do **DataSet** bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="fc3f8-103">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="fc3f8-104">Na przykład, zamiast używać **wybierz** metody <xref:System.Data.DataTable> do nawigowanie po relacjach z innymi tabelami w **zestawu danych**, można wykonać zapytania XPath na **XmlDataDocument**  , jest zsynchronizowany z **DataSet**, aby uzyskać listę elementów XML w formie <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="fc3f8-104">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="fc3f8-105">Węzły w **XmlNodeList**, rzutowania jako <xref:System.Xml.XmlElement> węzłów, może być następnie przekazywany do **GetRowFromElement** metody **XmlDataDocument**, aby zwrócić dopasowania <xref:System.Data.DataRow> odwołania do wierszy w tabeli zsynchronizowane **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="fc3f8-105">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="fc3f8-106">Na przykład poniższy przykładowy kod wykonuje zapytanie XPath "podwójnym".</span><span class="sxs-lookup"><span data-stu-id="fc3f8-106">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="fc3f8-107">**DataSet** jest wypełniany trzy tabele: **klientów**, **zamówienia**, i **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="fc3f8-107">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="fc3f8-108">W tym przykładzie najpierw tworzenie relacji nadrzędny podrzędny między **klientów** i **zamówienia** tabel oraz między **zamówienia** i **OrderDetails** tabel.</span><span class="sxs-lookup"><span data-stu-id="fc3f8-108">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="fc3f8-109">Zapytania XPath następnie odbywa się do zwrócenia **XmlNodeList** z **klientów** węzły w przypadku, gdy podwójnym **OrderDetails** węzeł ma **ProductID**węzła z wartością 43.</span><span class="sxs-lookup"><span data-stu-id="fc3f8-109">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="fc3f8-110">W zasadzie próbka używa zapytanie XPath do określenia, którzy mają uporządkowane produktu, który ma **ProductID** 43.</span><span class="sxs-lookup"><span data-stu-id="fc3f8-110">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fc3f8-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc3f8-111">See Also</span></span>  
 [<span data-ttu-id="fc3f8-112">Synchronizacja elementów DataSet i XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="fc3f8-112">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [<span data-ttu-id="fc3f8-113">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="fc3f8-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
