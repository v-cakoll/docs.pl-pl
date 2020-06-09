---
title: Rozszerzalność hosta usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: 4c2edec8c23e27f019b95223c998c72069384c75
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594897"
---
# <a name="workflow-service-host-extensibility"></a>Rozszerzalność hosta usługi przepływu pracy
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]udostępnia <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasę do hostowania usług przepływu pracy. Ta klasa jest używana podczas samodzielnego udostępniania usługi przepływu pracy w aplikacji zarządzanej lub usłudze systemu Windows. Ta klasa jest również używana podczas hostowania usługi przepływu pracy z usługą Internet Information Services (IIS) lub usługą aktywacji procesów systemu Windows (WAS). <xref:System.ServiceModel.Activities.WorkflowServiceHost>Klasa zawiera punkty rozszerzenia, które umożliwiają dodawanie rozszerzeń niestandardowych, zmianę zachowania bezczynności i hosta przepływów innych niż usługi (przepływy pracy, które nie korzystają z działań związanych z obsługą wiadomości).  
  
## <a name="workflow-service-host-extensions"></a>Rozszerzenia hosta usługi przepływu pracy  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>Zawiera <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> Właściwość typu <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> , która dostarcza metody do dodawania rozszerzeń do <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Użyj <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metody, aby dodać rozszerzenie dla każdego wystąpienia usługi przepływu pracy. Określony delegat jest wywoływany, aby utworzyć nowe rozszerzenie podczas tworzenia lub ładowania wystąpienia usługi przepływu pracy z magazynu trwałości. Użyj <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metody, aby dodać rozszerzenie dla każdego hosta usługi przepływu pracy, jedno wystąpienie rozszerzenia jest udostępniane dla wszystkich wystąpień usługi przepływu pracy.  
  
## <a name="react-to-unhandled-exceptions"></a>Reagowanie na Nieobsłużone wyjątki  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>Umożliwia określenie akcji do wykonania w przypadku wystąpienia nieobsłużonego wyjątku w ramach usługi przepływu pracy. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A>Właściwość określa jedną z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> wartości:  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon>— Przerywa wystąpienie usługi przepływu pracy.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend>— Przywraca ostatni stan trwały i wstrzymuje wystąpienie usługi przepływu pracy. Ta sytuacja występuje tylko wtedy, gdy przepływ pracy został już utrwalony co najmniej raz. Jeśli nie, wystąpienie przepływu pracy zostało przerwane.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>— Anuluje wystąpienie.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate>— Kończy wystąpienie.  
  
 Takie zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Można ją również skonfigurować w pliku konfiguracji, jak pokazano w poniższym przykładzie.  
  
```xml
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />
        </behavior>  
      </serviceBehaviors>  
</behaviors>
```  
  
## <a name="hosting-non-service-workflows"></a>Obsługiwanie przepływów pracy innych niż usługi  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>może służyć do hostowania przepływów pracy innych niż usługi lub przepływów pracy, które nie zaczynają się od <xref:System.ServiceModel.Activities.Receive> działania lub przepływów pracy, które nie korzystają z działań związanych z obsługą komunikatów. Usługi przepływu pracy zwykle zaczynają się od <xref:System.ServiceModel.Activities.Receive> działania. Gdy <xref:System.ServiceModel.Activities.WorkflowServiceHost> odbierze komunikat dla usługi przepływu pracy, jeśli nie jest jeszcze uruchomiony (lub utrwalony) nowe wystąpienie usługi przepływu pracy zostanie utworzone. Jeśli przepływ pracy nie zaczyna się od działania Receive, nie można go uruchomić przez wysłanie komunikatu, ponieważ nie ma aktywności do odebrania komunikatu. Aby hostować przepływ pracy spoza usługi, należy utworzyć klasę z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> i zastąpić <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> , <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> , i <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> . Przesłoń <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> , jeśli chcesz podać preferowany identyfikator wystąpienia. Przesłoń <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> , aby utworzyć niestandardowy kontekst tworzenia przepływu pracy lub wypełnić wystąpienie istniejącego elementu <xref:System.ServiceModel.Activities.WorkflowCreationContext> . Przesłoń, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> Aby ręcznie wyodrębnić zakładkę z wiadomości przychodzącej. Jeśli zastąpisz tę metodę, musisz wywołać ją <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> w swojej treści, aby odpowiedzieć na komunikat wysłany do WorkflowHostingEndpoint. Jeśli tego nie zrobisz, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> limit może zostać przekroczony. W przypadku kontraktów dwukierunkowych może być możliwe wykrycie niepowodzenia wywołania z <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> powodu niepowodzenia odpowiedzi klienta. W przypadku kontraktów jednokierunkowych nie można rozpoznać błędu niepowodzenia wywołania <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> , dopóki nie zostanie ono zbyt opóźnione po <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> przekroczeniu limitu ograniczania. Aby uzyskać więcej informacji, zapoznaj się z [zakładką WorkflowHostingEndpoint Resume](../../windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md), aby utworzyć nowe wystąpienie przepływu pracy, który nie jest usługą, zadeklaruj kontrakt usługi, który definiuje operację, która tworzy nowe wystąpienie. Operacja tworzenia powinna przyjmować Interfejs IDictionary \<string, object> , aby przekazać wszystkie wymagane parametry przepływu pracy. Ten kontrakt jest niejawnie zaimplementowany przez <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> klasę pochodną. Podczas hostowania przepływu pracy Dodaj wystąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> klasy pochodnej do hosta przez wywołanie metody <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> i wywołanie metody <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> . Aby utworzyć wystąpienie przepływu pracy, należy utworzyć <xref:System.ServiceModel.ChannelFactory%601> Typ kontraktu usługi i wywoływać <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> . Następnie można wywołać operację tworzenia zdefiniowaną w kontrakcie usługi.  
  
## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](workflow-services.md)
- [Działania dotyczące komunikatów](messaging-activities.md)
