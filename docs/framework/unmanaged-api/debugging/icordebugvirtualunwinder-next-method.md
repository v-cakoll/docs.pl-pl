---
title: "ICorDebugVirtualUnwinder::Next — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4dc0b8bf7915fe579c4764bc06c1f2534eeb759
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="54128-102">ICorDebugVirtualUnwinder::Next — metoda</span><span class="sxs-lookup"><span data-stu-id="54128-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="54128-103">Przechodzi do kontekstu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="54128-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54128-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54128-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54128-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54128-105">Parameters</span></span>  
 <span data-ttu-id="54128-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="54128-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54128-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="54128-107">Return Value</span></span>  
 <span data-ttu-id="54128-108">`S_OK`Jeśli unwind wystąpił pomyślnie, lub `CORDBG_S_AT_END_OF_STACK` Jeżeli nie można ukończyć unwind, ponieważ nie ma więcej ramek.</span><span class="sxs-lookup"><span data-stu-id="54128-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="54128-109">Jeśli przerwane zwrócony wynik HRESULT, interfejsy API ICorDebug zwróci `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="54128-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54128-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54128-110">Remarks</span></span>  
 <span data-ttu-id="54128-111">Walkera stosu upewnić się, że postęp, tak że ostatecznie powoduje wywołanie `Next` zwróci przerwane HRESULT lub `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="54128-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="54128-112">Zwracanie `S_OK` nieskończoność może spowodować nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="54128-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54128-113">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="54128-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54128-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54128-114">Requirements</span></span>  
 <span data-ttu-id="54128-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54128-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54128-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54128-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54128-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54128-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54128-118">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54128-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54128-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54128-119">See Also</span></span>  
 [<span data-ttu-id="54128-120">Interfejs ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="54128-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="54128-121">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="54128-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
