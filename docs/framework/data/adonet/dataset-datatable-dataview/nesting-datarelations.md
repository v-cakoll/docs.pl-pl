---
title: Zagnieżdżanie elementów DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 08149de9222c34928078c0ca9d88096f7a4a88d1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203268"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="b9331-102">Zagnieżdżanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="b9331-102">Nesting DataRelations</span></span>
<span data-ttu-id="b9331-103">W relacyjnej reprezentacji danych poszczególne tabele zawierają wiersze, które są ze sobą powiązane, przy użyciu kolumny lub zestawu kolumn.</span><span class="sxs-lookup"><span data-stu-id="b9331-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="b9331-104">W ADO.NET <xref:System.Data.DataSet>relacja między tabelami jest implementowana <xref:System.Data.DataRelation>przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="b9331-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="b9331-105">Podczas tworzenia **relacji**datarelationship relacje z relacją nadrzędny-podrzędny kolumn są zarządzane tylko za pomocą relacji.</span><span class="sxs-lookup"><span data-stu-id="b9331-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="b9331-106">Tabele i kolumny są oddzielnymi jednostkami.</span><span class="sxs-lookup"><span data-stu-id="b9331-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="b9331-107">W hierarchicznej reprezentacji danych dostarczanych przez XML, relacje nadrzędny-podrzędny są reprezentowane przez elementy nadrzędne, które zawierają zagnieżdżone elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="b9331-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="b9331-108">Aby ułatwić zagnieżdżanie obiektów podrzędnych, gdy **zestaw danych** <xref:System.Xml.XmlDataDocument> jest synchronizowany z lub zapisywany jako dane XML przy użyciu **WriteXml**, **relacja** danych ujawnia Właściwość **zagnieżdżoną** .</span><span class="sxs-lookup"><span data-stu-id="b9331-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="b9331-109">Ustawienie właściwości **zagnieżdżonej** **relacji** na **wartość true** powoduje, że wiersze podrzędne relacji mają być zagnieżdżone w kolumnie nadrzędnej podczas zapisywania jako dane XML lub synchronizowane z **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="b9331-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="b9331-110">**Zagnieżdżona** właściwość elementu DataRelation ma domyślnie **wartość false**.</span><span class="sxs-lookup"><span data-stu-id="b9331-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="b9331-111">Rozważmy na przykład następujący **zestaw danych**.</span><span class="sxs-lookup"><span data-stu-id="b9331-111">For example, consider the following **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="b9331-112">Ponieważ **zagnieżdżona** właściwość obiektu nie jest ustawiona na **wartość true** dla tego **zestawu danych**, obiekty podrzędne nie są zagnieżdżane w elementach nadrzędnych, gdy ten **zestaw danych** jest reprezentowany jako dane XML.</span><span class="sxs-lookup"><span data-stu-id="b9331-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="b9331-113">Przekształcanie reprezentacji XML **zestawu danych** , który zawiera powiązane elementy **DataSet**z niezagnieżdżonymi relacjami danych może spowodować niską wydajność.</span><span class="sxs-lookup"><span data-stu-id="b9331-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="b9331-114">Zalecamy zagnieżdżanie relacji danych.</span><span class="sxs-lookup"><span data-stu-id="b9331-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="b9331-115">W tym celu ustaw właściwość **zagnieżdżoną** na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="b9331-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="b9331-116">Następnie napisz kod w arkuszu stylów XSLT, który używa hierarchicznych wyrażeń zapytania XPath do lokalizowania i przekształcania danych.</span><span class="sxs-lookup"><span data-stu-id="b9331-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="b9331-117">Poniższy przykład kodu ilustruje wynik wywołania **WriteXml** na **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="b9331-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="b9331-118">Należy zauważyć, że element **Customers** i elementy Orders są wyświetlane jako elementy równorzędne.</span><span class="sxs-lookup"><span data-stu-id="b9331-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="b9331-119">Jeśli chcesz, aby elementy **zamówienia** były wyświetlane jako elementy podrzędne odpowiednich elementów nadrzędnych, właściwość **zagnieżdżona** elementu DataRelation powinna mieć wartość **true** i dodać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="b9331-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="b9331-120">Poniższy kod pokazuje, jak będzie wyglądać wynikowe dane wyjściowe, a elementy **Orders** są zagnieżdżone w odpowiednich elementach nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b9331-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b9331-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9331-121">See also</span></span>

- [<span data-ttu-id="b9331-122">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="b9331-122">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="b9331-123">Dodawanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="b9331-123">Adding DataRelations</span></span>](adding-datarelations.md)
- [<span data-ttu-id="b9331-124">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="b9331-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="b9331-125">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="b9331-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
