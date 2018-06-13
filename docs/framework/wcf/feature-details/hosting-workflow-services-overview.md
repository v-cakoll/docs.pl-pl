---
title: Przegląd hostowania usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 7b5de31b5931af13b41b11af6e48a52b5628e27c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489563"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="e8da3-102">Przegląd hostowania usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e8da3-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="e8da3-103">Usługi przepływu pracy musi być hostowany na wykonanie.</span><span class="sxs-lookup"><span data-stu-id="e8da3-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="e8da3-104"><xref:System.ServiceModel.WorkflowServiceHost> Jest hostem poza pole przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i wiadomości WCF (mimo że przepływy pracy nie są wymagane do obsługi komunikatów znajdować).</span><span class="sxs-lookup"><span data-stu-id="e8da3-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="e8da3-105">Integruje się również z utrwalania, śledzenia i kontroli wystąpienia za pomocą zestawu zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="e8da3-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="e8da3-106">Podobnie jak jego WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> mogą być samodzielnie hostowana w dowolnej aplikacji zarządzanej .NET lub sieci web hostowanej (jako plik .xamlx) w usługach IIS / WAS.</span><span class="sxs-lookup"><span data-stu-id="e8da3-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="e8da3-107">Tematy w tej sekcji opisano sposób hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e8da3-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8da3-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e8da3-108">In This Section</span></span>  
 [<span data-ttu-id="e8da3-109">Hostowanie usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e8da3-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="e8da3-110">W tym artykule opisano hostowania usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e8da3-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="e8da3-111">Elementy wewnętrzne hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e8da3-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="e8da3-112">Opisuje sposób <xref:System.ServiceModel.WorkflowServiceHost> przetwarza wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e8da3-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="e8da3-113">Rozszerzalność hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e8da3-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="e8da3-114">Opisuje sposób rozszerzyć funkcjonalność hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e8da3-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="e8da3-115">Punkt końcowy kontroli przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e8da3-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="e8da3-116">Opisuje sposób zdefiniowania punktu końcowego, który służy do tworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e8da3-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>  
  
 [<span data-ttu-id="e8da3-117">Instrukcje: hostowanie przepływu pracy bez usługi przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="e8da3-117">How to: Host a non-service workflow in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 <span data-ttu-id="e8da3-118">Pokazuje hosting przepływu pracy, który nie jest usługi przepływu pracy w programie IIS.</span><span class="sxs-lookup"><span data-stu-id="e8da3-118">Demonstrates hosting a workflow that is not a workflow service in IIS.</span></span>  
  
 [<span data-ttu-id="e8da3-119">Instrukcje: hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="e8da3-119">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="e8da3-120">Pokazuje, jak udostępniać istniejącej usługi przepływu pracy w systemu Windows Server AppFabric.</span><span class="sxs-lookup"><span data-stu-id="e8da3-120">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="e8da3-121">Konfigurowanie elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="e8da3-121">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="e8da3-122">Zawiera opis sposobu kontrolowania utrwalania, śledzenia zachowania bezczynności i nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e8da3-122">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e8da3-123">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="e8da3-123">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="e8da3-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e8da3-124">Related Sections</span></span>  
 [<span data-ttu-id="e8da3-125">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e8da3-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
