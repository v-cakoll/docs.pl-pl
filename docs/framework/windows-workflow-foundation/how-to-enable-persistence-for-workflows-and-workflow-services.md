---
title: 'Instrukcje: Włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 6a2a8d73298e14f92f376b97b9637db91532e937
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761432"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="fe701-102">Instrukcje: Włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fe701-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="fe701-103">W tym temacie opisano włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fe701-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>  
  
## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="fe701-104">Włączanie stanów trwałych dla przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="fe701-104">Enable Persistence for Workflows</span></span>  
 <span data-ttu-id="fe701-105">Możesz skojarzyć magazyn wystąpienia z **WorkflowApplication** przy użyciu <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwość <xref:System.Activities.WorkflowApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="fe701-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="fe701-106"><xref:System.Activities.WorkflowApplication.Persist%2A> Metody zapisuje lub będzie się powtarzał przepływu pracy do wystąpienia magazynu skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="fe701-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="fe701-107"><xref:System.Activities.WorkflowApplication.Unload%2A> Metoda się powtarza przepływu pracy do magazynu wystąpienia, a następnie zwalnia wystąpienie z pamięci.</span><span class="sxs-lookup"><span data-stu-id="fe701-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="fe701-108">**Obciążenia** metoda ładuje przepływu pracy do ilości pamięci za pomocą danych przepływu pracy, przechowywane w magazynie w trwałości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fe701-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>  
  
 <span data-ttu-id="fe701-109">**Utrwalanie** metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fe701-109">The **Persist** method performs the following steps:</span></span>  
  
1. <span data-ttu-id="fe701-110">Wstrzymuje harmonogram przepływu pracy i czeka, aż przepływ pracy przejdzie w stan bezczynności.</span><span class="sxs-lookup"><span data-stu-id="fe701-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2. <span data-ttu-id="fe701-111">Będzie się powtarzał lub zapisuje przepływ pracy w magazynie w trwałości.</span><span class="sxs-lookup"><span data-stu-id="fe701-111">Persists or saves the workflow into the persistence store.</span></span>  
  
3. <span data-ttu-id="fe701-112">Wznawia harmonogram przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fe701-112">Resumes the workflow scheduler.</span></span>  
  
 <span data-ttu-id="fe701-113">**Zwolnienie** metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fe701-113">The **Unload** method performs the following steps:</span></span>  
  
1. <span data-ttu-id="fe701-114">Wstrzymuje harmonogram przepływu pracy i czeka, aż przepływ pracy przejdzie w stan bezczynności.</span><span class="sxs-lookup"><span data-stu-id="fe701-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2. <span data-ttu-id="fe701-115">Będzie się powtarzał lub zapisuje przepływ pracy w magazynie w trwałości.</span><span class="sxs-lookup"><span data-stu-id="fe701-115">Persists or saves the workflow into the persistence store.</span></span>  
  
3. <span data-ttu-id="fe701-116">Usuwa wystąpienie przepływu pracy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="fe701-116">Disposes the workflow instance in the memory.</span></span>  
  
 <span data-ttu-id="fe701-117">Zarówno **utrwalanie** i **zwolnienie** metody są blokowane, gdy przepływ pracy jest w strefie no-persist aż przepływ pracy zamyka strefy no-persist.</span><span class="sxs-lookup"><span data-stu-id="fe701-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="fe701-118">Metody będzie kontynuowane przy użyciu operacji utrwalania lub zwolnij, po zakończeniu strefy utrwalanie nie.</span><span class="sxs-lookup"><span data-stu-id="fe701-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="fe701-119">Jeśli strefa no-persist nie zostanie zakończone, zanim upłynie limit czasu lub jeśli proces trwałości trwa zbyt długo, zostanie zgłoszony TimeoutException.</span><span class="sxs-lookup"><span data-stu-id="fe701-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="fe701-120">Włączanie stanów trwałych dla usług przepływu pracy w kodzie</span><span class="sxs-lookup"><span data-stu-id="fe701-120">Enable Persistence for Workflow Services in Code</span></span>  
 <span data-ttu-id="fe701-121">**DurableInstancingOptions** członkiem <xref:System.ServiceModel.WorkflowServiceHost> klasa ma właściwość o nazwie **objekt InstanceStore** służące do kojarzenia magazyn wystąpienia z **elementu WorkflowServiceHost** .</span><span class="sxs-lookup"><span data-stu-id="fe701-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 <span data-ttu-id="fe701-122">Gdy **WorkflowServiceHost** jest otwarty, trwałości jest włączany automatycznie, jeżeli **DurableInstancingOptions.InstanceStore** nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="fe701-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>  
  
 <span data-ttu-id="fe701-123">Zazwyczaj zachowanie usługi zawiera konkretne wystąpienie magazynu do użycia z hosta usługi przepływu pracy przy użyciu **objekt InstanceStore** właściwości.</span><span class="sxs-lookup"><span data-stu-id="fe701-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="fe701-124">Na przykład SqlWorkflowInstanceStoreBehavior tworzy wystąpienie **SqlWorkflowInstanceStore**, konfiguruje je i przypisuje go do **DurableInstancingOptions.InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="fe701-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="fe701-125">Włączanie stanów trwałych dla przepływów pracy usługi przy użyciu pliku konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="fe701-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>  
 <span data-ttu-id="fe701-126">Stan trwały można włączyć za pomocą pliku konfiguracji aplikacji, dodając następujący kod do pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="fe701-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```
