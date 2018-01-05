---
title: "Podstawowy przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f0d5c25e2b2d3dac042ef93e5a174b25ce17314
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="basic-sample"></a><span data-ttu-id="87a04-102">Podstawowy przykład</span><span class="sxs-lookup"><span data-stu-id="87a04-102">Basic Sample</span></span>
<span data-ttu-id="87a04-103">W tym przykładzie pokazano, jak sprawiają, że usługa wykrywania urządzeń oraz sposób wyszukiwania i wywołać wykrywalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="87a04-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="87a04-104">W tym przykładzie składa się z dwóch projektów: usługa i klient.</span><span class="sxs-lookup"><span data-stu-id="87a04-104">This sample is composed of two projects: service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87a04-105">W tym przykładzie implementuje odnajdywania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="87a04-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="87a04-106">Dla przykładu, który implementuje odnajdywania w konfiguracji, zobacz [konfiguracji](../../../../docs/framework/wcf/samples/configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="87a04-106">For a sample that implements discovery in configuration, see [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span></span>  
  
## <a name="service"></a><span data-ttu-id="87a04-107">Usługa</span><span class="sxs-lookup"><span data-stu-id="87a04-107">Service</span></span>  
 <span data-ttu-id="87a04-108">Jest to prosty kalkulator implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="87a04-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="87a04-109">Odnajdywanie powiązane kod można znaleźć w `Main` gdzie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> zostanie dodany do usługi hosta i <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> zostanie dodany, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="87a04-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>  
  
```  
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
  
## <a name="client"></a><span data-ttu-id="87a04-110">Klient</span><span class="sxs-lookup"><span data-stu-id="87a04-110">Client</span></span>  
 <span data-ttu-id="87a04-111">Klient używa <xref:System.ServiceModel.Discovery.DynamicEndpoint> do lokalizowania usługi.</span><span class="sxs-lookup"><span data-stu-id="87a04-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="87a04-112"><xref:System.ServiceModel.Discovery.DynamicEndpoint>, Standardowy punkt końcowy rozpoznaje punktu końcowego usługi, gdy klient jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="87a04-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="87a04-113">W takim przypadku <xref:System.ServiceModel.Discovery.DynamicEndpoint> szuka usługi oparte na kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="87a04-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="87a04-114"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Przeprowadza wyszukiwanie za pośrednictwem <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> domyślnie.</span><span class="sxs-lookup"><span data-stu-id="87a04-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="87a04-115">Gdy klient zlokalizuje punkt końcowy usługi, klient łączy się z tej usługi za pośrednictwem określonego powiązania.</span><span class="sxs-lookup"><span data-stu-id="87a04-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 <span data-ttu-id="87a04-116">Klient definiuje metodę o nazwie `InvokeCalculatorService` używającą <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="87a04-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="87a04-117"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Dziedziczy <xref:System.ServiceModel.Description.ServiceEndpoint>, więc można go przekazać do `InvokeCalculatorService` metody.</span><span class="sxs-lookup"><span data-stu-id="87a04-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="87a04-118">W przykładzie następnie użyto <xref:System.ServiceModel.Discovery.DynamicEndpoint> można utworzyć wystąpienia `CalculatorServiceClient` i wywołuje różnych operacji usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="87a04-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="87a04-119">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="87a04-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="87a04-120">W przykładzie użyto punktów końcowych HTTP i do uruchomienia tego przykładu, muszą zostać dodane odpowiednie listy ACL adresu URL.</span><span class="sxs-lookup"><span data-stu-id="87a04-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="87a04-121">[Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="87a04-121"> [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="87a04-122">Następujące polecenie w pełnych uprawnień do wykonania należy dodać odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="87a04-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="87a04-123">Można zastąpić użytkownika domena i nazwa użytkownika dla następujących argumentów, jeśli polecenie nie działa, ponieważ jest.</span><span class="sxs-lookup"><span data-stu-id="87a04-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="87a04-124">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz Basic.sln i tworzyć przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="87a04-124">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Basic.sln and build the sample.</span></span>  
  
3.  <span data-ttu-id="87a04-125">Uruchom aplikację service.exe.</span><span class="sxs-lookup"><span data-stu-id="87a04-125">Run the service.exe application.</span></span>  
  
4.  <span data-ttu-id="87a04-126">Po uruchomieniu usługi, uruchom client.exe.</span><span class="sxs-lookup"><span data-stu-id="87a04-126">After the service has started, run the client.exe.</span></span>  
  
5.  <span data-ttu-id="87a04-127">Sprawdź, czy klient mógł znaleźć usługi bez uprzedniego uzyskania informacji o jego adres.</span><span class="sxs-lookup"><span data-stu-id="87a04-127">Observe that the client was able to find the service without knowing its address.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="87a04-128">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="87a04-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="87a04-129">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="87a04-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="87a04-130">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="87a04-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="87a04-131">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="87a04-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a><span data-ttu-id="87a04-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87a04-132">See Also</span></span>
