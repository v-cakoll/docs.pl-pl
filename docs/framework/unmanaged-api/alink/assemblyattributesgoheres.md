---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 135938c4ed91423145ca46b743620f4236f7f818
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742256"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="6dc44-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="6dc44-102">AssemblyAttributesGoHereS</span></span>

<span data-ttu-id="6dc44-103">Używane przez ALink, jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6dc44-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="6dc44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6dc44-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a><span data-ttu-id="6dc44-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6dc44-105">Remarks</span></span>

<span data-ttu-id="6dc44-106">Odwołania do tego typu może być osadzony wewnątrz modułów sieciowych, których źródła zawierają zestaw atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6dc44-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="6dc44-107">Podczas tworzenia manifestu zestawu z jednego lub więcej modułów sieciowych, które zawierają odwołania do tych typów, ALink używa informacji o dołączonych do tych odwołań do emitowania rzeczywiste niestandardowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6dc44-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="6dc44-108">W efekcie tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji i spełniać nie zadania w końcowym zestawie.</span><span class="sxs-lookup"><span data-stu-id="6dc44-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="6dc44-109">Odwołania do tego typu wskazują atrybutów niestandardowych, które są związane z zabezpieczeniami i nie są wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="6dc44-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>

<span data-ttu-id="6dc44-110">Te typy są oznaczone jako "internal" w ramach programu .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6dc44-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="6dc44-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6dc44-111">Requirements</span></span>

<span data-ttu-id="6dc44-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="6dc44-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="6dc44-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6dc44-113">See also</span></span>

- [<span data-ttu-id="6dc44-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="6dc44-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="6dc44-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="6dc44-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="6dc44-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="6dc44-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
