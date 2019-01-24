---
title: Lokalizacja zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0b065fe488031329815f6ec38da9661fd19700d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529937"
---
# <a name="assembly-location"></a><span data-ttu-id="0e902-102">Lokalizacja zestawu</span><span class="sxs-lookup"><span data-stu-id="0e902-102">Assembly Location</span></span>
<span data-ttu-id="0e902-103">Lokalizacja zestawu Określa, czy można wyszukanie w przypadku odwołania do środowiska uruchomieniowego języka wspólnego i można również określić, czy zestaw mogą być współużytkowane z innymi zestawami.</span><span class="sxs-lookup"><span data-stu-id="0e902-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="0e902-104">Można wdrożyć zestaw w następujących lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="0e902-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="0e902-105">Katalog aplikacji lub podkatalogi.</span><span class="sxs-lookup"><span data-stu-id="0e902-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="0e902-106">Jest to najbardziej typowe lokalizacja do wdrażania zestawu.</span><span class="sxs-lookup"><span data-stu-id="0e902-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="0e902-107">Podkatalogi katalogu głównego aplikacji może bazować na języka lub kultury.</span><span class="sxs-lookup"><span data-stu-id="0e902-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="0e902-108">Jeśli zestaw ma informacje w atrybucie kultury, należy w podkatalogu w katalogu aplikacji o nazwie tej kultury.</span><span class="sxs-lookup"><span data-stu-id="0e902-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="0e902-109">Global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="0e902-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="0e902-110">Jest to pamięć podręczna kodu dla całego komputera, zainstalowanym wszędzie tam, gdzie zainstalowano środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="0e902-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="0e902-111">W większości przypadków Jeśli zamierzasz dzielenie się zestawem z wielu aplikacji, należy wdrożyć ją w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0e902-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="0e902-112">Na serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="0e902-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="0e902-113">Zestaw wdrożonych na serwerze HTTP musi mieć silną nazwą; wskaż zestawu w części bazy kodu w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0e902-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e902-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e902-114">See also</span></span>
- [<span data-ttu-id="0e902-115">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="0e902-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="0e902-116">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="0e902-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="0e902-117">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0e902-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="0e902-118">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="0e902-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
