---
title: Rozszerzalność hosta usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: 776fc78cd3f5b012dd40576fe56f71835e949708
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184156"
---
# <a name="workflow-service-host-extensibility"></a>Rozszerzalność hosta usługi przepływu pracy
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]zapewnia <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasę hostingu usług przepływu pracy. Ta klasa jest używana, gdy samodzielnie hostujesz usługę przepływu pracy w aplikacji zarządzanej lub usłudze systemu Windows. Ta klasa jest również używana podczas hostowania usługi przepływu pracy za pomocą internetowych usług informacyjnych (IIS) lub usługi aktywacji procesów systemu Windows (WAS). Klasa <xref:System.ServiceModel.Activities.WorkflowServiceHost> udostępnia punkty rozszerzenia, które umożliwiają dodawanie rozszerzeń niestandardowych, zmienianie bezczynności i hostowanie przepływów pracy niezwiązanych z usługą (przepływów pracy, które nie używają działań związanych z wiadomością).  
  
## <a name="workflow-service-host-extensions"></a>Rozszerzenia hosta usług przepływu pracy  
 Zawiera <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> właściwość typu, <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> która zawiera metody dodawania rozszerzeń do . <xref:System.ServiceModel.Activities.WorkflowServiceHost> Użyj <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metody, aby dodać rozszerzenie dla każdego wystąpienia usługi przepływu pracy. Określony pełnomocnik jest wywoływany w celu utworzenia nowego rozszerzenia, gdy wystąpienie usługi przepływu pracy jest tworzone lub ładowane z magazynu trwałości. Użyj <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metody, aby dodać rozszerzenie dla każdego hosta usługi przepływu pracy, jedno wystąpienie rozszerzenia jest współużytkowane dla wszystkich wystąpień usługi przepływu pracy.  
  
## <a name="react-to-unhandled-exceptions"></a>Reaguj na nieobsługiwały się wyjątki  
 Umożliwia <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> określenie akcji do podjęcia, jeśli nieobsługiwać wyjątek występuje w usłudze przepływu pracy. Właściwość <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> określa jedną <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> z wartości:  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon>– Przerywa wystąpienie usługi przepływu pracy.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend>– Wycofuje do ostatniego stanu utrwalone i zawiesza wystąpienie usługi przepływu pracy. Dzieje się tak tylko wtedy, gdy przepływ pracy został już utrwalony co najmniej raz. Jeśli nie wystąpienie przepływu pracy zostanie przerwane.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>– Anuluje wystąpienie.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate>– Kończy wystąpienie.  
  
 To zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Można go również skonfigurować w pliku konfiguracyjnym, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="hosting-non-service-workflows"></a>Hostowanie przepływów pracy niesłużących  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>może służyć do obsługi przepływów pracy niezwiązanych z usługą <xref:System.ServiceModel.Activities.Receive> lub przepływów pracy, które nie rozpoczynają się od działania lub przepływów pracy, które nie używają działań obsługi wiadomości. Usługi przepływu pracy zwykle <xref:System.ServiceModel.Activities.Receive> zaczynają się od działania. Po <xref:System.ServiceModel.Activities.WorkflowServiceHost> odebraniu komunikatu dla usługi przepływu pracy, jeśli nie jest jeszcze uruchomiony (lub utrwalił) nowe wystąpienie usługi przepływu pracy jest tworzony. Jeśli przepływ pracy nie rozpoczyna się od Receive działania, nie można uruchomić przez wysłanie wiadomości, ponieważ nie ma żadnych działań, aby otrzymać wiadomość. Aby hostować nieusługowy przepływ pracy, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> wyjdź <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>klasę <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>i <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>zastąpij , i . Zastądeń, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> jeśli chcesz podać identyfikator wystąpienia preferowanego. Zastąd, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> aby utworzyć niestandardowy kontekst tworzenia przepływu pracy <xref:System.ServiceModel.Activities.WorkflowCreationContext>lub wypełnić wystąpienie istniejącego pliku . Zastądnij, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> aby ręcznie wyodrębnić zakładkę z wiadomości przychodzącej. Jeśli zastąpisz tę metodę, należy <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> wywołać w jego treści, tak aby odpowiedzieć na wiadomość wysłaną do WorkflowHostingEndpoint. Jeśli tego nie zrobisz, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> limit może zostać ostatecznie przekroczony. W kontraktach dwukierunkowych <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> może być w stanie wykryć niepowodzenie wywołania z powodu niepowodzenia klienta do odbierania odpowiedzi. W kontraktach jednokierunkowych nie można rozpoznać <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> błędu niepodjęcia połączenia, dopóki nie będzie za późno, po <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> przekroczeniu limitu przepustnicy. Aby uzyskać więcej informacji, zobacz [Zakładka wznowienia workflowHostingEndpoint](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)Aby utworzyć nowe wystąpienie nieusługowego przepływu pracy, zadeklaruj umowę serwisową definiującą operację, która tworzy nowe wystąpienie. Operacja tworzenia powinna przyjmować ciąg\<IDictionary, obiekt> do przekazywania wszelkich wymaganych parametrów przepływu pracy. Ten kontrakt jest niejawnie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>implementowane przez -derived klasy. Podczas hostowania przepływu pracy dodaj <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>wystąpienie klasy pochodnej do <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> hosta, wywołując i wywołując <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Aby utworzyć wystąpienie przepływu pracy, <xref:System.ServiceModel.ChannelFactory%601> utwórz typ umowy serwisowej i wywołaj program <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Następnie można wywołać operację tworzenia zdefiniowaną w umowie serwisowej.  
  
## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Działania dotyczące komunikatów](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
