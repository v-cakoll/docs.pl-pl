---
title: AssemblyAttributesGoHereS
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyAttributesGoHereS
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8ed5e0ee6559747604a3bd060386c65548460b37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="d1d00-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="d1d00-102">AssemblyAttributesGoHereS</span></span>
<span data-ttu-id="d1d00-103">Używane przez ALink jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d1d00-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d00-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1d00-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereS  
```  
  
## <a name="remarks"></a><span data-ttu-id="d1d00-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1d00-105">Remarks</span></span>  
 <span data-ttu-id="d1d00-106">Odwołania do tego typu może być osadzony wewnątrz netmodules, których źródła zawierają niestandardowe atrybuty zestawu.</span><span class="sxs-lookup"><span data-stu-id="d1d00-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="d1d00-107">Podczas tworzenia manifestu zestawu z co najmniej jeden netmodules, które zawierają odwołania do tych typów, ALink używa informacji dołączonych do tych odwołań do emisji rzeczywistym niestandardowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d1d00-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="d1d00-108">W związku tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji oraz udostępni bezcelowe w zestawie końcowym.</span><span class="sxs-lookup"><span data-stu-id="d1d00-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="d1d00-109">Odwołania do tego typu wskazuje atrybutów niestandardowych, które są związane z zabezpieczeń i nie są wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="d1d00-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="d1d00-110">Te typy są oznaczone jako "wewnętrzne" w programie .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="d1d00-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1d00-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1d00-111">Requirements</span></span>  
 <span data-ttu-id="d1d00-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="d1d00-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d00-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1d00-113">See Also</span></span>  
 [<span data-ttu-id="d1d00-114">Assemblyattributesgohere —</span><span class="sxs-lookup"><span data-stu-id="d1d00-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="d1d00-115">Assemblyattributesgoherem —</span><span class="sxs-lookup"><span data-stu-id="d1d00-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="d1d00-116">Assemblyattributesgoheresm —</span><span class="sxs-lookup"><span data-stu-id="d1d00-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
