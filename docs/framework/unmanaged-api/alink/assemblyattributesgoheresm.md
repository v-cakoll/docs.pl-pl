---
title: Assemblyattributesgoheresm — klasa (System.Runtime.CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereSM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01b156ed9c318e71a408ea10f2744911a85faedc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975371"
---
# <a name="assemblyattributesgoheresm-class"></a><span data-ttu-id="fedab-102">Assemblyattributesgoheresm — klasa</span><span class="sxs-lookup"><span data-stu-id="fedab-102">AssemblyAttributesGoHereSM Class</span></span>

<span data-ttu-id="fedab-103">Używane przez ALink, jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fedab-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="fedab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fedab-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a><span data-ttu-id="fedab-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fedab-105">Remarks</span></span>

<span data-ttu-id="fedab-106">Odwołania do tego typu może być osadzony wewnątrz modułów sieciowych, których źródła zawierają zestaw atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fedab-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="fedab-107">Podczas tworzenia manifestu zestawu z jednego lub więcej modułów sieciowych, które zawierają odwołania do tych typów, ALink używa informacji o dołączonych do tych odwołań do emitowania rzeczywiste niestandardowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="fedab-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="fedab-108">W efekcie tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji i spełniać nie zadania w końcowym zestawie.</span><span class="sxs-lookup"><span data-stu-id="fedab-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="fedab-109">Odwołania do tego typu wskazują atrybutów niestandardowych, które są powiązane i wielokrotnego użytku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fedab-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>

<span data-ttu-id="fedab-110">Te typy są oznaczone jako "internal" w ramach programu .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fedab-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="fedab-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fedab-111">Requirements</span></span>

<span data-ttu-id="fedab-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="fedab-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="fedab-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fedab-113">See also</span></span>

- [<span data-ttu-id="fedab-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="fedab-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="fedab-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="fedab-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="fedab-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="fedab-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
