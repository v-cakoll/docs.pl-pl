---
title: Tworzenie kolumn wyrażeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 11bacf436daf2a77a9cf46b4883d282143572e27
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="creating-expression-columns"></a>Tworzenie kolumn wyrażeń
Wyrażenie dla kolumny można zdefiniować, umożliwiając zawierać wartość obliczana z innych wartości kolumn, w tym samym wierszu lub wartości w kolumnie wielu wierszy w tabeli. Aby zdefiniować wyrażenie, które ma zostać obliczone, należy użyć <xref:System.Data.DataColumn.Expression%2A> właściwość kolumny docelowej i użyj <xref:System.Data.DataColumn.ColumnName%2A> właściwości do odwoływania się do kolumn w wyrażeniu. <xref:System.Data.DataColumn.DataType%2A> Dla wyrażenia musi być zgodna wartość, która zwraca wyrażenie kolumny.  
  
 W poniższej tabeli wymieniono kilka możliwych zastosowań dla kolumny wyrażenia w tabeli.  
  
|Typ wyrażenia|Przykład|  
|---------------------|-------------|  
|Porównanie|"Całkowita > = 500"|  
|Obliczenia|"UnitPrice * ilość"|  
|Agregacji|Sum(price)|  
  
 Można ustawić **wyrażenie** właściwości na istniejącym **DataColumn** obiekt, lub można dodać właściwość jako trzeci argument przekazany do <xref:System.Data.DataColumn> konstruktora, jak pokazano w poniższym przykładzie.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 Wyrażenia mogą odwoływać się do innych kolumn wyrażenie; Jednak odwołanie cykliczne, w którym dwóch wyrażeń zależą od siebie, zostanie wygenerowany wyjątek. W przypadku reguł dotyczących wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość **DataColumn** klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
