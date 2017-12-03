---
title: "Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6868bbecd83305c07e0b547d0102d7bca48d41f8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="1a3a9-102">Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych</span><span class="sxs-lookup"><span data-stu-id="1a3a9-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="1a3a9-103">Svcutil.exe służy do pobierania metadanych z uruchomionymi usługami i zapisać metadanych do plików lokalnych.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="1a3a9-104">Schematy HTTP i HTTPS URL, aby uzyskać Svcutil.exe próbuje pobrać metadanych za pomocą usługi WS-MetadataExchange i [odnajdowanie usługi XML sieci Web](http://go.microsoft.com/fwlink/?LinkId=94950).</span><span class="sxs-lookup"><span data-stu-id="1a3a9-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](http://go.microsoft.com/fwlink/?LinkId=94950).</span></span> <span data-ttu-id="1a3a9-105">W przypadku innych Schematy adresów URL Svcutil.exe używa tylko WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="1a3a9-106">Domyślnie korzysta z powiązań zdefiniowanych w Svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="1a3a9-107">Aby skonfigurować powiązanie użyte dla protokołu WS-MetadataExchange, należy zdefiniować punkt końcowy klienta w pliku konfiguracji dla Svcutil.exe (svcutil.exe.config) używa `IMetadataExchange` kontraktu i który ma taką samą nazwę jak jednolity identyfikator zasobów (URI) Schemat adres punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1a3a9-108">Gdy uruchomiony Svcutil.exe można pobrać metadanych dla usługi, która udostępnia dwa różne usługi umów, że każdy zawierać operacji o tej samej nazwie, Svcutil.exe jest wyświetlany błąd informujący o tym, "Nie można uzyskać metadanych z..." Na przykład jeśli masz usługę, która uwidacznia kontraktu usługi o nazwie ICarService zawierający operacji Get (samochód c) i tej samej usługi udostępnia kontraktu usługi o nazwie IBookService zawierający operacji Get (książka b).</span><span class="sxs-lookup"><span data-stu-id="1a3a9-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called ICarService that has an operation Get(Car c) and the same service exposes a service contract called IBookService that has an operation Get(Book b).</span></span> <span data-ttu-id="1a3a9-109">Aby obejść ten problem, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1a3a9-109">To work around this issue, do one of the following:</span></span>  
>   
>  -   <span data-ttu-id="1a3a9-110">Zmień nazwę jednej z operacji</span><span class="sxs-lookup"><span data-stu-id="1a3a9-110">Rename one of the operations</span></span>  
> -   <span data-ttu-id="1a3a9-111">Ustaw <xref:System.ServiceModel.OperationContractAttribute.Name%2A> pod inną nazwą.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>  
> -   <span data-ttu-id="1a3a9-112">Wartość jednej z operacji w przestrzeni nazw przy użyciu różnych nazw <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
### <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="1a3a9-113">Do pobierania metadanych za pomocą Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="1a3a9-113">To download metadata using Svcutil.exe</span></span>  
  
1.  <span data-ttu-id="1a3a9-114">Zlokalizuj narzędzia Svcutil.exe w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="1a3a9-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="1a3a9-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="1a3a9-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2.  <span data-ttu-id="1a3a9-116">W wierszu polecenia Uruchom narzędzie w następującym formacie.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="1a3a9-117">Należy określić `/t:metadata` opcję, aby pobrać metadanych.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="1a3a9-118">W przeciwnym razie wygenerowany kod klienta i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-118">Otherwise, client code and configuration are generated.</span></span>  
  
3.  <span data-ttu-id="1a3a9-119"><`url`> Argument określa adres URL punktu końcowego usługi, która udostępnia metadane lub dokument metadanych, hostowana w trybie online.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="1a3a9-120"><`epr`> Argument określa ścieżkę do pliku XML, który zawiera WS-Addressing `EndpointAddress` punktu końcowego usługi, która obsługuje WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="1a3a9-121">Aby wyświetlić więcej opcji dotyczących dla pobierania metadanych za pomocą tego narzędzia, zobacz [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1a3a9-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a3a9-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a3a9-122">Example</span></span>  
 <span data-ttu-id="1a3a9-123">Polecenie pobiera dokumentów metadanych z uruchomioną usługę.</span><span class="sxs-lookup"><span data-stu-id="1a3a9-123">The following command downloads metadata documents from a running service.</span></span>  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a3a9-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a3a9-124">See Also</span></span>  
 [<span data-ttu-id="1a3a9-125">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="1a3a9-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
