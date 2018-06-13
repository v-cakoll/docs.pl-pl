---
title: Tworzenie elementu DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: c5073a553926fdfdd78b0b6837cdc07b58ac7faf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755516"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="9a4c3-102">Tworzenie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="9a4c3-102">Creating a DataReader</span></span>
<span data-ttu-id="9a4c3-103"><xref:System.Data.DataTable> i <xref:System.Data.DataSet> klasy mają <xref:System.Data.DataTable.CreateDataReader%2A> metodę, która zwraca zawartość <xref:System.Data.DataTable> lub zawartość <xref:System.Data.DataSet> obiektu <xref:System.Data.DataSet.Tables%2A> kolekcji jako jeden lub więcej zestawów wyników tylko do odczytu, tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="9a4c3-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a4c3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a4c3-104">Example</span></span>  
 <span data-ttu-id="9a4c3-105">Tworzy następującej aplikacji konsoli <xref:System.Data.DataTable> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9a4c3-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="9a4c3-106">Przykład następnie przekazuje wypełniony <xref:System.Data.DataTable> do procedury, która wywołuje <xref:System.Data.DataTable.CreateDataReader%2A> metodę, która iterację w wynikach zawartych w <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="9a4c3-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="9a4c3-107">W przykładzie przedstawiono następujące wyniki w oknie konsoli:</span><span class="sxs-lookup"><span data-stu-id="9a4c3-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a4c3-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a4c3-108">See Also</span></span>  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [<span data-ttu-id="9a4c3-109">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="9a4c3-109">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="9a4c3-110">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="9a4c3-110">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
