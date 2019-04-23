---
title: Zachowanie publikowania metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 20922636f140e0ac9faff55bf94c0b2633a8070d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773925"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="07f49-102">Zachowanie publikowania metadanych</span><span class="sxs-lookup"><span data-stu-id="07f49-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="07f49-103">Przykład zachowania publikowania metadanych pokazuje, jak do kontrolowania funkcji publikowania metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="07f49-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="07f49-104">Aby zapobiegać niezamierzonym ujawnieniem metadanych usługi potencjalnie poufnych, konfigurację domyślną dla usług Windows Communication Foundation (WCF) powoduje wyłączenie publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="07f49-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="07f49-105">To zachowanie jest domyślnie bezpieczny, ale również zaimportować narzędzia (takie jak Svcutil.exe) oznacza, że metadane nie można użyć do wygenerowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie publikowania metadanych usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="07f49-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07f49-106">Dla jasności ten przykład przedstawia sposób tworzenia punkt końcowy publikowania metadanych niezabezpieczona.</span><span class="sxs-lookup"><span data-stu-id="07f49-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="07f49-107">Takie punkty końcowe są potencjalnie dostępne dla anonimowe, nieuwierzytelnione konsumentów i należy uważać, przed wdrożeniem tych punktów końcowych w celu zapewnienia publicznie ujawniająca metadanych usługi odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="07f49-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="07f49-108">Zobacz [niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) próbki dla przykładu, który zabezpiecza punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="07f49-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="07f49-109">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="07f49-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="07f49-110">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="07f49-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07f49-111">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="07f49-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="07f49-112">Usługi do udostępnienia metadanych <xref:System.ServiceModel.Description.ServiceMetadataBehavior> musi być skonfigurowany w usłudze.</span><span class="sxs-lookup"><span data-stu-id="07f49-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="07f49-113">Jeśli jest to zachowanie, możesz opublikować metadanych, konfigurując punkt końcowy do udostępnienia <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt co implementacją protokołu WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="07f49-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="07f49-114">Dla wygody ten kontrakt nadano nazwę skróconą konfiguracji "IMetadataExchange".</span><span class="sxs-lookup"><span data-stu-id="07f49-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="07f49-115">W tym przykładzie użyto `mexHttpBinding`, czyli standardowa powiązanie udogodnienie jest odpowiednikiem `wsHttpBinding` tryb zabezpieczeń, ustawiono na `None`.</span><span class="sxs-lookup"><span data-stu-id="07f49-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="07f49-116">Względna adres "mex" jest używany w punkcie końcowym, który, gdy rozstrzygnięte na usług podstawowy adres skutkuje adres punktu końcowego `http://localhost/servicemodelsamples/service.svc/mex`.</span><span class="sxs-lookup"><span data-stu-id="07f49-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="07f49-117">Poniżej przedstawiono konfigurację zachowania:</span><span class="sxs-lookup"><span data-stu-id="07f49-117">The following shows the behavior configuration:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="07f49-118">Poniżej przedstawiono końcowy wymiany Metadanych.</span><span class="sxs-lookup"><span data-stu-id="07f49-118">The following shows the MEX endpoint.</span></span>  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="07f49-119">W tym przykładzie ustawia <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwość `true`, która udostępnia również metadane usługi przy użyciu HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="07f49-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="07f49-120">Aby włączyć punkt końcowy metadanych HTTP GET, usługa musi mieć określony podstawowy adres HTTP.</span><span class="sxs-lookup"><span data-stu-id="07f49-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="07f49-121">Ciąg zapytania `?wsdl` na adres podstawowy usługi służy do dostępu do metadanych.</span><span class="sxs-lookup"><span data-stu-id="07f49-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="07f49-122">Na przykład, aby zobaczyć WSDL usługi w przeglądarce sieci Web możesz użyć adresu `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="07f49-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="07f49-123">Alternatywnie możesz użyć tego zachowania do udostępnienia metadanych za pośrednictwem protokołu HTTPS, ustawiając <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> do `true`.</span><span class="sxs-lookup"><span data-stu-id="07f49-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="07f49-124">Wymaga to bazowy adres HTTPS.</span><span class="sxs-lookup"><span data-stu-id="07f49-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="07f49-125">Użyj punktu końcowego MEX usługi dostępu do [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="07f49-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="07f49-126">Spowoduje to wygenerowanie klienta na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="07f49-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="07f49-127">Aby uzyskać dostęp do metadanych usługi przy użyciu HTTP GET, należy wskazać przeglądarkę, aby `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="07f49-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="07f49-128">Jeśli możesz usunąć to zachowanie i spróbuj otworzyć usługi otrzymujesz wyjątek.</span><span class="sxs-lookup"><span data-stu-id="07f49-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="07f49-129">Ten błąd występuje, ponieważ bez zachowania, punkt końcowy skonfigurowany przy użyciu `IMetadataExchange` Umowy nie ma implementacji.</span><span class="sxs-lookup"><span data-stu-id="07f49-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="07f49-130">Jeśli ustawisz `HttpGetEnabled` do `false`, zostanie wyświetlona strona pomocy CalculatorService zamiast zobaczyć metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="07f49-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="07f49-131">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="07f49-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="07f49-132">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="07f49-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="07f49-133">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="07f49-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="07f49-134">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="07f49-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07f49-135">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="07f49-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="07f49-136">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="07f49-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="07f49-137">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="07f49-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07f49-138">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="07f49-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
