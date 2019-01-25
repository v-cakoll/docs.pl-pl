---
title: AssemblyAttributesGoHere
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHere
api_location:
- alink.dll
api_type:
- COM
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
ms.openlocfilehash: cde96ed9089416fa5febe55e49b4109cfeb11f40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722143"
---
# <a name="assemblyattributesgohere"></a><span data-ttu-id="4e8ee-102">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="4e8ee-102">AssemblyAttributesGoHere</span></span>
<span data-ttu-id="4e8ee-103">Używane przez ALink, jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4e8ee-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e8ee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e8ee-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a><span data-ttu-id="4e8ee-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e8ee-105">Remarks</span></span>  
 <span data-ttu-id="4e8ee-106">Odwołania do tego typu może być osadzony wewnątrz modułów sieciowych, których źródła zawierają zestaw atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4e8ee-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="4e8ee-107">Podczas tworzenia manifestu zestawu z jednego lub więcej modułów sieciowych, które zawierają odwołania do tych typów, ALink używa informacji o dołączonych do tych odwołań do emitowania rzeczywiste niestandardowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4e8ee-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="4e8ee-108">W efekcie tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji i spełniać nie zadania w końcowym zestawie.</span><span class="sxs-lookup"><span data-stu-id="4e8ee-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="4e8ee-109">Odwołania do tego typu wskazują atrybutów niestandardowych, które nie są związane z zabezpieczeniami i nie są wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="4e8ee-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="4e8ee-110">Te typy są oznaczone jako "internal" w ramach programu .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="4e8ee-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e8ee-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e8ee-111">Requirements</span></span>  
 <span data-ttu-id="4e8ee-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="4e8ee-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e8ee-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e8ee-113">See also</span></span>
- [<span data-ttu-id="4e8ee-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="4e8ee-114">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)
- [<span data-ttu-id="4e8ee-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="4e8ee-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
- [<span data-ttu-id="4e8ee-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="4e8ee-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
