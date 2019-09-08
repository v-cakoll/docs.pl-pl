---
title: Elementy DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785344"
---
# <a name="datatablereaders"></a><span data-ttu-id="0a8c8-102">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="0a8c8-102">DataTableReaders</span></span>
<span data-ttu-id="0a8c8-103">Przedstawia zawartość a <xref:System.Data.DataTable> lub a <xref:System.Data.DataSet> w postaci co najmniej jednego zestawu wyników tylko do odczytu. <xref:System.Data.DataTableReader></span><span class="sxs-lookup"><span data-stu-id="0a8c8-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="0a8c8-104">Po utworzeniu **DataTableReader** z **tabeli DataTable**wynikowy obiekt **DataTableReader** zawiera jeden zestaw wyników z tymi samymi danymi co element **DataTable** , z którego został utworzony, z wyjątkiem wierszy, które zostały oznaczone jako skasowan.</span><span class="sxs-lookup"><span data-stu-id="0a8c8-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="0a8c8-105">Kolumny są wyświetlane w takiej samej kolejności jak w oryginalnej **tabeli DataTable**.</span><span class="sxs-lookup"><span data-stu-id="0a8c8-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="0a8c8-106">**DataTableReader** może zawierać wiele zestawów wyników, jeśli został utworzony przez wywołanie <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a8c8-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="0a8c8-107">Wyniki znajdują się w takiej samej kolejności jak w **tabelach** **danych** w <xref:System.Data.DataSet.Tables%2A> kolekcji obiektów DataSet.</span><span class="sxs-lookup"><span data-stu-id="0a8c8-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a8c8-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0a8c8-108">In This Section</span></span>  
 [<span data-ttu-id="0a8c8-109">Tworzenie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="0a8c8-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="0a8c8-110">W tym artykule omówiono sposób tworzenia obiektu **DataTableReader** .</span><span class="sxs-lookup"><span data-stu-id="0a8c8-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="0a8c8-111">Nawigowanie w elementach DataTable</span><span class="sxs-lookup"><span data-stu-id="0a8c8-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="0a8c8-112">Opisuje użycie metody **Read** , aby przejść przez zawartość **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="0a8c8-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8c8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a8c8-113">See also</span></span>

- [<span data-ttu-id="0a8c8-114">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0a8c8-114">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="0a8c8-115">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0a8c8-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
