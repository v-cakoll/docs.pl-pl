---
title: 'Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych'
description: Dowiedz się, jak używać Svcutil.exe do pobierania metadanych z uruchomionych usług i zapisywania metadanych w plikach lokalnych.
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 42df55fe7bbae6d8c977263e05053d8a8fa87aff
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246769"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="ef513-103">Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych</span><span class="sxs-lookup"><span data-stu-id="ef513-103">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="ef513-104">Za pomocą Svcutil.exe można pobrać metadane z uruchomionych usług i zapisać metadane w plikach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="ef513-104">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="ef513-105">W przypadku schematów adresów URL protokołu HTTP i HTTPS Svcutil.exe próbuje pobrać metadane przy użyciu protokołu WS-MetadataExchange i [odnajdywania usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ef513-105">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="ef513-106">W przypadku wszystkich innych schematów adresów URL Svcutil.exe używa tylko protokołu WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="ef513-106">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="ef513-107">Domyślnie Svcutil.exe używa powiązań zdefiniowanych w <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasie.</span><span class="sxs-lookup"><span data-stu-id="ef513-107">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="ef513-108">Aby skonfigurować powiązanie używane dla protokołu WS-MetadataExchange, należy zdefiniować punkt końcowy klienta w pliku konfiguracyjnym dla Svcutil.exe (svcutil.exe.config), który używa `IMetadataExchange` kontraktu i ma taką samą nazwę jak schemat Uniform Resource Identifier (URI) adresu punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="ef513-108">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="ef513-109">Podczas uruchamiania Svcutil.exe, aby uzyskać metadane dla usługi, która ujawnia dwie różne kontrakty usługi, które zawierają operację o tej samej nazwie, Svcutil.exe wyświetla błąd mówiący "nie można uzyskać metadanych z..." Na przykład jeśli masz usługę, która ujawnia kontrakt usługi o nazwie `ICarService` , który ma operację, `Get(Car c)` a ta sama usługa ujawnia kontrakt usługi o nazwie `IBookService` , który ma operację `Get(Book b)` .</span><span class="sxs-lookup"><span data-stu-id="ef513-109">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="ef513-110">Aby obejść ten problem, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ef513-110">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="ef513-111">Zmień nazwę jednej z operacji.</span><span class="sxs-lookup"><span data-stu-id="ef513-111">Rename one of the operations.</span></span>
> - <span data-ttu-id="ef513-112">Ustaw <xref:System.ServiceModel.OperationContractAttribute.Name%2A> inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="ef513-112">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="ef513-113">Ustaw jedną z przestrzeni nazw operacji na inną przestrzeń nazw przy użyciu <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ef513-113">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="ef513-114">Aby pobrać metadane przy użyciu Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="ef513-114">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="ef513-115">Znajdź narzędzie Svcutil.exe w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="ef513-115">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="ef513-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="ef513-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="ef513-117">W wierszu polecenia Uruchom narzędzie przy użyciu następującego formatu.</span><span class="sxs-lookup"><span data-stu-id="ef513-117">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="ef513-118">Należy określić `/t:metadata` opcję pobierania metadanych.</span><span class="sxs-lookup"><span data-stu-id="ef513-118">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="ef513-119">W przeciwnym razie jest generowany kod i konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="ef513-119">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="ef513-120"><`url` argument>określa adres URL punktu końcowego usługi, który udostępnia metadane lub dokument metadanych hostowany w trybie online.</span><span class="sxs-lookup"><span data-stu-id="ef513-120">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="ef513-121"><`epr` argument> określa ścieżkę do pliku XML, który zawiera WS-Addressing `EndpointAddress` dla punktu końcowego usługi, który obsługuje protokół WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="ef513-121">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="ef513-122">Aby uzyskać więcej opcji dotyczących używania tego narzędzia do pobierania metadanych, zobacz [Narzędzie narzędzia metadanych ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ef513-122">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef513-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef513-123">Example</span></span>  
 <span data-ttu-id="ef513-124">Następujące polecenie pobiera dokumenty metadanych z uruchomionej usługi.</span><span class="sxs-lookup"><span data-stu-id="ef513-124">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef513-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef513-125">See also</span></span>

- [<span data-ttu-id="ef513-126">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="ef513-126">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
