---
title: 'Instrukcje: Rozwiązywanie konfliktów z zachowaniem wartości bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: e42f48a188741c3ddff44f6444fa351192c8175f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793338"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="81f3b-102">Instrukcje: Rozwiązywanie konfliktów z zachowaniem wartości bazy danych</span><span class="sxs-lookup"><span data-stu-id="81f3b-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="81f3b-103">Aby uzgodnić różnice między oczekiwanymi i rzeczywistymi wartościami bazy danych przed próbą ponownego przesłania zmian, można użyć <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> programu w celu zachowania wartości znalezionych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="81f3b-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="81f3b-104">Bieżące wartości w modelu obiektów są następnie zastępowane.</span><span class="sxs-lookup"><span data-stu-id="81f3b-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="81f3b-105">Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="81f3b-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81f3b-106">We wszystkich przypadkach rekord na kliencie jest najpierw odświeżany przez pobranie zaktualizowanych danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="81f3b-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="81f3b-107">Ta akcja zapewnia, że kolejna próba aktualizacji nie powiedzie się na tych samych kontrolach współbieżności.</span><span class="sxs-lookup"><span data-stu-id="81f3b-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81f3b-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="81f3b-108">Example</span></span>  
 <span data-ttu-id="81f3b-109">W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy Użytkownik1 próbuje przesłać zmiany, ponieważ w międzyczasie została zmieniona kolumna asystenta i działu.</span><span class="sxs-lookup"><span data-stu-id="81f3b-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="81f3b-110">W poniższej tabeli przedstawiono sytuację.</span><span class="sxs-lookup"><span data-stu-id="81f3b-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="81f3b-111">maszyny wirtualnej</span><span class="sxs-lookup"><span data-stu-id="81f3b-111">Manager</span></span>|<span data-ttu-id="81f3b-112">Pomocnik</span><span class="sxs-lookup"><span data-stu-id="81f3b-112">Assistant</span></span>|<span data-ttu-id="81f3b-113">Dział</span><span class="sxs-lookup"><span data-stu-id="81f3b-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="81f3b-114">Oryginalny stan bazy danych podczas wykonywania zapytania przez Użytkownik1 i.</span><span class="sxs-lookup"><span data-stu-id="81f3b-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="81f3b-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="81f3b-115">Alfreds</span></span>|<span data-ttu-id="81f3b-116">Maria</span><span class="sxs-lookup"><span data-stu-id="81f3b-116">Maria</span></span>|<span data-ttu-id="81f3b-117">Sprzedaż</span><span class="sxs-lookup"><span data-stu-id="81f3b-117">Sales</span></span>|  
|<span data-ttu-id="81f3b-118">Użytkownik1 przygotowuje się do przesłania tych zmian.</span><span class="sxs-lookup"><span data-stu-id="81f3b-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="81f3b-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="81f3b-119">Alfred</span></span>||<span data-ttu-id="81f3b-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="81f3b-120">Marketing</span></span>|  
|<span data-ttu-id="81f3b-121">Do tego celu zostały już przesłane te zmiany.</span><span class="sxs-lookup"><span data-stu-id="81f3b-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="81f3b-122">Anna</span><span class="sxs-lookup"><span data-stu-id="81f3b-122">Mary</span></span>|<span data-ttu-id="81f3b-123">Usługa</span><span class="sxs-lookup"><span data-stu-id="81f3b-123">Service</span></span>|  
  
 <span data-ttu-id="81f3b-124">Użytkownik1 decyduje się rozwiązać ten konflikt, mając nowsze wartości bazy danych zastępują bieżące wartości w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="81f3b-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="81f3b-125">Gdy Użytkownik1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, wynik w bazie danych jest następujący w tabeli:</span><span class="sxs-lookup"><span data-stu-id="81f3b-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="81f3b-126">maszyny wirtualnej</span><span class="sxs-lookup"><span data-stu-id="81f3b-126">Manager</span></span>|<span data-ttu-id="81f3b-127">Pomocnik</span><span class="sxs-lookup"><span data-stu-id="81f3b-127">Assistant</span></span>|<span data-ttu-id="81f3b-128">Dział</span><span class="sxs-lookup"><span data-stu-id="81f3b-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="81f3b-129">Nowy stan po rozwiązaniu konfliktu.</span><span class="sxs-lookup"><span data-stu-id="81f3b-129">New state after conflict resolution.</span></span>|<span data-ttu-id="81f3b-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="81f3b-130">Alfreds</span></span><br /><br /> <span data-ttu-id="81f3b-131">oryginalnego</span><span class="sxs-lookup"><span data-stu-id="81f3b-131">(original)</span></span>|<span data-ttu-id="81f3b-132">Anna</span><span class="sxs-lookup"><span data-stu-id="81f3b-132">Mary</span></span><br /><br /> <span data-ttu-id="81f3b-133">(od b do)</span><span class="sxs-lookup"><span data-stu-id="81f3b-133">(from User2)</span></span>|<span data-ttu-id="81f3b-134">Usługa</span><span class="sxs-lookup"><span data-stu-id="81f3b-134">Service</span></span><br /><br /> <span data-ttu-id="81f3b-135">(od b do)</span><span class="sxs-lookup"><span data-stu-id="81f3b-135">(from User2)</span></span>|  
  
 <span data-ttu-id="81f3b-136">Poniższy przykładowy kod pokazuje, jak zastąpić bieżące wartości w modelu obiektów wartościami bazy danych.</span><span class="sxs-lookup"><span data-stu-id="81f3b-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="81f3b-137">(Żadna Inspekcja lub Niestandardowa obsługa konfliktów poszczególnych członków nie występuje).</span><span class="sxs-lookup"><span data-stu-id="81f3b-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="81f3b-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81f3b-138">See also</span></span>

- [<span data-ttu-id="81f3b-139">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="81f3b-139">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
