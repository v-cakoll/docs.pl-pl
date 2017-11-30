---
title: "Porady: zapytanie o-utrwalony wystąpień"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c83e9364fa599d4356b69fe93ae3eaaa618c2f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-for-non-persisted-instances"></a><span data-ttu-id="05225-102">Porady: zapytanie o-utrwalony wystąpień</span><span class="sxs-lookup"><span data-stu-id="05225-102">How to: Query for Non-persisted Instances</span></span>
<span data-ttu-id="05225-103">Po utworzeniu nowego wystąpienia usługi, a usługa zachowanie magazynu wystąpienia przepływu pracy SQL zdefiniowane, host usługi tworzy początkowej wpis dla tego wystąpienia usługi w magazynie wystąpień.</span><span class="sxs-lookup"><span data-stu-id="05225-103">When a new instance of a service is created and the service has the SQL Workflow Instance Store behavior defined, the service host creates a initial entry for that service instance in the instance store.</span></span> <span data-ttu-id="05225-104">Następnie, gdy wystąpienie usługi będzie nadal występować po raz pierwszy, zachowanie magazynu wystąpienia przepływu pracy SQL przechowuje bieżący stan wystąpienia oraz dodatkowe dane, które jest wymagane dla aktywacji, odzyskiwania i kontroli.</span><span class="sxs-lookup"><span data-stu-id="05225-104">Subsequently when the service instance persists for the first time, the SQL Workflow Instance Store behavior stores the current instance state together with additional data that is required for activation, recovery, and control.</span></span>  
  
 <span data-ttu-id="05225-105">Jeśli wystąpienie nie jest trwały, po utworzeniu początkowej wpis dla tego wystąpienia, wystąpienie usługi jest określany jako nietrwałe stan.</span><span class="sxs-lookup"><span data-stu-id="05225-105">If an instance is not persisted after the initial entry for the instance is created, the service instance is said to be in the non-persisted state.</span></span> <span data-ttu-id="05225-106">Wszystkie wystąpienia usług utrwalonych można zbadać i kontrolowane.</span><span class="sxs-lookup"><span data-stu-id="05225-106">All the persisted service instances can be queried and controlled.</span></span> <span data-ttu-id="05225-107">Wystąpienie usługi non utrwalony nie można można zbadać ani pod kontrolą.</span><span class="sxs-lookup"><span data-stu-id="05225-107">Non-persisted service instances can neither be queried nor controlled.</span></span> <span data-ttu-id="05225-108">Jeśli wystąpienie-utrwalony jest wstrzymana z powodu nieobsługiwanego wyjątku można zbadać ale nie kontroluje.</span><span class="sxs-lookup"><span data-stu-id="05225-108">If a non-persisted instance is suspended due to an unhandled exception it can be queried but not controlled.</span></span>  
  
 <span data-ttu-id="05225-109">Usługa trwała wystąpień, które nie są jeszcze utrwalone pozostają w stanie nietrwałe w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="05225-109">Durable service instances that are not yet persisted remain in a non-persisted state in the following scenarios:</span></span>  
  
-   <span data-ttu-id="05225-110">Host usługi ulegnie awarii przed wystąpienie utrwalone po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="05225-110">The service host crashes before the instance persisted for the first time.</span></span> <span data-ttu-id="05225-111">Zapis początkowa dla wystąpienia pozostaje w magazynie wystąpień.</span><span class="sxs-lookup"><span data-stu-id="05225-111">The initial entry for the instance remains in the instance store.</span></span> <span data-ttu-id="05225-112">Wystąpienie nie jest możliwe do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="05225-112">The instance is not recoverable.</span></span> <span data-ttu-id="05225-113">Jeśli wiadomość skorelowane, wystąpienie stanie się ponownie aktywna.</span><span class="sxs-lookup"><span data-stu-id="05225-113">If a correlated message arrives, the instance becomes active again.</span></span>  
  
