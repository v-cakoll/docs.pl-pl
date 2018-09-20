---
title: Nawigowanie w elementach DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: f00e2171c1adf4ff99a669085131ebc8d38f7006
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46322978"
---
# <a name="navigating-datatables"></a><span data-ttu-id="51abe-102">Nawigowanie w elementach DataTable</span><span class="sxs-lookup"><span data-stu-id="51abe-102">Navigating DataTables</span></span>
<span data-ttu-id="51abe-103"><xref:System.Data.DataTableReader> Uzyskuje zawartość jednego lub więcej <xref:System.Data.DataTable> obiektów w postaci jednego lub więcej zestawów wyników tylko do odczytu, tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="51abe-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="51abe-104">A <xref:System.Data.DataTableReader> może zawierać wiele zestawów wyników, jeśli jest tworzona przy użyciu <xref:System.Data.DataSet.CreateDataReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="51abe-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="51abe-105">Jeśli istnieje więcej niż jeden zestaw wyników, <xref:System.Data.DataTableReader.NextResult%2A> metoda przesuwa kursor do następnego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="51abe-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="51abe-106">Jest to proces tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="51abe-106">This is a forward-only process.</span></span> <span data-ttu-id="51abe-107">Nie jest możliwe powrócić do poprzedniego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="51abe-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51abe-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="51abe-108">Example</span></span>  
 <span data-ttu-id="51abe-109">W poniższym przykładzie `TestConstructor` metoda tworzy dwa <xref:System.Data.DataTable> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="51abe-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="51abe-110">W celu przedstawienia tej Konstruktor <xref:System.Data.DataTableReader> klasy Przykładowa aplikacja tworzy nową **elementu DataTableReader** na podstawie tablicy, która zawiera dwa **DataTables**i wykonuje prostą operacją Drukowanie zawartości z pierwszego mało kolumn w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="51abe-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="51abe-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51abe-111">See Also</span></span>  
 [<span data-ttu-id="51abe-112">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="51abe-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="51abe-113">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="51abe-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
