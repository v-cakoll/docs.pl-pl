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
ms.openlocfilehash: dae04e1809c1bb3260461086a4953b8b4e5cce52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122572"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="8e72b-102">ICorDebugManagedCallback::BreakpointSetError — Metoda</span><span class="sxs-lookup"><span data-stu-id="8e72b-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="8e72b-103">Powiadamia debuger, że środowisko uruchomieniowe języka wspólnego nie mogło prawidłowo powiązać punktu przerwania, który został ustawiony przed skompilowaniem funkcji just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="8e72b-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e72b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e72b-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e72b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e72b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8e72b-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która zawiera niezwiązany punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="8e72b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="8e72b-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który zawiera niezwiązany punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="8e72b-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="8e72b-108">podczas Wskaźnik do obiektu ICorDebugBreakpoint, który reprezentuje niezwiązany punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="8e72b-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="8e72b-109">podczas Liczba całkowita, która wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="8e72b-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e72b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e72b-110">Remarks</span></span>  
 <span data-ttu-id="8e72b-111">Dany punkt przerwania nigdy nie zostanie trafiony.</span><span class="sxs-lookup"><span data-stu-id="8e72b-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="8e72b-112">Debuger powinien dezaktywować i ponownie powiązać go.</span><span class="sxs-lookup"><span data-stu-id="8e72b-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e72b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e72b-113">Requirements</span></span>  
 <span data-ttu-id="8e72b-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e72b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e72b-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8e72b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e72b-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8e72b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e72b-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e72b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e72b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e72b-118">See also</span></span>

- [<span data-ttu-id="8e72b-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e72b-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
