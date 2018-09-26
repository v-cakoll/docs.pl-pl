---
title: Przegląd hostowania usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: dbe271e30e9c4e98a52c01ffaa21de25c127c7ff
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208460"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="0a3e5-102">Przegląd hostowania usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0a3e5-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="0a3e5-103">Musi być hostowany usług przepływu pracy do wykonania.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="0a3e5-104"><xref:System.ServiceModel.WorkflowServiceHost> Jest hostem out-of--box przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i komunikatów WCF (mimo że przepływy pracy nie są wymagane do obsługi komunikatów można hostować).</span><span class="sxs-lookup"><span data-stu-id="0a3e5-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="0a3e5-105">Integruje się również z trwałości, śledzenia i kontrolowania wystąpienia za pomocą zestawu zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="0a3e5-106">Podobnie jak w przypadku firmy WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> mogą być samodzielnie hostowane w dowolnej aplikacji zarządzanej .NET lub sieci web hostowanych (w formacie .xamlx) w usługach IIS / WAS.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="0a3e5-107">Tematy w tej sekcji opisano sposób hostowanie usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a3e5-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0a3e5-108">In This Section</span></span>  
 [<span data-ttu-id="0a3e5-109">Hostowanie usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0a3e5-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="0a3e5-110">W tym artykule opisano hostowania usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="0a3e5-111">Elementy wewnętrzne hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0a3e5-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="0a3e5-112">W tym artykule opisano sposób <xref:System.ServiceModel.WorkflowServiceHost> przetwarza przychodzące wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="0a3e5-113">Rozszerzalność hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0a3e5-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="0a3e5-114">Opisuje sposób rozszerzyć funkcjonalność hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="0a3e5-115">Punkt końcowy kontroli przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0a3e5-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="0a3e5-116">W tym artykule opisano, jak zdefiniować punkt końcowy, który służy do tworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>
  
 [<span data-ttu-id="0a3e5-117">Instrukcje: hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="0a3e5-117">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="0a3e5-118">Pokazuje, jak do hostowania istniejącej usługi przepływu pracy w AppFabric w systemie Windows Server.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-118">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="0a3e5-119">Konfigurowanie elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="0a3e5-119">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="0a3e5-120">W tym artykule opisano sposób kontrolowania trwałości, śledzenia i zachowanie bezczynności i nieobsługiwanych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-120">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0a3e5-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="0a3e5-121">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="0a3e5-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0a3e5-122">Related Sections</span></span>  
 [<span data-ttu-id="0a3e5-123">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0a3e5-123">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
