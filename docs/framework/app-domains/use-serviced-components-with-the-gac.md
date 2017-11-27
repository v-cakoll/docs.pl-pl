---
title: "Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45fd02c4f87d33766741e6fd023f9b40b9964d63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="ba5e9-102">Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="ba5e9-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="ba5e9-103">Obsługiwane składniki (zarządzany kod modelu COM +) należy umieścić w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="ba5e9-103">Serviced components (managed code COM+ components) should be put in the global assembly cache.</span></span> <span data-ttu-id="ba5e9-104">W niektórych scenariuszach środowisko uruchomieniowe języka wspólnego i usług COM + mogą obsługiwać obsługiwanych składników, które nie znajdują się w globalnej pamięci podręcznej zestawów; w innych sytuacjach nie jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ba5e9-104">In some scenarios, the common language runtime and COM+ Services can handle serviced components that are not in the global assembly cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="ba5e9-105">Poniższe scenariusze ilustrują to:</span><span class="sxs-lookup"><span data-stu-id="ba5e9-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="ba5e9-106">Dla obsługiwanych składników w aplikacji COM + serwera zestaw zawierający składniki musi być w globalnej pamięci podręcznej zestawów, ponieważ Dllhost.exe nie działa w tym samym katalogu co, która zawiera serwisowanych składników.</span><span class="sxs-lookup"><span data-stu-id="ba5e9-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the global assembly cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="ba5e9-107">Dla obsługiwanych składników w aplikacji COM + biblioteki środowiska uruchomieniowego i usług COM + mogą rozpoznać odwołania do zestawu zawierającego składników przez wyszukiwanie w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ba5e9-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="ba5e9-108">W takim przypadku zestaw nie ma w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="ba5e9-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="ba5e9-109">Obsługiwane składniki w aplikacji ASP.NET sytuacji różni się.</span><span class="sxs-lookup"><span data-stu-id="ba5e9-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="ba5e9-110">Umieść zestaw zawierający obsługiwanych składników w katalogu bin baza aplikacji, użyj rejestracji na żądanie zestawu będzie można skopiować cienia w pamięci podręcznej pobierania, ponieważ ASP.NET wykorzystuje funkcje tle środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ba5e9-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5e9-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba5e9-111">See Also</span></span>  
 [<span data-ttu-id="ba5e9-112">Praca z zestawami i Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="ba5e9-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="ba5e9-113">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="ba5e9-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
