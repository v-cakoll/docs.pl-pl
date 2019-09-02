---
title: Tworzenie elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 19badb009ebe95c52ab1dbbaef96f280c769553b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205155"
---
# <a name="creating-a-dataset"></a>Tworzenie elementu DataSet
Można utworzyć wystąpienie <xref:System.Data.DataSet> obiektu przez <xref:System.Data.DataSet> wywołanie konstruktora. Opcjonalnie można określić argument nazwy. Jeśli nie określisz nazwy dla <xref:System.Data.DataSet>, nazwa zostanie ustawiona na "NewDataSet".  
  
 Możesz również utworzyć nowy <xref:System.Data.DataSet> oparty na istniejącym. <xref:System.Data.DataSet> <xref:System.Data.DataSet> Nowy może być dokładną kopią istniejącej <xref:System.Data.DataSet> <xref:System.Data.DataSet> ; klon, który kopiuje strukturę relacyjną lub schemat <xref:System.Data.DataSet>, ale nie zawiera żadnych danych z istniejącego <xref:System.Data.DataSet>lub podzestawu, zawierający tylko zmodyfikowane wiersze z istniejących <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> przy użyciu metody. Aby uzyskać więcej informacji, zobacz [kopiowanie zawartości zestawu danych](copying-dataset-contents.md).  
  
 Poniższy przykład kodu demonstruje sposób konstruowania wystąpienia <xref:System.Data.DataSet>obiektu.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Zobacz także

- [Wypełnianie zestawu danych z elementu DataAdapter](../populating-a-dataset-from-a-dataadapter.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
