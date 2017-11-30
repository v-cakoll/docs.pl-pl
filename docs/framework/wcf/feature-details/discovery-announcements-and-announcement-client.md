---
title: "Anonse odnajdywania i klient anonsów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36003933a9fb49fe4fe4f0b677ee584066d415ac
ms.sourcegitcommit: ea1fd4ff4c36169fc722ef263e24884c5cd431a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2017
---
# <a name="discovery-announcements-and-announcement-client"></a>Anonse odnajdywania i klient anonsów
[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Odnajdywania funkcja umożliwia składniki poinformować ich dostępności. Jeśli skonfigurowana, aby to zrobić, usługa wysyła Hello i Bye anonsów. Klientów ani innych składników można nasłuchiwać takie komunikaty anonsów i działają na nich. Zapewnia to alternatywna metoda klientów pod uwagę usług. Funkcje anons ma kilka zastosowań, na przykład usługi wprowadź, pozostaw sieci często anonsów może być lepszym niż w przypadku usługi wyszukiwania. Takie podejście zmniejsza ruch w sieci i klienta można zapoznać się obecności lub wysyłki usługi jak Anonse są odbierane.  
  
## <a name="discovery-announcements"></a>Anonse odnajdywania  
 Gdy Usługa skonfigurowana dla anonsów łączy sieci i staje się wykrywalny, wysyła wiadomość Hello informującą jego dostępność do nasłuchiwania klientów. Komunikat zawiera odnajdywanie powiązane informacje o usłudze, takich jak jej kontrakt adres punktu końcowego i skojarzone zakresów. Można określić, gdzie komunikat powiadomienia są wysyłane z <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> klasy. Jeśli punkt końcowy powiadomienia jest <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Hello i Bye są odpowiednio multiemisji lub punkt końcowy powiadomienia w przypadku emisji pojedynczej, komunikaty są wysyłane bezpośrednio do określonego punktu końcowego.  
  
> [!NOTE]
>  Anonse są wysyłane, jeśli host usługi zostanie otwarty i zamyka. Jeśli tych wywołań nie zakończy się poprawnie nie można wysłać komunikatu powiadomienia. Na przykład jeśli usługa błędów, a następnie Bye komunikat powiadomienia nie są wysyłane.  
  
> [!TIP]
>  Można dostosować funkcje anons, co umożliwia wysyłanie powiadomień, zawsze, gdy zostanie wybrana.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]definiuje <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jako standardowych punktów końcowych, aby umożliwić usług i klientów w celu łatwego wysyłania anonsów Hello i Bye.  
  
### <a name="announcements-on-the-service"></a>Anonsy w usłudze  
 Aby skonfigurować usługę, aby wysłać powiadomienia, Dodaj <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> z punktem końcowym anonsu. Poniższy przykład przedstawia sposób programowego dodawania tego zachowania do hosta usługi. W tym przykładzie użyto `UdpAnnouncementEndpoint`, co oznacza, że anonsy są multiemisji do lokalizacji określonej przez tego standardowego punktu końcowego.  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 To zachowanie można skonfigurować w pliku konfiguracji, jak również, jak pokazano w poniższym przykładzie.  
  
```xml  
<services>
  <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">
    <!--Add Discovery Endpoint-->
    <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorBehavior">
      <!--Add Discovery behavior-->
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
 Powyższych przykładach skonfigurować usługę automatycznie wysyłać powiadomienia. Również wiadomości można wysyłać powiadomienia bezpośrednio za pomocą <xref:System.ServiceModel.Discovery.AnnouncementClient> klasy.  
  
### <a name="announcements-on-the-client"></a>Anonse na kliencie  
 Aplikacja kliencka musi obsługiwać usługę anonsu odpowiada na wiadomości powitania i Bye i subskrybowanie <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> i <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> zdarzenia. W przykładzie poniżej pokazano, jak to zrobić.  
  
```  
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();
  
// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
  
// Create ServiceHost for the AnnouncementService
using (ServiceHost announcementServiceHost = new ServiceHost(announcementService))
{  
    // Listen for the announcements sent over UDP multicast
    announcementServiceHost.AddServiceEndpoint(new UdpAnnouncementEndpoint());
    announcementServiceHost.Open();
  
    Console.WriteLine("Press <ENTER> to terminate.");
    Console.ReadLine();
}  
```  
  
 Po odebraniu wiadomości powitania lub Bye są dostępne metadane odnajdowania punktu końcowego za pośrednictwem <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> jak pokazano w poniższym przykładzie.  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an online announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an offline announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}
```