-   <span data-ttu-id="05225-114">Wystąpienie napotka nieobsługiwany wyjątek, przed jego utrwalone po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="05225-114">The instance experiences an unhandled exception before it persisted for the first time.</span></span> <span data-ttu-id="05225-115">Następujące scenariusze wystąpić</span><span class="sxs-lookup"><span data-stu-id="05225-115">The following scenarios arise</span></span>  
  
    -   <span data-ttu-id="05225-116">Jeśli wartość **wartość UnhandledExceptionAction** właściwość jest ustawiona na **Abandon**, informacje na temat wdrażania usługi są zapisywane w magazynie wystąpień, a wystąpienie jest usuwane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="05225-116">If the value of the **UnhandledExceptionAction** property is set to **Abandon**, the service deployment information is written to the instance store and the instance is unloaded from memory.</span></span> <span data-ttu-id="05225-117">Wystąpienie pozostaje w stanie nietrwałe w bazie danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="05225-117">The instance remains in non-persisted state in the persistence database.</span></span>  
  
    -   <span data-ttu-id="05225-118">Jeśli wartość **wartość UnhandledExceptionAction** właściwość jest ustawiona na **AbandonAndSuspsend**, informacje na temat wdrażania usługi jest zapisane w bazie danych trwałości i ustawionystanwystąpienia **Zawieszone**.</span><span class="sxs-lookup"><span data-stu-id="05225-118">If the value of the **UnhandledExceptionAction** property is set to **AbandonAndSuspsend**, the service deployment information is written to the persistence database and the instance state is set to **Suspended**.</span></span> <span data-ttu-id="05225-119">Wystąpienie nie może zostać wznowione, anulowania lub zakończenia.</span><span class="sxs-lookup"><span data-stu-id="05225-119">The instance cannot be resumed, canceled, or terminated.</span></span> <span data-ttu-id="05225-120">Host usługi nie można załadować wystąpienia, ponieważ wystąpienie nie jeszcze utrwalone, i dlatego wpis bazy danych dla tego wystąpienia nie jest ukończone.</span><span class="sxs-lookup"><span data-stu-id="05225-120">The service host cannot load the instance because the instance hasn't persisted yet and, hence the database entry for the instance is not complete.</span></span>  
  
    -   <span data-ttu-id="05225-121">Jeśli wartość **wartość UnhandledExceptionAction** właściwość jest ustawiona na **anulować** lub **przerwania**, informacje na temat wdrażania usługi są zapisywane w magazynie wystąpień i stan wystąpienia ma ustawioną wartość **Ukończono**.</span><span class="sxs-lookup"><span data-stu-id="05225-121">If the value of the **UnhandledExceptionAction** property is set to **Cancel** or **Terminate**, the service deployment information is written to the instance store and the instance state is set to **Completed**.</span></span>  
  
 <span data-ttu-id="05225-122">Przykładowe zapytania można znaleźć w bazie danych SQL trwałości-utrwalony wystąpień i usunąć te wystąpienia z bazy danych można znaleźć w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="05225-122">The following sections provide sample queries to find non-persisted instances in the SQL persistence database and to delete these instances from the database.</span></span>  
  
## <a name="to-find-all-instances-not-persisted-yet"></a><span data-ttu-id="05225-123">Aby znaleźć wszystkie wystąpienia nie jeszcze utrwalone</span><span class="sxs-lookup"><span data-stu-id="05225-123">To find all instances not persisted yet</span></span>  
 <span data-ttu-id="05225-124">Następujące zapytanie SQL zwraca identyfikator i tworzenia czasu dla wszystkich wystąpień, które nie są zachowywane w jeszcze w bazie danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="05225-124">The following SQL query returns the ID and creation time for all instances that are not persisted in to the persistence database yet.</span></span>  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;  
