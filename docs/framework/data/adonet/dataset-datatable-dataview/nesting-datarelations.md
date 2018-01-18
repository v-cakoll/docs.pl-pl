---
title: "DataRelations zagnieżdżenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c057e836e8903fc2f5cb28f74858be97d2ffcc14
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="nesting-datarelations"></a><span data-ttu-id="09856-102">DataRelations zagnieżdżenia</span><span class="sxs-lookup"><span data-stu-id="09856-102">Nesting DataRelations</span></span>
<span data-ttu-id="09856-103">Poszczególnych tabel relacyjnych reprezentację danych, zawierać wierszy, które są powiązane ze sobą przy użyciu kolumny lub zestaw kolumn.</span><span class="sxs-lookup"><span data-stu-id="09856-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="09856-104">W ADO.NET <xref:System.Data.DataSet>, relacji między tabelami jest implementowane za pomocą <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="09856-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="09856-105">Po utworzeniu **DataRelation**, relacje nadrzędny podrzędny kolumn są zarządzane za pośrednictwem tylko relacja.</span><span class="sxs-lookup"><span data-stu-id="09856-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="09856-106">Tabele i kolumny są osobne jednostki.</span><span class="sxs-lookup"><span data-stu-id="09856-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="09856-107">W hierarchiczną reprezentację danych XML zawiera relacje nadrzędny podrzędny są reprezentowane przez elementy nadrzędne, zawierające elementy zagnieżdżonych elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="09856-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="09856-108">Ułatwia to zagnieżdżania obiektów podrzędnych podczas **DataSet** jest zsynchronizowany z <xref:System.Xml.XmlDataDocument> lub zapisywane jako danych XML przy użyciu **WriteXml**, **DataRelation** przedstawia **zagnieżdżone** właściwości.</span><span class="sxs-lookup"><span data-stu-id="09856-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="09856-109">Ustawienie **zagnieżdżone** właściwość **DataRelation** do **true** powoduje, że obiekt podrzędny wierszy relacji do być zagnieżdżony w kolumnie nadrzędnej, gdy zapisywane jako dane XML lub synchronizowane z **dokumentu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="09856-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="09856-110">**Zagnieżdżone** właściwość **DataRelation** jest **false**, domyślnie.</span><span class="sxs-lookup"><span data-stu-id="09856-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="09856-111">Na przykład, należy wziąć pod uwagę następujące **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="09856-111">For example, consider the following **DataSet**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 <span data-ttu-id="09856-112">Ponieważ **zagnieżdżone** właściwość **DataRelation** obiektu nie jest ustawiony na **true** tego **zestawu danych**, obiekty podrzędne nie są zagnieżdżone w ramach elementy nadrzędne podczas to **DataSet** jest reprezentowany jako dane XML.</span><span class="sxs-lookup"><span data-stu-id="09856-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="09856-113">Przekształcanie XML reprezentację **zestawu danych** zawiera powiązane **zestawu danych**s z relacjami-nested danych może spowodować spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="09856-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="09856-114">Firma Microsoft zaleca, aby zagnieździć relacji danych.</span><span class="sxs-lookup"><span data-stu-id="09856-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="09856-115">Aby to zrobić, ustaw **zagnieżdżone** właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="09856-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="09856-116">Następnie należy napisać kod w arkusz stylów XSLT, który używa wyrażenia zapytania XPath góra dół hierarchiczne do lokalizowania i przekształcania danych.</span><span class="sxs-lookup"><span data-stu-id="09856-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="09856-117">Poniższy przykładowy kod przedstawia wynik wywołania **WriteXml** na **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="09856-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 <span data-ttu-id="09856-118">Należy pamiętać, że **klientów** elementu i **zamówień** elementy są wyświetlane jako elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="09856-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="09856-119">Jeśli potrzebujesz **zamówień** elementy wyświetlane jako elementy podrzędne ich elementów nadrzędnych odpowiednich, **zagnieżdżone** właściwość **DataRelation** musi mieć ustawioną **true** i należy dodać następujące:</span><span class="sxs-lookup"><span data-stu-id="09856-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="09856-120">Poniższy kod przedstawia, jak dane wyjściowe będą wyglądać, z **zamówień** elementy zagnieżdżone w obrębie ich elementów nadrzędnych odpowiednich.</span><span class="sxs-lookup"><span data-stu-id="09856-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09856-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09856-121">See Also</span></span>  
 [<span data-ttu-id="09856-122">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="09856-122">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="09856-123">Dodawanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="09856-123">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 [<span data-ttu-id="09856-124">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="09856-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="09856-125">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="09856-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
