---
title: Anonse — przykład
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: c3824fb0dc7ab4169c309d1a5154127d6bc3b78f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747001"
---
# <a name="announcements-sample"></a><span data-ttu-id="d199e-102">Anonse — przykład</span><span class="sxs-lookup"><span data-stu-id="d199e-102">Announcements Sample</span></span>

<span data-ttu-id="d199e-103">Ten przykład pokazuje, jak używać funkcji anonsu funkcji odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="d199e-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="d199e-104">Anonsy umożliwiają usługom wysyłanie komunikatów anonsu zawierających metadane dotyczące usługi.</span><span class="sxs-lookup"><span data-stu-id="d199e-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="d199e-105">Domyślnie anons powitalny jest wysyłany podczas uruchamiania usługi i wysyłany jest anons bye po zamknięciu usługi.</span><span class="sxs-lookup"><span data-stu-id="d199e-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="d199e-106">Anonse mogą być multiemisje lub mogą być wysyłane jako punkt-punkt.</span><span class="sxs-lookup"><span data-stu-id="d199e-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="d199e-107">Ten przykład składa się z dwóch projektów usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="d199e-107">This sample consists of two projects service and client.</span></span>

## <a name="service"></a><span data-ttu-id="d199e-108">Usługa</span><span class="sxs-lookup"><span data-stu-id="d199e-108">Service</span></span>

<span data-ttu-id="d199e-109">Ten projekt zawiera samohostowaną usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="d199e-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="d199e-110">W metodzie `Main` jest tworzony Host usługi i zostaje do niego dodany punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="d199e-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="d199e-111">Następnie zostanie utworzony <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d199e-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="d199e-112">Aby włączyć Anonsy, należy dodać punkt końcowy anonsu do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d199e-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="d199e-113">W tym przypadku standardowym punktem końcowym przy użyciu multiemisji UDP jest dodawany jako punkt końcowy anonsu.</span><span class="sxs-lookup"><span data-stu-id="d199e-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="d199e-114">Emituje anonse za pośrednictwem dobrze znanego adresu UDP.</span><span class="sxs-lookup"><span data-stu-id="d199e-114">This broadcasts the announcements over a well-known UDP address.</span></span>

```csharp
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

## <a name="client"></a><span data-ttu-id="d199e-115">Klient</span><span class="sxs-lookup"><span data-stu-id="d199e-115">Client</span></span>

<span data-ttu-id="d199e-116">W tym projekcie należy zauważyć, że klient obsługuje <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="d199e-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="d199e-117">Co więcej, dwa Delegaty są rejestrowane ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="d199e-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="d199e-118">Te zdarzenia określają, co klient wykonuje po odebraniu anonsów online i offline.</span><span class="sxs-lookup"><span data-stu-id="d199e-118">These events dictate what the client does when online and offline announcements are received.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

<span data-ttu-id="d199e-119">Metody `OnOnlineEvent` i `OnOfflineEvent` obsługują odpowiednio Komunikaty anonsu Hello i bye.</span><span class="sxs-lookup"><span data-stu-id="d199e-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>

```csharp
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

#### <a name="to-use-this-sample"></a><span data-ttu-id="d199e-120">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="d199e-120">To use this sample</span></span>

1. <span data-ttu-id="d199e-121">Ten przykład korzysta z punktów końcowych HTTP i do uruchomienia tego przykładu należy dodać prawidłowe listy ACL adresów URL.</span><span class="sxs-lookup"><span data-stu-id="d199e-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="d199e-122">Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i https](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="d199e-122">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="d199e-123">Wykonanie następującego polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="d199e-123">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="d199e-124">Można zastąpić domenę i nazwę użytkownika dla następujących argumentów, jeśli polecenie nie działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="d199e-124">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="d199e-125">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="d199e-125">Build the solution.</span></span>

3. <span data-ttu-id="d199e-126">Uruchom aplikację Client. exe.</span><span class="sxs-lookup"><span data-stu-id="d199e-126">Run the client.exe application.</span></span>

4. <span data-ttu-id="d199e-127">Uruchom aplikację Service. exe.</span><span class="sxs-lookup"><span data-stu-id="d199e-127">Run the service.exe application.</span></span> <span data-ttu-id="d199e-128">Zwróć uwagę, że klient otrzymuje Anons online.</span><span class="sxs-lookup"><span data-stu-id="d199e-128">Note the client receives an online announcement.</span></span>

5. <span data-ttu-id="d199e-129">Zamknij aplikację Service. exe.</span><span class="sxs-lookup"><span data-stu-id="d199e-129">Close the service.exe application.</span></span> <span data-ttu-id="d199e-130">Zwróć uwagę, że klient otrzymuje anons w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="d199e-130">Note the client receives an offline announcement.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d199e-131">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d199e-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d199e-132">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="d199e-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d199e-133">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d199e-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d199e-134">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d199e-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
