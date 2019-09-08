---
title: Tworzenie elementu DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 79cb2ce7ffae81aeba9aaca557e37ba566a8370c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784767"
---
# <a name="creating-a-datareader"></a>Tworzenie elementu DataReader
<xref:System.Data.DataTable> <xref:System.Data.DataSet.Tables%2A> Klasy i <xref:System.Data.DataSet>mają metodę<xref:System.Data.DataTable.CreateDataReader%2A> , która zwraca<xref:System.Data.DataSet> zawartość lub zawartość kolekcji obiektu jako co najmniej jeden zestaw wyników tylko do odczytu. <xref:System.Data.DataTable>  
  
## <a name="example"></a>Przykład  
 Następująca aplikacja konsolowa tworzy <xref:System.Data.DataTable> wystąpienie. Następnie przykład przekazuje wypełniony <xref:System.Data.DataTable> do procedury, która <xref:System.Data.DataTable.CreateDataReader%2A> wywołuje metodę, która wykonuje iterację przez wyniki zawarte w <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 W przykładzie są wyświetlane następujące dane wyjściowe w oknie konsoli:  
  
```  
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