```  
  
## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a><span data-ttu-id="05225-125">Aby znaleźć wszystkie wystąpienia nie jest jeszcze utrwalone i również nie załadowany</span><span class="sxs-lookup"><span data-stu-id="05225-125">To find all instances not persisted yet and also not loaded</span></span>  
 <span data-ttu-id="05225-126">Następujące zapytanie SQL zwraca identyfikator i tworzenia czasu dla wszystkich wystąpień, które nie są zachowywane, a także nie są ładowane.</span><span class="sxs-lookup"><span data-stu-id="05225-126">The following SQL query returns ID and creation time for all instances that are not persisted and also are not loaded.</span></span>  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;  
```  
  
## <a name="to-find-all-suspended-instances-not-persisted-yet"></a><span data-ttu-id="05225-127">Aby znaleźć wszystkie wstrzymane wystąpienia nie jeszcze utrwalone</span><span class="sxs-lookup"><span data-stu-id="05225-127">To find all suspended instances not persisted yet</span></span>  
 <span data-ttu-id="05225-128">Następujące zapytanie SQL zwraca identyfikator, czas utworzenia przyczyna zawieszenia i zawieszenie nazwa wyjątku dla wszystkich wystąpień, które nie są zachowywane, a także w stanie wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="05225-128">The following SQL query returns ID, creation time, suspension reason, and suspension exception name for all instances that are not persisted and also in a suspended state.</span></span>  
  
```  
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;  
```  
  
## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a><span data-ttu-id="05225-129">Aby usunąć-utrwalony wystąpienia z bazy danych trwałości</span><span class="sxs-lookup"><span data-stu-id="05225-129">To delete non-persisted instances from the persistence database</span></span>  
 <span data-ttu-id="05225-130">Należy okresowo Wyszukaj w sklepie wystąpienia-utrwalony wystąpień i usuń wystąpienia w sklepie wystąpienia, jeśli masz pewności, czy wystąpienie nie zostanie wyświetlony komunikat z skorelowane.</span><span class="sxs-lookup"><span data-stu-id="05225-130">You should periodically check the instance store for non-persisted instances and remove instances from the instance store if you are sure that the instance will not receive a correlated message.</span></span> <span data-ttu-id="05225-131">Na przykład jeśli wystąpienie było w bazie danych kilka miesięcy, wiadomo, że przepływ pracy ma zazwyczaj w okresie istnienia za kilka dni byłoby bezpiecznie założono, że jest to niezainicjowanym wystąpieniem, w którym miała awaria.</span><span class="sxs-lookup"><span data-stu-id="05225-131">For example, if the instance has been in the database for several months and you know that the workflow typically has a lifetime of a few days, it would be safe to assume that this is an uninitialized instance that had crashed.</span></span>  
  
 <span data-ttu-id="05225-132">Ogólnie rzecz biorąc jest bezpiecznie usunąć-utrwalony wystąpień, które nie jest wstrzymana lub nie został załadowany.</span><span class="sxs-lookup"><span data-stu-id="05225-132">In general, it is safe to delete non-persisted instances that are not suspended or not loaded.</span></span> <span data-ttu-id="05225-133">Nie należy usuwać **wszystkie** wystąpień-utrwalony, ponieważ ten zestaw wystąpienia zawiera wystąpień, które zostały utworzone, ale nie są jeszcze utrwalone.</span><span class="sxs-lookup"><span data-stu-id="05225-133">You should not delete **all** the non-persisted instances because this instance set includes instances that are just created but are not persisted yet.</span></span> <span data-ttu-id="05225-134">Należy usunąć tylko-utrwalony wystąpień, które są pozostawione ponieważ hosta usługi przepływu pracy, który miał załadować wystąpienia spowodowała wyjątek lub wystąpienie spowodowała wyjątek.</span><span class="sxs-lookup"><span data-stu-id="05225-134">You should only delete non-persisted instances that are left over because the workflow service host that had the instance loaded caused an exception or the instance itself caused an exception.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="05225-135">Usuwanie instancji nietrwałe w sklepie wystąpienia zmniejsza rozmiar magazynu i może zwiększyć wydajność operacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="05225-135">Deleting non-persisted instances from the instance store decreases the size of the store and may improve the performance of store operations.</span></span>
