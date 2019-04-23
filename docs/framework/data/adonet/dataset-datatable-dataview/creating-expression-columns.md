---
title: Tworzenie kolumn wyrażeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 6e19e4e7cc0ea92e9d93e45c2a50d009e46b78c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175503"
---
# <a name="creating-expression-columns"></a>Tworzenie kolumn wyrażeń
Można zdefiniować wyrażenie dla kolumny, dzięki czemu może zawierać wartość obliczana z innych wartości kolumn, w tym samym wierszu lub wartości w kolumnach wiele wierszy w tabeli. Aby określić wyrażenie, które ma zostać obliczone, użyj <xref:System.Data.DataColumn.Expression%2A> właściwość kolumna docelowa i użyj <xref:System.Data.DataColumn.ColumnName%2A> właściwości do odwoływania się do innych kolumn w wyrażeniu. <xref:System.Data.DataColumn.DataType%2A> Wyrażenia kolumny musi być zgodna wartość, która zwraca wartość wyrażenia.  
  
 Poniższa tabela zawiera listę kilku możliwych zastosowań wyrażenie kolumny w tabeli.  
  
|Typ wyrażenia|Przykład|  
|---------------------|-------------|  
|Porównanie|"Całkowitą > = 500"|  
|Obliczenie|"UnitPrice * Quantity"|  
|Agregacji|Sum(price)|  
  
 Możesz ustawić **wyrażenie** właściwości na istniejącym **DataColumn** obiektu lub mogą one obejmować właściwość trzeci argument przekazany do <xref:System.Data.DataColumn> konstruktora, jak pokazano w poniższym przykładzie.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 Wyrażenia mogą odwoływać się do innych kolumn wyrażenie; Jednak odwołanie cykliczne, w którym dwóch wyrażeń odwoływać się do siebie nawzajem, spowoduje wygenerowanie wyjątku. Reguły dotyczące wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość **DataColumn** klasy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
