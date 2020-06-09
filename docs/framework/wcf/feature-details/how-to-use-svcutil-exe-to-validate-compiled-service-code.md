---
title: 'Instrukcje: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 6f2064c696e3186c3208a7e57dc51655056d23ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595352"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="8d150-102">Instrukcje: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="8d150-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>
<span data-ttu-id="8d150-103">Za pomocą narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) można wykrywać błędy w implementacjach i konfiguracjach usług bez konieczności obsługiwania usługi.</span><span class="sxs-lookup"><span data-stu-id="8d150-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="8d150-104">Aby sprawdzić poprawność usługi</span><span class="sxs-lookup"><span data-stu-id="8d150-104">To validate a service</span></span>  
  
1. <span data-ttu-id="8d150-105">Skompiluj usługę do pliku wykonywalnego i jednego lub więcej zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="8d150-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2. <span data-ttu-id="8d150-106">Otwórz wiersz polecenia zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="8d150-106">Open an SDK command prompt</span></span>  
  
3. <span data-ttu-id="8d150-107">W wierszu polecenia Uruchom narzędzie Svcutil. exe, używając następującego formatu.</span><span class="sxs-lookup"><span data-stu-id="8d150-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="8d150-108">Aby uzyskać więcej informacji na temat różnych parametrów, zobacz Validationsection usługi w temacie [Narzędzie metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="8d150-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```console
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="8d150-109">Musisz użyć opcji, `/serviceName` Aby wskazać nazwę konfiguracji usługi, którą chcesz zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="8d150-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="8d150-110">`assemblyPath`Argument określa ścieżkę do pliku wykonywalnego usługi i co najmniej jeden zestaw zawierający typy usługi do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="8d150-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="8d150-111">Zestaw wykonywalny musi mieć skojarzony plik konfiguracji, aby zapewnić konfigurację usługi.</span><span class="sxs-lookup"><span data-stu-id="8d150-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="8d150-112">Możesz użyć standardowych symboli wieloznacznych wiersza polecenia, aby udostępnić wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="8d150-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d150-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d150-113">Example</span></span>  
 <span data-ttu-id="8d150-114">Następujące polecenie jest zaimplementowane w pliku wykonywalnym myServiceHost. exe.</span><span class="sxs-lookup"><span data-stu-id="8d150-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="8d150-115">Plik konfiguracji usługi (myServiceHost. exe. config) jest ładowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="8d150-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```console  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d150-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d150-116">See also</span></span>

- [<span data-ttu-id="8d150-117">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="8d150-117">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
