---
title: Podstawowy przykład
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 2ea5af0a1c05b5632632b2619c0ee4813696d2fc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738173"
---
# <a name="basic-sample"></a><span data-ttu-id="41806-102">Podstawowy przykład</span><span class="sxs-lookup"><span data-stu-id="41806-102">Basic Sample</span></span>

<span data-ttu-id="41806-103">Ten przykład pokazuje, jak umożliwić odnajdywanie usługi i wyszukiwanie i wywoływanie usługi wykrywalnej.</span><span class="sxs-lookup"><span data-stu-id="41806-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="41806-104">Ten przykład składa się z dwóch projektów: Service i Client.</span><span class="sxs-lookup"><span data-stu-id="41806-104">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="41806-105">Ten przykład implementuje odnajdywanie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="41806-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="41806-106">Aby uzyskać przykład, który implementuje odnajdywanie w konfiguracji, zobacz [Konfiguracja](../../../../docs/framework/wcf/samples/configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="41806-106">For a sample that implements discovery in configuration, see [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span></span>

## <a name="service"></a><span data-ttu-id="41806-107">NDES</span><span class="sxs-lookup"><span data-stu-id="41806-107">Service</span></span>

<span data-ttu-id="41806-108">To jest prosta implementacja usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="41806-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="41806-109">Kod związany z odnajdywaniem można znaleźć w `Main`, w którym <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> zostanie dodany do hosta usługi i zostanie dodana <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="41806-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new
      WSHttpBinding(), String.Empty);

    // Make the service discoverable over UDP multicast
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    serviceHost.Open();
    // ...
}
```

## <a name="client"></a><span data-ttu-id="41806-110">Klient</span><span class="sxs-lookup"><span data-stu-id="41806-110">Client</span></span>

<span data-ttu-id="41806-111">Klient używa <xref:System.ServiceModel.Discovery.DynamicEndpoint> do lokalizowania usługi.</span><span class="sxs-lookup"><span data-stu-id="41806-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="41806-112"><xref:System.ServiceModel.Discovery.DynamicEndpoint>, standardowy punkt końcowy, rozwiązuje punkt końcowy usługi podczas otwierania klienta.</span><span class="sxs-lookup"><span data-stu-id="41806-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="41806-113">W tym przypadku <xref:System.ServiceModel.Discovery.DynamicEndpoint> szuka usługi na podstawie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="41806-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="41806-114"><xref:System.ServiceModel.Discovery.DynamicEndpoint> domyślnie przeszukiwane jest <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="41806-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="41806-115">Po znalezieniu punktu końcowego usługi klient nawiązuje połączenie z tą usługą względem określonego powiązania.</span><span class="sxs-lookup"><span data-stu-id="41806-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

<span data-ttu-id="41806-116">Klient definiuje metodę o nazwie `InvokeCalculatorService`, która używa klasy <xref:System.ServiceModel.Discovery.DiscoveryClient> do wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="41806-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="41806-117"><xref:System.ServiceModel.Discovery.DynamicEndpoint> dziedziczy po <xref:System.ServiceModel.Description.ServiceEndpoint>, więc można go przesłać do metody `InvokeCalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="41806-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="41806-118">Przykład używa <xref:System.ServiceModel.Discovery.DynamicEndpoint>, aby utworzyć wystąpienie `CalculatorServiceClient` i wywołuje różne operacje usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="41806-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>

```csharp
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)
{
   // Create a client
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);

   Console.WriteLine("Invoking CalculatorService");
   Console.WriteLine();

   double value1 = 100.00D;
   double value2 = 15.99D;

   // Call the Add service operation.
   double result = client.Add(value1, value2);
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

   // Call the Subtract service operation.
   result = client.Subtract(value1, value2);
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

   // Call the Multiply service operation.
   result = client.Multiply(value1, value2);
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

   // Call the Divide service operation.
   result = client.Divide(value1, value2);
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
   Console.WriteLine();

   //Closing the client gracefully closes the connection and cleans up resources
   client.Close();
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="41806-119">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="41806-119">To use this sample</span></span>

1. <span data-ttu-id="41806-120">Ten przykład korzysta z punktów końcowych HTTP i do uruchomienia tego przykładu należy dodać prawidłowe listy ACL adresów URL.</span><span class="sxs-lookup"><span data-stu-id="41806-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="41806-121">Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i https](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="41806-121">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="41806-122">Wykonanie następującego polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="41806-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="41806-123">Można zastąpić domenę i nazwę użytkownika dla następujących argumentów, jeśli polecenie nie działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="41806-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="41806-124">Za pomocą programu Visual Studio 2012 Otwórz podstawową. sln i skompiluj przykład.</span><span class="sxs-lookup"><span data-stu-id="41806-124">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>

3. <span data-ttu-id="41806-125">Uruchom aplikację Service. exe.</span><span class="sxs-lookup"><span data-stu-id="41806-125">Run the service.exe application.</span></span>

4. <span data-ttu-id="41806-126">Po uruchomieniu usługi Uruchom program Client. exe.</span><span class="sxs-lookup"><span data-stu-id="41806-126">After the service has started, run the client.exe.</span></span>

5. <span data-ttu-id="41806-127">Zwróć uwagę, że klient mógł znaleźć usługę bez znajomości jej adresu.</span><span class="sxs-lookup"><span data-stu-id="41806-127">Observe that the client was able to find the service without knowing its address.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41806-128">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="41806-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="41806-129">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="41806-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="41806-130">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41806-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="41806-131">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="41806-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
