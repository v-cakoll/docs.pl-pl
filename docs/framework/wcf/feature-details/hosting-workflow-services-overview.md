---
title: Przegląd hostowania usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 10ea35fc1988e1b3e6ceb44aca098e63bfc7d7e4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597296"
---
# <a name="hosting-workflow-services-overview"></a>Przegląd hostowania usług przepływu pracy
Usługi przepływu pracy muszą być hostowane do wykonania. <xref:System.ServiceModel.WorkflowServiceHost>Jest hostem przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i komunikatów WCF (chociaż przepływy pracy nie są wymagane do obsługi komunikatów, aby można było je obsługiwać).  Integruje się ona również z zachowaniem trwałości, śledzenia i kontroli wystąpienia za pomocą zestawu zachowań usługi.  Podobnie jak w przypadku platformy WCF <xref:System.ServiceModel.ServiceHost> , <xref:System.ServiceModel.WorkflowServiceHost> może być samodzielny w dowolnej zarządzanej aplikacji .NET lub hostowanej w sieci Web (jako plik. xamlx) w usługach IIS/was.  W tematach w tej sekcji opisano sposób hostowania usługi przepływu pracy.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Hostowanie usług przepływu pracy](hosting-workflow-services.md)  
 Opisuje hostowanie usług przepływu pracy.  
  
 [Elementy wewnętrzne hosta usługi przepływu pracy](workflow-service-host-internals.md)  
 Opisuje sposób <xref:System.ServiceModel.WorkflowServiceHost> przetwarzania komunikatów przychodzących.  
  
 [Rozszerzalność hosta usługi przepływu pracy](workflow-service-host-extensibility.md)  
 Opisuje sposób rozszerania funkcji hosta usługi przepływu pracy.  
  
 [Punkt końcowy kontroli przepływu pracy](workflow-control-endpoint.md)  
 Opisuje sposób definiowania punktu końcowego, który umożliwia tworzenie wystąpień przepływu pracy.
  
 [Instrukcje: hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server](how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Demonstruje sposób hostowania istniejącej usługi przepływu pracy w sieci szkieletowej aplikacji systemu Windows Server.  
  
 [Konfigurowanie elementu WorkflowServiceHost](configuring-workflowservicehost.md)  
 Opisuje sposób kontrolowania zachowania trwałości, śledzenia, bezczynności i nieobsłużonego wyjątku.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Usługi przepływu pracy](workflow-services.md)
