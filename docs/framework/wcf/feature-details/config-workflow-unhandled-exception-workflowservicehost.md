---
title: 'Instrukcje: konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: aec2fd80e10ae1959b29c0883d51c4045517d792
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957257"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="7cc45-102">Instrukcje: konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="7cc45-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="7cc45-103">Jest zachowanie, które pozwala określić akcję do wykonania, jeśli wystąpi nieobsługiwany wyjątek w przepływie pracy hostowanym w <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior></span><span class="sxs-lookup"><span data-stu-id="7cc45-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="7cc45-104">W tym temacie opisano sposób konfigurowania tego zachowania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7cc45-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="7cc45-105">Aby skonfigurować WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="7cc45-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="7cc45-106">Dodaj element <`workflowUnhandledException`> w elemencie <`behavior`> w elemencie <`serviceBehaviors`>, używając `action` atrybutu, aby określić akcję wykonywaną po wystąpieniu nieobsługiwanego wyjątku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7cc45-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="7cc45-107">Poprzedni przykład konfiguracji używa uproszczonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7cc45-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="7cc45-108">Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="7cc45-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="7cc45-109">Takie zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7cc45-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="7cc45-110">`action` Atrybut<`workflowUnhandledException`elementu > można ustawić na jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="7cc45-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="7cc45-111">**rzucić**</span><span class="sxs-lookup"><span data-stu-id="7cc45-111">**abandon**</span></span>  
     <span data-ttu-id="7cc45-112">Przerywa wystąpienie w pamięci bez dotykania utrwalonego stanu wystąpienia (oznacza to, że wraca do ostatniego punktu utrwalania).</span><span class="sxs-lookup"><span data-stu-id="7cc45-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="7cc45-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="7cc45-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="7cc45-114">Przerywa wystąpienie w pamięci i aktualizuje wystąpienie trwałe, które zostanie zawieszone.</span><span class="sxs-lookup"><span data-stu-id="7cc45-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="7cc45-115">**cancel**</span><span class="sxs-lookup"><span data-stu-id="7cc45-115">**cancel**</span></span>  
     <span data-ttu-id="7cc45-116">Wywołuje programy obsługi anulowania dla wystąpienia, a następnie kończy wystąpienie w pamięci, co może również usunąć je z magazynu wystąpień</span><span class="sxs-lookup"><span data-stu-id="7cc45-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="7cc45-117">**kończyć**</span><span class="sxs-lookup"><span data-stu-id="7cc45-117">**terminate**</span></span>  
     <span data-ttu-id="7cc45-118">Kończy wystąpienie w pamięci i usuwa je z magazynu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="7cc45-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="7cc45-119">Aby uzyskać więcej informacji <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>na temat, zobacz [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="7cc45-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc45-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cc45-120">See also</span></span>

- [<span data-ttu-id="7cc45-121">Rozszerzalność hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7cc45-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="7cc45-122">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7cc45-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
