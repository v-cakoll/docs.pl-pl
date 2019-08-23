---
title: 'Instrukcje: Rozwiązywanie konfliktów z zastąpieniem wartości bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: f6721234d2d3920343bc72889c7683fb6ee662a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928759"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="85064-102">Instrukcje: Rozwiązywanie konfliktów z zastąpieniem wartości bazy danych</span><span class="sxs-lookup"><span data-stu-id="85064-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="85064-103">Aby uzgodnić różnice między oczekiwanymi i rzeczywistymi wartościami bazy danych przed próbą ponownego przesłania zmian, można użyć <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> do zastępowania wartości bazy danych.</span><span class="sxs-lookup"><span data-stu-id="85064-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="85064-104">Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="85064-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85064-105">We wszystkich przypadkach rekord na kliencie jest najpierw odświeżany przez pobranie zaktualizowanych danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="85064-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="85064-106">Ta akcja zapewnia, że kolejna próba aktualizacji nie powiedzie się na tych samych kontrolach współbieżności.</span><span class="sxs-lookup"><span data-stu-id="85064-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85064-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="85064-107">Example</span></span>  
 <span data-ttu-id="85064-108">W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy Użytkownik1 próbuje przesłać zmiany, ponieważ w międzyczasie została zmieniona kolumna asystenta i działu.</span><span class="sxs-lookup"><span data-stu-id="85064-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="85064-109">W poniższej tabeli przedstawiono sytuację.</span><span class="sxs-lookup"><span data-stu-id="85064-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="85064-110">maszyny wirtualnej</span><span class="sxs-lookup"><span data-stu-id="85064-110">Manager</span></span>|<span data-ttu-id="85064-111">Pomocnik</span><span class="sxs-lookup"><span data-stu-id="85064-111">Assistant</span></span>|<span data-ttu-id="85064-112">Dział</span><span class="sxs-lookup"><span data-stu-id="85064-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="85064-113">Oryginalny stan bazy danych podczas wykonywania zapytania przez Użytkownik1 i.</span><span class="sxs-lookup"><span data-stu-id="85064-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="85064-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="85064-114">Alfreds</span></span>|<span data-ttu-id="85064-115">Maria</span><span class="sxs-lookup"><span data-stu-id="85064-115">Maria</span></span>|<span data-ttu-id="85064-116">Sprzedaż</span><span class="sxs-lookup"><span data-stu-id="85064-116">Sales</span></span>|  
|<span data-ttu-id="85064-117">Użytkownik1 przygotowuje się do przesłania tych zmian.</span><span class="sxs-lookup"><span data-stu-id="85064-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="85064-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="85064-118">Alfred</span></span>||<span data-ttu-id="85064-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="85064-119">Marketing</span></span>|  
|<span data-ttu-id="85064-120">Do tego celu zostały już przesłane te zmiany.</span><span class="sxs-lookup"><span data-stu-id="85064-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="85064-121">Anna</span><span class="sxs-lookup"><span data-stu-id="85064-121">Mary</span></span>|<span data-ttu-id="85064-122">Usługa</span><span class="sxs-lookup"><span data-stu-id="85064-122">Service</span></span>|  
  
 <span data-ttu-id="85064-123">Użytkownik1 decyduje się rozwiązać ten konflikt przez zastąpienie wartości bazy danych bieżącymi wartościami członków klienta.</span><span class="sxs-lookup"><span data-stu-id="85064-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="85064-124">Gdy Użytkownik1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, wynik w bazie danych jest jak w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="85064-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="85064-125">maszyny wirtualnej</span><span class="sxs-lookup"><span data-stu-id="85064-125">Manager</span></span>|<span data-ttu-id="85064-126">Pomocnik</span><span class="sxs-lookup"><span data-stu-id="85064-126">Assistant</span></span>|<span data-ttu-id="85064-127">Dział</span><span class="sxs-lookup"><span data-stu-id="85064-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="85064-128">Nowy stan po rozwiązaniu konfliktu.</span><span class="sxs-lookup"><span data-stu-id="85064-128">New state after conflict resolution.</span></span>|<span data-ttu-id="85064-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="85064-129">Alfred</span></span><br /><br /> <span data-ttu-id="85064-130">(od Użytkownik1)</span><span class="sxs-lookup"><span data-stu-id="85064-130">(from User1)</span></span>|<span data-ttu-id="85064-131">Maria</span><span class="sxs-lookup"><span data-stu-id="85064-131">Maria</span></span><br /><br /> <span data-ttu-id="85064-132">oryginalnego</span><span class="sxs-lookup"><span data-stu-id="85064-132">(original)</span></span>|<span data-ttu-id="85064-133">Marketing</span><span class="sxs-lookup"><span data-stu-id="85064-133">Marketing</span></span><br /><br /> <span data-ttu-id="85064-134">(od Użytkownik1)</span><span class="sxs-lookup"><span data-stu-id="85064-134">(from User1)</span></span>|  
  
 <span data-ttu-id="85064-135">Poniższy przykładowy kod pokazuje, jak zastąpić wartości bazy danych z bieżącymi wartościami członków klienta.</span><span class="sxs-lookup"><span data-stu-id="85064-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="85064-136">(Żadna Inspekcja lub Niestandardowa obsługa konfliktów poszczególnych członków nie występuje).</span><span class="sxs-lookup"><span data-stu-id="85064-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="85064-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85064-137">See also</span></span>

- [<span data-ttu-id="85064-138">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="85064-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
