---
title: "Rozszerzalność hosta usługi przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caff90b66007310c7b3ad24f2f084cc2282a7021
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-service-host-extensibility"></a>Rozszerzalność hosta usługi przepływu pracy
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]udostępnia <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasy do hostowania usług przepływu pracy. Ta klasa jest używana, gdy są samodzielnej obsługi usługi przepływu pracy w zarządzanej aplikacji lub usługi systemu Windows. Ta klasa służy również odnośnie do hostowania usługi przepływu pracy za pomocą usług Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS). <xref:System.ServiceModel.Activities.WorkflowServiceHost> Klasa udostępnia punkty rozszerzenia, dzięki którym można dodać niestandardowe rozszerzenia zmianę zachowania bezczynności i obsługi innych niż usługowe przepływów pracy (przepływy pracy, które nie należy używać działania obsługi komunikatów).  
  
## <a name="workflow-service-host-extensions"></a>Rozszerzenia hosta usługi przepływu pracy  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> Zawiera <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> właściwości typu <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> zapewnia metody do dodawania rozszerzenia do <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Użyj <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metodę, aby dodać rozszerzenie dla każdego wystąpienia usługi przepływu pracy. Delegat określony nazywa się do utworzenia nowego rozszerzenia, gdy wystąpienie usługi przepływu pracy jest utworzony lub załadowany z magazynu. Użyj <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metodę, aby dodać rozszerzenie dla każdego hosta usługi przepływu pracy, jedno wystąpienie rozszerzenia jest współdzielona przez wszystkie wystąpienia usługi przepływu pracy.  
  
## <a name="react-to-unhandled-exceptions"></a>Reagowanie na nieobsługiwanych wyjątków  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Umożliwia określenie akcji do wykonania, jeśli wystąpi nieobsługiwany wyjątek w ramach usługi przepływu pracy. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> Właściwość określa jeden z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> wartości:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon>— Przerywa wystąpienie usługi przepływu pracy.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend>— Przywraca do ostatniego utrwalonego stanu i wstrzymuje wystąpienie usługi przepływu pracy. To tylko wtedy, gdy przepływ pracy jest już co najmniej raz utrwalone. Jeśli nie jest wystąpieniem przepływu pracy zostało przerwane.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>— Umożliwia anulowanie tego wystąpienia.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate>— Kończy wystąpienie.  
  
 To zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Go można również skonfigurować w pliku konfiguracji, jak pokazano w poniższym przykładzie.  
  
```xml
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />        
        </behavior>  
      </serviceBehaviors>  
```  
  
## <a name="hosting-non-service-workflows"></a>Hosting innych niż usługowe przepływów pracy  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>może służyć do obsługi przepływów pracy z systemem innym niż usługi lub przepływy pracy, które albo zaczyna się od <xref:System.ServiceModel.Activities.Receive> działania lub przepływów pracy, które nie korzystają z działania obsługi wiadomości. Usługi przepływu pracy, ale zwykle zaczynać <xref:System.ServiceModel.Activities.Receive> działania. Gdy <xref:System.ServiceModel.Activities.WorkflowServiceHost> odbiera komunikat dla usługi przepływu pracy, jeśli nie jest jeszcze uruchomiona (lub utrwalone) nowego wystąpienia usługi przepływu pracy jest tworzona. Jeśli przepływ pracy nie zaczyna się od działania Receive, nie można uruchomić wysyłając wiadomość, ponieważ nie istnieje żadne działania do odbierania wiadomości. Do obsługi innych niż usługowe przepływu pracy, klasa wyprowadzona z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> i zastąpić <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>, i <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>. Zastąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> aby Podaj identyfikator wystąpienia preferowany. Zastąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> można utworzyć kontekstu Tworzenie niestandardowego przepływu pracy lub wypełnić istniejące wystąpienie <xref:System.ServiceModel.Activities.WorkflowCreationContext>. Zastąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> ręcznie wyodrębnić zakładki z komunikatu przychodzącego. Jeśli przesłonięcia tej metody należy wywołać <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> w jego treści, tak aby odpowiedzieć na wiadomość wysłana do WorkflowHostingEndpoint. Jeśli to zrobisz, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> limit może zostać przekroczony po pewnym czasie. W kontrakty dwukierunkowe, można wykryć niewykonanie wywołania <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> ze względu na błąd klienta odpowiedzi. W kontraktach jednokierunkowe nie może rozpoznać błąd do wywołania, które uległy awarii <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> momentu za późno po <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> został przekroczony limit przepustnicy. Aby uzyskać więcej informacji, zobacz [WorkflowHostingEndpoint Wznów zakładki](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)do utworzenia nowego wystąpienia przepływu pracy z systemem innym niż usługi, należy zadeklarować kontraktu usługi, który definiuje operację, która tworzy nowe wystąpienie. Operacja tworzenia powinno zająć IDictionary\<string, object > do przekazania wszelkie wymagane parametry przepływu pracy. Ten kontrakt niejawnie jest implementowany przez <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-klasy. Odnośnie do hostowania przepływu pracy, dodaje wystąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-pochodnej klasy do hosta przez wywołanie metody <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> i Wywołaj <!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`. Aby utworzyć wystąpienie przepływu pracy, należy utworzyć <xref:System.ServiceModel.ChannelFactory%601> typ kontraktu usługi i wywołania <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Następnie można wywołać operacji tworzenia zdefiniowane w umowy serwisowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Działania dotyczące komunikatów](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
