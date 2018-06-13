---
title: AssemblyAttributesGoHereSM
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereSM
api_location:
- alink.dll
api_type:
- COM
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
ms.openlocfilehash: bed903c7380bc73601f03a83d2c637ef34d9b9e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405217"
---
# <a name="assemblyattributesgoheresm"></a><span data-ttu-id="251eb-102">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="251eb-102">AssemblyAttributesGoHereSM</span></span>
<span data-ttu-id="251eb-103">Używane przez ALink jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="251eb-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="251eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="251eb-104">Syntax</span></span>  
  
```  
AssemblyAttributeGoHereSM  
```  
  
## <a name="remarks"></a><span data-ttu-id="251eb-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="251eb-105">Remarks</span></span>  
 <span data-ttu-id="251eb-106">Odwołania do tego typu może być osadzony wewnątrz netmodules, których źródła zawierają niestandardowe atrybuty zestawu.</span><span class="sxs-lookup"><span data-stu-id="251eb-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="251eb-107">Podczas tworzenia manifestu zestawu z co najmniej jeden netmodules, które zawierają odwołania do tych typów, ALink używa informacji dołączonych do tych odwołań do emisji rzeczywistym niestandardowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="251eb-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="251eb-108">W związku tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji oraz udostępni bezcelowe w zestawie końcowym.</span><span class="sxs-lookup"><span data-stu-id="251eb-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="251eb-109">Odwołania do tego typu wskazuje atrybutów niestandardowych, które są powiązane i wielokrotnego użytku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="251eb-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>  
  
 <span data-ttu-id="251eb-110">Te typy są oznaczone jako "wewnętrzne" w programie .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="251eb-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="251eb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="251eb-111">Requirements</span></span>  
 <span data-ttu-id="251eb-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="251eb-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251eb-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="251eb-113">See Also</span></span>  
 [<span data-ttu-id="251eb-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="251eb-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="251eb-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="251eb-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="251eb-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="251eb-116">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
