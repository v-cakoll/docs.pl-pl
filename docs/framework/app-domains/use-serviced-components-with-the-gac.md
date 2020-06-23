---
title: Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów
description: Korzystaj z serwisowanych składników (składników kodu modelu COM+) z globalną pamięcią podręczną zestawów w programie .NET. Sprawdź, czy usługi CLR i COM+ mogą obsługiwać składniki nie korzystające z pamięci podręcznej.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
ms.openlocfilehash: 6b7371865b7b1cedda0ee03b2cc28c74b5c3da0b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104477"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="7d9a1-104">Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="7d9a1-104">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="7d9a1-105">Składniki obsługiwane (zarządzane kod modelu COM+) należy umieścić w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-105">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="7d9a1-106">W niektórych scenariuszach środowisko uruchomieniowe języka wspólnego i usługi modelu COM+ mogą obsługiwać składniki obsługiwane przez program, które nie znajdują się w globalnej pamięci podręcznej zestawów; w innych scenariuszach nie mogą.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-106">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="7d9a1-107">Poniższe scenariusze ilustrują:</span><span class="sxs-lookup"><span data-stu-id="7d9a1-107">The following scenarios illustrate this:</span></span>  
  
- <span data-ttu-id="7d9a1-108">W przypadku składników usługi w aplikacji serwera COM+ zestaw zawierający składniki musi znajdować się w globalnej pamięci podręcznej zestawów, ponieważ Dllhost.exe nie działa w tym samym katalogu, w którym znajdują się składniki obsługiwane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-108">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
- <span data-ttu-id="7d9a1-109">W przypadku składników usługi w aplikacji biblioteki modelu COM+ środowisko uruchomieniowe i usługi COM+ mogą rozpoznać odwołanie do zestawu zawierającego składniki, wyszukując w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-109">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="7d9a1-110">W takim przypadku zestaw nie musi znajdować się w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-110">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
- <span data-ttu-id="7d9a1-111">W przypadku składników usługi w aplikacji ASP.NET sytuacja jest inna.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-111">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="7d9a1-112">Jeśli umieścisz zestaw zawierający składniki usługi w katalogu bin bazy aplikacji i użyjesz rejestracji na żądanie, zestaw będzie kopiowany w tle do pamięci podręcznej pobierania, ponieważ ASP.NET wykorzystuje możliwości w tle środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-112">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d9a1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d9a1-113">See also</span></span>

- [<span data-ttu-id="7d9a1-114">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="7d9a1-114">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="7d9a1-115">Gacutil.exe (Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="7d9a1-115">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
