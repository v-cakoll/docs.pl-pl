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
ms.openlocfilehash: c6c361113a441df050a8e7cd5219819cc8332581
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131483"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="6ea7f-102">ICorDebugManagedCallback2::FunctionRemapOpportunity — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ea7f-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="6ea7f-103">Powiadamia debuger, że wykonanie kodu osiągnęło punkt sekwencji w starszej wersji edytowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="6ea7f-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ea7f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ea7f-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ea7f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ea7f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6ea7f-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą edytowaną funkcję.</span><span class="sxs-lookup"><span data-stu-id="6ea7f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6ea7f-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym napotkano punkt przerwania mapowania.</span><span class="sxs-lookup"><span data-stu-id="6ea7f-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="6ea7f-108">podczas Wskaźnik do obiektu ICorDebugFunction, który reprezentuje wersję funkcji, która jest aktualnie uruchomiona w wątku.</span><span class="sxs-lookup"><span data-stu-id="6ea7f-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="6ea7f-109">podczas Wskaźnik do obiektu ICorDebugFunction, który reprezentuje najnowszą wersję funkcji.</span><span class="sxs-lookup"><span data-stu-id="6ea7f-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="6ea7f-110">podczas Przesunięcie języka pośredniego firmy Microsoft (MSIL) wskaźnika instrukcji w starej wersji funkcji.</span><span class="sxs-lookup"><span data-stu-id="6ea7f-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ea7f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ea7f-111">Remarks</span></span>  
 <span data-ttu-id="6ea7f-112">To wywołanie zwrotne daje debugerowi możliwość ponownego mapowania wskaźnika instrukcji do odpowiedniego miejsca w nowej wersji określonej funkcji przez wywołanie metody [ICorDebugILFrame2:: RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6ea7f-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="6ea7f-113">Jeśli debuger nie wywołuje `RemapFunction` przed wywołaniem metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , środowisko uruchomieniowe będzie kontynuowało wykonywanie starego kodu i spowoduje uruchomienie innego `FunctionRemapOpportunity` wywołania zwrotnego w następnym punkcie sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6ea7f-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="6ea7f-114">To wywołanie zwrotne zostanie wywołane dla każdej ramki, która wykonuje starszą wersję danej funkcji, dopóki debuger nie zwróci S_OK.</span><span class="sxs-lookup"><span data-stu-id="6ea7f-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ea7f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ea7f-115">Requirements</span></span>  
 <span data-ttu-id="6ea7f-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ea7f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ea7f-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ea7f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ea7f-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6ea7f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ea7f-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ea7f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea7f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ea7f-120">See also</span></span>

- [<span data-ttu-id="6ea7f-121">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ea7f-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="6ea7f-122">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ea7f-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
