---
title: Przegląd hostowania usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: dbe271e30e9c4e98a52c01ffaa21de25c127c7ff
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850651"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="9c161-102">Przegląd hostowania usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9c161-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="9c161-103">Musi być hostowany usług przepływu pracy do wykonania.</span><span class="sxs-lookup"><span data-stu-id="9c161-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="9c161-104"><xref:System.ServiceModel.WorkflowServiceHost> Jest hostem out-of--box przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i komunikatów WCF (mimo że przepływy pracy nie są wymagane do obsługi komunikatów można hostować).</span><span class="sxs-lookup"><span data-stu-id="9c161-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="9c161-105">Integruje się również z trwałości, śledzenia i kontrolowania wystąpienia za pomocą zestawu zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="9c161-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="9c161-106">Podobnie jak w przypadku firmy WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> mogą być samodzielnie hostowane w dowolnej aplikacji zarządzanej .NET lub sieci web hostowanych (w formacie .xamlx) w usługach IIS / WAS.</span><span class="sxs-lookup"><span data-stu-id="9c161-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="9c161-107">Tematy w tej sekcji opisano sposób hostowanie usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9c161-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c161-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9c161-108">In This Section</span></span>  
 [<span data-ttu-id="9c161-109">Hostowanie usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9c161-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="9c161-110">W tym artykule opisano hostowania usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9c161-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="9c161-111">Elementy wewnętrzne hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9c161-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="9c161-112">W tym artykule opisano sposób <xref:System.ServiceModel.WorkflowServiceHost> przetwarza przychodzące wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9c161-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="9c161-113">Rozszerzalność hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9c161-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="9c161-114">Opisuje sposób rozszerzyć funkcjonalność hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9c161-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="9c161-115">Punkt końcowy kontroli przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9c161-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="9c161-116">W tym artykule opisano, jak zdefiniować punkt końcowy, który służy do tworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9c161-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>
  
 [<span data-ttu-id="9c161-117">Instrukcje: hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="9c161-117">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="9c161-118">Pokazuje, jak do hostowania istniejącej usługi przepływu pracy w AppFabric w systemie Windows Server.</span><span class="sxs-lookup"><span data-stu-id="9c161-118">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="9c161-119">Konfigurowanie elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="9c161-119">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="9c161-120">W tym artykule opisano sposób kontrolowania trwałości, śledzenia i zachowanie bezczynności i nieobsługiwanych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="9c161-120">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9c161-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="9c161-121">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="9c161-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9c161-122">Related Sections</span></span>  
 [<span data-ttu-id="9c161-123">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9c161-123">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
