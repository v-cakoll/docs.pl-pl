---
title: "ICorDebugManagedCallback2::FunctionRemapOpportunity — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a8360913597dfb5156399a45f86d2cc1a9f453d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="48e69-102">ICorDebugManagedCallback2::FunctionRemapOpportunity — Metoda</span><span class="sxs-lookup"><span data-stu-id="48e69-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="48e69-103">Powiadamia debuger osiągnięcie w wykonanie kodu punktu sekwencji w starszej wersji funkcji edytowany.</span><span class="sxs-lookup"><span data-stu-id="48e69-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="48e69-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48e69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48e69-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="48e69-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierający funkcję edytowany.</span><span class="sxs-lookup"><span data-stu-id="48e69-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="48e69-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku podczas ponownego mapowania punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="48e69-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="48e69-108">[in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje wersji funkcji, która jest obecnie uruchomiony w wątku.</span><span class="sxs-lookup"><span data-stu-id="48e69-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="48e69-109">[in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje najnowszą wersję funkcji.</span><span class="sxs-lookup"><span data-stu-id="48e69-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="48e69-110">[in] Język pośredni (MSIL) firmy Microsoft przesunięcie wskaźnika instrukcji w starej wersji funkcji.</span><span class="sxs-lookup"><span data-stu-id="48e69-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48e69-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48e69-111">Remarks</span></span>  
 <span data-ttu-id="48e69-112">To wywołanie zwrotne daje debuger możliwość ponownie zamapować wskaźnik instrukcji, aby jego właściwe miejsce w nowej wersji określona funkcja wywołując [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="48e69-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="48e69-113">Jeśli debuger nie wywołuje `RemapFunction` przed wywołaniem [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody środowiska uruchomieniowego będzie kontynuować jego wykonywanie poprzedni kod i uruchomią innego `FunctionRemapOpportunity` wywołanie zwrotne z następnego punktu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="48e69-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="48e69-114">To wywołanie zwrotne zostanie wywołany dla każdej ramki, w której jest wykonywany starszą wersję danej funkcji, dopóki debuger zwraca wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="48e69-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48e69-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48e69-115">Requirements</span></span>  
 <span data-ttu-id="48e69-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48e69-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e69-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48e69-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48e69-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48e69-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48e69-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48e69-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e69-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48e69-120">See Also</span></span>  
 [<span data-ttu-id="48e69-121">ICorDebugManagedCallback2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="48e69-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="48e69-122">ICorDebugManagedCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="48e69-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
