---
title: "Porady: Rozwiązywanie konfliktów, zastępując wartości bazy danych"
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
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1dd9a6be51ad1723aab7c3102387a42d1c24996
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="c3b3f-102">Porady: Rozwiązywanie konfliktów, zastępując wartości bazy danych</span><span class="sxs-lookup"><span data-stu-id="c3b3f-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="c3b3f-103">Uzgadnianie różnic pomiędzy wartościami oczekiwanymi i rzeczywistymi bazy danych, aby spróbować ponownie przesłać zmiany, umożliwia <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> zastąpić wartościami bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="c3b3f-104">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c3b3f-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3b3f-105">We wszystkich przypadkach rekord klienta jest najpierw odświeżyć pobierając zaktualizowane dane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="c3b3f-106">Ta akcja gwarantuje, że następnej próbie aktualizacji zakończy się niepowodzeniem na tym samym kontrolach współbieżności.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3b3f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3b3f-107">Example</span></span>  
 <span data-ttu-id="c3b3f-108">W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek próba Użytkownik1 przesyłanie zmian, ponieważ Użytkownik2 w tym samym czasie została zmieniona kolumny Asystenta i działu.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="c3b3f-109">W poniższej tabeli przedstawiono tę sytuację.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="c3b3f-110">Menedżer</span><span class="sxs-lookup"><span data-stu-id="c3b3f-110">Manager</span></span>|<span data-ttu-id="c3b3f-111">Asystent</span><span class="sxs-lookup"><span data-stu-id="c3b3f-111">Assistant</span></span>|<span data-ttu-id="c3b3f-112">Dział</span><span class="sxs-lookup"><span data-stu-id="c3b3f-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="c3b3f-113">Oryginalny stan bazy danych po otrzymaniu kwerendy od użytkownika Użytkownik1 i Użytkownik2.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="c3b3f-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="c3b3f-114">Alfreds</span></span>|<span data-ttu-id="c3b3f-115">Maria</span><span class="sxs-lookup"><span data-stu-id="c3b3f-115">Maria</span></span>|<span data-ttu-id="c3b3f-116">Sprzedaży</span><span class="sxs-lookup"><span data-stu-id="c3b3f-116">Sales</span></span>|  
|<span data-ttu-id="c3b3f-117">Użytkownik1 przygotowuje się do przesyłania tych zmian.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="c3b3f-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="c3b3f-118">Alfred</span></span>||<span data-ttu-id="c3b3f-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="c3b3f-119">Marketing</span></span>|  
|<span data-ttu-id="c3b3f-120">UŻYTKOWNIK2 zostało już przesłane tych zmian.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="c3b3f-121">Joanna</span><span class="sxs-lookup"><span data-stu-id="c3b3f-121">Mary</span></span>|<span data-ttu-id="c3b3f-122">Usługa</span><span class="sxs-lookup"><span data-stu-id="c3b3f-122">Service</span></span>|  
  
 <span data-ttu-id="c3b3f-123">Użytkownik1 decyduje o tym rozwiązać ten konflikt, zastępując wartości bazy danych z bieżącej wartości elementu członkowskiego klienta.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="c3b3f-124">Gdy Użytkownik1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, wynik w bazie danych jest w następującej tabeli:</span><span class="sxs-lookup"><span data-stu-id="c3b3f-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="c3b3f-125">Menedżer</span><span class="sxs-lookup"><span data-stu-id="c3b3f-125">Manager</span></span>|<span data-ttu-id="c3b3f-126">Asystent</span><span class="sxs-lookup"><span data-stu-id="c3b3f-126">Assistant</span></span>|<span data-ttu-id="c3b3f-127">Dział</span><span class="sxs-lookup"><span data-stu-id="c3b3f-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="c3b3f-128">Nowy stan po rozwiązywania konfliktów.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-128">New state after conflict resolution.</span></span>|<span data-ttu-id="c3b3f-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="c3b3f-129">Alfred</span></span><br /><br /> <span data-ttu-id="c3b3f-130">(z poziomu konta użytkownik1)</span><span class="sxs-lookup"><span data-stu-id="c3b3f-130">(from User1)</span></span>|<span data-ttu-id="c3b3f-131">Maria</span><span class="sxs-lookup"><span data-stu-id="c3b3f-131">Maria</span></span><br /><br /> <span data-ttu-id="c3b3f-132">(oryginalny)</span><span class="sxs-lookup"><span data-stu-id="c3b3f-132">(original)</span></span>|<span data-ttu-id="c3b3f-133">Marketing</span><span class="sxs-lookup"><span data-stu-id="c3b3f-133">Marketing</span></span><br /><br /> <span data-ttu-id="c3b3f-134">(z poziomu konta użytkownik1)</span><span class="sxs-lookup"><span data-stu-id="c3b3f-134">(from User1)</span></span>|  
  
 <span data-ttu-id="c3b3f-135">Poniższy przykład kodu pokazuje, jak zastąpić wartościami bazy danych z bieżącej wartości elementu członkowskiego klienta.</span><span class="sxs-lookup"><span data-stu-id="c3b3f-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="c3b3f-136">(Nie inspekcji lub niestandardową obsługę wystąpił konflikt elementu członkowskiego poszczególnych występuje.)</span><span class="sxs-lookup"><span data-stu-id="c3b3f-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c3b3f-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3b3f-137">See Also</span></span>  
 [<span data-ttu-id="c3b3f-138">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="c3b3f-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
