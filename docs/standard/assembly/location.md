---
title: Lokalizacja zestawu
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6427f7d005c43ef9e83387e865f71009b683a7c4
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973181"
---
# <a name="assembly-location"></a><span data-ttu-id="ecb4a-102">Lokalizacja zestawu</span><span class="sxs-lookup"><span data-stu-id="ecb4a-102">Assembly location</span></span>
<span data-ttu-id="ecb4a-103">Lokalizacja zestawu określa, czy środowisko uruchomieniowe języka wspólnego może je zlokalizować w przypadku odwołania, a także określić, czy zestaw może być współużytkowany z innymi zestawami.</span><span class="sxs-lookup"><span data-stu-id="ecb4a-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="ecb4a-104">Zestaw można wdrożyć w następujących lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="ecb4a-104">You can deploy an assembly in the following locations:</span></span>  
  
- <span data-ttu-id="ecb4a-105">Katalog lub podkatalogi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ecb4a-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="ecb4a-106">Jest to najczęściej używane miejsce wdrożenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="ecb4a-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="ecb4a-107">Podkatalogi katalogu głównego aplikacji mogą opierać się na języku lub kulturze.</span><span class="sxs-lookup"><span data-stu-id="ecb4a-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="ecb4a-108">Jeśli zestaw zawiera informacje w atrybucie Culture, musi znajdować się w podkatalogu w katalogu aplikacji z nazwą tej kultury.</span><span class="sxs-lookup"><span data-stu-id="ecb4a-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
- <span data-ttu-id="ecb4a-109">Globalna pamięć podręczna zestawów.</span><span class="sxs-lookup"><span data-stu-id="ecb4a-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="ecb4a-110">Jest to pamięć podręczna kodu całego komputera zainstalowana wszędzie tam, gdzie jest zainstalowany aparat plików wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="ecb4a-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="ecb4a-111">W większości przypadków, jeśli zamierzasz udostępnić zestaw z wieloma aplikacjami, należy wdrożyć go w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="ecb4a-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
- <span data-ttu-id="ecb4a-112">Na serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="ecb4a-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="ecb4a-113">Zestaw wdrożony na serwerze HTTP musi mieć silną nazwę; Wskaż zestaw w sekcji codebase w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ecb4a-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb4a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecb4a-114">See also</span></span>

- [<span data-ttu-id="ecb4a-115">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="ecb4a-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="ecb4a-116">Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="ecb4a-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="ecb4a-117">Jak środowisko uruchomieniowe lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="ecb4a-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ecb4a-118">Program z zestawami</span><span class="sxs-lookup"><span data-stu-id="ecb4a-118">Program with assemblies</span></span>](program.md)
