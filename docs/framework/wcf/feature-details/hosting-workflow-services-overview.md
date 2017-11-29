---
title: "Przegląd hostowania usług przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2c38cd352eb860982b9b1e3aa32daa7aeeee9ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
  
 [Porady: hosta z systemem innym niż usługi przepływu pracy w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 Pokazuje hosting przepływu pracy, który nie jest usługi przepływu pracy w programie IIS.  
  
 [Porady: hostowanie usługi przepływu pracy przy użyciu rozwiązania Windows Server AppFabric](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
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
