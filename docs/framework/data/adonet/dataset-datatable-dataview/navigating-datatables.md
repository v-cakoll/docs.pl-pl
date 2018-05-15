---
title: Nawigowanie po DataTables
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 3bd10694512e828354254588361cc009aac6602f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="navigating-datatables"></a><span data-ttu-id="97490-102">Nawigowanie po DataTables</span><span class="sxs-lookup"><span data-stu-id="97490-102">Navigating DataTables</span></span>
<span data-ttu-id="97490-103"><xref:System.Data.DataTableReader> Uzyskuje zawartość jednego lub więcej <xref:System.Data.DataTable> obiekty w postaci jednego lub więcej zestawów wyników tylko do odczytu, tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="97490-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="97490-104">A <xref:System.Data.DataTableReader> może zawierać wiele zestawów wyników, jeśli jest tworzona przy użyciu <xref:System.Data.DataSet.CreateDataReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="97490-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="97490-105">Jeśli istnieje więcej niż jeden zestaw wyników, <xref:System.Data.DataTableReader.NextResult%2A> metody przesuwa kursor do następnego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="97490-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="97490-106">Jest to proces tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="97490-106">This is a forward-only process.</span></span> <span data-ttu-id="97490-107">Nie jest możliwe powrócić do poprzedniego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="97490-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97490-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="97490-108">Example</span></span>  
 <span data-ttu-id="97490-109">W poniższym przykładzie `TestConstructor` metoda tworzy dwa <xref:System.Data.DataTable> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="97490-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="97490-110">W celu zaprezentowania tego konstruktora dla <xref:System.Data.DataTableReader> klasy, tworzy nową próbkę **Element DataTableReader** na podstawie tablicy, która zawiera dwa **DataTables**i wykonuje operację proste Drukowanie zawartości z pierwszego kilka kolumn, w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="97490-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="97490-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97490-111">See Also</span></span>  
 [<span data-ttu-id="97490-112">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="97490-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="97490-113">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="97490-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
