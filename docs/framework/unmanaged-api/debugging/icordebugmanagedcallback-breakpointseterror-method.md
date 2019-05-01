---
title: ICorDebugManagedCallback::BreakpointSetError — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27d5b8e0127971cc3a46560590fd9d95f0ffd1f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988328"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="f275c-102">ICorDebugManagedCallback::BreakpointSetError — Metoda</span><span class="sxs-lookup"><span data-stu-id="f275c-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="f275c-103">Powiadamia debuger środowiska uruchomieniowego języka wspólnego i nie można powiązać dokładnie punkcie przerwania, który został ustawiony, aby funkcja była just-in-time (JIT) skompilowany.</span><span class="sxs-lookup"><span data-stu-id="f275c-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f275c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f275c-104">Syntax</span></span>  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f275c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f275c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f275c-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która zawiera niepowiązanych punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="f275c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f275c-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który zawiera niepowiązanych punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="f275c-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="f275c-108">[in] Wskaźnik do obiektu ICorDebugBreakpoint, który reprezentuje niepowiązanych punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="f275c-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="f275c-109">[in] Liczba całkowita, która wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="f275c-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f275c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f275c-110">Remarks</span></span>  
 <span data-ttu-id="f275c-111">Dany punkt przerwania, nigdy nie zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="f275c-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="f275c-112">Debuger powinien dezaktywować i powiąż ją ponownie.</span><span class="sxs-lookup"><span data-stu-id="f275c-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f275c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f275c-113">Requirements</span></span>  
 <span data-ttu-id="f275c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f275c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f275c-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f275c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f275c-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f275c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f275c-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f275c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f275c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f275c-118">See also</span></span>

- [<span data-ttu-id="f275c-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f275c-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
