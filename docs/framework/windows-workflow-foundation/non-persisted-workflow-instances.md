---
title: Wystąpienia-utrwalony przepływu pracy
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 410451f0dfeb91111e77634245aa786c4afc5b04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516753"
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="06749-102">Wystąpienia-utrwalony przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="06749-102">Non-Persisted Workflow Instances</span></span>
<span data-ttu-id="06749-103">Jeśli nowe wystąpienie przepływu pracy jest utworzony utrwala swój stan w <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, host usługi tworzy wpis dla tej usługi w magazynie wystąpień.</span><span class="sxs-lookup"><span data-stu-id="06749-103">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="06749-104">Później, gdy trwała wystąpienia przepływu pracy po raz pierwszy, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zapisuje bieżący stan wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="06749-104">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="06749-105">Jeśli przepływ pracy jest hostowana w usłudze aktywacji procesów systemu Windows, danych wdrożenia usługi są równocześnie zapisywane w magazynie wystąpień, gdy wystąpienie jest zachowywane po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="06749-105">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>  
  
 <span data-ttu-id="06749-106">Tak długo, jak wystąpienie przepływu pracy nie zostały utrwalone, znajduje się w **-utrwalony** stanu.</span><span class="sxs-lookup"><span data-stu-id="06749-106">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="06749-107">W tym stanie, wystąpienie przepływu pracy nie można odzyskać po odtwarzania domen aplikacji, awarii hosta lub awarii komputera.</span><span class="sxs-lookup"><span data-stu-id="06749-107">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>  
  
## <a name="the-non-persisted-state"></a><span data-ttu-id="06749-108">Stan nietrwałe</span><span class="sxs-lookup"><span data-stu-id="06749-108">The Non-Persisted State</span></span>  
 <span data-ttu-id="06749-109">Wystąpienia przepływu pracy trwałe, które nie zostały utrwalone pozostają w stanie nietrwałe w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="06749-109">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>  
  
-   <span data-ttu-id="06749-110">Host usługi ulegnie awarii, przed wystąpieniem przepływu pracy jest zachowywane po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="06749-110">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="06749-111">Wystąpienie przepływu pracy pozostaje w magazynie wystąpień i nie została odzyskana.</span><span class="sxs-lookup"><span data-stu-id="06749-111">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="06749-112">Jeśli wiadomość skorelowane, wystąpienie przepływu pracy staje się aktywny ponownie.</span><span class="sxs-lookup"><span data-stu-id="06749-112">If a correlated message arrives, the workflow instance becomes active again.</span></span>  
  
