---
title: AssemblyAttributesGoHereM
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereM
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbd5428039144fd38796ed6865c24a605f236ccd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733808"
---
# <a name="assemblyattributesgoherem"></a><span data-ttu-id="fd508-102">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="fd508-102">AssemblyAttributesGoHereM</span></span>
<span data-ttu-id="fd508-103">Używane przez ALink, jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fd508-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd508-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd508-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereM  
```  
  
## <a name="remarks"></a><span data-ttu-id="fd508-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd508-105">Remarks</span></span>  
 <span data-ttu-id="fd508-106">Odwołania do tego typu może być osadzony wewnątrz modułów sieciowych, których źródła zawierają zestaw atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fd508-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="fd508-107">Podczas tworzenia manifestu zestawu z jednego lub więcej modułów sieciowych, które zawierają odwołania do tych typów, ALink używa informacji o dołączonych do tych odwołań do emitowania rzeczywiste niestandardowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="fd508-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="fd508-108">W efekcie tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji i spełniać nie zadania w końcowym zestawie.</span><span class="sxs-lookup"><span data-stu-id="fd508-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="fd508-109">Odwołania do tego typu wskazują atrybutów niestandardowych, które nie są związane z zabezpieczeniami, ale są wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="fd508-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>  
  
 <span data-ttu-id="fd508-110">Te typy są oznaczone jako "internal" w ramach programu .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="fd508-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd508-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd508-111">Requirements</span></span>  
 <span data-ttu-id="fd508-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="fd508-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd508-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd508-113">See also</span></span>
- [<span data-ttu-id="fd508-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="fd508-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)
- [<span data-ttu-id="fd508-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="fd508-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
- [<span data-ttu-id="fd508-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="fd508-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
