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
ms.openlocfilehash: c24ca43f35e237b6387e108563b1f9c9ed432242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402398"
---
# <a name="assemblyattributesgohere"></a><span data-ttu-id="096f0-102">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="096f0-102">AssemblyAttributesGoHere</span></span>
<span data-ttu-id="096f0-103">Używane przez ALink jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="096f0-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="096f0-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a><span data-ttu-id="096f0-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="096f0-105">Remarks</span></span>  
 <span data-ttu-id="096f0-106">Odwołania do tego typu może być osadzony wewnątrz netmodules, których źródła zawierają niestandardowe atrybuty zestawu.</span><span class="sxs-lookup"><span data-stu-id="096f0-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="096f0-107">Podczas tworzenia manifestu zestawu z co najmniej jeden netmodules, które zawierają odwołania do tych typów, ALink używa informacji dołączonych do tych odwołań do emisji rzeczywistym niestandardowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="096f0-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="096f0-108">W związku tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji oraz udostępni bezcelowe w zestawie końcowym.</span><span class="sxs-lookup"><span data-stu-id="096f0-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="096f0-109">Odwołania do tego typu wskazuje atrybutów niestandardowych, które nie są związane z zabezpieczeń i nie są wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="096f0-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="096f0-110">Te typy są oznaczone jako "wewnętrzne" w programie .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="096f0-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="096f0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="096f0-111">Requirements</span></span>  
 <span data-ttu-id="096f0-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="096f0-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="096f0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="096f0-113">See Also</span></span>  
 [<span data-ttu-id="096f0-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="096f0-114">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="096f0-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="096f0-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="096f0-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="096f0-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
