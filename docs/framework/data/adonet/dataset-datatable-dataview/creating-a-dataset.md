---
title: Tworzenie elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d496167b7bce31491402414c43ae0bcdee423b89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786504"
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
- [Omówienie ADO.NET](../ado-net-overview.md)
