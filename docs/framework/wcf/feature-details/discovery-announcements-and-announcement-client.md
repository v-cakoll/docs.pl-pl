---
title: Anonse odnajdywania i klient anonsów
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 4ad0b3ea5c257fa3117c426391bd59ad7b560d4f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040181"
---
# <a name="discovery-announcements-and-announcement-client"></a>Anonse odnajdywania i klient anonsów

Funkcja odnajdywania WCF umożliwia składnikom ogłaszanie ich dostępności. W przypadku skonfigurowania tej usługi usługa wysyła anonse Witaj i bye. Klienci lub inne składniki mogą nasłuchiwać takich komunikatów anonsu i wykonywać na nich działania. Zapewnia to alternatywną metodę dla klientów, którzy mają znać usługi. Funkcja anonsowania ma kilka zastosowania, na przykład jeśli usługi zmieniają i opuszczają sieć, anonse mogą być lepszym rozwiązaniem alternatywnym niż wyszukiwanie usług. W tym podejściu ruch sieciowy zostaje zredukowany, a klient może dowiedzieć się o obecności lub wyjściu usługi zaraz po odebraniu anonsów.

## <a name="discovery-announcements"></a>Anonse odnajdywania

Gdy Usługa skonfigurowana pod kątem anonsów dołącza do sieci i zostaje wykrywalna, wysyła komunikat powitalny informujący o jego dostępności do nasłuchiwania klientów. Komunikat zawiera informacje dotyczące odnajdywania usługi, takie jak jej kontrakt, adres punktu końcowego i skojarzone zakresy. Możesz określić miejsce, do którego wiadomość anonsu ma być <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> wysyłana z klasą. Jeśli punkt końcowy anonsu to <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> , powitanie i bye są odpowiednio multiemisje lub jeśli punkt końcowy anonsu jest emisją pojedynczą, komunikaty są wysyłane bezpośrednio do określonego punktu końcowego.

> [!NOTE]
> Anonsy są wysyłane po otwarciu i zamknięciu hosta usługi. Jeśli te wywołania nie zakończą się prawidłowo, komunikat anonsu nie może zostać wysłany. Jeśli na przykład wystąpią błędy usługi, komunikat anonsu bye nie zostanie wysłany.

> [!TIP]
> Możesz dostosować funkcje anonsowania, co pozwala na wysyłanie anonsów w każdym przypadku.

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<xref:System.ServiceModel.Discovery.AnnouncementEndpoint> definiuje i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jako standardowe punkty końcowe, które umożliwiają usługom i klientom łatwe wysyłanie anonsów Hello i bye.

### <a name="announcements-on-the-service"></a>Anonse w usłudze

Aby skonfigurować usługę do wysyłania anonsów, Dodaj element <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> z punktem końcowym anonsu. Poniższy przykład pokazuje, jak programowo dodać to zachowanie do hosta usługi. W `UdpAnnouncementEndpoint`tym przykładzie użyto, co oznacza, że anonse są multiemisją do lokalizacji określonej przez standardowy punkt końcowy.

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

Zachowanie można skonfigurować również w pliku konfiguracji, jak pokazano w poniższym przykładzie.

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

Powyższe przykłady umożliwiają skonfigurowanie usługi do automatycznego wysyłania komunikatów anonsu. Komunikaty anonsu można również jawnie wysyłać przy użyciu <xref:System.ServiceModel.Discovery.AnnouncementClient> klasy.

### <a name="announcements-on-the-client"></a>Anonse na kliencie

Aplikacja kliencka musi obsługiwać usługę anonsowania, aby odpowiedzieć na wiadomości Hello i bye oraz subskrybować <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> zdarzenia i. <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> W przykładzie poniżej pokazano, jak to zrobić.

```csharp
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

Po odebraniu komunikatu powitanie lub bye można uzyskać dostęp do metadanych <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> odnajdowania punktów końcowych, jak pokazano w poniższym przykładzie.

```csharp
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
