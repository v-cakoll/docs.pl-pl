---
title: Nietrwałe wystąpienia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 315d791585ace6ce4adf281abbba0a4c8c72d75a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663046"
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="3c9ef-102">Nietrwałe wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3c9ef-102">Non-Persisted Workflow Instances</span></span>

<span data-ttu-id="3c9ef-103">Nowe wystąpienie przepływu pracy utworzenia trwające jego stan w <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, host usługi tworzy wpis dla tej usługi w sklepie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-103">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="3c9ef-104">Później, gdy wystąpienie przepływu pracy jest trwały po raz pierwszy <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zapisuje bieżący stan wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-104">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="3c9ef-105">Jeśli przepływ pracy znajduje się w usłudze aktywacji procesów Windows, danych wdrożenia usługi są również zapisywane do magazynu wystąpienia, gdy wystąpienie jest trwały po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-105">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>

<span data-ttu-id="3c9ef-106">Tak długo, jak nie został utrwalony wystąpienia przepływu pracy, jest **nieutrwaloną** stanu.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-106">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="3c9ef-107">W tym stanie wystąpienie przepływu pracy nie można odzyskać po odtwarzanie domeny aplikacji, awarii komputera lub awarii hosta.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-107">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>

## <a name="the-non-persisted-state"></a><span data-ttu-id="3c9ef-108">Stan nietrwałe</span><span class="sxs-lookup"><span data-stu-id="3c9ef-108">The Non-Persisted State</span></span>

<span data-ttu-id="3c9ef-109">Wystąpienia trwałość przepływu pracy, które nie zostały utrwalone pozostają w stanie nieutrwaloną w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="3c9ef-109">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>

- <span data-ttu-id="3c9ef-110">Host usługi ulegnie awarii, przed wystąpieniem przepływu pracy jest trwały po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-110">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="3c9ef-111">Wystąpienie przepływu pracy pozostaje w magazynie wystąpienia i nie została odzyskana.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-111">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="3c9ef-112">Jeśli zostanie odebrana wiadomość skorelowane, wystąpienie przepływu pracy staje się aktywny ponownie.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-112">If a correlated message arrives, the workflow instance becomes active again.</span></span>

- <span data-ttu-id="3c9ef-113">Wystąpienie przepływu pracy napotka wyjątek, zanim są utrwalane po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-113">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="3c9ef-114">W zależności od <xref:System.Activities.UnhandledExceptionAction> zwrócone, występują następujące scenariusze:</span><span class="sxs-lookup"><span data-stu-id="3c9ef-114">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>

  - <span data-ttu-id="3c9ef-115"><xref:System.Activities.UnhandledExceptionAction> ustawiono <xref:System.Activities.UnhandledExceptionAction.Abort>: Gdy wystąpi wyjątek, informacje o wdrożeniu usługi są zapisywane do magazynu wystąpienia, a wystąpienie przepływu pracy jest usuwane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-115"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="3c9ef-116">Wystąpienie przepływu pracy pozostaje w stanie nietrwałe i nie można ponownie załadować.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-116">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>

  - <span data-ttu-id="3c9ef-117"><xref:System.Activities.UnhandledExceptionAction> ustawiono <xref:System.Activities.UnhandledExceptionAction.Cancel> lub <xref:System.Activities.UnhandledExceptionAction.Terminate>: Gdy wystąpi wyjątek, informacje o wdrożeniu usługi są zapisywane do magazynu wystąpienie i stan wystąpienia działania jest równa <xref:System.Activities.ActivityInstanceState.Closed>.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-117"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>

<span data-ttu-id="3c9ef-118">Aby zminimalizować ryzyko zostają zwolnione przepływu pracy, które są nietrwałe wystąpienia, firma Microsoft zaleca utrwalanie przepływu pracy na wczesnym etapie cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-118">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>

## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="3c9ef-119">Wykrywanie i usuwanie wystąpień nietrwałych</span><span class="sxs-lookup"><span data-stu-id="3c9ef-119">Detection and Removal of Non-Persisted Instances</span></span>

<span data-ttu-id="3c9ef-120"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Nie powoduje usunięcia wszelkich nietrwałe wystąpienia przepływu pracy w sklepie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-120">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="3c9ef-121">Ponadto nie powoduje usunięcia wszystkich właścicieli blokada wygasła, którzy mają nietrwałe wystąpienia przepływu pracy skojarzonych z nimi.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-121">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>

<span data-ttu-id="3c9ef-122">Zaleca się, że administrator okresowo sprawdza magazyn wystąpień do wystąpień nietrwałych.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-122">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="3c9ef-123">Administratorzy mogą usunąć te wystąpienia w sklepie wystąpienia, tak długo, jak, które znają tego przepływu pracy nie będą otrzymywać skorelowanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-123">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="3c9ef-124">Na przykład jeśli wystąpienie było w bazie danych przez kilka miesięcy, a wiadomo, że przepływ pracy ma zazwyczaj ważności kilka dni, będzie bezpiecznie przyjąć założenie było to wystąpienie zainicjowane, które miały wystąpiła awaria.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-124">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>

<span data-ttu-id="3c9ef-125">Aby znaleźć wystąpień nietrwałych w Store wystąpienia przepływu pracy SQL można użyć następujących zapytań SQL:</span><span class="sxs-lookup"><span data-stu-id="3c9ef-125">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>

- <span data-ttu-id="3c9ef-126">To zapytanie wyszukuje wszystkie wystąpienia, które nie zostały utrwalone i zwraca identyfikator i tworzenia czas (przechowywany w czasie UTC) dla nich.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-126">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
  ```

- <span data-ttu-id="3c9ef-127">To zapytanie wyszukuje wszystkie wystąpienia, która nie została utrwalona i nie są ładowane i zwraca identyfikator i tworzenia czas (przechowywany w czasie UTC) dla nich.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-127">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and CurrentMachine is NULL
  ```

- <span data-ttu-id="3c9ef-128">To zapytanie wyszukuje wszystkie wstrzymane wystąpień, które nie zostały utrwalone i zwraca identyfikator, czas utworzenia (przechowywanej w czasie UTC), powodem zawieszenia, a nazwa wyjątku dla nich.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-128">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>

  ```sql
  select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and IsSuspended = 1
  ```

<span data-ttu-id="3c9ef-129">Usunięcie wystąpień nietrwałych, należy zachować ostrożność.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-129">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="3c9ef-130">Ogólnie rzecz biorąc, jest bezpieczne usuwanie nietrwałe wystąpienia utworzone przez <xref:System.ServiceModel.Activities.WorkflowServiceHost> , są zawieszone lub nie są ładowane.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-130">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="3c9ef-131">Tych konkretnych wystąpień może zostać usunięta z magazynu przez usuwanie ich z `[System.Activities.DurableInstancing].[Instances]` za pomocą następującego polecenia SQL, podstawiając identyfikator wystąpienia jest poprawny.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-131">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>

```sql
delete [System.Activities.DurableInstancing].[Instances]
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’
```

> [!WARNING]
> <span data-ttu-id="3c9ef-132">Firma Microsoft nie zaleca się usunięcie wszystkich wystąpień nietrwałych, ponieważ w tym wystąpienia, które właśnie utworzony i nie zostały jeszcze utrwalone.</span><span class="sxs-lookup"><span data-stu-id="3c9ef-132">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
