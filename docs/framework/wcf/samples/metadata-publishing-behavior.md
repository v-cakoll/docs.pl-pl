---
title: Zachowanie publikowania metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: dade6d1a53fd99b994fb3c027db4e51392bfdcda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144399"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="8713b-102">Zachowanie publikowania metadanych</span><span class="sxs-lookup"><span data-stu-id="8713b-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="8713b-103">Przykład zachowania publikowania metadanych pokazuje, jak kontrolować funkcje publikowania metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="8713b-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="8713b-104">Aby zapobiec niezamierzonemu ujawnieniu potencjalnie poufnych metadanych usługi, domyślna konfiguracja usług Windows Communication Foundation (WCF) wyłącza publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8713b-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="8713b-105">To zachowanie jest domyślnie bezpieczne, ale oznacza również, że nie można użyć narzędzia importu metadanych (na przykład Svcutil.exe) do generowania kodu klienta wymaganego do wywołania usługi, chyba że zachowanie publikowania metadanych usługi jest jawnie włączone w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8713b-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8713b-106">Dla jasności w tym przykładzie pokazano, jak utworzyć niezabezpieczony punkt końcowy publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="8713b-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="8713b-107">Takie punkty końcowe są potencjalnie dostępne dla anonimowych nieuwierzytetycznych konsumentów i należy zwrócić uwagę przed wdrożeniem takich punktów końcowych, aby upewnić się, że publiczne ujawnienie metadanych usługi jest właściwe.</span><span class="sxs-lookup"><span data-stu-id="8713b-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="8713b-108">Zobacz przykład [niestandardowego bezpiecznego punktu końcowego metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) dla przykładu, który zabezpiecza punkt końcowy metadanych.</span><span class="sxs-lookup"><span data-stu-id="8713b-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="8713b-109">Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` który implementuje umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="8713b-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="8713b-110">W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="8713b-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8713b-111">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="8713b-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8713b-112">Aby usługa uwidaczniała <xref:System.ServiceModel.Description.ServiceMetadataBehavior> metadane, musi być skonfigurowana w usłudze.</span><span class="sxs-lookup"><span data-stu-id="8713b-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="8713b-113">Gdy to zachowanie jest obecny, można opublikować metadane, <xref:System.ServiceModel.Description.IMetadataExchange> konfigurując punkt końcowy, aby udostępnić kontrakt jako implementację protokołu WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="8713b-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="8713b-114">Dla wygody tego kontraktu nadano skróconą nazwę konfiguracji "IMetadataExchange".</span><span class="sxs-lookup"><span data-stu-id="8713b-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="8713b-115">W tym przykładzie użyto wiązania standardowego, `mexHttpBinding`który `wsHttpBinding` jest odpowiednikiem `None`z trybem zabezpieczeń ustawionym na .</span><span class="sxs-lookup"><span data-stu-id="8713b-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="8713b-116">Względny adres "mex" jest używany w punkcie końcowym, który po rozwiązaniu względem adresu `http://localhost/servicemodelsamples/service.svc/mex`podstawowego usług powoduje adres końcowy .</span><span class="sxs-lookup"><span data-stu-id="8713b-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="8713b-117">Poniżej przedstawiono konfigurację zachowania:</span><span class="sxs-lookup"><span data-stu-id="8713b-117">The following shows the behavior configuration:</span></span>  
  
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
  
 <span data-ttu-id="8713b-118">Poniżej przedstawiono punkt końcowy MEX.</span><span class="sxs-lookup"><span data-stu-id="8713b-118">The following shows the MEX endpoint.</span></span>  
  
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
  
 <span data-ttu-id="8713b-119">W tym <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> przykładzie `true`ustawia właściwość, która również udostępnia metadane usługi przy użyciu protokołu HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="8713b-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="8713b-120">Aby włączyć punkt końcowy metadanych HTTP GET, usługa musi mieć adres podstawowy HTTP.</span><span class="sxs-lookup"><span data-stu-id="8713b-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="8713b-121">Ciąg `?wsdl` zapytania jest używany na adres podstawowy usługi, aby uzyskać dostęp do metadanych.</span><span class="sxs-lookup"><span data-stu-id="8713b-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="8713b-122">Na przykład, aby wyświetlić WSDL dla usługi w przeglądarce sieci Web, należy użyć adresu `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="8713b-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="8713b-123">Alternatywnie można użyć tego zachowania, aby udostępnić <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> metadane za pośrednictwem protokołu HTTPS, ustawiając na `true`.</span><span class="sxs-lookup"><span data-stu-id="8713b-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="8713b-124">Wymaga to adresu podstawowego HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8713b-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="8713b-125">Aby uzyskać dostęp do punktu końcowego MEX usługi, użyj [narzędzia narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="8713b-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="8713b-126">Spowoduje to wygenerowanie klienta na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="8713b-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="8713b-127">Aby uzyskać dostęp do metadanych usługi za `http://localhost/servicemodelsamples/service.svc?wsdl`pomocą protokołu HTTP GET, wskaż przeglądarkę na .</span><span class="sxs-lookup"><span data-stu-id="8713b-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="8713b-128">Jeśli usuniesz to zachowanie i spróbuj otworzyć usługę, otrzymasz wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8713b-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="8713b-129">Ten błąd występuje, ponieważ bez zachowania, punkt `IMetadataExchange` końcowy skonfigurowany z umową nie ma implementacji.</span><span class="sxs-lookup"><span data-stu-id="8713b-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="8713b-130">Jeśli ustawisz `HttpGetEnabled` , `false`zostanie wyświetlona strona pomocy CalculatorService zamiast wyświetlania metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="8713b-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8713b-131">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="8713b-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8713b-132">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8713b-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8713b-133">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8713b-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8713b-134">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8713b-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8713b-135">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8713b-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8713b-136">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="8713b-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8713b-137">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="8713b-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8713b-138">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8713b-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
