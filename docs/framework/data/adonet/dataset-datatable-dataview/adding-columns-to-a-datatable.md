---
title: Dodawanie kolumn do DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 892c0488588e9a5b59650f4a815ba9819493a610
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538274"
---
# <a name="adding-columns-to-a-datatable"></a>Dodawanie kolumn do DataTable
A <xref:System.Data.DataTable> zawiera zbiór <xref:System.Data.DataColumn> obiektów, odwołuje się **kolumn** właściwości tabeli. Ta kolekcja kolumn, wraz ze wszystkimi ograniczeniami definiuje schemat lub strukturę tabeli.  
  
 Możesz utworzyć **DataColumn** obiektów w tabeli za pomocą **DataColumn** konstruktora, lub przez wywołanie **Dodaj** metody **kolumn**właściwości tabeli, który jest <xref:System.Data.DataColumnCollection>. **Dodaj** metoda przyjmuje opcjonalny **ColumnName**, **DataType**, i **wyrażenie** argumentów i tworzy nową  **DataColumn** jako członka kolekcji. Akceptuje ona również, istniejące **DataColumn** obiektu i dodaje go do kolekcji i zwraca odwołanie do dodany **DataColumn** Jeśli jest to wymagane. Ponieważ **DataTable** obiekty nie są specyficzne dla dowolnego źródła danych, typów programu .NET Framework są używane podczas określania typu danych **DataColumn**.  
  
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
  
 W tym przykładzie należy zauważyć, że właściwości **CustID** kolumna są ustawione na Zezwalaj **DBNull** wartości i ograniczyć wartości, które mają być unikatowe. Jednak jeśli zdefiniujesz **CustID** kolumny jako kolumny klucza podstawowego tabeli **AllowDBNull** właściwość zostanie automatycznie ustawiony w pozycji **false** i **Unikatowe** właściwość zostanie automatycznie ustawiony w pozycji **true**. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
>  Jeśli nie podano nazwy kolumny dla kolumny, kolumna jest otrzymuje nazwę przyrostowe domyślne kolumny*N,* począwszy od "Kolumna1", gdy jest ona dodawana do **DataColumnCollection**. Firma Microsoft zaleca, aby unikać konwencji nazewnictwa "kolumna*N*" po użytkownik poda nazwę kolumny, ponieważ nazwa podana może spowodować konflikt z istniejącą nazwą kolumny domyślne w **DataColumnCollection**. Jeśli podana nazwa już istnieje, zostanie zgłoszony wyjątek.  
  
 Jeśli używasz <xref:System.Xml.Linq.XElement> jako <xref:System.Data.DataColumn.DataType%2A> z <xref:System.Data.DataColumn> w <xref:System.Data.DataTable>, serializacji XML nie będzie działać podczas odczytywania danych. Na przykład, jeśli możesz zapisać <xref:System.Xml.XmlDocument> przy użyciu `DataTable.WriteXml` metoda po serializacji XML jest dodatkowe nadrzędnym w <xref:System.Xml.Linq.XElement>. Aby obejść ten problem, należy użyć <xref:System.Data.SqlTypes.SqlXml> wpisz zamiast <xref:System.Xml.Linq.XElement>. `ReadXml` i `WriteXml` działają prawidłowo z <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
