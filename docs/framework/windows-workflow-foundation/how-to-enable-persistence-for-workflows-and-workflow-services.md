---
title: 'Instrukcje: Włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy'
description: Dowiedz się, jak skonfigurować magazyn wystąpień przepływu pracy SQL, aby zapewnić trwałość dla przepływów pracy i usług przepływu pracy programowo oraz przy użyciu pliku konfiguracji.
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 31fe6e3f06989e9a42254747565342cf97e4b9f1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421517"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="ab3ca-103">Instrukcje: Włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ab3ca-103">How to: Enable Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="ab3ca-104">W tym temacie opisano sposób włączania trwałości dla przepływów pracy i usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-104">This topic describes how to enable persistence for workflows and workflow services.</span></span>

## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="ab3ca-105">Włącz trwałość dla przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="ab3ca-105">Enable Persistence for Workflows</span></span>

<span data-ttu-id="ab3ca-106">Można skojarzyć magazyn wystąpień z obiektem **WorkflowApplication** przy użyciu <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwości <xref:System.Activities.WorkflowApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-106">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="ab3ca-107"><xref:System.Activities.WorkflowApplication.Persist%2A>Metoda zapisuje lub utrzymuje przepływ pracy w magazynie wystąpień skojarzonym z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-107">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="ab3ca-108"><xref:System.Activities.WorkflowApplication.Unload%2A>Metoda utrzymuje przepływ pracy w magazynie wystąpień, a następnie zwalnia wystąpienie z pamięci.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-108">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="ab3ca-109">Metoda **Load** ładuje przepływ pracy do pamięci przy użyciu danych przepływu pracy przechowywanych w magazynie trwałości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-109">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>

<span data-ttu-id="ab3ca-110">Metoda **utrwalania** wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ab3ca-110">The **Persist** method performs the following steps:</span></span>

1. <span data-ttu-id="ab3ca-111">Wstrzymuje harmonogram przepływu pracy i czeka, aż przepływ pracy przejdzie do stanu bezczynności.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-111">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="ab3ca-112">Zachowuje lub zapisuje przepływ pracy w magazynie trwałości.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-112">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="ab3ca-113">Wznawia harmonogram przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-113">Resumes the workflow scheduler.</span></span>

 <span data-ttu-id="ab3ca-114">Metoda **Unload** wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ab3ca-114">The **Unload** method performs the following steps:</span></span>

1. <span data-ttu-id="ab3ca-115">Wstrzymuje harmonogram przepływu pracy i czeka, aż przepływ pracy przejdzie do stanu bezczynności.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-115">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="ab3ca-116">Zachowuje lub zapisuje przepływ pracy w magazynie trwałości.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-116">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="ab3ca-117">Usuwa wystąpienie przepływu pracy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-117">Disposes the workflow instance in the memory.</span></span>

<span data-ttu-id="ab3ca-118">Metody **utrwalania** i **zwalniania** będą blokowane, gdy przepływ pracy jest w strefie no-utrwalania, dopóki przepływ pracy nie spowoduje zakończenia strefy braku trwałej.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-118">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="ab3ca-119">Metoda kontynuuje działanie z operacją utrwalania lub zwalniania po zakończeniu strefy No-utrwalania.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-119">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="ab3ca-120">Jeśli strefa braku utrwalania nie zostanie zakończona przed upływem limitu czasu lub jeśli proces trwałości trwa zbyt długo, zostanie zgłoszony limit czasu.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-120">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>

## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="ab3ca-121">Włącz trwałość dla usług przepływu pracy w kodzie</span><span class="sxs-lookup"><span data-stu-id="ab3ca-121">Enable Persistence for Workflow Services in Code</span></span>

<span data-ttu-id="ab3ca-122">Element członkowski **DurableInstancingOptions** <xref:System.ServiceModel.WorkflowServiceHost> klasy ma właściwość o nazwie **InstanceStore** , której można użyć do skojarzenia magazynu wystąpień z obiektem **WorkflowServiceHost**.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-122">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

<span data-ttu-id="ab3ca-123">Gdy obiekt **WorkflowServiceHost** jest otwarty, trwałość jest włączana automatycznie, jeśli **DurableInstancingOptions. InstanceStore** nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-123">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>

<span data-ttu-id="ab3ca-124">Zwykle zachowanie usługi zapewnia konkretny magazyn wystąpień do użycia z hostem usługi przepływu pracy przy użyciu właściwości **InstanceStore** .</span><span class="sxs-lookup"><span data-stu-id="ab3ca-124">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="ab3ca-125">Na przykład SqlWorkflowInstanceStoreBehavior tworzy wystąpienie **obiekt SqlWorkflowInstanceStore**, konfiguruje je i przypisuje go do **DurableInstancingOptions. InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="ab3ca-125">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="ab3ca-126">Włącz trwałość dla usług przepływu pracy przy użyciu pliku konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="ab3ca-126">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>

<span data-ttu-id="ab3ca-127">Trwałości można włączyć za pomocą pliku konfiguracji aplikacji, dodając następujący kod do pliku App. config lub Web. config:</span><span class="sxs-lookup"><span data-stu-id="ab3ca-127">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
