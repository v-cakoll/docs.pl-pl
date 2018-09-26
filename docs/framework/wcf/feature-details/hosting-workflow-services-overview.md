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
# <a name="hosting-workflow-services-overview"></a>Przegląd hostowania usług przepływu pracy
Musi być hostowany usług przepływu pracy do wykonania. <xref:System.ServiceModel.WorkflowServiceHost> Jest hostem out-of--box przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i komunikatów WCF (mimo że przepływy pracy nie są wymagane do obsługi komunikatów można hostować).  Integruje się również z trwałości, śledzenia i kontrolowania wystąpienia za pomocą zestawu zachowania usługi.  Podobnie jak w przypadku firmy WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> mogą być samodzielnie hostowane w dowolnej aplikacji zarządzanej .NET lub sieci web hostowanych (w formacie .xamlx) w usługach IIS / WAS.  Tematy w tej sekcji opisano sposób hostowanie usługi przepływu pracy.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Hostowanie usług przepływu pracy](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 W tym artykule opisano hostowania usług przepływu pracy.  
  
 [Elementy wewnętrzne hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 W tym artykule opisano sposób <xref:System.ServiceModel.WorkflowServiceHost> przetwarza przychodzące wiadomości.  
  
 [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 Opisuje sposób rozszerzyć funkcjonalność hosta usługi przepływu pracy.  
  
 [Punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 W tym artykule opisano, jak zdefiniować punkt końcowy, który służy do tworzenia wystąpienia przepływu pracy.
  
 [Instrukcje: hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Pokazuje, jak do hostowania istniejącej usługi przepływu pracy w AppFabric w systemie Windows Server.  
  
 [Konfigurowanie elementu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 W tym artykule opisano sposób kontrolowania trwałości, śledzenia i zachowanie bezczynności i nieobsługiwanych wyjątków.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
