---
title: Zestawy i wykonywanie równoczesne
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6f5d4b6bf94300872f85c118bd149d12cea65d0
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973069"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="5ebc0-102">Zestawy i wykonywanie równoczesne</span><span class="sxs-lookup"><span data-stu-id="5ebc0-102">Assemblies and side-by-side execution</span></span>
<span data-ttu-id="5ebc0-103">Wykonywanie równoczesne to możliwość przechowywania i wykonywania wielu wersji aplikacji lub składnika na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5ebc0-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="5ebc0-104">Oznacza to, że można korzystać z wielu wersji środowiska uruchomieniowego oraz wielu wersji aplikacji i składników, które używają wersji środowiska uruchomieniowego, na tym samym komputerze w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="5ebc0-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="5ebc0-105">Wykonywanie równoczesne daje większą kontrolę nad wersjami składnika, z którym jest powiązana aplikacja, oraz większą kontrolę nad wersją środowiska uruchomieniowego używaną przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="5ebc0-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="5ebc0-106">Obsługa magazynu Side-by-Side i wykonywania różnych wersji tego samego zestawu jest integralną częścią silnego nazewnictwa i jest wbudowana w infrastrukturę środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5ebc0-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="5ebc0-107">Ponieważ numer wersji zestawu o silnej nazwie jest częścią swojej tożsamości, środowisko uruchomieniowe może przechowywać wiele wersji tego samego zestawu w globalnej pamięci podręcznej zestawów i ładować te zestawy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5ebc0-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="5ebc0-108">Chociaż środowisko uruchomieniowe zapewnia możliwość tworzenia aplikacji obok siebie, wykonywanie równoczesne nie jest automatyczne.</span><span class="sxs-lookup"><span data-stu-id="5ebc0-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="5ebc0-109">Aby uzyskać więcej informacji na temat tworzenia aplikacji do wykonywania równoczesnego, zobacz [wskazówki dotyczące tworzenia składników do wykonywania równoczesnego](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="5ebc0-109">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebc0-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ebc0-110">See also</span></span>

- [<span data-ttu-id="5ebc0-111">Jak środowisko uruchomieniowe lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="5ebc0-111">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="5ebc0-112">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="5ebc0-112">Assemblies in .NET</span></span>](index.md)
