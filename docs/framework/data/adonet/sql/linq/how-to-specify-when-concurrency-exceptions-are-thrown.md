---
title: 'Instrukcje: Określanie, kiedy są zgłaszane wyjątki współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: c0f41d23264bbe5c9130cb5a0b03686331bc92b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781621"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="043cb-102">Instrukcje: Określanie, kiedy są zgłaszane wyjątki współbieżności</span><span class="sxs-lookup"><span data-stu-id="043cb-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="043cb-103">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy obiekty nie są aktualizowane z powodu nieoptymistycznych konfliktów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="043cb-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="043cb-104">Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="043cb-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="043cb-105">Przed przesłaniem zmian do bazy danych można określić, kiedy mają być zgłaszane wyjątki współbieżności:</span><span class="sxs-lookup"><span data-stu-id="043cb-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="043cb-106">Zgłoś wyjątek przy pierwszym błędzie (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="043cb-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="043cb-107">Zakończ wszystkie próby aktualizacji, zakumulowanie wszystkich błędów i Zgłoś błędy skumulowane w wyjątku (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="043cb-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="043cb-108">Gdy zostanie <xref:System.Data.Linq.ChangeConflictException> zgłoszony, wyjątek zapewnia dostęp <xref:System.Data.Linq.ChangeConflictCollection> do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="043cb-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="043cb-109">Ta kolekcja zawiera szczegółowe informacje dotyczące każdego konfliktu (zamapowane do pojedynczej nieudanej aktualizacji), w tym <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> dostęp do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="043cb-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="043cb-110">Konflikty każdego elementu członkowskiego są mapowane na pojedynczy element członkowski w aktualizacji, która nie mogła sprawdzić współbieżności.</span><span class="sxs-lookup"><span data-stu-id="043cb-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="043cb-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="043cb-111">Example</span></span>  
 <span data-ttu-id="043cb-112">Poniższy kod przedstawia przykłady obu wartości.</span><span class="sxs-lookup"><span data-stu-id="043cb-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="043cb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="043cb-113">See also</span></span>

- [<span data-ttu-id="043cb-114">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="043cb-114">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="043cb-115">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="043cb-115">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
