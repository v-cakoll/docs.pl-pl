---
title: Tworzenie kolumn typu AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: b4beffb3c5072e9eaa398e7433b363babadbb9eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528644"
---
# <a name="creating-autoincrement-columns"></a>Tworzenie kolumn typu AutoIncrement
Aby zapewnić unikatową kolumnę wartości, można ustawić wartości kolumn, aby zwiększyć automatycznie po dodaniu nowych wierszy w tabeli. Do utworzenia, zwiększając automatycznie <xref:System.Data.DataColumn>ustaw <xref:System.Data.DataColumn.AutoIncrement%2A> właściwości kolumny, która ma **true**. <xref:System.Data.DataColumn> Następnie rozpoczyna się od wartości zdefiniowanej w <xref:System.Data.DataColumn.AutoIncrementSeed%2A> właściwości i z każdego wiersza dodano wartość **AutoIncrement** zwiększa wartość zdefiniowana w kolumnie <xref:System.Data.DataColumn.AutoIncrementStep%2A> właściwości kolumny.  
  
 Dla **AutoIncrement** kolumn, zaleca się <xref:System.Data.DataColumn.ReadOnly%2A> właściwość **DataColumn** można ustawić **true**.  
  
 Poniższy przykład przedstawia sposób tworzenia kolumny, która rozpoczyna się o wartości 200 i dodaje stopniowo w krokach 3.  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Data.DataColumn>
- [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
