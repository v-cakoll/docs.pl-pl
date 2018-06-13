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
ms.openlocfilehash: 8cc437f63621c451c0af796513d4646fe0668c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418382"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="f1cb4-102">ICorDebugManagedCallback::BreakpointSetError — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1cb4-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="f1cb4-103">Powiadamia debugera, że środowisko uruchomieniowe języka wspólnego nie może powiązać dokładnie punkt przerwania ustawiony przed funkcją just-in-time (JIT) skompilowany.</span><span class="sxs-lookup"><span data-stu-id="f1cb4-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1cb4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1cb4-104">Syntax</span></span>  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1cb4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1cb4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f1cb4-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, która zawiera niezwiązanego punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="f1cb4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f1cb4-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, który zawiera niezwiązanego punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="f1cb4-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="f1cb4-108">[in] Wskaźnik do obiektu ICorDebugBreakpoint, który reprezentuje niezwiązanego punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="f1cb4-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="f1cb4-109">[in] Liczba całkowita, która wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="f1cb4-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1cb4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1cb4-110">Remarks</span></span>  
 <span data-ttu-id="f1cb4-111">Podany punkt przerwania nigdy nie zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="f1cb4-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="f1cb4-112">Debuger należy go najpierw dezaktywować i ponownie ją powiązać.</span><span class="sxs-lookup"><span data-stu-id="f1cb4-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1cb4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1cb4-113">Requirements</span></span>  
 <span data-ttu-id="f1cb4-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1cb4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1cb4-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1cb4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1cb4-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1cb4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1cb4-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1cb4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1cb4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1cb4-118">See Also</span></span>  
 [<span data-ttu-id="f1cb4-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f1cb4-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
