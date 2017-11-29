---
title: DataTableReaders
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ed9094a036262bac2e101e7b4268aac2e66a0d10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="datatablereaders"></a><span data-ttu-id="3dc8e-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="3dc8e-102">DataTableReaders</span></span>
<span data-ttu-id="3dc8e-103"><xref:System.Data.DataTableReader> Przedstawia informacje o zawartości <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> w formie co najmniej jeden wynik tylko do odczytu, tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="3dc8e-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="3dc8e-104">Po utworzeniu **Element DataTableReader** z **DataTable**, powstałe w ten sposób **Element DataTableReader** obiekt zawiera jeden zestaw danych o tej samej jako wyników  **Element DataTable** z którego został utworzony, z wyjątkiem wszystkie wiersze, które zostały oznaczone jako usunięte.</span><span class="sxs-lookup"><span data-stu-id="3dc8e-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="3dc8e-105">Kolumny pojawiają się w tej samej kolejności jak w oryginalnym **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3dc8e-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="3dc8e-106">A **Element DataTableReader** może zawierać wiele zestawów wyników, jeśli została utworzona przez wywołanie metody <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="3dc8e-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="3dc8e-107">Wyniki są w tej samej kolejności jak **DataTables** w **DataSet** obiektu <xref:System.Data.DataSet.Tables%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3dc8e-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3dc8e-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3dc8e-108">In This Section</span></span>  
 [<span data-ttu-id="3dc8e-109">Tworzenie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="3dc8e-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="3dc8e-110">W tym artykule omówiono sposób tworzenia **Element DataTableReader** obiektu.</span><span class="sxs-lookup"><span data-stu-id="3dc8e-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="3dc8e-111">Nawigowanie po DataTables</span><span class="sxs-lookup"><span data-stu-id="3dc8e-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="3dc8e-112">Opisuje **odczytu** metody, aby przeglądać zawartość **Element DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="3dc8e-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc8e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dc8e-113">See Also</span></span>  
 [<span data-ttu-id="3dc8e-114">Trwa pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3dc8e-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="3dc8e-115">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="3dc8e-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
