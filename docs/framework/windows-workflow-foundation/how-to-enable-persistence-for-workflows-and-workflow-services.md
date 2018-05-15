---
title: 'Porady: Włącz trwałość dla przepływów pracy i usług przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 35158c45217e764bc2e27dac26f8d680e5897fa9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="288a8-102">Porady: Włącz trwałość dla przepływów pracy i usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="288a8-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="288a8-103">W tym temacie opisano, jak do włączenia trwałości dla przepływów pracy i usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="288a8-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>  
  
## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="288a8-104">Włącz trwałość dla przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="288a8-104">Enable Persistence for Workflows</span></span>  
 <span data-ttu-id="288a8-105">Można skojarzyć magazyn wystąpienia z **WorkflowApplication** za pomocą <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwość <xref:System.Activities.WorkflowApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="288a8-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="288a8-106"><xref:System.Activities.WorkflowApplication.Persist%2A> Metody zapisuje lub będzie się powtarzał przepływu pracy do wystąpienia magazynu skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="288a8-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="288a8-107"><xref:System.Activities.WorkflowApplication.Unload%2A> Metoda się powtarza przepływu pracy w magazynie wystąpień, a następnie zwalnia wystąpienie z pamięci.</span><span class="sxs-lookup"><span data-stu-id="288a8-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="288a8-108">**Obciążenia** metody ładuje przepływu pracy do pamięci za pomocą przepływu pracy danych przechowywanych w magazynie informacji o trwałości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="288a8-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>  
  
 <span data-ttu-id="288a8-109">**Utrwalanie** metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="288a8-109">The **Persist** method performs the following steps:</span></span>  
  
1.  <span data-ttu-id="288a8-110">Wstrzymuje harmonogramu przepływu pracy i czeka, aż przepływ pracy wchodzi w stan bezczynności.</span><span class="sxs-lookup"><span data-stu-id="288a8-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2.  <span data-ttu-id="288a8-111">Będzie nadal występował lub zapisuje przepływ pracy w magazynie informacji o trwałości.</span><span class="sxs-lookup"><span data-stu-id="288a8-111">Persists or saves the workflow into the persistence store.</span></span>  
  
3.  <span data-ttu-id="288a8-112">Wznawia harmonogramu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="288a8-112">Resumes the workflow scheduler.</span></span>  
  
 <span data-ttu-id="288a8-113">**Zwolnienie** metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="288a8-113">The **Unload** method performs the following steps:</span></span>  
  
1.  <span data-ttu-id="288a8-114">Wstrzymuje harmonogramu przepływu pracy i czeka, aż przepływ pracy wchodzi w stan bezczynności.</span><span class="sxs-lookup"><span data-stu-id="288a8-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2.  <span data-ttu-id="288a8-115">Będzie nadal występował lub zapisuje przepływ pracy w magazynie informacji o trwałości.</span><span class="sxs-lookup"><span data-stu-id="288a8-115">Persists or saves the workflow into the persistence store.</span></span>  
  
3.  <span data-ttu-id="288a8-116">Usuwa wystąpienie przepływu pracy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="288a8-116">Disposes the workflow instance in the memory.</span></span>  
  
 <span data-ttu-id="288a8-117">Zarówno **utrwalanie** i **zwolnienie** metody zablokuje podczas przepływu pracy jest w strefie no-persist strefy no-persist kończy działanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="288a8-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="288a8-118">Metody będzie kontynuowane przy użyciu operacji utrwalania lub unload po zakończeniu strefy utrwalania nie.</span><span class="sxs-lookup"><span data-stu-id="288a8-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="288a8-119">Jeśli strefa no-persist nie zostanie zakończone, zanim upłynie limit czasu lub zbyt długo procesu trwałości, zostanie zgłoszony TimeoutException.</span><span class="sxs-lookup"><span data-stu-id="288a8-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="288a8-120">Włącz trwałość dla usług przepływu pracy w kodzie</span><span class="sxs-lookup"><span data-stu-id="288a8-120">Enable Persistence for Workflow Services in Code</span></span>  
 <span data-ttu-id="288a8-121">**DurableInstancingOptions** członkiem <xref:System.ServiceModel.WorkflowServiceHost> klasa ma właściwości o nazwie **InstanceStore** której można skojarzyć magazyn wystąpienia z **obiektu WorkflowServiceHost** .</span><span class="sxs-lookup"><span data-stu-id="288a8-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 <span data-ttu-id="288a8-122">Gdy **obiektu WorkflowServiceHost** jest otwarty, trwałości jest włączany automatycznie, jeżeli **DurableInstancingOptions.InstanceStore** nie jest zerowa.</span><span class="sxs-lookup"><span data-stu-id="288a8-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>  
  
 <span data-ttu-id="288a8-123">Zwykle, zachowanie usługi zapewnia magazynu konkretne wystąpienie ma być używany z hosta usługi przepływu pracy przy użyciu **InstanceStore** właściwości.</span><span class="sxs-lookup"><span data-stu-id="288a8-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="288a8-124">Na przykład SqlWorkflowInstanceStoreBehavior tworzy wystąpienie **SqlWorkflowInstanceStore**, konfiguruje ją i przypisuje go do **DurableInstancingOptions.InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="288a8-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="288a8-125">Włącz trwałość dla usług przepływu pracy przy użyciu pliku konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="288a8-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>  
 <span data-ttu-id="288a8-126">Trwałości można włączyć przy użyciu pliku konfiguracji aplikacji, dodając następujący kod do pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="288a8-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>  
  
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
