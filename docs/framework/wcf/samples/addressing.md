---
title: Adresowanie
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 2a737552ef5ea2a8e4544f9ec2c2f84b4b994a75
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715876"
---
# <a name="addressing"></a><span data-ttu-id="903df-102">Adresowanie</span><span class="sxs-lookup"><span data-stu-id="903df-102">Addressing</span></span>
<span data-ttu-id="903df-103">Przykład Addressing ilustruje różne aspekty i funkcje adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="903df-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="903df-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="903df-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="903df-105">W tym przykładzie usługa jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="903df-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="903df-106">Zarówno usługa, jak i klient są aplikacjami konsolowymi.</span><span class="sxs-lookup"><span data-stu-id="903df-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="903df-107">Usługa definiuje wiele punktów końcowych przy użyciu kombinacji względnych i bezwzględnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="903df-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="903df-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="903df-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="903df-109">Plik konfiguracji usługi określa adres podstawowy i cztery punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="903df-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="903df-110">Adres podstawowy jest określany przy użyciu elementu Add, w obszarze Service/Host/baseAddresses, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="903df-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 <span data-ttu-id="903df-111">Definicja pierwszego punktu końcowego pokazana w poniższej konfiguracji przykładowej określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adresu względnego, zgodnie z regułami kompozycji identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="903df-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="903df-112">W takim przypadku adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="903df-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="903df-113">Rzeczywisty adres punktu końcowego to `http://localhost:8000/servicemodelsamples/service`.</span><span class="sxs-lookup"><span data-stu-id="903df-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="903df-114">Druga definicja punktu końcowego określa adres względny, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="903df-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="903df-115">Adres względny "test" jest dołączany do adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="903df-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="903df-116">Rzeczywisty adres punktu końcowego to `http://localhost:8000/servicemodelsamples/service/test`.</span><span class="sxs-lookup"><span data-stu-id="903df-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="903df-117">Definicja trzeciego punktu końcowego określa adres bezwzględny, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="903df-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="903df-118">Adres podstawowy nie pełni żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="903df-118">The base address plays no role in the address.</span></span> <span data-ttu-id="903df-119">Rzeczywisty adres punktu końcowego to `http://localhost:8001/hello/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="903df-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="903df-120">Czwarty adres punktu końcowego określa adres bezwzględny i inny transport — TCP.</span><span class="sxs-lookup"><span data-stu-id="903df-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="903df-121">Adres podstawowy nie pełni żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="903df-121">The base address plays no role in the address.</span></span> <span data-ttu-id="903df-122">Rzeczywisty adres punktu końcowego to `net.tcp://localhost:9000/servicemodelsamples/service`.</span><span class="sxs-lookup"><span data-stu-id="903df-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 <span data-ttu-id="903df-123">Klient uzyskuje dostęp tylko do jednego z czterech punktów końcowych usługi, ale wszystkie cztery są zdefiniowane w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="903df-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="903df-124">Po utworzeniu obiektu `CalculatorProxy` klient wybierze punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="903df-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="903df-125">Zmieniając nazwę konfiguracji z `CalculatorEndpoint1` na `CalculatorEndpoint4`, można wykonać każdy z punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="903df-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="903df-126">Po uruchomieniu przykładu usługa wylicza adres, nazwę powiązania i nazwę kontraktu dla każdego z punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="903df-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="903df-127">Punkt końcowy wymiany metadanych (MEX) jest tylko innym punktem końcowym w perspektywie hosta ServiceHost, aby został wyświetlony na liście.</span><span class="sxs-lookup"><span data-stu-id="903df-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```console  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="903df-128">Po uruchomieniu klienta żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="903df-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="903df-129">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="903df-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="903df-130">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="903df-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="903df-131">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="903df-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="903df-132">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="903df-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="903df-133">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="903df-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="903df-134">Jeśli używasz programu Svcutil. exe w celu ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj, aby zmodyfikować nazwę punktu końcowego w konfiguracji klienta w celu dopasowania go do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="903df-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="903df-135">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="903df-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="903df-136">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="903df-136">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="903df-137">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="903df-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="903df-138">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="903df-138">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
