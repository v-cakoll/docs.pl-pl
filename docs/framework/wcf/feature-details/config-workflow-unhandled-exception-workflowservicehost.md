---
title: 'Instrukcje: konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: cd3729019b5371b5313bba3814758c723c0d448a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318750"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="ac375-102">Instrukcje: konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="ac375-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="ac375-103"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> To zachowanie, które można określić akcję do wykonania sytuacji Wystąpił nieobsługiwany wyjątek w przepływie pracy hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ac375-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="ac375-104">W tym temacie przedstawiono sposób skonfigurowania tego zachowania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ac375-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="ac375-105">Aby skonfigurować WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="ac375-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="ac375-106">Dodaj <`workflowUnhandledException`> elementu <`behavior`> elemencie <`serviceBehaviors`> element, przy użyciu `action` atrybutu, aby określić akcję do wykonania po wystąpieniu nieobsługiwanego wyjątku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ac375-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="ac375-107">Poprzedni przykład konfiguracji używa uproszczona konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="ac375-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="ac375-108">Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ac375-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="ac375-109">To zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ac375-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="ac375-110">`action` Atrybut <`workflowUnhandledException`> element może być ustawiony na jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="ac375-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     **<span data-ttu-id="ac375-111">Porzuć</span><span class="sxs-lookup"><span data-stu-id="ac375-111">abandon</span></span>**  
     <span data-ttu-id="ac375-112">Przerywa wystąpienia w pamięci bez dotykania stanu utrwalonego wystąpienia, (który jest wycofać do ostatniego punktu utrwalanie).</span><span class="sxs-lookup"><span data-stu-id="ac375-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     **<span data-ttu-id="ac375-113">abandonAndSuspend</span><span class="sxs-lookup"><span data-stu-id="ac375-113">abandonAndSuspend</span></span>**  
     <span data-ttu-id="ac375-114">Przerywa wystąpienia w pamięci i aktualizuje utrwalonego wystąpienia zawieszona.</span><span class="sxs-lookup"><span data-stu-id="ac375-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     **<span data-ttu-id="ac375-115">Anuluj</span><span class="sxs-lookup"><span data-stu-id="ac375-115">cancel</span></span>**  
     <span data-ttu-id="ac375-116">Wywołuje anulowania obsługi dla tego wystąpienia, a następnie przetwarza wystąpienia w pamięci, co może też spowodować usunięcie go z magazynu wystąpień</span><span class="sxs-lookup"><span data-stu-id="ac375-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     **<span data-ttu-id="ac375-117">terminate</span><span class="sxs-lookup"><span data-stu-id="ac375-117">terminate</span></span>**  
     <span data-ttu-id="ac375-118">Kończy wystąpienia w pamięci i usuwa go z magazynu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ac375-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="ac375-119">Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, zobacz [rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="ac375-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac375-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac375-120">See also</span></span>

- [<span data-ttu-id="ac375-121">Rozszerzalność hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ac375-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="ac375-122">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ac375-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
