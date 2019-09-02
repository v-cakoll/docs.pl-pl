---
title: Dodawanie elementów DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: fde1e2ace09e31234d199876ae7f063e01e7a7e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203980"
---
# <a name="adding-datarelations"></a>Dodawanie elementów DataRelation
W przypadku <xref:System.Data.DataTable>zwieloma obiektami można użyć <xref:System.Data.DataRelation> obiektów, aby powiązać jedną tabelę z inną, aby nawigować przez tabele i zwracać elementy podrzędne lub nadrzędne z powiązanej tabeli. <xref:System.Data.DataSet>  
  
 Argumenty wymagane do utworzenia **relacji** datarelationship są nazwami tworzonego elementu datarelationship i tablicą zawierającą <xref:System.Data.DataColumn> co najmniej jedno odwołanie do kolumn, które pełnią rolę kolumn nadrzędnych i podrzędnych w relacji. Po utworzeniu **relacji**można jej używać do nawigowania między tabelami i pobierania wartości.  
  
 Dodawanie **relacji** do <xref:System.Data.DataSet> dodawania, domyślnie, <xref:System.Data.UniqueConstraint> do tabeli nadrzędnej i <xref:System.Data.ForeignKeyConstraint> do tabeli podrzędnej. Aby uzyskać więcej informacji o tych domyślnych ograniczeniach, zobacz temat [ograniczenia DataTable](datatable-constraints.md).  
  
 Poniższy przykład kodu tworzy relację danych przy użyciu dwóch <xref:System.Data.DataTable> obiektów w <xref:System.Data.DataSet>. Każda <xref:System.Data.DataTable> z nich zawiera kolumnę o nazwie **CustId**, która służy jako link między dwoma <xref:System.Data.DataTable> obiektami. Przykład dodaje pojedyncze **powiązanie** do <xref:System.Data.DataSet>kolekcji **relacji** . Pierwszy argument w przykładzie określa nazwę tworzonego **powiązania** . Drugi argument ustawia nadrzędną **kolumnę** danych, a trzeci argument ustawia podrzędną **kolumnę**danych.  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 **Relacja** danych ma również **zagnieżdżoną** właściwość, która po ustawieniu na **wartość true**powoduje, że wiersze z tabeli podrzędnej będą zagnieżdżone w skojarzonym wierszu z tabeli nadrzędnej, gdy są zapisywane jako elementy <xref:System.Data.DataSet.WriteXml%2A> XML przy użyciu. Aby uzyskać więcej informacji, zobacz [Używanie języka XML w zestawie danych](using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
