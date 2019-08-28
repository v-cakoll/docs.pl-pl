---
title: Anonse — przykład
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 1acf51ebe36872424be1e0fdda65a7d18aa737f2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045795"
---
# <a name="announcements-sample"></a><span data-ttu-id="68ed8-102">Anonse — przykład</span><span class="sxs-lookup"><span data-stu-id="68ed8-102">Announcements Sample</span></span>

<span data-ttu-id="68ed8-103">Ten przykład pokazuje, jak używać funkcji anonsu funkcji odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="68ed8-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="68ed8-104">Anonsy umożliwiają usługom wysyłanie komunikatów anonsu zawierających metadane dotyczące usługi.</span><span class="sxs-lookup"><span data-stu-id="68ed8-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="68ed8-105">Domyślnie anons powitalny jest wysyłany podczas uruchamiania usługi i wysyłany jest anons bye po zamknięciu usługi.</span><span class="sxs-lookup"><span data-stu-id="68ed8-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="68ed8-106">Anonse mogą być multiemisje lub mogą być wysyłane jako punkt-punkt.</span><span class="sxs-lookup"><span data-stu-id="68ed8-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="68ed8-107">Ten przykład składa się z dwóch projektów usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="68ed8-107">This sample consists of two projects service and client.</span></span>

## <a name="service"></a><span data-ttu-id="68ed8-108">Usługa</span><span class="sxs-lookup"><span data-stu-id="68ed8-108">Service</span></span>

<span data-ttu-id="68ed8-109">Ten projekt zawiera samohostowaną usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="68ed8-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="68ed8-110">`Main` W metodzie zostanie utworzony host usługi i do niego zostanie dodany punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="68ed8-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="68ed8-111"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Następnie jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="68ed8-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="68ed8-112">Aby włączyć Anonsy, należy dodać punkt końcowy anonsu do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="68ed8-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="68ed8-113">W tym przypadku standardowym punktem końcowym przy użyciu multiemisji UDP jest dodawany jako punkt końcowy anonsu.</span><span class="sxs-lookup"><span data-stu-id="68ed8-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="68ed8-114">Emituje anonse za pośrednictwem dobrze znanego adresu UDP.</span><span class="sxs-lookup"><span data-stu-id="68ed8-114">This broadcasts the announcements over a well-known UDP address.</span></span>

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

## <a name="client"></a><span data-ttu-id="68ed8-115">Klient</span><span class="sxs-lookup"><span data-stu-id="68ed8-115">Client</span></span>

<span data-ttu-id="68ed8-116">W tym projekcie należy zauważyć, że klient obsługuje <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="68ed8-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="68ed8-117">Co więcej, dwa Delegaty są rejestrowane ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="68ed8-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="68ed8-118">Te zdarzenia określają, co klient wykonuje po odebraniu anonsów online i offline.</span><span class="sxs-lookup"><span data-stu-id="68ed8-118">These events dictate what the client does when online and offline announcements are received.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

<span data-ttu-id="68ed8-119">Metody `OnOnlineEvent` i`OnOfflineEvent` obsługują odpowiednio Komunikaty anonsu Hello i bye.</span><span class="sxs-lookup"><span data-stu-id="68ed8-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="68ed8-120">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="68ed8-120">To use this sample</span></span>

1. <span data-ttu-id="68ed8-121">Ten przykład korzysta z punktów końcowych HTTP i do uruchamiania tego przykładu należy dodać odpowiednie listy ACL adresów URL, aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie protokołu HTTP i https](https://go.microsoft.com/fwlink/?LinkId=70353) .</span><span class="sxs-lookup"><span data-stu-id="68ed8-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="68ed8-122">Wykonanie następującego polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="68ed8-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="68ed8-123">Można zastąpić domenę i nazwę użytkownika dla następujących argumentów, jeśli polecenie nie działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="68ed8-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="68ed8-124">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="68ed8-124">Build the solution.</span></span>

3. <span data-ttu-id="68ed8-125">Uruchom aplikację Client. exe.</span><span class="sxs-lookup"><span data-stu-id="68ed8-125">Run the client.exe application.</span></span>

4. <span data-ttu-id="68ed8-126">Uruchom aplikację Service. exe.</span><span class="sxs-lookup"><span data-stu-id="68ed8-126">Run the service.exe application.</span></span> <span data-ttu-id="68ed8-127">Zwróć uwagę, że klient otrzymuje Anons online.</span><span class="sxs-lookup"><span data-stu-id="68ed8-127">Note the client receives an online announcement.</span></span>

5. <span data-ttu-id="68ed8-128">Zamknij aplikację Service. exe.</span><span class="sxs-lookup"><span data-stu-id="68ed8-128">Close the service.exe application.</span></span> <span data-ttu-id="68ed8-129">Zwróć uwagę, że klient otrzymuje anons w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="68ed8-129">Note the client receives an offline announcement.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="68ed8-130">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="68ed8-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="68ed8-131">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="68ed8-131">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="68ed8-132">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="68ed8-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="68ed8-133">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="68ed8-133">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
