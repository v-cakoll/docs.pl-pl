---
title: Zestawy i wykonywanie równoczesne
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 234efba66d87b520b54d6d113afcc4bba0bfe06a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138657"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="1e82f-102">Zestawy i wykonywanie równoczesne</span><span class="sxs-lookup"><span data-stu-id="1e82f-102">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="1e82f-103">Wykonanie side-by-side jest możliwość przechowywania i wykonywania wielu wersji aplikacji lub składnika na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1e82f-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="1e82f-104">Oznacza to, że na tym samym komputerze może być dostępnych wiele wersji programu runtime oraz wiele wersji aplikacji i składników korzystających z wersji programu runtime.</span><span class="sxs-lookup"><span data-stu-id="1e82f-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="1e82f-105">Wykonanie side-by-side zapewnia większą kontrolę nad wersjami składnika, z którym aplikacja jest powiązana, oraz większą kontrolę nad wersją czasu wykonawczego używaną przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="1e82f-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="1e82f-106">Obsługa magazynu side-by-side i wykonywania różnych wersji tego samego zestawu jest integralną częścią silnego nazewnictwa i jest wbudowana w infrastrukturę czasu wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="1e82f-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="1e82f-107">Ponieważ numer wersji zestawu o silnej nazwie jest częścią jego tożsamości, w czasie wykonywania można przechowywać wiele wersji tego samego zestawu w globalnej pamięci podręcznej zestawów i załadować te zestawy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1e82f-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="1e82f-108">Mimo że czas wykonywania zapewnia możliwość tworzenia aplikacji side-by-side, wykonanie side-by-side nie jest automatyczne.</span><span class="sxs-lookup"><span data-stu-id="1e82f-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="1e82f-109">Aby uzyskać więcej informacji na temat tworzenia aplikacji do wykonywania obok siebie, zobacz [Wskazówki dotyczące tworzenia składników do wykonywania obok siebie](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="1e82f-109">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e82f-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e82f-110">See also</span></span>

- [<span data-ttu-id="1e82f-111">Jak program runtime lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="1e82f-111">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1e82f-112">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="1e82f-112">Assemblies in .NET</span></span>](index.md)
