---
title: "Porady: Rozwiązywanie konfliktów przez scalanie z wartościami bazy danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8e5114052951950c5866d80c974555678b1d040a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="58a78-102">Porady: Rozwiązywanie konfliktów przez scalanie z wartościami bazy danych</span><span class="sxs-lookup"><span data-stu-id="58a78-102">How to: Resolve Conflicts by Merging with Database Values</span></span>
<span data-ttu-id="58a78-103">Uzgadnianie różnic pomiędzy wartościami oczekiwanymi i rzeczywistymi bazy danych, aby spróbować ponownie przesłać zmiany, umożliwia <xref:System.Data.Linq.RefreshMode.KeepChanges> do scalenia wartościami bazy danych z bieżącej wartości elementu członkowskiego klienta.</span><span class="sxs-lookup"><span data-stu-id="58a78-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="58a78-104">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="58a78-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58a78-105">We wszystkich przypadkach rekord klienta jest najpierw odświeżyć pobierając zaktualizowane dane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="58a78-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="58a78-106">Ta akcja gwarantuje, że następnej próbie aktualizacji zakończy się niepowodzeniem na tym samym kontrolach współbieżności.</span><span class="sxs-lookup"><span data-stu-id="58a78-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58a78-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="58a78-107">Example</span></span>  
 <span data-ttu-id="58a78-108">W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek próba Użytkownik1 przesyłanie zmian, ponieważ Użytkownik2 w tym samym czasie została zmieniona kolumny Asystenta i działu.</span><span class="sxs-lookup"><span data-stu-id="58a78-108">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="58a78-109">W poniższej tabeli przedstawiono tę sytuację.</span><span class="sxs-lookup"><span data-stu-id="58a78-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="58a78-110">Menedżer</span><span class="sxs-lookup"><span data-stu-id="58a78-110">Manager</span></span>|<span data-ttu-id="58a78-111">Asystent</span><span class="sxs-lookup"><span data-stu-id="58a78-111">Assistant</span></span>|<span data-ttu-id="58a78-112">Dział</span><span class="sxs-lookup"><span data-stu-id="58a78-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="58a78-113">Oryginalny stan bazy danych po otrzymaniu kwerendy od użytkownika Użytkownik1 i Użytkownik2.</span><span class="sxs-lookup"><span data-stu-id="58a78-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="58a78-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="58a78-114">Alfreds</span></span>|<span data-ttu-id="58a78-115">Maria</span><span class="sxs-lookup"><span data-stu-id="58a78-115">Maria</span></span>|<span data-ttu-id="58a78-116">Sprzedaży</span><span class="sxs-lookup"><span data-stu-id="58a78-116">Sales</span></span>|  
|<span data-ttu-id="58a78-117">Użytkownik1 przygotowuje się do przesyłania tych zmian.</span><span class="sxs-lookup"><span data-stu-id="58a78-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="58a78-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="58a78-118">Alfred</span></span>||<span data-ttu-id="58a78-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="58a78-119">Marketing</span></span>|  
|<span data-ttu-id="58a78-120">UŻYTKOWNIK2 zostało już przesłane tych zmian.</span><span class="sxs-lookup"><span data-stu-id="58a78-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="58a78-121">Joanna</span><span class="sxs-lookup"><span data-stu-id="58a78-121">Mary</span></span>|<span data-ttu-id="58a78-122">Usługa</span><span class="sxs-lookup"><span data-stu-id="58a78-122">Service</span></span>|  
  
 <span data-ttu-id="58a78-123">Użytkownik1 decyduje o tym rozwiązać ten konflikt przez scalenie wartościami bazy danych z bieżącej wartości elementu członkowskiego klienta.</span><span class="sxs-lookup"><span data-stu-id="58a78-123">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="58a78-124">Wynik będzie tej bazy danych, które wartości są zastępowane tylko wtedy, gdy bieżący zestaw zmian zmodyfikował również tej wartości.</span><span class="sxs-lookup"><span data-stu-id="58a78-124">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="58a78-125">Gdy Użytkownik1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.KeepChanges>, wynik w bazie danych jest w następującej tabeli:</span><span class="sxs-lookup"><span data-stu-id="58a78-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="58a78-126">Menedżer</span><span class="sxs-lookup"><span data-stu-id="58a78-126">Manager</span></span>|<span data-ttu-id="58a78-127">Asystent</span><span class="sxs-lookup"><span data-stu-id="58a78-127">Assistant</span></span>|<span data-ttu-id="58a78-128">Dział</span><span class="sxs-lookup"><span data-stu-id="58a78-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="58a78-129">Nowy stan po rozwiązywania konfliktów.</span><span class="sxs-lookup"><span data-stu-id="58a78-129">New state after conflict resolution.</span></span>|<span data-ttu-id="58a78-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="58a78-130">Alfred</span></span><br /><br /> <span data-ttu-id="58a78-131">(z poziomu konta użytkownik1)</span><span class="sxs-lookup"><span data-stu-id="58a78-131">(from User1)</span></span>|<span data-ttu-id="58a78-132">Joanna</span><span class="sxs-lookup"><span data-stu-id="58a78-132">Mary</span></span><br /><br /> <span data-ttu-id="58a78-133">(z Użytkownik2)</span><span class="sxs-lookup"><span data-stu-id="58a78-133">(from User2)</span></span>|<span data-ttu-id="58a78-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="58a78-134">Marketing</span></span><br /><br /> <span data-ttu-id="58a78-135">(z poziomu konta użytkownik1)</span><span class="sxs-lookup"><span data-stu-id="58a78-135">(from User1)</span></span>|  
  
 <span data-ttu-id="58a78-136">Poniższy przykład przedstawia sposób scalania wartościami bazy danych z bieżącej wartości elementu członkowskiego klienta (chyba że klient został zmieniony tej wartości).</span><span class="sxs-lookup"><span data-stu-id="58a78-136">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="58a78-137">Występuje, nie inspekcji lub niestandardową obsługę konfliktów poszczególnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="58a78-137">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="58a78-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58a78-138">See Also</span></span>  
 [<span data-ttu-id="58a78-139">Porady: Rozwiązywanie konfliktów, zastępując wartości bazy danych</span><span class="sxs-lookup"><span data-stu-id="58a78-139">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 [<span data-ttu-id="58a78-140">Porady: Rozwiązywanie konfliktów, zachowując wartości bazy danych</span><span class="sxs-lookup"><span data-stu-id="58a78-140">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 [<span data-ttu-id="58a78-141">Porady: Zarządzanie konfliktów zmian</span><span class="sxs-lookup"><span data-stu-id="58a78-141">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
