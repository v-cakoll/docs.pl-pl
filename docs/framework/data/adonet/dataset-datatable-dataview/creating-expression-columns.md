---
title: Tworzenie kolumn wyrażeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 9c7a656e82198568c39b9bb58f8708f563d6caa2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520830"
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
