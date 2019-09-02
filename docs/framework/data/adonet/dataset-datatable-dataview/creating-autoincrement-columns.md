---
title: Tworzenie kolumn typu AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 2548ad9382b406978dac0a3d366207626278f501
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205131"
---
# <a name="creating-autoincrement-columns"></a>Tworzenie kolumn typu AutoIncrement
Aby zapewnić unikatowe wartości kolumn, można ustawić wartości kolumn, które mają być zwiększane automatycznie po dodaniu nowych wierszy do tabeli. Aby utworzyć funkcję autozwiększania <xref:System.Data.DataColumn>, <xref:System.Data.DataColumn.AutoIncrement%2A> ustaw właściwość kolumny na **true**. Następnie rozpoczyna się od wartości zdefiniowanej <xref:System.Data.DataColumn.AutoIncrementSeed%2A> we właściwości, a każdy wiersz dodaliśmy wartość kolumny **AutoIncrement** <xref:System.Data.DataColumn.AutoIncrementStep%2A> zwiększa się o wartość zdefiniowaną we właściwości kolumny. <xref:System.Data.DataColumn>  
  
 W przypadku kolumn typu **AutoIncrement** <xref:System.Data.DataColumn.ReadOnly%2A> zalecamy, aby właściwość **DataColumn** była ustawiona na **wartość true**.  
  
 W poniższym przykładzie pokazano, jak utworzyć kolumnę rozpoczynającą się od wartości 200 i dodać przyrostowo w krokach 3.  
  
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
- [Definicja schematu elementu DataTable](datatable-schema-definition.md)
- [Elementy DataTable](datatables.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
