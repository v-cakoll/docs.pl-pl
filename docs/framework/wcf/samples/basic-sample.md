---
title: Podstawowy przykład
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 29edc8acb0293210e66e31660e3215220440fbae
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580319"
---
# <a name="basic-sample"></a><span data-ttu-id="3c32c-102">Podstawowy przykład</span><span class="sxs-lookup"><span data-stu-id="3c32c-102">Basic Sample</span></span>
<span data-ttu-id="3c32c-103">Niniejszy przykład pokazuje, jak usługa stał się wykrywalny i jak wyszukiwanie i wywoływać odnajdywanej usługi.</span><span class="sxs-lookup"><span data-stu-id="3c32c-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="3c32c-104">W tym przykładzie składa się z dwóch projektów: usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="3c32c-104">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
>  <span data-ttu-id="3c32c-105">W tym przykładzie implementuje odnajdywania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3c32c-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="3c32c-106">Dla przykładu, który implementuje odnajdywania w konfiguracji, zobacz [konfiguracji](../../../../docs/framework/wcf/samples/configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3c32c-106">For a sample that implements discovery in configuration, see [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span></span>  
  
## <a name="service"></a><span data-ttu-id="3c32c-107">Usługa</span><span class="sxs-lookup"><span data-stu-id="3c32c-107">Service</span></span>  
 <span data-ttu-id="3c32c-108">Jest to implementacja usługi prosty kalkulator.</span><span class="sxs-lookup"><span data-stu-id="3c32c-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="3c32c-109">Odnajdywanie związane z kodem znajduje się w `Main` gdzie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> jest dodawany do hosta usługi i <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> jest dodawany, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="3c32c-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="3c32c-110">Klient</span><span class="sxs-lookup"><span data-stu-id="3c32c-110">Client</span></span>  
 <span data-ttu-id="3c32c-111">Klient używa <xref:System.ServiceModel.Discovery.DynamicEndpoint> do lokalizowania usługi.</span><span class="sxs-lookup"><span data-stu-id="3c32c-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="3c32c-112"><xref:System.ServiceModel.Discovery.DynamicEndpoint>, Standardowy punkt końcowy jest rozpoznawany jako punkt końcowy usługi po otwarciu klienta.</span><span class="sxs-lookup"><span data-stu-id="3c32c-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="3c32c-113">W tym przypadku <xref:System.ServiceModel.Discovery.DynamicEndpoint> szuka usługi, w oparciu kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="3c32c-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="3c32c-114"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Przeprowadza wyszukiwanie ciągu <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> domyślnie.</span><span class="sxs-lookup"><span data-stu-id="3c32c-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="3c32c-115">Gdy klient zlokalizuje punkt końcowy usługi, klient łączy się z tej usługi za pośrednictwem określonego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3c32c-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 <span data-ttu-id="3c32c-116">Klient definiuje metodę o nazwie `InvokeCalculatorService` , który używa <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy w celu wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="3c32c-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="3c32c-117"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Dziedziczy <xref:System.ServiceModel.Description.ServiceEndpoint>, dzięki czemu mogą być przekazywane do `InvokeCalculatorService` metody.</span><span class="sxs-lookup"><span data-stu-id="3c32c-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="3c32c-118">Następnie w przykładzie <xref:System.ServiceModel.Discovery.DynamicEndpoint> do utworzenia wystąpienia `CalculatorServiceClient` i wywołuje różne operacje usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="3c32c-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="3c32c-119">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="3c32c-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="3c32c-120">W tym przykładzie użyto punktów końcowych HTTP i aby uruchomić ten przykład, muszą zostać dodane odpowiednie listy ACL adresu URL.</span><span class="sxs-lookup"><span data-stu-id="3c32c-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="3c32c-121">Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="3c32c-121">For more information, see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="3c32c-122">Wykonując następujące polecenie w podwyższonym poziomem uprawnień, należy dodać odpowiednie listy ACL.</span><span class="sxs-lookup"><span data-stu-id="3c32c-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="3c32c-123">Można zastąpić Twoja domena i nazwa użytkownika o wprowadzenie następujących argumentów, jeśli polecenie nie działa, ponieważ jest.</span><span class="sxs-lookup"><span data-stu-id="3c32c-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="3c32c-124">Za pomocą programu Visual Studio 2012, otwórz Basic.sln i stworzyć próbkę.</span><span class="sxs-lookup"><span data-stu-id="3c32c-124">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>  
  
3.  <span data-ttu-id="3c32c-125">Uruchom aplikację service.exe.</span><span class="sxs-lookup"><span data-stu-id="3c32c-125">Run the service.exe application.</span></span>  
  
4.  <span data-ttu-id="3c32c-126">Po uruchomieniu usługi, uruchom client.exe.</span><span class="sxs-lookup"><span data-stu-id="3c32c-126">After the service has started, run the client.exe.</span></span>  
  
5.  <span data-ttu-id="3c32c-127">Sprawdź, czy klient mógł znaleźć tę usługę, nie wiedząc o tym adresu.</span><span class="sxs-lookup"><span data-stu-id="3c32c-127">Observe that the client was able to find the service without knowing its address.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3c32c-128">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3c32c-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3c32c-129">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3c32c-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3c32c-130">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="3c32c-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3c32c-131">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3c32c-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a><span data-ttu-id="3c32c-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c32c-132">See Also</span></span>
