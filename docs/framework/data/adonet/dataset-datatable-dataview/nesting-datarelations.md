---
title: Zagnieżdżanie elementów DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 9255615c7786773f1d4f453b910fdccdf191721f
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360575"
---
# <a name="nesting-datarelations"></a>Zagnieżdżanie elementów DataRelation
W relacyjnej reprezentację danych poszczególne tabele zawierają wiersze, które są powiązane ze sobą za pomocą kolumny lub zestaw kolumn. W ADO.NET <xref:System.Data.DataSet>, relacje między tabelami jest implementowany przy użyciu <xref:System.Data.DataRelation>. Po utworzeniu **DataRelation**, relacji nadrzędny podrzędny kolumn odbywa się wyłącznie za pośrednictwem relacji. Tabele i kolumny są osobne jednostki. W hierarchiczną reprezentację XML udostępnia dane relacji nadrzędny podrzędny są reprezentowane przez elementy nadrzędne, które zawierają elementy zagnieżdżonych elementów podrzędnych.  
  
 Aby ułatwić zagnieżdżania obiektów podrzędnych podczas **zestawu danych** jest zsynchronizowany z <xref:System.Xml.XmlDataDocument> lub zapisywane w postaci danych XML przy użyciu **WriteXml**, **DataRelation** udostępnia **zagnieżdżone** właściwości. Ustawienie **zagnieżdżone** właściwość **DataRelation** do **true** powoduje, że element podrzędny wiersze w relacji do być zagnieżdżony w kolumnie nadrzędnej przy zapisywaniu danych XML lub synchronizowane z **XmlDataDocument**. **Zagnieżdżone** właściwość **DataRelation** jest **false**, domyślnie.  
  
 Na przykład, należy wziąć pod uwagę następujące **zestawu danych**.  
  
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
  
 Ponieważ **zagnieżdżone** właściwość **DataRelation** obiektu nie jest ustawiony na **true** tego **zestawu danych**, obiekty podrzędne nie są zagnieżdżone w ramach elementów nadrzędnych przy to **zestawu danych** jest reprezentowany jako danych XML. Przekształcanie reprezentację XML **zestawu danych** zawierający powiązane **DataSet**s z relacjami danych-nested mogą powodować spadek wydajności. Firma Microsoft zaleca, aby zagnieździć relacji danych. Aby to zrobić, należy ustawić **zagnieżdżone** właściwości **true**. Następnie napisz kod w arkusza stylów XSLT, który używa wyrażenia kwerendy XPath hierarchiczne góra dół do lokalizowania i przekształcania danych.  
  
 Poniższy przykład kodu pokazuje wynik wywołania **WriteXml** na **zestawu danych**.  
  
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
  
 Należy pamiętać, że **klientów** elementu i **zamówienia** elementy są wyświetlane jako elementów równorzędnych. Jeżeli chcesz **zamówienia** elementy, które są wyświetlane jako elementy podrzędne ich elementy nadrzędne odpowiednich **zagnieżdżone** właściwość **DataRelation** musi być równa **true** i należy dodać następujące czynności:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 W poniższym kodzie pokazano, jak dane wyjściowe będą wyglądać, za pomocą **zamówienia** elementy zagnieżdżone w obrębie ich elementy nadrzędne odpowiednich.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Dodawanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
