---
title: 'Instrukcje: Konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 69c6b1ce11d735181390a0c67df2f8dbea4f906c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185310"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="9a668-102">Instrukcje: Konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="9a668-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="9a668-103">Jest <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> to zachowanie, które umożliwia określenie akcji do podjęcia, jeśli nieobsługiwać <xref:System.ServiceModel.Activities.WorkflowServiceHost>wyjątek występuje w przepływie pracy hostowane w .</span><span class="sxs-lookup"><span data-stu-id="9a668-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="9a668-104">W tym temacie pokazano, jak skonfigurować to zachowanie w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="9a668-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="9a668-105">Aby skonfigurować przepływ pracyUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="9a668-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="9a668-106">Dodaj `workflowUnhandledException` <> element w <`behavior`> element w <`serviceBehaviors`> element, przy użyciu atrybutu, `action` aby określić akcję do podjęcia, gdy wystąpi nieobsługiwany wyjątek, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9a668-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="9a668-107">W poprzedniej próbce konfiguracji jest obsługiwana uproszczona konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="9a668-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="9a668-108">Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="9a668-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="9a668-109">To zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9a668-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="9a668-110">Atrybut `action` <`workflowUnhandledException`> element można ustawić na jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="9a668-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="9a668-111">**Porzucić**</span><span class="sxs-lookup"><span data-stu-id="9a668-111">**abandon**</span></span>  
     <span data-ttu-id="9a668-112">Przerywa wystąpienie w pamięci bez dotykania stanu utrwalone wystąpienie (oznacza to, że wycofać do ostatniego punktu persist).</span><span class="sxs-lookup"><span data-stu-id="9a668-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="9a668-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="9a668-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="9a668-114">Przerywa wystąpienie w pamięci i aktualizuje utrwalone wystąpienie do zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="9a668-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="9a668-115">**Anuluj**</span><span class="sxs-lookup"><span data-stu-id="9a668-115">**cancel**</span></span>  
     <span data-ttu-id="9a668-116">Wywołuje programy obsługi anulowania dla wystąpienia, a następnie kończy wystąpienie w pamięci, co może również usunąć go z magazynu wystąpień</span><span class="sxs-lookup"><span data-stu-id="9a668-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="9a668-117">**Zakończyć**</span><span class="sxs-lookup"><span data-stu-id="9a668-117">**terminate**</span></span>  
     <span data-ttu-id="9a668-118">Kończy wystąpienie w pamięci i usuwa je z magazynu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="9a668-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="9a668-119">Aby uzyskać <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>więcej informacji na temat , zobacz [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="9a668-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a668-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a668-120">See also</span></span>

- [<span data-ttu-id="9a668-121">Rozszerzalność hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9a668-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="9a668-122">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9a668-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
