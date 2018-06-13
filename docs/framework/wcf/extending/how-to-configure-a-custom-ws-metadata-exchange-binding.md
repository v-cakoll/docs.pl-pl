---
title: 'Instrukcje: Konfigurowanie niestandardowego powiązania WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 0596e91204a2a9dbaed2fdbe85387ec3785fd3db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488702"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="7f097-102">Instrukcje: Konfigurowanie niestandardowego powiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="7f097-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="7f097-103">W tym temacie będzie wyjaśniają sposób konfigurowania niestandardowych WS-Metadata exchange powiązania.</span><span class="sxs-lookup"><span data-stu-id="7f097-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="7f097-104">Windows Communication Foundation (WCF) zawiera cztery powiązania zdefiniowane przez system metadanych, ale można opublikować metadanych za pomocą żadnego powiązania, które mają.</span><span class="sxs-lookup"><span data-stu-id="7f097-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="7f097-105">W tym temacie opisano sposób publikowania metadanych za pomocą `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="7f097-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="7f097-106">To powiązanie daje możliwość udostępnia metadane w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="7f097-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="7f097-107">Kod w tym artykule jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7f097-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="7f097-108">Użycie pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7f097-108">Using a configuration file</span></span>  
  
1.  <span data-ttu-id="7f097-109">W pliku konfiguracji usługi, dodać zachowanie usługi, który zawiera `serviceMetadata` tagu:</span><span class="sxs-lookup"><span data-stu-id="7f097-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="7f097-110">Dodaj `behaviorConfiguration` atrybut do tagu usługi, który odwołuje się do tego nowe zachowanie:</span><span class="sxs-lookup"><span data-stu-id="7f097-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  <span data-ttu-id="7f097-111">Dodawanie punktu końcowego metadanych Określanie mex jako adres, `wsHttpBinding` jako powiązanie, i <xref:System.ServiceModel.Description.IMetadataExchange> jako kontraktu:</span><span class="sxs-lookup"><span data-stu-id="7f097-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  <span data-ttu-id="7f097-112">Aby sprawdzić, czy punkt końcowy wymiany metadanych jest pracy poprawnie dodać tag końcowy w pliku konfiguracji klienta:</span><span class="sxs-lookup"><span data-stu-id="7f097-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  <span data-ttu-id="7f097-113">W metodzie Main() klienta, Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, ustaw jej <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `true`, wywołania <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , a następnie wykonać iterację kolekcji metadane zwrócony:</span><span class="sxs-lookup"><span data-stu-id="7f097-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="7f097-114">Konfigurowanie przez kod</span><span class="sxs-lookup"><span data-stu-id="7f097-114">Configuring by code</span></span>  
  
1.  <span data-ttu-id="7f097-115">Utwórz <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> wystąpienie obiektu binding:</span><span class="sxs-lookup"><span data-stu-id="7f097-115">Create a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  <span data-ttu-id="7f097-116">Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="7f097-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  <span data-ttu-id="7f097-117">Dodaj punkt końcowy usługi i Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="7f097-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  <span data-ttu-id="7f097-118">Dodaj punkt końcowy wymiany metadanych, określając <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> utworzony wcześniej:</span><span class="sxs-lookup"><span data-stu-id="7f097-118">Add a metadata exchange endpoint, specifying the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  <span data-ttu-id="7f097-119">Aby sprawdzić, czy punkt końcowy wymiany metadanych działa prawidłowo, należy dodać tag końcowy w pliku konfiguracji klienta:</span><span class="sxs-lookup"><span data-stu-id="7f097-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  <span data-ttu-id="7f097-120">W metodzie Main() klienta, Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, należy ustawić <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , a następnie wykonać iterację kolekcji metadane zwrócony:</span><span class="sxs-lookup"><span data-stu-id="7f097-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7f097-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f097-121">See Also</span></span>  
 [<span data-ttu-id="7f097-122">Zachowanie publikowania metadanych</span><span class="sxs-lookup"><span data-stu-id="7f097-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [<span data-ttu-id="7f097-123">Pobieranie metadanych</span><span class="sxs-lookup"><span data-stu-id="7f097-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [<span data-ttu-id="7f097-124">Metadane</span><span class="sxs-lookup"><span data-stu-id="7f097-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="7f097-125">Publikowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="7f097-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [<span data-ttu-id="7f097-126">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="7f097-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
