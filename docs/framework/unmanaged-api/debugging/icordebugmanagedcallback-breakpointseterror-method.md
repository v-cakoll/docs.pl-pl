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
ms.openlocfilehash: 67d4972ee38a54d43b4a096847cc61fa3402b042
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788435"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="002a4-102">ICorDebugManagedCallback::BreakpointSetError — Metoda</span><span class="sxs-lookup"><span data-stu-id="002a4-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="002a4-103">Powiadamia debuger, że środowisko uruchomieniowe języka wspólnego nie mogło prawidłowo powiązać punktu przerwania, który został ustawiony przed skompilowaniem funkcji just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="002a4-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="002a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="002a4-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="002a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="002a4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="002a4-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która zawiera niezwiązany punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="002a4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="002a4-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który zawiera niezwiązany punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="002a4-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="002a4-108">podczas Wskaźnik do obiektu ICorDebugBreakpoint, który reprezentuje niezwiązany punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="002a4-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="002a4-109">podczas Liczba całkowita, która wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="002a4-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="002a4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="002a4-110">Remarks</span></span>  
 <span data-ttu-id="002a4-111">Dany punkt przerwania nigdy nie zostanie trafiony.</span><span class="sxs-lookup"><span data-stu-id="002a4-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="002a4-112">Debuger powinien dezaktywować i ponownie powiązać go.</span><span class="sxs-lookup"><span data-stu-id="002a4-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="002a4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="002a4-113">Requirements</span></span>  
 <span data-ttu-id="002a4-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="002a4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="002a4-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="002a4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="002a4-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="002a4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="002a4-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="002a4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002a4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="002a4-118">See also</span></span>

- [<span data-ttu-id="002a4-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="002a4-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
