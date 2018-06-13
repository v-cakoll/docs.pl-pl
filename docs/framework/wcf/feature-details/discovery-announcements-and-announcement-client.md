---
title: Anonse odnajdywania i klient anonsów
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: c32aca5e6deab01423d61c516ee924d00bc041ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490288"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="41740-102">Anonse odnajdywania i klient anonsów</span><span class="sxs-lookup"><span data-stu-id="41740-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="41740-103">Funkcja odnajdywania WCF umożliwia składniki poinformować ich dostępności.</span><span class="sxs-lookup"><span data-stu-id="41740-103">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="41740-104">Jeśli skonfigurowana, aby to zrobić, usługa wysyła Hello i Bye anonsów.</span><span class="sxs-lookup"><span data-stu-id="41740-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="41740-105">Klientów ani innych składników można nasłuchiwać takie komunikaty anonsów i działają na nich.</span><span class="sxs-lookup"><span data-stu-id="41740-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="41740-106">Zapewnia to alternatywna metoda klientów pod uwagę usług.</span><span class="sxs-lookup"><span data-stu-id="41740-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="41740-107">Funkcje anons ma kilka zastosowań, na przykład usługi wprowadź, pozostaw sieci często anonsów może być lepszym niż w przypadku usługi wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="41740-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="41740-108">Takie podejście zmniejsza ruch w sieci i klienta można zapoznać się obecności lub wysyłki usługi jak Anonse są odbierane.</span><span class="sxs-lookup"><span data-stu-id="41740-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="41740-109">Anonse odnajdywania</span><span class="sxs-lookup"><span data-stu-id="41740-109">Discovery Announcements</span></span>  
 <span data-ttu-id="41740-110">Gdy Usługa skonfigurowana dla anonsów łączy sieci i staje się wykrywalny, wysyła wiadomość Hello informującą jego dostępność do nasłuchiwania klientów.</span><span class="sxs-lookup"><span data-stu-id="41740-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="41740-111">Komunikat zawiera odnajdywanie powiązane informacje o usłudze, takich jak jej kontrakt adres punktu końcowego i skojarzone zakresów.</span><span class="sxs-lookup"><span data-stu-id="41740-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="41740-112">Można określić, gdzie komunikat powiadomienia są wysyłane z <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> klasy.</span><span class="sxs-lookup"><span data-stu-id="41740-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="41740-113">Jeśli punkt końcowy powiadomienia jest <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Hello i Bye są odpowiednio multiemisji lub punkt końcowy powiadomienia w przypadku emisji pojedynczej, komunikaty są wysyłane bezpośrednio do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="41740-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41740-114">Anonse są wysyłane, jeśli host usługi zostanie otwarty i zamyka.</span><span class="sxs-lookup"><span data-stu-id="41740-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="41740-115">Jeśli tych wywołań nie zakończy się poprawnie nie można wysłać komunikatu powiadomienia. Na przykład jeśli usługa błędów, a następnie Bye komunikat powiadomienia nie są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="41740-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="41740-116">Można dostosować funkcje anons, co umożliwia wysyłanie powiadomień, zawsze, gdy zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="41740-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="41740-117"> definiuje <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jako standardowych punktów końcowych, aby umożliwić usług i klientów w celu łatwego wysyłania anonsów Hello i Bye.</span><span class="sxs-lookup"><span data-stu-id="41740-117"> defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="41740-118">Anonsy w usłudze</span><span class="sxs-lookup"><span data-stu-id="41740-118">Announcements on the Service</span></span>  
 <span data-ttu-id="41740-119">Aby skonfigurować usługę, aby wysłać powiadomienia, Dodaj <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> z punktem końcowym anonsu.</span><span class="sxs-lookup"><span data-stu-id="41740-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="41740-120">Poniższy przykład przedstawia sposób programowego dodawania tego zachowania do hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="41740-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="41740-121">W tym przykładzie użyto `UdpAnnouncementEndpoint`, co oznacza, że anonsy są multiemisji do lokalizacji określonej przez tego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="41740-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="41740-122">To zachowanie można skonfigurować w pliku konfiguracji, jak również, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="41740-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="41740-123">Powyższych przykładach skonfigurować usługę automatycznie wysyłać powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="41740-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="41740-124">Również wiadomości można wysyłać powiadomienia bezpośrednio za pomocą <xref:System.ServiceModel.Discovery.AnnouncementClient> klasy.</span><span class="sxs-lookup"><span data-stu-id="41740-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="41740-125">Anonse na kliencie</span><span class="sxs-lookup"><span data-stu-id="41740-125">Announcements on the Client</span></span>  
 <span data-ttu-id="41740-126">Aplikacja kliencka musi obsługiwać usługę anonsu odpowiada na wiadomości powitania i Bye i subskrybowanie <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> i <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="41740-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="41740-127">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="41740-127">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="41740-128">Po odebraniu wiadomości powitania lub Bye są dostępne metadane odnajdowania punktu końcowego za pośrednictwem <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="41740-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
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
