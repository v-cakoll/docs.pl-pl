---
title: Tworzenie elementu DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: cb39ead1fe15e3bfcf67370e4675dcae3bbf9801
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203897"
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
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
