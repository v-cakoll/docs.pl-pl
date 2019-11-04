---
title: 'Instrukcje: Włączanie trwałości dla przepływów pracy i usług przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 5d0eeb8ad40f2f4f3349ab48487316014a561a1b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460894"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="f993c-102">Instrukcje: Włączanie trwałości dla przepływów pracy i usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f993c-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="f993c-103">W tym temacie opisano sposób włączania trwałości dla przepływów pracy i usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f993c-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>

## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="f993c-104">Włącz trwałość dla przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="f993c-104">Enable Persistence for Workflows</span></span>

<span data-ttu-id="f993c-105">Można skojarzyć magazyn wystąpień z obiektem **WorkflowApplication** przy użyciu właściwości <xref:System.Activities.WorkflowApplication.InstanceStore%2A> klasy <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="f993c-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="f993c-106">Metoda <xref:System.Activities.WorkflowApplication.Persist%2A> zapisuje lub utrzymuje przepływ pracy w magazynie wystąpień skojarzonym z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="f993c-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="f993c-107">Metoda <xref:System.Activities.WorkflowApplication.Unload%2A> utrzymuje przepływ pracy w magazynie wystąpień, a następnie zwalnia wystąpienie z pamięci.</span><span class="sxs-lookup"><span data-stu-id="f993c-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="f993c-108">Metoda **Load** ładuje przepływ pracy do pamięci przy użyciu danych przepływu pracy przechowywanych w magazynie trwałości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f993c-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>

<span data-ttu-id="f993c-109">Metoda **utrwalania** wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f993c-109">The **Persist** method performs the following steps:</span></span>

1. <span data-ttu-id="f993c-110">Wstrzymuje harmonogram przepływu pracy i czeka, aż przepływ pracy przejdzie do stanu bezczynności.</span><span class="sxs-lookup"><span data-stu-id="f993c-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="f993c-111">Zachowuje lub zapisuje przepływ pracy w magazynie trwałości.</span><span class="sxs-lookup"><span data-stu-id="f993c-111">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="f993c-112">Wznawia harmonogram przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f993c-112">Resumes the workflow scheduler.</span></span>

 <span data-ttu-id="f993c-113">Metoda **Unload** wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f993c-113">The **Unload** method performs the following steps:</span></span>

1. <span data-ttu-id="f993c-114">Wstrzymuje harmonogram przepływu pracy i czeka, aż przepływ pracy przejdzie do stanu bezczynności.</span><span class="sxs-lookup"><span data-stu-id="f993c-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="f993c-115">Zachowuje lub zapisuje przepływ pracy w magazynie trwałości.</span><span class="sxs-lookup"><span data-stu-id="f993c-115">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="f993c-116">Usuwa wystąpienie przepływu pracy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f993c-116">Disposes the workflow instance in the memory.</span></span>

<span data-ttu-id="f993c-117">Metody **utrwalania** i **zwalniania** będą blokowane, gdy przepływ pracy jest w strefie no-utrwalania, dopóki przepływ pracy nie spowoduje zakończenia strefy braku trwałej.</span><span class="sxs-lookup"><span data-stu-id="f993c-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="f993c-118">Metoda kontynuuje działanie z operacją utrwalania lub zwalniania po zakończeniu strefy No-utrwalania.</span><span class="sxs-lookup"><span data-stu-id="f993c-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="f993c-119">Jeśli strefa braku utrwalania nie zostanie zakończona przed upływem limitu czasu lub jeśli proces trwałości trwa zbyt długo, zostanie zgłoszony limit czasu.</span><span class="sxs-lookup"><span data-stu-id="f993c-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>

## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="f993c-120">Włącz trwałość dla usług przepływu pracy w kodzie</span><span class="sxs-lookup"><span data-stu-id="f993c-120">Enable Persistence for Workflow Services in Code</span></span>

<span data-ttu-id="f993c-121">Składowa **DurableInstancingOptions** klasy <xref:System.ServiceModel.WorkflowServiceHost> ma właściwość o nazwie **InstanceStore** , której można użyć do skojarzenia magazynu wystąpień z obiektem **WorkflowServiceHost**.</span><span class="sxs-lookup"><span data-stu-id="f993c-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

<span data-ttu-id="f993c-122">Gdy obiekt **WorkflowServiceHost** jest otwarty, trwałość jest włączana automatycznie, jeśli **DurableInstancingOptions. InstanceStore** nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="f993c-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>

<span data-ttu-id="f993c-123">Zwykle zachowanie usługi zapewnia konkretny magazyn wystąpień do użycia z hostem usługi przepływu pracy przy użyciu właściwości **InstanceStore** .</span><span class="sxs-lookup"><span data-stu-id="f993c-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="f993c-124">Na przykład SqlWorkflowInstanceStoreBehavior tworzy wystąpienie **obiekt SqlWorkflowInstanceStore**, konfiguruje je i przypisuje go do **DurableInstancingOptions. InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="f993c-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="f993c-125">Włącz trwałość dla usług przepływu pracy przy użyciu pliku konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="f993c-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>

<span data-ttu-id="f993c-126">Trwałości można włączyć za pomocą pliku konfiguracji aplikacji, dodając następujący kod do pliku App. config lub Web. config:</span><span class="sxs-lookup"><span data-stu-id="f993c-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>

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
