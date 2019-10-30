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
# <a name="creating-a-datareader"></a><span data-ttu-id="f8c9b-102">Tworzenie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="f8c9b-102">Creating a DataReader</span></span>
<span data-ttu-id="f8c9b-103">Klasy <xref:System.Data.DataTable> i <xref:System.Data.DataSet> mają metodę <xref:System.Data.DataTable.CreateDataReader%2A>, która zwraca zawartość <xref:System.Data.DataTable> lub zawartość kolekcji <xref:System.Data.DataSet> obiektu <xref:System.Data.DataSet.Tables%2A> jako co najmniej jeden zestaw wyników tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8c9b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8c9b-104">Example</span></span>  
 <span data-ttu-id="f8c9b-105">Następująca aplikacja konsolowa tworzy wystąpienie <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="f8c9b-106">Przykład przekazuje wypełniony <xref:System.Data.DataTable> do procedury, która wywołuje metodę <xref:System.Data.DataTable.CreateDataReader%2A>, która wykonuje iterację w wynikach zawartych w <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="f8c9b-107">W przykładzie są wyświetlane następujące dane wyjściowe w oknie konsoli:</span><span class="sxs-lookup"><span data-stu-id="f8c9b-107">The example displays the following output in the console window:</span></span>  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8c9b-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8c9b-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="f8c9b-109">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="f8c9b-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="f8c9b-110">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f8c9b-110">ADO.NET Overview</span></span>](../ado-net-overview.md)
