---
title: Wiele punktów końcowych
ms.date: 03/30/2017
helpviewer_keywords:
- Multiple EndPoints
ms.assetid: 8f0c2e1f-9aee-41c2-8301-c72b7f664412
ms.openlocfilehash: 7fe38e685b662a0dbfe6f818a597776802eada42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930350"
---
# <a name="multiple-endpoints"></a><span data-ttu-id="d404e-102">Wiele punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="d404e-102">Multiple Endpoints</span></span>
<span data-ttu-id="d404e-103">Przykład wielu punktów końcowych pokazuje, jak skonfigurować wiele punktów końcowych w usłudze i jak komunikować się z każdym punktem końcowym klienta.</span><span class="sxs-lookup"><span data-stu-id="d404e-103">The Multiple Endpoints sample demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span> <span data-ttu-id="d404e-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d404e-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="d404e-105">Konfiguracja usługi została zmodyfikowana w celu zdefiniowania dwóch punktów końcowych `ICalculator` , które obsługują kontrakt, ale każdy z nich na innym adresie przy użyciu innego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d404e-105">The service configuration has been modified to define two endpoints that support the `ICalculator` contract, but each at a different address using a different binding.</span></span> <span data-ttu-id="d404e-106">Konfiguracja i kod klienta zostały zmodyfikowane w celu komunikowania się z obydwoma punktami końcowymi usługi.</span><span class="sxs-lookup"><span data-stu-id="d404e-106">The client configuration and code have been modified to communicate with both of the service endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d404e-107">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d404e-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d404e-108">Plik Web. config usługi został zmodyfikowany w celu zdefiniowania dwóch punktów końcowych, z których `ICalculator` każdy obsługuje ten sam kontrakt, ale na różnych adresach przy użyciu różnych powiązań.</span><span class="sxs-lookup"><span data-stu-id="d404e-108">The service Web.config file has been modified to define two endpoints, each supporting the same `ICalculator` contract, but at different addresses using different bindings.</span></span> <span data-ttu-id="d404e-109">Pierwszy punkt końcowy jest zdefiniowany pod adresem podstawowym przy użyciu `basicHttpBinding` powiązania, które nie ma włączonej funkcji zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="d404e-109">The first endpoint is defined at the base address using a `basicHttpBinding` binding, which does not have security enabled.</span></span> <span data-ttu-id="d404e-110">Drugi punkt końcowy jest zdefiniowany w lokalizacji {BaseAddress}/Secure przy `wsHttpBinding` użyciu powiązania, które jest zabezpieczone domyślnie przy użyciu protokołu WS-Security z uwierzytelnianiem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d404e-110">The second endpoint is defined at {baseaddress}/secure using a `wsHttpBinding` binding, which is secure by default, using WS-Security with Windows authentication.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- This endpoint is exposed at the base address provided by host:  
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- secure endpoint exposed at {base address}/secure:  
       http://localhost/servicemodelsamples/service.svc/secure -->  
  <endpoint address="secure"  
            binding="wsHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="d404e-111">Oba punkty końcowe są również skonfigurowane na kliencie.</span><span class="sxs-lookup"><span data-stu-id="d404e-111">Both endpoints are also configured on the client.</span></span> <span data-ttu-id="d404e-112">Te punkty końcowe są podane nazwami, dzięki czemu obiekt wywołujący może przekazać odpowiednią nazwę punktu końcowego do konstruktora klienta.</span><span class="sxs-lookup"><span data-stu-id="d404e-112">These endpoints are given names so that the caller can pass the desired endpoint name into the constructor of the client.</span></span>  
  
```xml  
<client>  
  <!-- Passing "basic" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="basic"  
            address="http://localhost/servicemodelsamples/service.svc"   
            binding="basicHttpBinding"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- Passing "secure" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="secure"  
            address="http://localhost/servicemodelsamples/service.svc/secure"   
            binding="wsHttpBinding"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 <span data-ttu-id="d404e-113">Klient używa obu punktów końcowych, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d404e-113">The client uses both endpoints as shown in the following code.</span></span>  
  
```csharp  
static void Main()  
{  
    // Create a client to the basic endpoint configuration.  
    CalculatorClient client = new CalculatorClient("basic");  
    Console.WriteLine("Communicate with basic endpoint.");  
    // call operations  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    // Create a client to the secure endpoint configuration.  
    client = new CalculatorClient("secure");  
    Console.WriteLine("Communicate with secure endpoint.");  
    // Call operations.  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="d404e-114">Po uruchomieniu klienta wyświetlane są interakcje z obu punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="d404e-114">When you run the client, interactions with both endpoints are displayed.</span></span>  
  
```  
Communicate with basic endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Communicate with secure endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d404e-115">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="d404e-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d404e-116">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d404e-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d404e-117">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d404e-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d404e-118">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d404e-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d404e-119">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d404e-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d404e-120">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="d404e-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d404e-121">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d404e-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d404e-122">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d404e-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpoints`  
