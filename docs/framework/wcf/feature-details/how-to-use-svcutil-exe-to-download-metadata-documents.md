---
title: 'Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 359cdb58ef65c9fb69c0ecfc759f70164a369cce
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212112"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="cc7a0-102">Instrukcje: Używanie programu Svcutil.exe do pobierania dokumentów metadanych</span><span class="sxs-lookup"><span data-stu-id="cc7a0-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="cc7a0-103">Programu Svcutil. exe można użyć do pobierania metadanych z uruchomionych usług i zapisywania metadanych w plikach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="cc7a0-104">W przypadku schematów adresów URL protokołu HTTP i HTTPS Svcutil. exe próbuje pobrać metadane za pomocą usługi WS-MetadataExchange i [odnajdowania usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cc7a0-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="cc7a0-105">W przypadku wszystkich innych schematów adresów URL Svcutil. exe używa tylko protokołu WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="cc7a0-106">Domyślnie Svcutil. exe używa powiązań zdefiniowanych w klasie <xref:System.ServiceModel.Description.MetadataExchangeBindings>.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="cc7a0-107">Aby skonfigurować powiązanie używane dla protokołu WS-MetadataExchange, należy zdefiniować punkt końcowy klienta w pliku konfiguracyjnym programu Svcutil. exe (Svcutil. exe. config), który używa kontraktu `IMetadataExchange` i który ma taką samą nazwę jak schemat Uniform Resource Identifier (URI) adresu punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="cc7a0-108">Podczas uruchamiania programu Svcutil. exe w celu uzyskania metadanych dla usługi, która ujawnia dwie różne kontrakty usługi, które zawierają operacje o tej samej nazwie, Svcutil. exe wyświetla błąd mówiący "nie można uzyskać metadanych z..." Na przykład jeśli masz usługę, która ujawnia kontrakt usługi o nazwie `ICarService`, która ma `Get(Car c)` operacji, a ta sama usługa ujawnia kontrakt usługi o nazwie `IBookService`, która ma `Get(Book b)`operacji.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="cc7a0-109">Aby obejść ten problem, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="cc7a0-109">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="cc7a0-110">Zmień nazwę jednej z operacji.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-110">Rename one of the operations.</span></span>
> - <span data-ttu-id="cc7a0-111">Ustaw <xref:System.ServiceModel.OperationContractAttribute.Name%2A> na inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="cc7a0-112">Ustaw jedną z przestrzeni nazw operacji na inną przestrzeń nazw przy użyciu właściwości <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="cc7a0-113">Aby pobrać metadane przy użyciu programu Svcutil. exe</span><span class="sxs-lookup"><span data-stu-id="cc7a0-113">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="cc7a0-114">Znajdź narzędzie Svcutil. exe w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="cc7a0-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="cc7a0-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="cc7a0-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="cc7a0-116">W wierszu polecenia Uruchom narzędzie przy użyciu następującego formatu.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="cc7a0-117">Należy określić opcję `/t:metadata`, aby pobrać metadane.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="cc7a0-118">W przeciwnym razie jest generowany kod i konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-118">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="cc7a0-119"><`url`> argument określa adres URL punktu końcowego usługi, który udostępnia metadane lub dokument metadanych hostowany w trybie online.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="cc7a0-120">`epr`> argument określa ścieżkę do pliku XML, który zawiera `EndpointAddress` adresu WS-Addressing dla punktu końcowego usługi, który obsługuje protokół WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="cc7a0-121">Aby uzyskać więcej opcji dotyczących używania tego narzędzia do pobierania metadanych, zobacz [Narzędzie do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cc7a0-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc7a0-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc7a0-122">Example</span></span>  
 <span data-ttu-id="cc7a0-123">Następujące polecenie pobiera dokumenty metadanych z uruchomionej usługi.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-123">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc7a0-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc7a0-124">See also</span></span>

- [<span data-ttu-id="cc7a0-125">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="cc7a0-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
