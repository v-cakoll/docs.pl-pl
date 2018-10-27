---
title: Zestawy i wykonywanie równoczesne
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e192266aa7b98637cb05f400901f51afd3046a72
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "49415207"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="61690-102">Zestawy i wykonywanie równoczesne</span><span class="sxs-lookup"><span data-stu-id="61690-102">Assemblies and Side-by-Side Execution</span></span>
<span data-ttu-id="61690-103">Wykonanie Side-by-side jest możliwość przechowywania i wykonywania wielu wersji aplikacji lub składnika na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="61690-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="61690-104">Oznacza to, że można mieć wiele wersji środowiska uruchomieniowego i wiele wersji aplikacji i składników, które używają wersji środowiska uruchomieniowego, na tym samym komputerze, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="61690-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="61690-105">Wykonanie Side-by-side daje większą kontrolę nad jakie wersje składnika jest powiązana aplikacja, i mieć większą kontrolę nad jakie wersje środowiska uruchomieniowego używa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="61690-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="61690-106">Obsługa magazynu side-by-side i wykonywanie różnych wersji tego samego zestawu jest integralną częścią — silne nazwy i jest wbudowana w infrastrukturze środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="61690-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="61690-107">Numer wersji zestawu o silnej nazwie jest częścią swoją tożsamość, środowisko uruchomieniowe można przechowywać wiele wersji tego samego zestawu w globalnej pamięci podręcznej i ładowania tych zestawów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="61690-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="61690-108">Chociaż środowisko uruchomieniowe umożliwia tworzenie aplikacji side-by-side, wykonywania side-by-side nie jest automatyczna.</span><span class="sxs-lookup"><span data-stu-id="61690-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="61690-109">Aby uzyskać więcej informacji na temat tworzenia aplikacji w celu wykonania side-by-side, zobacz [wytyczne dotyczące tworzenia składników Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="61690-109">For more information on creating applications for side-by-side execution, see [Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61690-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61690-110">See Also</span></span>  
- [<span data-ttu-id="61690-111">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="61690-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [<span data-ttu-id="61690-112">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="61690-112">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
