---
title: Zachowanie publikowania metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 3b3057d845ac37280ff46e6e15415758f1f0ba77
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714781"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="2647f-102">Zachowanie publikowania metadanych</span><span class="sxs-lookup"><span data-stu-id="2647f-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="2647f-103">Przykład zachowania publikowania metadanych pokazuje, jak sterować funkcjami publikowania metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="2647f-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="2647f-104">Aby zapobiec przypadkowemu ujawnieniu potencjalnie poufnych metadanych usługi, konfiguracja domyślna dla usług Windows Communication Foundation (WCF) wyłącza Publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="2647f-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="2647f-105">To zachowanie jest domyślnie bezpieczne, ale oznacza to, że nie można użyć narzędzia do importowania metadanych (takiego jak Svcutil. exe) w celu wygenerowania kodu klienta wymaganego do wywołania usługi, chyba że zachowanie publikowania metadanych usługi jest jawnie włączone w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2647f-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2647f-106">Dla jasności ten przykład pokazuje, jak utworzyć niezabezpieczony punkt końcowy publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="2647f-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="2647f-107">Takie punkty końcowe są potencjalnie dostępne dla anonimowych użytkowników nieuwierzytelnionych i należy zachować ostrożność przed wdrożeniem takich punktów końcowych, aby upewnić się, że można publicznie odzamknąć metadane usługi.</span><span class="sxs-lookup"><span data-stu-id="2647f-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="2647f-108">Zapoznaj się z przykładem [niestandardowego bezpiecznego punktu końcowego metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) dla przykładu, który zabezpiecza punkt końcowy metadanych.</span><span class="sxs-lookup"><span data-stu-id="2647f-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="2647f-109">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje kontrakt usługi `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="2647f-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="2647f-110">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="2647f-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2647f-111">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2647f-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2647f-112">Aby usługa mogła uwidaczniać metadane, należy skonfigurować <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w usłudze.</span><span class="sxs-lookup"><span data-stu-id="2647f-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="2647f-113">Gdy to zachowanie jest obecne, można opublikować metadane, konfigurując punkt końcowy, aby uwidocznić kontrakt <xref:System.ServiceModel.Description.IMetadataExchange> jako implementację protokołu WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="2647f-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="2647f-114">Jako wygoda, ten kontrakt uzyskał skróconą nazwę konfiguracji "kontraktem IMetadataExchange".</span><span class="sxs-lookup"><span data-stu-id="2647f-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="2647f-115">Ten przykład używa `mexHttpBinding`, który jest wygodnym powiązaniem standardowym odpowiadającym `wsHttpBinding` z trybem zabezpieczeń ustawionym na `None`.</span><span class="sxs-lookup"><span data-stu-id="2647f-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="2647f-116">Adres względny "Mex" jest używany w punkcie końcowym, który po rozwiązaniu z adresem podstawowym usług powoduje adres punktu końcowego `http://localhost/servicemodelsamples/service.svc/mex`.</span><span class="sxs-lookup"><span data-stu-id="2647f-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="2647f-117">Poniżej przedstawiono konfigurację zachowania:</span><span class="sxs-lookup"><span data-stu-id="2647f-117">The following shows the behavior configuration:</span></span>  
  
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
  
 <span data-ttu-id="2647f-118">Poniżej przedstawiono punkt końcowy MEX.</span><span class="sxs-lookup"><span data-stu-id="2647f-118">The following shows the MEX endpoint.</span></span>  
  
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
  
 <span data-ttu-id="2647f-119">Ten przykład ustawia właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> na `true`, która udostępnia również metadane usługi przy użyciu protokołu HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="2647f-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="2647f-120">Aby włączyć punkt końcowy metadanych HTTP GET, usługa musi mieć podstawowy adres HTTP.</span><span class="sxs-lookup"><span data-stu-id="2647f-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="2647f-121">Ciąg zapytania `?wsdl` jest używany na adresie podstawowym usługi, aby uzyskać dostęp do metadanych.</span><span class="sxs-lookup"><span data-stu-id="2647f-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="2647f-122">Na przykład aby wyświetlić WSDL dla usługi w przeglądarce internetowej, użyj adresu `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="2647f-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="2647f-123">Można również użyć tego zachowania, aby udostępnić metadane za pośrednictwem protokołu HTTPS przez ustawienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> `true`.</span><span class="sxs-lookup"><span data-stu-id="2647f-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="2647f-124">Wymaga to adresu podstawowego HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2647f-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="2647f-125">Aby uzyskać dostęp do punktu końcowego MEX usługi, użyj [Narzędzia metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2647f-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="2647f-126">Spowoduje to wygenerowanie klienta na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="2647f-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="2647f-127">Aby uzyskać dostęp do metadanych usługi przy użyciu protokołu HTTP GET, wskaż swoją przeglądarkę `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="2647f-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="2647f-128">W przypadku usunięcia tego zachowania i próby otworzenia usługi zostanie wyświetlony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2647f-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="2647f-129">Ten błąd występuje, ponieważ nie jest to zachowanie, punkt końcowy skonfigurowany z umową `IMetadataExchange` nie ma implementacji.</span><span class="sxs-lookup"><span data-stu-id="2647f-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="2647f-130">Jeśli ustawisz `HttpGetEnabled` na `false`, zostanie wyświetlona strona pomocy CalculatorService zamiast wyświetlania metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="2647f-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2647f-131">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="2647f-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2647f-132">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2647f-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2647f-133">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2647f-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2647f-134">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2647f-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2647f-135">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2647f-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2647f-136">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="2647f-136">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2647f-137">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2647f-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2647f-138">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2647f-138">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
