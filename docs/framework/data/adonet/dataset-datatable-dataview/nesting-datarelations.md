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
# <a name="nesting-datarelations"></a>Zagnieżdżanie elementów DataRelation
W relacyjnej reprezentacji danych poszczególne tabele zawierają wiersze, które są ze sobą powiązane, przy użyciu kolumny lub zestawu kolumn. W ADO.NET <xref:System.Data.DataSet>relacja między tabelami jest implementowana <xref:System.Data.DataRelation>przy użyciu. Podczas tworzenia **relacji**datarelationship relacje z relacją nadrzędny-podrzędny kolumn są zarządzane tylko za pomocą relacji. Tabele i kolumny są oddzielnymi jednostkami. W hierarchicznej reprezentacji danych dostarczanych przez XML, relacje nadrzędny-podrzędny są reprezentowane przez elementy nadrzędne, które zawierają zagnieżdżone elementy podrzędne.  
  
 Aby ułatwić zagnieżdżanie obiektów podrzędnych, gdy **zestaw danych** <xref:System.Xml.XmlDataDocument> jest synchronizowany z lub zapisywany jako dane XML przy użyciu **WriteXml**, **relacja** danych ujawnia Właściwość **zagnieżdżoną** . Ustawienie właściwości **zagnieżdżonej** **relacji** na **wartość true** powoduje, że wiersze podrzędne relacji mają być zagnieżdżone w kolumnie nadrzędnej podczas zapisywania jako dane XML lub synchronizowane z **XmlDataDocument**. **Zagnieżdżona** właściwość elementu DataRelation ma domyślnie **wartość false**.  
  
 Rozważmy na przykład następujący **zestaw danych**.  
  
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
  
 Ponieważ **zagnieżdżona** właściwość obiektu nie jest ustawiona na **wartość true** dla tego **zestawu danych**, obiekty podrzędne nie są zagnieżdżane w elementach nadrzędnych, gdy ten **zestaw danych** jest reprezentowany jako dane XML. Przekształcanie reprezentacji XML **zestawu danych** , który zawiera powiązane elementy **DataSet**z niezagnieżdżonymi relacjami danych może spowodować niską wydajność. Zalecamy zagnieżdżanie relacji danych. W tym celu ustaw właściwość **zagnieżdżoną** na **wartość true**. Następnie napisz kod w arkuszu stylów XSLT, który używa hierarchicznych wyrażeń zapytania XPath do lokalizowania i przekształcania danych.  
  
 Poniższy przykład kodu ilustruje wynik wywołania **WriteXml** na **zestawie danych**.  
  
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
  
 Należy zauważyć, że element **Customers** i elementy Orders są wyświetlane jako elementy równorzędne. Jeśli chcesz, aby elementy **zamówienia** były wyświetlane jako elementy podrzędne odpowiednich elementów nadrzędnych, właściwość **zagnieżdżona** elementu DataRelation powinna mieć wartość **true** i dodać następujące elementy:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 Poniższy kod pokazuje, jak będzie wyglądać wynikowe dane wyjściowe, a elementy **Orders** są zagnieżdżone w odpowiednich elementach nadrzędnych.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Dodawanie elementów DataRelation](adding-datarelations.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
