---
title: Anonse odnajdywania i klient anonsów
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: c32aca5e6deab01423d61c516ee924d00bc041ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856594"
---
# <a name="discovery-announcements-and-announcement-client"></a>Anonse odnajdywania i klient anonsów
Funkcja odnajdywania WCF umożliwia składniki, aby poinformować o ich dostępności. Jeśli skonfigurowana, aby to zrobić, to usługa wysyła Hello i Bye anonsów. Klientów ani innych składników można nasłuchiwać takich komunikatów Anons i wykonywania względem nich działań. Zapewnia to alternatywna metoda klientów pod uwagę usług. Ogłoszenie funkcji ma kilka zastosowań, na przykład, jeśli usług wprowadź, pozostaw sieci często anonsów może być lepszym niż w przypadku usługi wyszukiwania. Takie podejście zmniejsza ruch w sieci i klienta można zapoznać się obecności lub wyjścia usługę tak szybko, jak Anonse są odbierane.  
  
## <a name="discovery-announcements"></a>Anonse odnajdywania  
 Gdy Usługa skonfigurowana dla anonsów łączy sieć i staje się wykrywalny, wysyła wiadomość powitania przedstawienie jej dostępność do nasłuchiwania klientów. Komunikat zawiera odnajdywanie pokrewne informacje dotyczące usługi, takie jak zmiana kontraktu adres punktu końcowego i skojarzone zakresy. Można określić, gdzie wysyłana jest wiadomość anonsu z <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> klasy. Jeśli punkt końcowy ogłoszenie jest <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Hello i Bye są odpowiednio multiemisji lub jeśli punkt końcowy ogłoszenie jest emisji pojedynczej, komunikaty są wysyłane bezpośrednio do określonego punktu końcowego.  
  
> [!NOTE]
>  Anonse są wysyłane, gdy host usługi otwiera i zamyka. Jeśli te wywołania kończy się prawidłowo komunikatów Anons nie może być wysłane z. Na przykład jeśli usługa błędów, a następnie komunikatów Anons Bye nie są wysyłane.  
  
> [!TIP]
>  Możesz dostosować funkcje anons, co umożliwia wysyłanie anonsów, zawsze wtedy, gdy wybierzesz.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] definiuje <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jako standardowe punkty końcowe, aby umożliwić usług i klientów w celu łatwego wysyłania anonsów Hello i Bye.  
  
### <a name="announcements-on-the-service"></a>Anonsy w usłudze  
 Aby skonfigurować usługę do wysyłania anonsów, Dodaj <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> z punktem końcowym anonsu. Poniższy przykład pokazuje, jak programowo dodać to zachowanie do hosta usługi. W tym przykładzie użyto `UdpAnnouncementEndpoint`, co oznacza, że anonse są multiemisji do lokalizacji określonej przez standardowy punkt końcowy.  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 Zachowanie można skonfigurować w pliku konfiguracji, a także, jak pokazano w poniższym przykładzie.  
  
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
  
 Powyższych przykładach skonfigurować usługę, aby automatycznie wysyłaj komunikaty anonsów. Możesz również wysłać komunikaty anonsów jawnie za pomocą <xref:System.ServiceModel.Discovery.AnnouncementClient> klasy.  
  
### <a name="announcements-on-the-client"></a>Ogłoszenia na komputerze klienckim  
 Aplikacja kliencka musi być hostem usługi ogłoszenie odpowiadanie na wiadomości powitania i Bye i subskrybowanie <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> i <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> zdarzenia. W przykładzie poniżej pokazano, jak to zrobić.  
  
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
  
 Po odebraniu wiadomości powitania lub Bye dostęp można uzyskać metadanych odnajdywania punktu końcowego za pośrednictwem <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> jak pokazano w poniższym przykładzie.  
  
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
