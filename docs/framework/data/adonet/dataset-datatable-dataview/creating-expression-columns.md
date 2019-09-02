---
title: Tworzenie kolumn wyrażeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 8ae8c8e020a3d8ada5bdcd5037187e6f3abd33a4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203833"
---
# <a name="creating-expression-columns"></a>Tworzenie kolumn wyrażeń
Można zdefiniować wyrażenie dla kolumny, aby zawierało wartość obliczoną na podstawie innych wartości kolumn w tym samym wierszu lub z wartości kolumn obejmujących wiele wierszy w tabeli. Aby zdefiniować wyrażenie do obliczenia, użyj <xref:System.Data.DataColumn.Expression%2A> właściwości kolumny Target i <xref:System.Data.DataColumn.ColumnName%2A> Użyj właściwości, aby odwołać się do innych kolumn w wyrażeniu. Kolumna <xref:System.Data.DataColumn.DataType%2A> dla wyrażenia musi być odpowiednia dla wartości zwracanej przez wyrażenie.  
  
 W poniższej tabeli przedstawiono kilka możliwych zastosowania kolumn wyrażeń w tabeli.  
  
|Typ wyrażenia|Przykład|  
|---------------------|-------------|  
|Porównanie|"Łącznie > = 500"|  
|Obliczeń|"CenaJednostkowa * ilooć"|  
|Agregacja|Sum (cena)|  
  
 Można ustawić właściwość **Expression** w istniejącym obiekcie DataColumn lub dodać właściwość jako trzeci argument do <xref:System.Data.DataColumn> konstruktora, jak pokazano w poniższym przykładzie.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 Wyrażenia mogą odwoływać się do innych kolumn wyrażeń; jednak odwołanie cykliczne, w którym dwa wyrażenia odwołuje się nawzajem, wygeneruje wyjątek. Aby uzyskać reguły dotyczące pisania wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość klasy DataColumn.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Definicja schematu elementu DataTable](datatable-schema-definition.md)
- [Elementy DataTable](datatables.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
