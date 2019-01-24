---
title: Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d42fa296585d26186a2e75a49c5b3cf761e846
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583249"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="65fb9-102">Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="65fb9-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="65fb9-103">Obsługiwane składniki (kodu zarządzanego modelu COM +) należy umieszczać w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="65fb9-103">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="65fb9-104">W niektórych scenariuszach środowisko uruchomieniowe języka wspólnego i usług COM + mogą obsługiwać obsługiwanych składników, które nie znajdują się w globalnej pamięci podręcznej zestawów; w innych sytuacjach nie jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="65fb9-104">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="65fb9-105">Następujące scenariusze przedstawiają to:</span><span class="sxs-lookup"><span data-stu-id="65fb9-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="65fb9-106">Dla obsługiwanych składników w aplikacji serwera COM + zestaw zawierający składniki musi być w globalnej pamięci podręcznej zestawów, ponieważ Dllhost.exe nie działa w tym samym katalogu, która zawiera obsługiwanych składników.</span><span class="sxs-lookup"><span data-stu-id="65fb9-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="65fb9-107">Dla obsługiwanych składników w aplikacji modelu COM + biblioteki środowiska uruchomieniowego i usług COM +, można rozwiązać odwołania do zestawu zawierającego składniki, wyszukując w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="65fb9-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="65fb9-108">W tym przypadku zestaw nie ma znajdować się w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="65fb9-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="65fb9-109">Dla obsługiwanych składników w aplikacji ASP.NET ta sytuacja jest różne.</span><span class="sxs-lookup"><span data-stu-id="65fb9-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="65fb9-110">Jeśli umieścić zestaw zawierający obsługiwanych składników w katalogu bin aplikacji i użyć rejestracji na żądanie, zestaw będą kopiowane w tle w pamięci podręcznej pobierania ponieważ ASP.NET wykorzystuje możliwości w tle środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="65fb9-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65fb9-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65fb9-111">See also</span></span>
- [<span data-ttu-id="65fb9-112">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="65fb9-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="65fb9-113">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="65fb9-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
