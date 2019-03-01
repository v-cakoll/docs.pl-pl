---
title: Assemblyattributesgohere — klasa (System.Runtime.CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHere
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 571c2f6723e827a1b385f77724c33703ae970ae3
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968121"
---
# <a name="assemblyattributesgohere-class"></a><span data-ttu-id="2b40e-102">Assemblyattributesgohere — klasa</span><span class="sxs-lookup"><span data-stu-id="2b40e-102">AssemblyAttributesGoHere Class</span></span>

<span data-ttu-id="2b40e-103">Używane przez ALink, jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2b40e-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b40e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b40e-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a><span data-ttu-id="2b40e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b40e-105">Remarks</span></span>

<span data-ttu-id="2b40e-106">Odwołania do tego typu może być osadzony wewnątrz modułów sieciowych, których źródła zawierają zestaw atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2b40e-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="2b40e-107">Podczas tworzenia manifestu zestawu z jednego lub więcej modułów sieciowych, które zawierają odwołania do tych typów, ALink używa informacji o dołączonych do tych odwołań do emitowania rzeczywiste niestandardowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2b40e-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="2b40e-108">W efekcie tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji i spełniać nie zadania w końcowym zestawie.</span><span class="sxs-lookup"><span data-stu-id="2b40e-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="2b40e-109">Odwołania do tego typu wskazują atrybutów niestandardowych, które nie są związane z zabezpieczeniami i nie są wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="2b40e-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>

<span data-ttu-id="2b40e-110">Te typy są oznaczone jako "internal" w ramach programu .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2b40e-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b40e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b40e-111">Requirements</span></span>

<span data-ttu-id="2b40e-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="2b40e-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="2b40e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b40e-113">See also</span></span>

- [<span data-ttu-id="2b40e-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="2b40e-114">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="2b40e-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="2b40e-115">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="2b40e-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="2b40e-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
