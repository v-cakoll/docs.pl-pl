---
title: 'Instrukcje: Określanie, kiedy są zgłaszane wyjątki współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 30dd83c68472ecd3244cfc87b6df97b948b9a84f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033634"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="0d4e8-102">Instrukcje: Określanie, kiedy są zgłaszane wyjątki współbieżności</span><span class="sxs-lookup"><span data-stu-id="0d4e8-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="0d4e8-103">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy obiekty nie są uaktualniane z powodu konfliktów optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="0d4e8-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="0d4e8-104">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0d4e8-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="0d4e8-105">Przed przesłaniem zmian do bazy danych można określić podczas powinny zostać zgłoszone wyjątki współbieżności:</span><span class="sxs-lookup"><span data-stu-id="0d4e8-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="0d4e8-106">Zgłoszenie wyjątku w pierwszym niepowodzeniu (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="0d4e8-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="0d4e8-107">Zakończenie wszystkich prób aktualizacji, są gromadzone wszystkie błędy i zgłaszać narastająco błędy w wyjątku (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="0d4e8-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="0d4e8-108">Jeśli zgłoszony, <xref:System.Data.Linq.ChangeConflictException> wyjątek zapewnia dostęp do <xref:System.Data.Linq.ChangeConflictCollection> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0d4e8-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="0d4e8-109">Ta kolekcja zawiera szczegółowe informacje dla wszystkich konfliktów (mapowane na blok try jednej aktualizacji nie powiodło się), łącznie z dostępem do <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0d4e8-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="0d4e8-110">Każdy konflikt składowej jest mapowany na jeden element członkowski w aktualizacji, który uległ awarii sprawdzania współbieżności.</span><span class="sxs-lookup"><span data-stu-id="0d4e8-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d4e8-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d4e8-111">Example</span></span>  
 <span data-ttu-id="0d4e8-112">Poniższy kod przedstawia przykładowe obu wartości.</span><span class="sxs-lookup"><span data-stu-id="0d4e8-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0d4e8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d4e8-113">See also</span></span>

- [<span data-ttu-id="0d4e8-114">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="0d4e8-114">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="0d4e8-115">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="0d4e8-115">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