-   <span data-ttu-id="06749-113">Wystąpienie przepływu pracy, wystąpi wyjątek przed jest zachowywane po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="06749-113">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="06749-114">W zależności od <xref:System.Activities.UnhandledExceptionAction> zwrócone, występują następujące scenariusze:</span><span class="sxs-lookup"><span data-stu-id="06749-114">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>  
  
    -   <span data-ttu-id="06749-115"><xref:System.Activities.UnhandledExceptionAction> ustawiono <xref:System.Activities.UnhandledExceptionAction.Abort>: po wystąpieniu wyjątku, informacje na temat wdrażania usługi są zapisywane w magazynie wystąpień i wystąpienia przepływu pracy jest usuwane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="06749-115"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="06749-116">Nie można ponownie załadować wystąpienia przepływu pracy i pozostaje w stanie nietrwałe.</span><span class="sxs-lookup"><span data-stu-id="06749-116">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>  
  
    -   <span data-ttu-id="06749-117"><xref:System.Activities.UnhandledExceptionAction> ustawiono <xref:System.Activities.UnhandledExceptionAction.Cancel> lub <xref:System.Activities.UnhandledExceptionAction.Terminate>: po wystąpieniu wyjątku, informacje na temat wdrażania usługi są zapisywane w magazynie wystąpień i ustawiono stan wystąpienia działania <xref:System.Activities.ActivityInstanceState.Closed>.</span><span class="sxs-lookup"><span data-stu-id="06749-117"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>  
  
 <span data-ttu-id="06749-118">Aby zminimalizować ryzyko napotkania wystąpienia zwolniony-utrwalony przepływu pracy, zalecamy utrwalanie przepływu pracy na wczesnym etapie cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="06749-118">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="06749-119">Wykrywanie i usuwanie wystąpienia nietrwałe</span><span class="sxs-lookup"><span data-stu-id="06749-119">Detection and Removal of Non-Persisted Instances</span></span>  
 <span data-ttu-id="06749-120"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Nie powoduje usunięcia żadnych-utrwalony wystąpienia przepływu pracy z w magazynie wystąpień.</span><span class="sxs-lookup"><span data-stu-id="06749-120">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="06749-121">Ponadto nie powoduje usunięcia wszystkich właścicieli wygasłe blokady, którzy mają-utrwalony wystąpień przepływów pracy związanych z nimi.</span><span class="sxs-lookup"><span data-stu-id="06749-121">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>  
  
 <span data-ttu-id="06749-122">Zaleca się, że administrator okresowo sprawdza, czy w magazynie wystąpień-utrwalony wystąpień.</span><span class="sxs-lookup"><span data-stu-id="06749-122">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="06749-123">Administratorzy mogą usunąć te wystąpienia, w sklepie wystąpienia tak długo, jak wiedzieli, że ten przepływ pracy nie będą otrzymywać wiadomości skorelowane.</span><span class="sxs-lookup"><span data-stu-id="06749-123">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="06749-124">Na przykład jeśli wystąpienie było w bazie danych kilka miesięcy, wiadomo, że przepływ pracy ma zazwyczaj w okresie istnienia kilka dni byłoby bezpiecznie założono było zainicjować wystąpienia awarii.</span><span class="sxs-lookup"><span data-stu-id="06749-124">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>  
  
 <span data-ttu-id="06749-125">Aby znaleźć wystąpień,-utrwalone w magazynie wystąpień przepływu pracy programu SQL można użyć następujące kwerendy SQL:</span><span class="sxs-lookup"><span data-stu-id="06749-125">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>  
  
-   <span data-ttu-id="06749-126">To zapytanie wyszukuje wszystkie wystąpienia, które nie zostały utrwalone i zwraca identyfikator i tworzenia czas (przechowywane w formacie UTC) dla nich.</span><span class="sxs-lookup"><span data-stu-id="06749-126">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
-   <span data-ttu-id="06749-127">To zapytanie wyszukuje wszystkich wystąpień, które nie zostały utrwalone, a które nie są ładowane i zwraca identyfikator i tworzenia czas (przechowywane w formacie UTC) dla nich.</span><span class="sxs-lookup"><span data-stu-id="06749-127">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
-   <span data-ttu-id="06749-128">To zapytanie wyszukuje wystąpienia wszystkie zawieszone, które nie zostały utrwalone i zwraca identyfikator, czas utworzenia (przechowywane w formacie UTC), przyczynę zawieszenia i nazwa wyjątku dla nich.</span><span class="sxs-lookup"><span data-stu-id="06749-128">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 <span data-ttu-id="06749-129">Należy zachować ostrożność, usuwając-utrwalony wystąpień.</span><span class="sxs-lookup"><span data-stu-id="06749-129">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="06749-130">Ogólnie rzecz biorąc, jest bezpiecznie usunąć-utrwalony wystąpienia utworzone przez <xref:System.ServiceModel.Activities.WorkflowServiceHost> są wstrzymane albo nie są ładowane.</span><span class="sxs-lookup"><span data-stu-id="06749-130">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="06749-131">Tych określonych wystąpień może zostać usunięta z magazynu przez usuwanie ich z `[System.Activities.DurableInstancing].[Instances]` przy użyciu następującego polecenia SQL, zastępując identyfikatora wystąpienia poprawne.</span><span class="sxs-lookup"><span data-stu-id="06749-131">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  <span data-ttu-id="06749-132">Nie zaleca się usunięcie wszystkich wystąpień-utrwalony, ponieważ w tym wystąpienia, które właśnie utworzony i nie zostały utrwalone.</span><span class="sxs-lookup"><span data-stu-id="06749-132">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
