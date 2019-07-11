---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24f058ff11a1155aa53a1d1f222ff1230c1c23e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760986"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="ce7c1-102">ICorDebugManagedCallback2::FunctionRemapOpportunity — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce7c1-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="ce7c1-103">Powiadamia debugera, że wykonywanie kodu osiągnęła punktu sekwencji w starszej wersji przeprowadzono edycję funkcji.</span><span class="sxs-lookup"><span data-stu-id="ce7c1-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce7c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce7c1-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce7c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce7c1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ce7c1-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą przeprowadzono edycję funkcji.</span><span class="sxs-lookup"><span data-stu-id="ce7c1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ce7c1-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek napotkano punkt przerwania ponowne mapowanie.</span><span class="sxs-lookup"><span data-stu-id="ce7c1-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="ce7c1-108">[in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje wersji funkcji, która jest aktualnie uruchomiona w wątku.</span><span class="sxs-lookup"><span data-stu-id="ce7c1-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="ce7c1-109">[in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje najnowszą wersję funkcji.</span><span class="sxs-lookup"><span data-stu-id="ce7c1-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="ce7c1-110">[in] Przesunięcie Microsoft intermediate language (MSIL) wskaźnik instrukcji w starej wersji funkcji.</span><span class="sxs-lookup"><span data-stu-id="ce7c1-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce7c1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce7c1-111">Remarks</span></span>  
 <span data-ttu-id="ce7c1-112">To wywołanie zwrotne zapewnia debugera można ponownie zamapować wskaźnik instrukcji do jego właściwe miejsce w nowej wersji określonej funkcji przez wywołanie metody [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ce7c1-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="ce7c1-113">Jeśli debuger nie mogą wywoływać `RemapFunction` przed wywołaniem [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody, środowisko uruchomieniowe będzie w dalszym ciągu wykonują poprzedni kod i zostanie uruchomiony inny `FunctionRemapOpportunity` wywołania zwrotnego w następnym punkcie sekwencji.</span><span class="sxs-lookup"><span data-stu-id="ce7c1-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="ce7c1-114">To wywołanie zwrotne zostanie wywołany dla każdej ramki, który jest wykonywany na starszą wersję danej funkcji, dopóki debuger nie zwróci S_OK.</span><span class="sxs-lookup"><span data-stu-id="ce7c1-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce7c1-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce7c1-115">Requirements</span></span>  
 <span data-ttu-id="ce7c1-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce7c1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce7c1-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce7c1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce7c1-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce7c1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce7c1-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce7c1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce7c1-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce7c1-120">See also</span></span>

- [<span data-ttu-id="ce7c1-121">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce7c1-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="ce7c1-122">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce7c1-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
