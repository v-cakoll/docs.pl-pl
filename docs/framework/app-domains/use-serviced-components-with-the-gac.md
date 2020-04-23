---
title: Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
ms.openlocfilehash: 99627cb14088f037c58bfa1eec72bd4f88d06011
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119768"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="8a6b6-102">Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="8a6b6-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="8a6b6-103">Składniki obsługiwane (zarządzane kod modelu COM+) należy umieścić w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="8a6b6-103">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="8a6b6-104">W niektórych scenariuszach środowisko uruchomieniowe języka wspólnego i usługi modelu COM+ mogą obsługiwać składniki obsługiwane przez program, które nie znajdują się w globalnej pamięci podręcznej zestawów; w innych scenariuszach nie mogą.</span><span class="sxs-lookup"><span data-stu-id="8a6b6-104">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="8a6b6-105">Poniższe scenariusze ilustrują:</span><span class="sxs-lookup"><span data-stu-id="8a6b6-105">The following scenarios illustrate this:</span></span>  
  
- <span data-ttu-id="8a6b6-106">W przypadku składników usługi w aplikacji serwera COM+ zestaw zawierający składniki musi znajdować się w globalnej pamięci podręcznej zestawów, ponieważ program dllhost. exe nie działa w tym samym katalogu, w którym znajdują się składniki obsługiwane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="8a6b6-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
- <span data-ttu-id="8a6b6-107">W przypadku składników usługi w aplikacji biblioteki modelu COM+ środowisko uruchomieniowe i usługi COM+ mogą rozpoznać odwołanie do zestawu zawierającego składniki, wyszukując w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8a6b6-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="8a6b6-108">W takim przypadku zestaw nie musi znajdować się w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="8a6b6-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
- <span data-ttu-id="8a6b6-109">W przypadku składników usługi w aplikacji ASP.NET sytuacja jest inna.</span><span class="sxs-lookup"><span data-stu-id="8a6b6-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="8a6b6-110">Jeśli umieścisz zestaw zawierający składniki usługi w katalogu bin bazy aplikacji i użyjesz rejestracji na żądanie, zestaw będzie kopiowany w tle do pamięci podręcznej pobierania, ponieważ ASP.NET wykorzystuje możliwości w tle środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8a6b6-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a6b6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a6b6-111">See also</span></span>

- [<span data-ttu-id="8a6b6-112">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="8a6b6-112">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="8a6b6-113">Gacutil. exe (Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="8a6b6-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
