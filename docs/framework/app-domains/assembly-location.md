---
title: Lokalizacja zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91fc7cf6ea66952fa5770ce73ecb1a8c129a9a2d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743917"
---
# <a name="assembly-location"></a><span data-ttu-id="737d4-102">Lokalizacja zestawu</span><span class="sxs-lookup"><span data-stu-id="737d4-102">Assembly Location</span></span>
<span data-ttu-id="737d4-103">Lokalizacji zestawu Określa, czy można zlokalizować gdy odwołuje się do środowisko uruchomieniowe języka wspólnego i można również określić, czy zestaw może być współużytkowana z innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="737d4-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="737d4-104">Można wdrożyć zestawu w następujących lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="737d4-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="737d4-105">Katalog aplikacji lub jego podkatalogach.</span><span class="sxs-lookup"><span data-stu-id="737d4-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="737d4-106">Jest to lokalizacja najczęściej używane do wdrażania zestawu.</span><span class="sxs-lookup"><span data-stu-id="737d4-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="737d4-107">Podkatalogi katalogu głównego aplikacji może być oparta na języka i kultury.</span><span class="sxs-lookup"><span data-stu-id="737d4-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="737d4-108">Jeśli zestaw informacji w atrybucie kultury, musi być w podkatalogu w katalogu aplikacji o nazwie tej kultury.</span><span class="sxs-lookup"><span data-stu-id="737d4-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="737d4-109">Globalna pamięć podręczna zestawów.</span><span class="sxs-lookup"><span data-stu-id="737d4-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="737d4-110">To jest kod komputera pamięci podręcznej, zainstalowanym wszędzie tam, gdzie jest zainstalowane środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="737d4-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="737d4-111">W większości przypadków Jeśli zamierzasz dzielenie się zestawem z wielu aplikacji, należy wdrożyć ją w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="737d4-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="737d4-112">Na serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="737d4-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="737d4-113">Zestaw wdrożonych na serwerze HTTP musi mieć silnej nazwy; wskaż zestawu w sekcji codebase pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="737d4-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="737d4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="737d4-114">See Also</span></span>  
 [<span data-ttu-id="737d4-115">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="737d4-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="737d4-116">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="737d4-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="737d4-117">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="737d4-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="737d4-118">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="737d4-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
