---
title: 'Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: c04b63fa4963a5df0f910da8702643a6484a4edd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596932"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="8b76e-102">Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych</span><span class="sxs-lookup"><span data-stu-id="8b76e-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="8b76e-103">Programu Svcutil. exe można użyć do pobierania metadanych z uruchomionych usług i zapisywania metadanych w plikach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="8b76e-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="8b76e-104">W przypadku schematów adresów URL protokołu HTTP i HTTPS Svcutil. exe próbuje pobrać metadane za pomocą usługi WS-MetadataExchange i [odnajdowania usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8b76e-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="8b76e-105">W przypadku wszystkich innych schematów adresów URL Svcutil. exe używa tylko protokołu WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="8b76e-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="8b76e-106">Domyślnie Svcutil. exe używa powiązań zdefiniowanych w <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasie.</span><span class="sxs-lookup"><span data-stu-id="8b76e-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="8b76e-107">Aby skonfigurować powiązanie używane dla protokołu WS-MetadataExchange, należy zdefiniować punkt końcowy klienta w pliku konfiguracyjnym programu Svcutil. exe (Svcutil. exe. config), który używa `IMetadataExchange` kontraktu i ma taką samą nazwę jak schemat Uniform Resource Identifier (URI) adresu punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="8b76e-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="8b76e-108">Podczas uruchamiania programu Svcutil. exe w celu uzyskania metadanych dla usługi, która ujawnia dwie różne kontrakty usługi, które zawierają operacje o tej samej nazwie, Svcutil. exe wyświetla błąd mówiący "nie można uzyskać metadanych z..." Na przykład jeśli masz usługę, która ujawnia kontrakt usługi o nazwie `ICarService` , który ma operację, `Get(Car c)` a ta sama usługa ujawnia kontrakt usługi o nazwie `IBookService` , który ma operację `Get(Book b)` .</span><span class="sxs-lookup"><span data-stu-id="8b76e-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="8b76e-109">Aby obejść ten problem, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8b76e-109">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="8b76e-110">Zmień nazwę jednej z operacji.</span><span class="sxs-lookup"><span data-stu-id="8b76e-110">Rename one of the operations.</span></span>
> - <span data-ttu-id="8b76e-111">Ustaw <xref:System.ServiceModel.OperationContractAttribute.Name%2A> inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="8b76e-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="8b76e-112">Ustaw jedną z przestrzeni nazw operacji na inną przestrzeń nazw przy użyciu <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8b76e-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="8b76e-113">Aby pobrać metadane przy użyciu programu Svcutil. exe</span><span class="sxs-lookup"><span data-stu-id="8b76e-113">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="8b76e-114">Znajdź narzędzie Svcutil. exe w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="8b76e-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="8b76e-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="8b76e-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="8b76e-116">W wierszu polecenia Uruchom narzędzie przy użyciu następującego formatu.</span><span class="sxs-lookup"><span data-stu-id="8b76e-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="8b76e-117">Należy określić `/t:metadata` opcję pobierania metadanych.</span><span class="sxs-lookup"><span data-stu-id="8b76e-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="8b76e-118">W przeciwnym razie jest generowany kod i konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="8b76e-118">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="8b76e-119"><`url` argument>określa adres URL punktu końcowego usługi, który udostępnia metadane lub dokument metadanych hostowany w trybie online.</span><span class="sxs-lookup"><span data-stu-id="8b76e-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="8b76e-120"><`epr` argument> określa ścieżkę do pliku XML, który zawiera WS-Addressing `EndpointAddress` dla punktu końcowego usługi, który obsługuje protokół WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="8b76e-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="8b76e-121">Aby uzyskać więcej opcji dotyczących używania tego narzędzia do pobierania metadanych, zobacz [Narzędzie do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8b76e-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b76e-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="8b76e-122">Example</span></span>  
 <span data-ttu-id="8b76e-123">Następujące polecenie pobiera dokumenty metadanych z uruchomionej usługi.</span><span class="sxs-lookup"><span data-stu-id="8b76e-123">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b76e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b76e-124">See also</span></span>

- [<span data-ttu-id="8b76e-125">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="8b76e-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
