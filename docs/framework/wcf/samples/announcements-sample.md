---
title: Anonse — przykład
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: ee58a2fef970fa3e7936e2fc26a9e7fd31633347
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="announcements-sample"></a><span data-ttu-id="fb0f5-102">Anonse — przykład</span><span class="sxs-lookup"><span data-stu-id="fb0f5-102">Announcements Sample</span></span>
<span data-ttu-id="fb0f5-103">Ten przykład przedstawia sposób użycia anonsu działanie funkcji odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="fb0f5-104">Anonse Zezwalaj usługom do wysłania wiadomości anonsów, zawierające metadane dotyczące usługi.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="fb0f5-105">Domyślnie powiadomienia hello są wysyłane podczas uruchamiania usługi i anonsu bye są wysyłane podczas zamykania usługi.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="fb0f5-106">Anonse te mogą być multiemisji lub mogą być wysyłane point-to-point.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="fb0f5-107">W tym przykładzie obejmuje dwa projekty usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-107">This sample consists of two projects service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="fb0f5-108">Usługa</span><span class="sxs-lookup"><span data-stu-id="fb0f5-108">Service</span></span>  
 <span data-ttu-id="fb0f5-109">Ten projekt zawiera usługi Kalkulator siebie.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="fb0f5-110">W `Main` metody, host usługi jest tworzony i punktu końcowego zostaną dodane do niego.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="fb0f5-111">Następnie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="fb0f5-112">Aby włączyć anonsów, punkt końcowy powiadomienia musi zostać dodany do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="fb0f5-113">W takim przypadku standardowy punkt końcowy, za pomocą multiemisji UDP jest dodawana jako punktu końcowego powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="fb0f5-114">Anonsy to emituje za pośrednictwem dobrze znanego adresu protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-114">This broadcasts the announcements over a well-known UDP address.</span></span>  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());  
  
// Create a ServiceHost for the CalculatorService type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);  
  
     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
  
     // Announce the availability of the service over UDP multicast  
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());  
  
    // Make the service discoverable over UDP multicast.  
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a><span data-ttu-id="fb0f5-115">Klient</span><span class="sxs-lookup"><span data-stu-id="fb0f5-115">Client</span></span>  
 <span data-ttu-id="fb0f5-116">W tym projekcie, należy pamiętać, że hosty klienta <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="fb0f5-117">Ponadto dwa obiekty delegowane są rejestrowane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="fb0f5-118">Zdarzenia te określają, co klient nie w przypadku online i offline anonse są odbierane.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-118">These events dictate what the client does when online and offline announcements are received.</span></span>  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 <span data-ttu-id="fb0f5-119">`OnOnlineEvent` i `OnOfflineEvent` metody obsługi wiadomości anonsów hello i bye odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();              
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
  
static void OnOfflineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();  
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="fb0f5-120">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="fb0f5-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="fb0f5-121">W przykładzie użyto punktów końcowych HTTP i do uruchomienia, to przykładowa, odpowiednich list ACL adresu URL muszą zostać dodane zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="fb0f5-122">Następujące polecenie w pełnych uprawnień do wykonania należy dodać odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="fb0f5-123">Można zastąpić użytkownika domena i nazwa użytkownika dla następujących argumentów, jeśli polecenie nie działa, ponieważ jest.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="fb0f5-124">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-124">Build the solution.</span></span>  
  
3.  <span data-ttu-id="fb0f5-125">Uruchom aplikację client.exe.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-125">Run the client.exe application.</span></span>  
  
4.  <span data-ttu-id="fb0f5-126">Uruchom aplikację service.exe.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-126">Run the service.exe application.</span></span> <span data-ttu-id="fb0f5-127">Należy zauważyć, że klient otrzymuje powiadomienia online.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-127">Note the client receives an online announcement.</span></span>  
  
5.  <span data-ttu-id="fb0f5-128">Zamknij aplikację service.exe.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-128">Close the service.exe application.</span></span> <span data-ttu-id="fb0f5-129">Należy zauważyć, że klient otrzymuje powiadomienia w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-129">Note the client receives an offline announcement.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fb0f5-130">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fb0f5-131">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fb0f5-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fb0f5-132">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fb0f5-133">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fb0f5-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a><span data-ttu-id="fb0f5-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb0f5-134">See Also</span></span>
