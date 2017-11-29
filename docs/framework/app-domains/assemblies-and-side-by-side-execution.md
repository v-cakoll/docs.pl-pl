---
title: "Zestawy i wykonywanie równoczesne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d0f5e5d0e9a2385d3ebf1c2f1dc7838de79b27e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="a60a8-102">Zestawy i wykonywanie równoczesne</span><span class="sxs-lookup"><span data-stu-id="a60a8-102">Assemblies and Side-by-Side Execution</span></span>
<span data-ttu-id="a60a8-103">Wykonanie Side-by-side jest możliwość przechowywania i wykonywanie wielu wersji aplikacji lub składnika na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a60a8-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="a60a8-104">Oznacza to, że może mieć wiele wersji środowiska uruchomieniowego i wiele wersji aplikacji i składników, których używana jest wersja środowiska uruchomieniowego, na tym samym komputerze, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="a60a8-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="a60a8-105">Wykonanie Side-by-side zapewnia większą kontrolę nad jakich wersji składnika aplikacji wiąże i większą kontrolę nad którą wersję środowiska uruchomieniowego aplikacji używane.</span><span class="sxs-lookup"><span data-stu-id="a60a8-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="a60a8-106">Obsługa magazynu side-by-side i wykonywania różnych wersji tego samego zestawu jest integralną częścią silne nazwy i jest wbudowana w infrastrukturze środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a60a8-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="a60a8-107">Ponieważ numer wersji zestawu o silnej nazwie jest częścią jego tożsamość, środowisko uruchomieniowe można przechowywać wiele wersji tego samego zestawu w pamięci podręcznej GAC i ładowanie tych zestawów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a60a8-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="a60a8-108">Mimo że środowisko uruchomieniowe umożliwia tworzenie aplikacji side-by-side, wykonanie side-by-side nie jest automatyczna.</span><span class="sxs-lookup"><span data-stu-id="a60a8-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="a60a8-109">Aby uzyskać więcej informacji na temat tworzenia aplikacji dla wykonywania side-by-side, zobacz [wytyczne dotyczące tworzenia składników do wykonania Side-by-Side](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="a60a8-109">For more information on creating applications for side-by-side execution, see [Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a60a8-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a60a8-110">See Also</span></span>  
 [<span data-ttu-id="a60a8-111">Jak lokalizuje zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a60a8-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="a60a8-112">Zestawy w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="a60a8-112">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
