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
ms.openlocfilehash: 14291ced9a606cc0b2a3792c2157b7bc2a3460a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190538"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="3dd17-102">ICorDebugManagedCallback2::FunctionRemapOpportunity — Metoda</span><span class="sxs-lookup"><span data-stu-id="3dd17-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="3dd17-103">Powiadamia debugera, że wykonywanie kodu osiągnęła punktu sekwencji w starszej wersji przeprowadzono edycję funkcji.</span><span class="sxs-lookup"><span data-stu-id="3dd17-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd17-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3dd17-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dd17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dd17-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3dd17-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą przeprowadzono edycję funkcji.</span><span class="sxs-lookup"><span data-stu-id="3dd17-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="3dd17-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek napotkano punkt przerwania ponowne mapowanie.</span><span class="sxs-lookup"><span data-stu-id="3dd17-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="3dd17-108">[in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje wersji funkcji, która jest aktualnie uruchomiona w wątku.</span><span class="sxs-lookup"><span data-stu-id="3dd17-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="3dd17-109">[in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje najnowszą wersję funkcji.</span><span class="sxs-lookup"><span data-stu-id="3dd17-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="3dd17-110">[in] Przesunięcie Microsoft intermediate language (MSIL) wskaźnik instrukcji w starej wersji funkcji.</span><span class="sxs-lookup"><span data-stu-id="3dd17-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dd17-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3dd17-111">Remarks</span></span>  
 <span data-ttu-id="3dd17-112">To wywołanie zwrotne zapewnia debugera można ponownie zamapować wskaźnik instrukcji do jego właściwe miejsce w nowej wersji określonej funkcji przez wywołanie metody [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3dd17-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="3dd17-113">Jeśli debuger nie mogą wywoływać `RemapFunction` przed wywołaniem [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody, środowisko uruchomieniowe będzie w dalszym ciągu wykonują poprzedni kod i zostanie uruchomiony inny `FunctionRemapOpportunity` wywołania zwrotnego w następnym punkcie sekwencji.</span><span class="sxs-lookup"><span data-stu-id="3dd17-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="3dd17-114">To wywołanie zwrotne zostanie wywołany dla każdej ramki, który jest wykonywany na starszą wersję danej funkcji, dopóki debuger nie zwróci S_OK.</span><span class="sxs-lookup"><span data-stu-id="3dd17-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dd17-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3dd17-115">Requirements</span></span>  
 <span data-ttu-id="3dd17-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dd17-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd17-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dd17-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dd17-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dd17-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dd17-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dd17-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd17-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3dd17-120">See also</span></span>

- [<span data-ttu-id="3dd17-121">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3dd17-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="3dd17-122">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="3dd17-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
