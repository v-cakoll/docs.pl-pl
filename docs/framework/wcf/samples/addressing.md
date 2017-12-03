---
title: Adresowanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05fe983832eb3931549bbda5ee7db7c70766cd3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="addressing"></a><span data-ttu-id="a4751-102">Adresowanie</span><span class="sxs-lookup"><span data-stu-id="a4751-102">Addressing</span></span>
<span data-ttu-id="a4751-103">Przykładowe adresowanie przedstawiono różne aspekty i funkcje adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a4751-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="a4751-104">Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a4751-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="a4751-105">W tym przykładzie usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="a4751-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="a4751-106">Zarówno usługa i klient są aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="a4751-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="a4751-107">Usługa definiuje wiele punktów końcowych przy użyciu kombinacji adresy punktów końcowych względne i bezwzględne.</span><span class="sxs-lookup"><span data-stu-id="a4751-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4751-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a4751-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a4751-109">Plik konfiguracyjny usługi Określa adres bazowy i czterech punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a4751-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="a4751-110">Adres podstawowy jest określona za pomocą elementu add, w obszarze usługi/hosta/baseAddress, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="a4751-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="a4751-111">Pierwszy definicji punktu końcowego pokazano w poniższych Przykładowa konfiguracja Określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adres względny zgodnie z regułami kompozycji identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="a4751-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="a4751-112">W takim przypadku adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="a4751-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="a4751-113">Adres rzeczywisty punkt końcowy jest http://localhost: 8000/servicemodelsamples/usług.</span><span class="sxs-lookup"><span data-stu-id="a4751-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
 <span data-ttu-id="a4751-114">Druga definicja punkt końcowy określa również adresem względnym, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="a4751-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="a4751-115">Adres względny "test", jest dołączany do adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="a4751-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="a4751-116">Adres rzeczywisty punkt końcowy jest http://localhost: 8000/servicemodelsamples/service/testowanie oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="a4751-116">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
 <span data-ttu-id="a4751-117">Trzeci definicji punktu końcowego określa adresu bezwzględnego, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="a4751-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="a4751-118">Adres podstawowy pełni żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="a4751-118">The base address plays no role in the address.</span></span> <span data-ttu-id="a4751-119">Adres rzeczywisty punkt końcowy jest http://localhost:8001/hello/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="a4751-119">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
 <span data-ttu-id="a4751-120">Adres punktu końcowego czwarty Określa adres bezwzględny i innego transportu — TCP.</span><span class="sxs-lookup"><span data-stu-id="a4751-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="a4751-121">Adres podstawowy pełni żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="a4751-121">The base address plays no role in the address.</span></span> <span data-ttu-id="a4751-122">Adres rzeczywisty punkt końcowy jest NET.TCP://localhost: 9000/servicemodelsamples/usług.</span><span class="sxs-lookup"><span data-stu-id="a4751-122">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
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
  
 <span data-ttu-id="a4751-123">Klient uzyskuje dostęp do co najmniej jeden punktów końcowych cztery usługi, ale wszystkie cztery są zdefiniowane w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a4751-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="a4751-124">Klient wybiera punkt końcowy, podczas tworzenia `CalculatorProxy` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a4751-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="a4751-125">Zmiana nazwy konfiguracji z `CalculatorEndpoint1` za pośrednictwem `CalculatorEndpoint4`, można wykonywać każdego z punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a4751-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="a4751-126">Po uruchomieniu próbki usługi wylicza adres powiązanie nazwy i nazwy kontraktu dla każdego z jego punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a4751-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="a4751-127">Punkt końcowy metadanych programu exchange (MEX) jest tylko inny punkt końcowy z punktu widzenia ServiceHost, jest wyświetlane na liście.</span><span class="sxs-lookup"><span data-stu-id="a4751-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```  
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
  
 <span data-ttu-id="a4751-128">Po uruchomieniu klienta operacji żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="a4751-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="a4751-129">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="a4751-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a4751-130">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="a4751-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a4751-131">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4751-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a4751-132">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4751-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a4751-133">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4751-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4751-134">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="a4751-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a4751-135">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a4751-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a4751-136">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a4751-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a4751-137">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a4751-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a4751-138">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a4751-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
  
## <a name="see-also"></a><span data-ttu-id="a4751-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4751-139">See Also</span></span>
