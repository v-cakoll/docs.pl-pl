---
title: 'Instrukcje: Konfigurowanie niestandardowego powiązania WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 3d6f74d88dc9db775718c0098eccced4750d3b75
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184507"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="20695-102">Instrukcje: Konfigurowanie niestandardowego powiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="20695-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="20695-103">W tym temacie wyjaśniono, jak skonfigurować niestandardowe protokołu WS-Metadata exchange powiązania.</span><span class="sxs-lookup"><span data-stu-id="20695-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="20695-104">Windows Communication Foundation (WCF) zawiera cztery powiązania metadane zdefiniowane przez system, ale można opublikować za pomocą dowolnego powiązania, który ma metadanych.</span><span class="sxs-lookup"><span data-stu-id="20695-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="20695-105">W tym temacie opisano, jak można opublikować za pomocą metadanych `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="20695-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="20695-106">To powiązanie zapewnia możliwość ujawnienia metadanych w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="20695-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="20695-107">Kod ten artykuł jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="20695-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="20695-108">Korzystanie z pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="20695-108">Using a configuration file</span></span>  
  
1.  <span data-ttu-id="20695-109">W pliku konfiguracji usługi, należy dodać zachowanie usługi, który zawiera `serviceMetadata` tag:</span><span class="sxs-lookup"><span data-stu-id="20695-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="20695-110">Dodaj `behaviorConfiguration` atrybut do tagu usługi, która odwołuje się to nowe zachowanie:</span><span class="sxs-lookup"><span data-stu-id="20695-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  <span data-ttu-id="20695-111">Dodawanie punktu końcowego metadanych, określając mex jako adres, `wsHttpBinding` używanego w powiązaniu i <xref:System.ServiceModel.Description.IMetadataExchange> jako umowy:</span><span class="sxs-lookup"><span data-stu-id="20695-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  <span data-ttu-id="20695-112">Aby sprawdzić, czy punkt końcowy wymiany metadanych jest pracy poprawnie dodać tag punktu końcowego w pliku konfiguracji klienta:</span><span class="sxs-lookup"><span data-stu-id="20695-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  <span data-ttu-id="20695-113">W metodzie Main() klienta, Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, ustaw jego <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> i następnie iterację kolekcji metadanych zwróconych:</span><span class="sxs-lookup"><span data-stu-id="20695-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="20695-114">Skonfigurować przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="20695-114">Configuring by code</span></span>  
  
1.  <span data-ttu-id="20695-115">Utwórz <xref:System.ServiceModel.WSHttpBinding> wystąpienie obiektu binding:</span><span class="sxs-lookup"><span data-stu-id="20695-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  <span data-ttu-id="20695-116">Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="20695-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  <span data-ttu-id="20695-117">Dodaj punkt końcowy usługi i Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="20695-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  <span data-ttu-id="20695-118">Dodaj punkt końcowy wymiany metadanych, określając <xref:System.ServiceModel.WSHttpBinding> utworzony wcześniej:</span><span class="sxs-lookup"><span data-stu-id="20695-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  <span data-ttu-id="20695-119">Aby sprawdzić, czy punkt końcowy wymiany metadanych działa poprawnie, należy dodać tag punktu końcowego w pliku konfiguracji klienta:</span><span class="sxs-lookup"><span data-stu-id="20695-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  <span data-ttu-id="20695-120">W metodzie Main() klienta, Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, należy ustawić <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> i następnie iterację kolekcji metadanych zwróconych:</span><span class="sxs-lookup"><span data-stu-id="20695-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="20695-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20695-121">See Also</span></span>  
 [<span data-ttu-id="20695-122">Zachowanie publikowania metadanych</span><span class="sxs-lookup"><span data-stu-id="20695-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [<span data-ttu-id="20695-123">Pobieranie metadanych</span><span class="sxs-lookup"><span data-stu-id="20695-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [<span data-ttu-id="20695-124">Metadane</span><span class="sxs-lookup"><span data-stu-id="20695-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="20695-125">Publikowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="20695-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [<span data-ttu-id="20695-126">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="20695-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
