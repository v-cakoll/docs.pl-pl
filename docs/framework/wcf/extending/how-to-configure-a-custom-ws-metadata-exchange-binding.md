---
title: 'Instrukcje: konfigurowanie niestandardowego wiązania WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: b4a4005a23c8c74edecb00475669e019b50a17af
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851222"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="1bf43-102">Instrukcje: konfigurowanie niestandardowego wiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="1bf43-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="1bf43-103">W tym temacie opisano sposób konfigurowania niestandardowego powiązania usługi WS-Metadata Exchange.</span><span class="sxs-lookup"><span data-stu-id="1bf43-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="1bf43-104">Windows Communication Foundation (WCF) obejmuje cztery zdefiniowane przez system powiązania metadanych, ale można opublikować metadane przy użyciu dowolnego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1bf43-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="1bf43-105">W `wsHttpBinding`tym temacie przedstawiono sposób publikowania metadanych przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="1bf43-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="1bf43-106">To powiązanie umożliwia bezpieczne udostępnianie metadanych.</span><span class="sxs-lookup"><span data-stu-id="1bf43-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="1bf43-107">Kod w tym artykule jest oparty na [wprowadzenie](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1bf43-107">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="1bf43-108">Korzystanie z pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1bf43-108">Using a configuration file</span></span>  
  
1. <span data-ttu-id="1bf43-109">W pliku konfiguracji usługi Dodaj zachowanie usługi, które zawiera `serviceMetadata` Tag:</span><span class="sxs-lookup"><span data-stu-id="1bf43-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="1bf43-110">`behaviorConfiguration` Dodaj atrybut do tagu usługi, który odwołuje się do tego nowego zachowania:</span><span class="sxs-lookup"><span data-stu-id="1bf43-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. <span data-ttu-id="1bf43-111">Dodaj punkt końcowy metadanych określający MEX jako adres, `wsHttpBinding` jako powiązanie i <xref:System.ServiceModel.Description.IMetadataExchange> jako kontrakt:</span><span class="sxs-lookup"><span data-stu-id="1bf43-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="1bf43-112">Aby sprawdzić, czy punkt końcowy wymiany metadanych działa prawidłowo, Dodaj tag punktu końcowego w pliku konfiguracji klienta:</span><span class="sxs-lookup"><span data-stu-id="1bf43-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="1bf43-113">W głównej <xref:System.ServiceModel.Description.MetadataExchangeClient> metodzie klienta Utwórz nowe wystąpienie, ustaw jego <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwość na `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , a następnie wykonaj iterację w kolekcji zwróconych metadanych:</span><span class="sxs-lookup"><span data-stu-id="1bf43-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="1bf43-114">Konfigurowanie przez kod</span><span class="sxs-lookup"><span data-stu-id="1bf43-114">Configuring by code</span></span>  
  
1. <span data-ttu-id="1bf43-115">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> powiązania:</span><span class="sxs-lookup"><span data-stu-id="1bf43-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="1bf43-116"><xref:System.ServiceModel.ServiceHost> Utwórz wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="1bf43-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="1bf43-117">Dodaj punkt końcowy usługi i Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="1bf43-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="1bf43-118">Dodaj punkt końcowy wymiany metadanych, określając <xref:System.ServiceModel.WSHttpBinding> utworzony wcześniej:</span><span class="sxs-lookup"><span data-stu-id="1bf43-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="1bf43-119">Aby sprawdzić, czy punkt końcowy wymiany metadanych działa prawidłowo, Dodaj tag punktu końcowego w pliku konfiguracji klienta:</span><span class="sxs-lookup"><span data-stu-id="1bf43-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="1bf43-120">W <xref:System.ServiceModel.Description.MetadataExchangeClient> głównej metodzie klienta Utwórz nowe wystąpienie, <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> ustaw właściwość na `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , a następnie wykonaj iterację w kolekcji zwróconych metadanych:</span><span class="sxs-lookup"><span data-stu-id="1bf43-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1bf43-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bf43-121">See also</span></span>

- [<span data-ttu-id="1bf43-122">Zachowanie publikowania metadanych</span><span class="sxs-lookup"><span data-stu-id="1bf43-122">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="1bf43-123">Pobieranie metadanych</span><span class="sxs-lookup"><span data-stu-id="1bf43-123">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="1bf43-124">Metadane</span><span class="sxs-lookup"><span data-stu-id="1bf43-124">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="1bf43-125">Publikowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="1bf43-125">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="1bf43-126">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="1bf43-126">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
