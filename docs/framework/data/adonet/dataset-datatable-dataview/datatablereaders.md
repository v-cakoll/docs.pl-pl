---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 9984dc9c215a34ab35524560e4dcbcd6bd12596d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602848"
---
# <a name="datatablereaders"></a><span data-ttu-id="d05ab-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="d05ab-102">DataTableReaders</span></span>
<span data-ttu-id="d05ab-103"><xref:System.Data.DataTableReader> Przedstawia zawartość <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> w postaci co najmniej jeden wynik tylko do odczytu, tylko do przodu ustawia.</span><span class="sxs-lookup"><span data-stu-id="d05ab-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="d05ab-104">Po utworzeniu **elementu DataTableReader** z **DataTable**, wynikowy **elementu DataTableReader** obiekt zawiera jeden zestaw wyników z tych samych danych co  **DataTable** z której została utworzona, z wyjątkiem wszystkich wierszy, które zostały oznaczone jako usunięte.</span><span class="sxs-lookup"><span data-stu-id="d05ab-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="d05ab-105">Kolumny są wyświetlane w tej samej kolejności jak w oryginalnym **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="d05ab-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="d05ab-106">A **elementu DataTableReader** może zawierać wiele zestawów wyników, jeśli został utworzony przez wywołanie metody <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="d05ab-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="d05ab-107">Wyniki są w tej samej kolejności jak **DataTables** w **DataSet** obiektu <xref:System.Data.DataSet.Tables%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d05ab-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d05ab-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d05ab-108">In This Section</span></span>  
 [<span data-ttu-id="d05ab-109">Tworzenie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="d05ab-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="d05ab-110">W tym artykule omówiono sposób tworzenia **elementu DataTableReader** obiektu.</span><span class="sxs-lookup"><span data-stu-id="d05ab-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="d05ab-111">Nawigowanie w elementach DataTable</span><span class="sxs-lookup"><span data-stu-id="d05ab-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="d05ab-112">W tym artykule opisano korzystanie z **odczytu** metodę, aby przeglądać zawartość **elementu DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="d05ab-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d05ab-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d05ab-113">See also</span></span>
- [<span data-ttu-id="d05ab-114">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d05ab-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="d05ab-115">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d05ab-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
