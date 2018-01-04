---
title: Lokalizacja zestawu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96b3105dcd1eaf6d95269d05518e6892b42a638f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-location"></a><span data-ttu-id="aa996-102">Lokalizacja zestawu</span><span class="sxs-lookup"><span data-stu-id="aa996-102">Assembly Location</span></span>
<span data-ttu-id="aa996-103">Lokalizacji zestawu Określa, czy można zlokalizować gdy odwołuje się do środowisko uruchomieniowe języka wspólnego i można również określić, czy zestaw może być współużytkowana z innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="aa996-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="aa996-104">Można wdrożyć zestawu w następujących lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="aa996-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="aa996-105">Katalog aplikacji lub jego podkatalogach.</span><span class="sxs-lookup"><span data-stu-id="aa996-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="aa996-106">Jest to lokalizacja najczęściej używane do wdrażania zestawu.</span><span class="sxs-lookup"><span data-stu-id="aa996-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="aa996-107">Podkatalogi katalogu głównego aplikacji może być oparta na języka i kultury.</span><span class="sxs-lookup"><span data-stu-id="aa996-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="aa996-108">Jeśli zestaw informacji w atrybucie kultury, musi być w podkatalogu w katalogu aplikacji o nazwie tej kultury.</span><span class="sxs-lookup"><span data-stu-id="aa996-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="aa996-109">Globalna pamięć podręczna zestawów.</span><span class="sxs-lookup"><span data-stu-id="aa996-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="aa996-110">To jest kod komputera pamięci podręcznej, zainstalowanym wszędzie tam, gdzie jest zainstalowane środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="aa996-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="aa996-111">W większości przypadków Jeśli zamierzasz dzielenie się zestawem z wielu aplikacji, należy wdrożyć ją w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="aa996-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="aa996-112">Na serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="aa996-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="aa996-113">Zestaw wdrożonych na serwerze HTTP musi mieć silnej nazwy; wskaż zestawu w sekcji codebase pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa996-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa996-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa996-114">See Also</span></span>  
 [<span data-ttu-id="aa996-115">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="aa996-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="aa996-116">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="aa996-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="aa996-117">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="aa996-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="aa996-118">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="aa996-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
