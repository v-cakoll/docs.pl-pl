---
title: 'Instrukcje: Rozwiązywanie konfliktów, zastępując wartości bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 38129996949bcfbd938038743897d1db5910fdfe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653908"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="514b0-102">Instrukcje: Rozwiązywanie konfliktów, zastępując wartości bazy danych</span><span class="sxs-lookup"><span data-stu-id="514b0-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="514b0-103">Aby uzgodnić różnice między wartościami oczekiwanymi i rzeczywistymi bazy danych, zanim spróbujesz ponownie prześlij zmiany, możesz użyć <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> zastąpić wartości bazy danych.</span><span class="sxs-lookup"><span data-stu-id="514b0-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="514b0-104">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="514b0-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="514b0-105">We wszystkich przypadkach rekordu na komputerze klienckim najpierw są odświeżane poprzez pobranie zaktualizowanych danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="514b0-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="514b0-106">Ta akcja gwarantuje, że następnej próbie aktualizacji zakończy się niepowodzeniem na tych samych kontroli współbieżności.</span><span class="sxs-lookup"><span data-stu-id="514b0-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="514b0-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="514b0-107">Example</span></span>  
 <span data-ttu-id="514b0-108">W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy użytkownik User1 próbuje przesłać zmiany, ponieważ użytkownik2, w tym samym czasie została zmieniona kolumny Asystenta ustawień i działu.</span><span class="sxs-lookup"><span data-stu-id="514b0-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="514b0-109">W poniższej tabeli przedstawiono tę sytuację.</span><span class="sxs-lookup"><span data-stu-id="514b0-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="514b0-110">maszyny wirtualnej</span><span class="sxs-lookup"><span data-stu-id="514b0-110">Manager</span></span>|<span data-ttu-id="514b0-111">Asystenta ustawień</span><span class="sxs-lookup"><span data-stu-id="514b0-111">Assistant</span></span>|<span data-ttu-id="514b0-112">Dział</span><span class="sxs-lookup"><span data-stu-id="514b0-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="514b0-113">Oryginalny stan bazy danych po otrzymaniu kwerendy od użytkownika Użytkownik1 i Użytkownik2.</span><span class="sxs-lookup"><span data-stu-id="514b0-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="514b0-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="514b0-114">Alfreds</span></span>|<span data-ttu-id="514b0-115">Maria</span><span class="sxs-lookup"><span data-stu-id="514b0-115">Maria</span></span>|<span data-ttu-id="514b0-116">Sprzedaż</span><span class="sxs-lookup"><span data-stu-id="514b0-116">Sales</span></span>|  
|<span data-ttu-id="514b0-117">Użytkownik1 przygotowuje się do przesyłania tych zmian.</span><span class="sxs-lookup"><span data-stu-id="514b0-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="514b0-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="514b0-118">Alfred</span></span>||<span data-ttu-id="514b0-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="514b0-119">Marketing</span></span>|  
|<span data-ttu-id="514b0-120">UŻYTKOWNIK2 zostało już przesłane te zmiany.</span><span class="sxs-lookup"><span data-stu-id="514b0-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="514b0-121">Mary</span><span class="sxs-lookup"><span data-stu-id="514b0-121">Mary</span></span>|<span data-ttu-id="514b0-122">Usługa</span><span class="sxs-lookup"><span data-stu-id="514b0-122">Service</span></span>|  
  
 <span data-ttu-id="514b0-123">Aby rozwiązać ten konflikt, zastępując wartości bazy danych przy użyciu bieżących wartości elementu członkowskiego klient decyduje o User1.</span><span class="sxs-lookup"><span data-stu-id="514b0-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="514b0-124">Gdy użytkownik User1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, wynik w bazie danych jest tak jak w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="514b0-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="514b0-125">maszyny wirtualnej</span><span class="sxs-lookup"><span data-stu-id="514b0-125">Manager</span></span>|<span data-ttu-id="514b0-126">Asystenta ustawień</span><span class="sxs-lookup"><span data-stu-id="514b0-126">Assistant</span></span>|<span data-ttu-id="514b0-127">Dział</span><span class="sxs-lookup"><span data-stu-id="514b0-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="514b0-128">Nowy stan po rozwiązywania konfliktów.</span><span class="sxs-lookup"><span data-stu-id="514b0-128">New state after conflict resolution.</span></span>|<span data-ttu-id="514b0-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="514b0-129">Alfred</span></span><br /><br /> <span data-ttu-id="514b0-130">(od użytkownika Użytkownik1)</span><span class="sxs-lookup"><span data-stu-id="514b0-130">(from User1)</span></span>|<span data-ttu-id="514b0-131">Maria</span><span class="sxs-lookup"><span data-stu-id="514b0-131">Maria</span></span><br /><br /> <span data-ttu-id="514b0-132">(oryginalny)</span><span class="sxs-lookup"><span data-stu-id="514b0-132">(original)</span></span>|<span data-ttu-id="514b0-133">Marketing</span><span class="sxs-lookup"><span data-stu-id="514b0-133">Marketing</span></span><br /><br /> <span data-ttu-id="514b0-134">(od użytkownika Użytkownik1)</span><span class="sxs-lookup"><span data-stu-id="514b0-134">(from User1)</span></span>|  
  
 <span data-ttu-id="514b0-135">Poniższy przykład kodu pokazuje, jak zastąpić wartości bazy danych przy użyciu bieżących wartości elementu członkowskiego klienta.</span><span class="sxs-lookup"><span data-stu-id="514b0-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="514b0-136">(Nie inspekcji lub niestandardową obsługę konflikty poszczególnym członkom występuje.)</span><span class="sxs-lookup"><span data-stu-id="514b0-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="514b0-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="514b0-137">See also</span></span>
- [<span data-ttu-id="514b0-138">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="514b0-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
