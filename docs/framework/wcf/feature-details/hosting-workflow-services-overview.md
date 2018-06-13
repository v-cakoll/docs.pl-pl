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
# <a name="hosting-workflow-services-overview"></a>Przegląd hostowania usług przepływu pracy
Usługi przepływu pracy musi być hostowany na wykonanie. <xref:System.ServiceModel.WorkflowServiceHost> Jest hostem poza pole przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i wiadomości WCF (mimo że przepływy pracy nie są wymagane do obsługi komunikatów znajdować).  Integruje się również z utrwalania, śledzenia i kontroli wystąpienia za pomocą zestawu zachowania usługi.  Podobnie jak jego WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> mogą być samodzielnie hostowana w dowolnej aplikacji zarządzanej .NET lub sieci web hostowanej (jako plik .xamlx) w usługach IIS / WAS.  Tematy w tej sekcji opisano sposób hosta usługi przepływu pracy.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Hostowanie usług przepływu pracy](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 W tym artykule opisano hostowania usług przepływu pracy.  
  
 [Elementy wewnętrzne hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 Opisuje sposób <xref:System.ServiceModel.WorkflowServiceHost> przetwarza wiadomości przychodzących.  
  
 [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 Opisuje sposób rozszerzyć funkcjonalność hosta usługi przepływu pracy.  
  
 [Punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 Opisuje sposób zdefiniowania punktu końcowego, który służy do tworzenia wystąpienia przepływu pracy.  
  
 [Instrukcje: hostowanie przepływu pracy bez usługi przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 Pokazuje hosting przepływu pracy, który nie jest usługi przepływu pracy w programie IIS.  
  
 [Instrukcje: hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Pokazuje, jak udostępniać istniejącej usługi przepływu pracy w systemu Windows Server AppFabric.  
  
 [Konfigurowanie elementu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 Zawiera opis sposobu kontrolowania utrwalania, śledzenia zachowania bezczynności i nieobsługiwany wyjątek.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
