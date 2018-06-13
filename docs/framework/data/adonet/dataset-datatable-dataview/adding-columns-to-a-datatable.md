---
title: Dodawanie kolumn do DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 8ee47ddce273e564673d96d2b2e276b68879373f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760469"
---
# <a name="adding-columns-to-a-datatable"></a>Dodawanie kolumn do DataTable
A <xref:System.Data.DataTable> zawiera kolekcję <xref:System.Data.DataColumn> odwołują się obiekty **kolumn** właściwość tabeli. W tej kolekcji kolumn, wraz ze wszystkimi ograniczeniami definiuje schemat lub struktury tabeli.  
  
 Możesz utworzyć **DataColumn** obiektów w tabeli za pomocą **DataColumn** konstruktora, lub przez wywołanie metody **Dodaj** metody **kolumn**właściwości tabeli, która jest <xref:System.Data.DataColumnCollection>. **Dodaj** metoda przyjmuje opcjonalny **ColumnName**, **DataType**, i **wyrażenie** argumentów i tworzy nowy  **Element DataColumn** jako członka kolekcji. Również akceptuje istniejące **DataColumn** obiektów i dodaje go do kolekcji i zwraca odwołanie do dodany **DataColumn** żądanie. Ponieważ **DataTable** obiekty nie są specyficzne dla dowolnego źródła danych, typy .NET Framework są używane podczas określania typu danych **DataColumn**.  
  
 W poniższym przykładzie dodano cztery kolumny w celu **DataTable**.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 W tym przykładzie należy zauważyć, że właściwości **IDKlienta** kolumny są ustawione na nie zezwalać na **DBNull** wartości i ograniczyć unikatowe wartości. Jednak w przypadku definiowania **IDKlienta** kolumny jako kolumny klucza podstawowego tabeli **AllowDBNull** zostanie automatycznie ustawiona właściwość do **false** i **Unique** zostanie automatycznie ustawiona właściwość do **true**. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
>  Jeśli nie podano nazwy kolumn dla kolumny, kolumnie podano przyrostowe domyślną nazwę kolumny*N,* począwszy od "Kolumna1", gdy jest ona dodawana do **DataColumnCollection**. Firma Microsoft zaleca, aby uniknąć z konwencją nazewnictwa "kolumny*N*" gdy Podaj nazwę kolumny, ponieważ Podaj nazwę może spowodować konflikt z istniejącą nazwą kolumny domyślne w **DataColumnCollection**. Jeśli podanej nazwie już istnieje, jest zwracany wyjątek.  
  
 Jeśli używasz <xref:System.Xml.Linq.XElement> jako <xref:System.Data.DataColumn.DataType%2A> z <xref:System.Data.DataColumn> w <xref:System.Data.DataTable>, podczas odczytu w danych serializacji XML nie będą działać. Na przykład, jeśli należy zapisać <xref:System.Xml.XmlDocument> za pomocą `DataTable.WriteXml` metody podczas serializacji XML jest dodatkowe nadrzędnym w <xref:System.Xml.Linq.XElement>. Aby obejść ten problem, należy użyć <xref:System.Data.SqlTypes.SqlXml> wpisz zamiast <xref:System.Xml.Linq.XElement>. `ReadXml` i `WriteXml` pracować poprawnie z <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
