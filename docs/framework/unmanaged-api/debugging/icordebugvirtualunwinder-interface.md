---
title: "ICorDebugVirtualUnwinder — interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d22fa926b300384b7f790468b1b3d0becafdb942
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="39393-102">ICorDebugVirtualUnwinder — interfejs</span><span class="sxs-lookup"><span data-stu-id="39393-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="39393-103">Udostępnia metody, aby pomóc w odwijanie stosu.</span><span class="sxs-lookup"><span data-stu-id="39393-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39393-104">Metody</span><span class="sxs-lookup"><span data-stu-id="39393-104">Methods</span></span>  
  
|<span data-ttu-id="39393-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="39393-105">Method</span></span>|<span data-ttu-id="39393-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="39393-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="39393-107">GetContext — metoda</span><span class="sxs-lookup"><span data-stu-id="39393-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="39393-108">Pobiera bieżący kontekst tego unwinder.</span><span class="sxs-lookup"><span data-stu-id="39393-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="39393-109">Next — metoda</span><span class="sxs-lookup"><span data-stu-id="39393-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="39393-110">Przechodzi do kontekstu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="39393-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39393-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39393-111">Remarks</span></span>  
 <span data-ttu-id="39393-112">Elementy członkowskie `ICorDebugVirtualUnwinder` interfejs jest implementowany przez debugera, aby pomóc w odwijanie stosu.</span><span class="sxs-lookup"><span data-stu-id="39393-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39393-113">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="39393-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="39393-114">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="39393-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39393-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39393-115">Requirements</span></span>  
 <span data-ttu-id="39393-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39393-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39393-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39393-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39393-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39393-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39393-119">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39393-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39393-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39393-120">See Also</span></span>  
 [<span data-ttu-id="39393-121">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="39393-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="39393-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="39393-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
