---
title: AssemblyAttributesGoHere
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3363ac5bd53688cfaa667a57afce17b6b52b1f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgohere"></a><span data-ttu-id="6ace2-102">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="6ace2-102">AssemblyAttributesGoHere</span></span>
<span data-ttu-id="6ace2-103">Używane przez ALink jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6ace2-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ace2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ace2-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a><span data-ttu-id="6ace2-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ace2-105">Remarks</span></span>  
 <span data-ttu-id="6ace2-106">Odwołania do tego typu może być osadzony wewnątrz netmodules, których źródła zawierają niestandardowe atrybuty zestawu.</span><span class="sxs-lookup"><span data-stu-id="6ace2-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="6ace2-107">Podczas tworzenia manifestu zestawu z co najmniej jeden netmodules, które zawierają odwołania do tych typów, ALink używa informacji dołączonych do tych odwołań do emisji rzeczywistym niestandardowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6ace2-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="6ace2-108">W związku tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji oraz udostępni bezcelowe w zestawie końcowym.</span><span class="sxs-lookup"><span data-stu-id="6ace2-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="6ace2-109">Odwołania do tego typu wskazuje atrybutów niestandardowych, które nie są związane z zabezpieczeń i nie są wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="6ace2-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="6ace2-110">Te typy są oznaczone jako "wewnętrzne" w programie .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="6ace2-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ace2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ace2-111">Requirements</span></span>  
 <span data-ttu-id="6ace2-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="6ace2-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ace2-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ace2-113">See Also</span></span>  
 [<span data-ttu-id="6ace2-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="6ace2-114">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="6ace2-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="6ace2-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="6ace2-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="6ace2-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
