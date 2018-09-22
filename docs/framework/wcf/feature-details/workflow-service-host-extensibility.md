---
title: Rozszerzalność hosta usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: 6541558601c8f5daf255f2e7e5d774e41b59be2d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696348"
---
# <a name="workflow-service-host-extensibility"></a>Rozszerzalność hosta usługi przepływu pracy
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] udostępnia <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasy do hostowania usług przepływu pracy. Ta klasa jest używana, gdy samodzielnie obsługujesz usługi przepływu pracy w zarządzanej aplikacji lub usługi Windows. Ta klasa jest również używana w przypadku hostowania usługi przepływu pracy przy użyciu usług Internet Information Services (IIS) lub Windows Process Activation Service (WAS). <xref:System.ServiceModel.Activities.WorkflowServiceHost> Klasa udostępnia punkty rozszerzenia, które umożliwiają dodanie rozszerzenia niestandardowe, zmienić zachowanie bezczynności, a następnie Hostuj przepływy pracy bez usługi (przepływy pracy, które nie korzystają z działań dotyczących komunikatów).  
  
## <a name="workflow-service-host-extensions"></a>Rozszerzenia hosta usługi przepływu pracy  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> Zawiera <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> właściwości typu <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> , udostępnia metody umożliwiające dodawanie rozszerzeń do <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Użyj <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metodę, aby dodać rozszerzenie dla poszczególnych wystąpień usługi przepływu pracy. Delegat określony jest wywoływana, aby utworzyć nowe rozszerzenie, gdy wystąpienie usługi przepływu pracy zostanie utworzony lub załadowane z magazynu stanu trwałego. Użyj <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metodę, aby dodać rozszerzenie dla każdego hosta usługi przepływu pracy, jedno wystąpienie rozszerzenia jest współdzielona przez wszystkich wystąpień usługi przepływu pracy.  
  
## <a name="react-to-unhandled-exceptions"></a>Reagowanie na nieobsłużonych wyjątków  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Można określić akcję do wykonania, jeśli wystąpił nieobsługiwany wyjątek wystąpi wewnątrz usługi przepływu pracy. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> Właściwości określa jedno z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> wartości:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon> — Przerywa wystąpienie usługi przepływu pracy.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend> — Wycofanie do ostatniego utrwalonego stanu i wstrzymuje wystąpienie usługi przepływu pracy. To tylko wtedy, gdy przepływ pracy już zawiera co najmniej raz utrwalone. W przeciwnym razie wystąpienie przepływu pracy zostało przerwane.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel> — Anuluje wystąpienia.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate> — Kończy się wystąpienia.  
  
 To zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Jego można również skonfigurować w pliku konfiguracji, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="hosting-non-service-workflows"></a>Hostowanie przepływów pracy bez usługi  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> może służyć do hostowania przepływów pracy bez usługi lub przepływów pracy, które albo nie zaczynają się od <xref:System.ServiceModel.Activities.Receive> działania lub przepływów pracy, które nie korzystają z działań dotyczących komunikatów. Usługi przepływu pracy zwykle zaczynają się od <xref:System.ServiceModel.Activities.Receive> działania. Gdy <xref:System.ServiceModel.Activities.WorkflowServiceHost> odbiera komunikat dla usługi przepływu pracy, jeśli go nie jest już uruchomiony (lub utrwalona) nowego wystąpienia usługi przepływu pracy jest tworzony. Jeśli przepływ pracy zaczyna się od działania odbierania, nie można uruchomić wysyłając wiadomość, ponieważ nie ma działania do odbierania wiadomości. Hostowanie przepływu pracy bez usługi, należy wyprowadzić klasę z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> i zastąpić <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>, i <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>. Zastąp <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> aby Podaj identyfikator wystąpienia preferowany. Zastąp <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> tworzy kontekst tworzenia niestandardowych przepływów pracy i wypełniać istniejące wystąpienie <xref:System.ServiceModel.Activities.WorkflowCreationContext>. Zastąp <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> ręcznie wyodrębnić zakładki z komunikatu przychodzącego. Jeśli zastąpisz tę metodę należy wywołać <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> w jej treści w taki sposób, aby odpowiedzieć na komunikat wysłany do WorkflowHostingEndpoint. Jeśli to zrobisz, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> limit może zostać przekroczony po pewnym czasie. W kontrakty dwukierunkowe, można wykryć usługi nie można wywołać <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> ze względu na błąd klienta odpowiedzi. W kontraktach jednokierunkowe nie może rozpoznać błędu elementu nie można wywołać <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> dopóki nie jest za późno po <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> został przekroczony limit przepustowości. Aby uzyskać więcej informacji, zobacz [WorkflowHostingEndpoint wznowienie zakładki](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)Aby utworzyć nowe wystąpienie przepływu pracy bez usługi, należy zadeklarować kontraktu usługi, który definiuje operację, która tworzy nowe wystąpienie. Operacja utworzenia powinno zająć elementu IDictionary\<string, object > przejdą którejkolwiek wymagane parametry przepływu pracy. Ten kontrakt niejawnie jest implementowany przez <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-klasy pochodnej. W przypadku hostowania przepływu pracy, dodaje wystąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-klasy pochodnej do hosta przez wywołanie metody <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> i wywołać <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Aby utworzyć wystąpienie przepływu pracy, należy utworzyć <xref:System.ServiceModel.ChannelFactory%601> typ kontraktu usługi i wywołania <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Następnie możesz wywołać operacji tworzenia, zdefiniowane w Twojej umowy serwisowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Działania dotyczące komunikatów](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
