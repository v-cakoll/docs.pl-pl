---
title: 'Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 6643f0a5dba98afcef38870cf24d91e7d69a1440
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481861"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="8ef03-102">Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych</span><span class="sxs-lookup"><span data-stu-id="8ef03-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="8ef03-103">Umożliwia Svcutil.exe do pobierania metadanych z uruchomionymi usługami i zapisać metadane do plików lokalnych.</span><span class="sxs-lookup"><span data-stu-id="8ef03-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="8ef03-104">HTTP i HTTPS URL schematów, Svcutil.exe podejmie próbę pobrania metadanych przy użyciu usługi WS-MetadataExchange i [odnajdywania usług sieci Web XML](https://go.microsoft.com/fwlink/?LinkId=94950).</span><span class="sxs-lookup"><span data-stu-id="8ef03-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://go.microsoft.com/fwlink/?LinkId=94950).</span></span> <span data-ttu-id="8ef03-105">Dla innych schematów adresów URL Svcutil.exe używa tylko protokołu WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="8ef03-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="8ef03-106">Domyślnie korzysta z powiązań zdefiniowanych w Svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy.</span><span class="sxs-lookup"><span data-stu-id="8ef03-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="8ef03-107">Aby skonfigurować powiązania, używany dla protokołu WS-MetadataExchange, należy zdefiniować punkt końcowy klienta w pliku konfiguracji dla Svcutil.exe (svcutil.exe.config) używa `IMetadataExchange` kontraktu i który ma taką samą nazwę jak jednolity identyfikator zasobów (URI) Schemat adresu punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="8ef03-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="8ef03-108">Podczas uruchamiania Svcutil.exe można pobrać metadanych dotyczących usługi, który udostępnia dwa różne usług kontraktów, każdy z nich zawiera operację o takiej samej nazwie, Svcutil.exe wyświetla komunikat o błędzie informujący o tym, "Nie można uzyskać metadanych z..." Na przykład, jeśli masz usługę, która udostępnia kontraktu usługi o nazwie `ICarService` zawierający operacją `Get(Car c)` i tej samej usłudze udostępnia kontraktu usługi o nazwie `IBookService` zawierający operacją `Get(Book b)`.</span><span class="sxs-lookup"><span data-stu-id="8ef03-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="8ef03-109">Aby obejść ten problem, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8ef03-109">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="8ef03-110">Zmień nazwę jednej z operacji.</span><span class="sxs-lookup"><span data-stu-id="8ef03-110">Rename one of the operations.</span></span>
> - <span data-ttu-id="8ef03-111">Ustaw <xref:System.ServiceModel.OperationContractAttribute.Name%2A> na inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="8ef03-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="8ef03-112">Wartość jednej z operacji w przestrzeni nazw za pomocą różnych nazw <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ef03-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="8ef03-113">Aby pobrać metadane przy użyciu Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="8ef03-113">To download metadata using Svcutil.exe</span></span>  
  
1.  <span data-ttu-id="8ef03-114">Znajdź narzędzia Svcutil.exe w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="8ef03-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="8ef03-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="8ef03-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2.  <span data-ttu-id="8ef03-116">W wierszu polecenia Uruchom narzędzie przy użyciu następującego formatu.</span><span class="sxs-lookup"><span data-stu-id="8ef03-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="8ef03-117">Należy określić `/t:metadata` umożliwiający pobranie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8ef03-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="8ef03-118">W przeciwnym razie wygenerowany kod klienta i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ef03-118">Otherwise, client code and configuration are generated.</span></span>  
  
3.  <span data-ttu-id="8ef03-119"><`url`> Argument określa adres URL punktu końcowego usługi, który udostępnia metadane lub dokumentu z metadanymi hostowanego w trybie online.</span><span class="sxs-lookup"><span data-stu-id="8ef03-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="8ef03-120"><`epr`> Argument określa ścieżkę do pliku XML, który zawiera WS-Addressing `EndpointAddress` dla punktu końcowego usługi, która obsługuje WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="8ef03-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="8ef03-121">Aby uzyskać więcej opcji dotyczących używania tego narzędzia do pobierania metadanych, zobacz [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8ef03-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ef03-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ef03-122">Example</span></span>  
 <span data-ttu-id="8ef03-123">Następujące polecenie pobiera dokumentów metadanych z uruchomioną usługę.</span><span class="sxs-lookup"><span data-stu-id="8ef03-123">The following command downloads metadata documents from a running service.</span></span>  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ef03-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ef03-124">See Also</span></span>  
 [<span data-ttu-id="8ef03-125">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="8ef03-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
