---
title: 'Instrukcje: Konfigurowanie niestandardowego wiązania WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 9676ae4053553b84488602627b28790aae22eff6
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345279"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="02694-102">Instrukcje: Konfigurowanie niestandardowego wiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="02694-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="02694-103">W tym temacie wyjaśniono, jak skonfigurować niestandardowe powiązanie wymiany metadanych w usłudze WS.</span><span class="sxs-lookup"><span data-stu-id="02694-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="02694-104">Windows Communication Foundation (WCF) zawiera cztery powiązania metadanych zdefiniowane przez system, ale można publikować metadane przy użyciu dowolnego powiązania, które chcesz.</span><span class="sxs-lookup"><span data-stu-id="02694-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="02694-105">W tym temacie pokazano, jak publikować metadane przy użyciu pliku `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="02694-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="02694-106">To powiązanie umożliwia udostępnianie metadanych w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="02694-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="02694-107">Kod w tym artykule jest oparty na [wprowadzenie](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="02694-107">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="02694-108">Korzystanie z pliku konfiguracyjnego</span><span class="sxs-lookup"><span data-stu-id="02694-108">Using a configuration file</span></span>  
  
1. <span data-ttu-id="02694-109">W pliku konfiguracyjnym usługi dodaj zachowanie `serviceMetadata` usługi zawierające znacznik:</span><span class="sxs-lookup"><span data-stu-id="02694-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="02694-110">Dodaj `behaviorConfiguration` atrybut do tagu usługi, który odwołuje się do tego nowego zachowania:</span><span class="sxs-lookup"><span data-stu-id="02694-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior" />
    ```  
  
3. <span data-ttu-id="02694-111">Dodaj punkt końcowy metadanych określając mex `wsHttpBinding` jako adres, <xref:System.ServiceModel.Description.IMetadataExchange> jako powiązanie i jako kontrakt:</span><span class="sxs-lookup"><span data-stu-id="02694-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="02694-112">Aby sprawdzić, czy punkt końcowy wymiany metadanych działa poprawnie, dodaj tag punktu końcowego w pliku konfiguracji klienta:</span><span class="sxs-lookup"><span data-stu-id="02694-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="02694-113">W metodzie Main() klienta utwórz <xref:System.ServiceModel.Description.MetadataExchangeClient> nowe wystąpienie, ustaw jego <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwość na , wywołaj, `true` <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a następnie iteruj za pomocą kolekcji zwróconych metadanych:</span><span class="sxs-lookup"><span data-stu-id="02694-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="02694-114">Konfigurowanie według kodu</span><span class="sxs-lookup"><span data-stu-id="02694-114">Configuring by code</span></span>  
  
1. <span data-ttu-id="02694-115">Tworzenie <xref:System.ServiceModel.WSHttpBinding> wystąpienia wiązania:</span><span class="sxs-lookup"><span data-stu-id="02694-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="02694-116">Tworzenie <xref:System.ServiceModel.ServiceHost> wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="02694-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="02694-117">Dodaj punkt końcowy usługi <xref:System.ServiceModel.Description.ServiceMetadataBehavior> i dodaj wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="02694-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="02694-118">Dodaj punkt końcowy wymiany metadanych, określając <xref:System.ServiceModel.WSHttpBinding> utworzony wcześniej:</span><span class="sxs-lookup"><span data-stu-id="02694-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="02694-119">Aby sprawdzić, czy punkt końcowy wymiany metadanych działa poprawnie, dodaj znacznik punktu końcowego w pliku konfiguracji klienta:</span><span class="sxs-lookup"><span data-stu-id="02694-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="02694-120">W metodzie Main() klienta utwórz <xref:System.ServiceModel.Description.MetadataExchangeClient> nowe wystąpienie, ustaw <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwość na , wywołaj, `true` <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a następnie iteruj za pomocą kolekcji zwróconych metadanych:</span><span class="sxs-lookup"><span data-stu-id="02694-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="02694-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02694-121">See also</span></span>

- [<span data-ttu-id="02694-122">Zachowanie publikowania metadanych</span><span class="sxs-lookup"><span data-stu-id="02694-122">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="02694-123">Pobieranie metadanych</span><span class="sxs-lookup"><span data-stu-id="02694-123">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="02694-124">Metadane</span><span class="sxs-lookup"><span data-stu-id="02694-124">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="02694-125">Publikowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="02694-125">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="02694-126">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="02694-126">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
