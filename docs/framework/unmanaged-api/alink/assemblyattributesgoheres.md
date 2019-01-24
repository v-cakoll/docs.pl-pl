---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereS
api_location:
- alink.dll
api_type:
- COM
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
ms.openlocfilehash: 3506462aaf8d040126d979801460772b3cd47f9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706290"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="bb791-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="bb791-102">AssemblyAttributesGoHereS</span></span>
<span data-ttu-id="bb791-103">Używane przez ALink, jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bb791-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb791-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb791-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereS  
```  
  
## <a name="remarks"></a><span data-ttu-id="bb791-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb791-105">Remarks</span></span>  
 <span data-ttu-id="bb791-106">Odwołania do tego typu może być osadzony wewnątrz modułów sieciowych, których źródła zawierają zestaw atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bb791-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="bb791-107">Podczas tworzenia manifestu zestawu z jednego lub więcej modułów sieciowych, które zawierają odwołania do tych typów, ALink używa informacji o dołączonych do tych odwołań do emitowania rzeczywiste niestandardowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="bb791-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="bb791-108">W efekcie tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji i spełniać nie zadania w końcowym zestawie.</span><span class="sxs-lookup"><span data-stu-id="bb791-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="bb791-109">Odwołania do tego typu wskazują atrybutów niestandardowych, które są związane z zabezpieczeniami i nie są wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="bb791-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="bb791-110">Te typy są oznaczone jako "internal" w ramach programu .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="bb791-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb791-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb791-111">Requirements</span></span>  
 <span data-ttu-id="bb791-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="bb791-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb791-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb791-113">See also</span></span>
- [<span data-ttu-id="bb791-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="bb791-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)
- [<span data-ttu-id="bb791-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="bb791-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)
- [<span data-ttu-id="bb791-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="bb791-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
