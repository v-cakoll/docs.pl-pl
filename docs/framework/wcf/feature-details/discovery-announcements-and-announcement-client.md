---
title: Anonse odnajdywania i klient anonsów
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 74362343dc1fd5df6d1b91537f7fed5bc08f8fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968817"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="b3996-102">Anonse odnajdywania i klient anonsów</span><span class="sxs-lookup"><span data-stu-id="b3996-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="b3996-103">Funkcja odnajdywania WCF umożliwia składnikom ogłaszanie ich dostępności.</span><span class="sxs-lookup"><span data-stu-id="b3996-103">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="b3996-104">W przypadku skonfigurowania tej usługi usługa wysyła anonse Witaj i bye.</span><span class="sxs-lookup"><span data-stu-id="b3996-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="b3996-105">Klienci lub inne składniki mogą nasłuchiwać takich komunikatów anonsu i wykonywać na nich działania.</span><span class="sxs-lookup"><span data-stu-id="b3996-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="b3996-106">Zapewnia to alternatywną metodę dla klientów, którzy mają znać usługi.</span><span class="sxs-lookup"><span data-stu-id="b3996-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="b3996-107">Funkcja anonsowania ma kilka zastosowania, na przykład jeśli usługi zmieniają i opuszczają sieć, anonse mogą być lepszym rozwiązaniem alternatywnym niż wyszukiwanie usług.</span><span class="sxs-lookup"><span data-stu-id="b3996-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="b3996-108">W tym podejściu ruch sieciowy zostaje zredukowany, a klient może dowiedzieć się o obecności lub wyjściu usługi zaraz po odebraniu anonsów.</span><span class="sxs-lookup"><span data-stu-id="b3996-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="b3996-109">Anonse odnajdywania</span><span class="sxs-lookup"><span data-stu-id="b3996-109">Discovery Announcements</span></span>  
 <span data-ttu-id="b3996-110">Gdy Usługa skonfigurowana pod kątem anonsów dołącza do sieci i zostaje wykrywalna, wysyła komunikat powitalny informujący o jego dostępności do nasłuchiwania klientów.</span><span class="sxs-lookup"><span data-stu-id="b3996-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="b3996-111">Komunikat zawiera informacje dotyczące odnajdywania usługi, takie jak jej kontrakt, adres punktu końcowego i skojarzone zakresy.</span><span class="sxs-lookup"><span data-stu-id="b3996-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="b3996-112">Możesz określić miejsce, do którego wiadomość anonsu ma być <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> wysyłana z klasą.</span><span class="sxs-lookup"><span data-stu-id="b3996-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="b3996-113">Jeśli punkt końcowy anonsu to <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> , powitanie i bye są odpowiednio multiemisje lub jeśli punkt końcowy anonsu jest emisją pojedynczą, komunikaty są wysyłane bezpośrednio do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b3996-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3996-114">Anonsy są wysyłane po otwarciu i zamknięciu hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="b3996-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="b3996-115">Jeśli te wywołania nie zakończą się prawidłowo, komunikat anonsu nie może zostać wysłany. Jeśli na przykład wystąpią błędy usługi, komunikat anonsu bye nie zostanie wysłany.</span><span class="sxs-lookup"><span data-stu-id="b3996-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="b3996-116">Możesz dostosować funkcje anonsowania, co pozwala na wysyłanie anonsów w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="b3996-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="b3996-117"><xref:System.ServiceModel.Discovery.AnnouncementEndpoint> definiuje i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jako standardowe punkty końcowe, które umożliwiają usługom i klientom łatwe wysyłanie anonsów Hello i bye.</span><span class="sxs-lookup"><span data-stu-id="b3996-117">defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="b3996-118">Anonse w usłudze</span><span class="sxs-lookup"><span data-stu-id="b3996-118">Announcements on the Service</span></span>  
 <span data-ttu-id="b3996-119">Aby skonfigurować usługę do wysyłania anonsów, Dodaj element <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> z punktem końcowym anonsu.</span><span class="sxs-lookup"><span data-stu-id="b3996-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="b3996-120">Poniższy przykład pokazuje, jak programowo dodać to zachowanie do hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="b3996-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="b3996-121">W `UdpAnnouncementEndpoint`tym przykładzie użyto, co oznacza, że anonse są multiemisją do lokalizacji określonej przez standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="b3996-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="b3996-122">Zachowanie można skonfigurować również w pliku konfiguracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b3996-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="b3996-123">Powyższe przykłady umożliwiają skonfigurowanie usługi do automatycznego wysyłania komunikatów anonsu.</span><span class="sxs-lookup"><span data-stu-id="b3996-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="b3996-124">Komunikaty anonsu można również jawnie wysyłać przy użyciu <xref:System.ServiceModel.Discovery.AnnouncementClient> klasy.</span><span class="sxs-lookup"><span data-stu-id="b3996-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="b3996-125">Anonse na kliencie</span><span class="sxs-lookup"><span data-stu-id="b3996-125">Announcements on the Client</span></span>  
 <span data-ttu-id="b3996-126">Aplikacja kliencka musi obsługiwać usługę anonsowania, aby odpowiedzieć na wiadomości Hello i bye oraz subskrybować <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> zdarzenia i. <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived></span><span class="sxs-lookup"><span data-stu-id="b3996-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="b3996-127">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="b3996-127">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="b3996-128">Po odebraniu komunikatu powitanie lub bye można uzyskać dostęp do metadanych <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> odnajdowania punktów końcowych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b3996-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
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
