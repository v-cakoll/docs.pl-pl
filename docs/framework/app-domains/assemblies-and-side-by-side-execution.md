---
title: Zestawy i wykonywanie równoczesne
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 605cb6dfd3232d90d6c278f9563ac8d9f101b053
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="a2421-102">Zestawy i wykonywanie równoczesne</span><span class="sxs-lookup"><span data-stu-id="a2421-102">Assemblies and Side-by-Side Execution</span></span>
<span data-ttu-id="a2421-103">Wykonanie Side-by-side jest możliwość przechowywania i wykonywanie wielu wersji aplikacji lub składnika na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a2421-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="a2421-104">Oznacza to, że może mieć wiele wersji środowiska uruchomieniowego i wiele wersji aplikacji i składników, których używana jest wersja środowiska uruchomieniowego, na tym samym komputerze, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="a2421-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="a2421-105">Wykonanie Side-by-side zapewnia większą kontrolę nad jakich wersji składnika aplikacji wiąże i większą kontrolę nad którą wersję środowiska uruchomieniowego aplikacji używane.</span><span class="sxs-lookup"><span data-stu-id="a2421-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="a2421-106">Obsługa magazynu side-by-side i wykonywania różnych wersji tego samego zestawu jest integralną częścią silne nazwy i jest wbudowana w infrastrukturze środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a2421-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="a2421-107">Ponieważ numer wersji zestawu o silnej nazwie jest częścią jego tożsamość, środowisko uruchomieniowe można przechowywać wiele wersji tego samego zestawu w pamięci podręcznej GAC i ładowanie tych zestawów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a2421-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="a2421-108">Mimo że środowisko uruchomieniowe umożliwia tworzenie aplikacji side-by-side, wykonanie side-by-side nie jest automatyczna.</span><span class="sxs-lookup"><span data-stu-id="a2421-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="a2421-109">Aby uzyskać więcej informacji na temat tworzenia aplikacji dla wykonywania side-by-side, zobacz [wytyczne dotyczące tworzenia składników do wykonania Side-by-Side](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="a2421-109">For more information on creating applications for side-by-side execution, see [Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2421-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2421-110">See Also</span></span>  
 [<span data-ttu-id="a2421-111">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a2421-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="a2421-112">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="a2421-112">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
