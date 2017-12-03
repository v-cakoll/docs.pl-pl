---
title: "Instrukcje: Konfigurowanie niestandardowego powiązania WS-Metadata Exchange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 497d7242b581a61aa156741a8c2f0ea278fe2372
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="4bf80-102">Instrukcje: Konfigurowanie niestandardowego powiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="4bf80-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="4bf80-103">W tym temacie będzie wyjaśniają sposób konfigurowania niestandardowych WS-Metadata exchange powiązania.</span><span class="sxs-lookup"><span data-stu-id="4bf80-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="4bf80-104">obejmuje cztery powiązań zdefiniowanych przez system metadanych, ale można opublikować metadanych za pomocą powiązania ma.</span><span class="sxs-lookup"><span data-stu-id="4bf80-104"> includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="4bf80-105">W tym temacie opisano sposób publikowania metadanych za pomocą `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="4bf80-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="4bf80-106">To powiązanie daje możliwość udostępnia metadane w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="4bf80-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="4bf80-107">Kod w tym artykule jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4bf80-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="4bf80-108">Użycie pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4bf80-108">Using a configuration file</span></span>  
  
1.  <span data-ttu-id="4bf80-109">W pliku konfiguracji usługi, dodać zachowanie usługi, który zawiera `serviceMetadata` tagu:</span><span class="sxs-lookup"><span data-stu-id="4bf80-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="4bf80-110">Dodaj `behaviorConfiguration` atrybut do tagu usługi, który odwołuje się do tego nowe zachowanie:</span><span class="sxs-lookup"><span data-stu-id="4bf80-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  <span data-ttu-id="4bf80-111">Dodawanie punktu końcowego metadanych Określanie mex jako adres, `wsHttpBinding` jako powiązanie, i <xref:System.ServiceModel.Description.IMetadataExchange> jako kontraktu:</span><span class="sxs-lookup"><span data-stu-id="4bf80-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  <span data-ttu-id="4bf80-112">Aby sprawdzić, czy punkt końcowy wymiany metadanych jest pracy poprawnie dodać tag końcowy w pliku konfiguracji klienta:</span><span class="sxs-lookup"><span data-stu-id="4bf80-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  <span data-ttu-id="4bf80-113">W metodzie Main() klienta, Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, ustaw jej <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `true`, wywołania <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , a następnie wykonać iterację kolekcji metadane zwrócony:</span><span class="sxs-lookup"><span data-stu-id="4bf80-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="4bf80-114">Konfigurowanie przez kod</span><span class="sxs-lookup"><span data-stu-id="4bf80-114">Configuring by code</span></span>  
  
1.  <span data-ttu-id="4bf80-115">Utwórz <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> wystąpienie obiektu binding:</span><span class="sxs-lookup"><span data-stu-id="4bf80-115">Create a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  <span data-ttu-id="4bf80-116">Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="4bf80-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  <span data-ttu-id="4bf80-117">Dodaj punkt końcowy usługi i Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="4bf80-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  <span data-ttu-id="4bf80-118">Dodaj punkt końcowy wymiany metadanych, określając <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> utworzony wcześniej:</span><span class="sxs-lookup"><span data-stu-id="4bf80-118">Add a metadata exchange endpoint, specifying the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  <span data-ttu-id="4bf80-119">Aby sprawdzić, czy punkt końcowy wymiany metadanych działa prawidłowo, należy dodać tag końcowy w pliku konfiguracji klienta:</span><span class="sxs-lookup"><span data-stu-id="4bf80-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  <span data-ttu-id="4bf80-120">W metodzie Main() klienta, Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, należy ustawić <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , a następnie wykonać iterację kolekcji metadane zwrócony:</span><span class="sxs-lookup"><span data-stu-id="4bf80-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4bf80-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4bf80-121">See Also</span></span>  
 [<span data-ttu-id="4bf80-122">Zachowanie publikowania metadanych</span><span class="sxs-lookup"><span data-stu-id="4bf80-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [<span data-ttu-id="4bf80-123">Pobieranie metadanych</span><span class="sxs-lookup"><span data-stu-id="4bf80-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [<span data-ttu-id="4bf80-124">Metadane</span><span class="sxs-lookup"><span data-stu-id="4bf80-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="4bf80-125">Publikowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="4bf80-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [<span data-ttu-id="4bf80-126">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="4bf80-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
