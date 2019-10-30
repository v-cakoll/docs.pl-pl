---
title: Tworzenie elementu DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 696eb4dfc334390e1968dd317d441f3c987a1f77
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040107"
---
# <a name="creating-a-datareader"></a>Tworzenie elementu DataReader
Klasy <xref:System.Data.DataTable> i <xref:System.Data.DataSet> mają metodę <xref:System.Data.DataTable.CreateDataReader%2A>, która zwraca zawartość <xref:System.Data.DataTable> lub zawartość kolekcji <xref:System.Data.DataSet> obiektu <xref:System.Data.DataSet.Tables%2A> jako co najmniej jeden zestaw wyników tylko do odczytu.  
  
## <a name="example"></a>Przykład  
 Następująca aplikacja konsolowa tworzy wystąpienie <xref:System.Data.DataTable>. Przykład przekazuje wypełniony <xref:System.Data.DataTable> do procedury, która wywołuje metodę <xref:System.Data.DataTable.CreateDataReader%2A>, która wykonuje iterację w wynikach zawartych w <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 W przykładzie są wyświetlane następujące dane wyjściowe w oknie konsoli:  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [Elementy DataTableReader](datatablereaders.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
