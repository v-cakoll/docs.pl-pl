---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: b3881ecfd895bd22a476bdac7dd0b7c1b112092e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425188"
---
# <a name="datatablereaders"></a><span data-ttu-id="3af02-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="3af02-102">DataTableReaders</span></span>
<span data-ttu-id="3af02-103"><xref:System.Data.DataTableReader> Przedstawia zawartość <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> w postaci co najmniej jeden wynik tylko do odczytu, tylko do przodu ustawia.</span><span class="sxs-lookup"><span data-stu-id="3af02-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="3af02-104">Po utworzeniu **elementu DataTableReader** z **DataTable**, wynikowy **elementu DataTableReader** obiekt zawiera jeden zestaw wyników z tych samych danych co  **DataTable** z której została utworzona, z wyjątkiem wszystkich wierszy, które zostały oznaczone jako usunięte.</span><span class="sxs-lookup"><span data-stu-id="3af02-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="3af02-105">Kolumny są wyświetlane w tej samej kolejności jak w oryginalnym **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3af02-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="3af02-106">A **elementu DataTableReader** może zawierać wiele zestawów wyników, jeśli został utworzony przez wywołanie metody <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="3af02-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="3af02-107">Wyniki są w tej samej kolejności jak **DataTables** w **DataSet** obiektu <xref:System.Data.DataSet.Tables%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3af02-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3af02-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3af02-108">In This Section</span></span>  
 [<span data-ttu-id="3af02-109">Tworzenie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="3af02-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="3af02-110">W tym artykule omówiono sposób tworzenia **elementu DataTableReader** obiektu.</span><span class="sxs-lookup"><span data-stu-id="3af02-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="3af02-111">Nawigowanie w elementach DataTable</span><span class="sxs-lookup"><span data-stu-id="3af02-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="3af02-112">W tym artykule opisano korzystanie z **odczytu** metodę, aby przeglądać zawartość **elementu DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="3af02-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af02-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3af02-113">See Also</span></span>  
 [<span data-ttu-id="3af02-114">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3af02-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="3af02-115">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="3af02-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
