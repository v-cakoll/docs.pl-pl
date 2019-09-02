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
# <a name="creating-a-datareader"></a><span data-ttu-id="2949f-102">Tworzenie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="2949f-102">Creating a DataReader</span></span>
<span data-ttu-id="2949f-103"><xref:System.Data.DataTable> <xref:System.Data.DataSet.Tables%2A> Klasy i <xref:System.Data.DataSet>mają metodę<xref:System.Data.DataTable.CreateDataReader%2A> , która zwraca<xref:System.Data.DataSet> zawartość lub zawartość kolekcji obiektu jako co najmniej jeden zestaw wyników tylko do odczytu. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="2949f-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2949f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2949f-104">Example</span></span>  
 <span data-ttu-id="2949f-105">Następująca aplikacja konsolowa tworzy <xref:System.Data.DataTable> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="2949f-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="2949f-106">Następnie przykład przekazuje wypełniony <xref:System.Data.DataTable> do procedury, która <xref:System.Data.DataTable.CreateDataReader%2A> wywołuje metodę, która wykonuje iterację przez wyniki zawarte w <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="2949f-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="2949f-107">W przykładzie są wyświetlane następujące dane wyjściowe w oknie konsoli:</span><span class="sxs-lookup"><span data-stu-id="2949f-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="2949f-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2949f-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="2949f-109">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="2949f-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="2949f-110">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2949f-110">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
