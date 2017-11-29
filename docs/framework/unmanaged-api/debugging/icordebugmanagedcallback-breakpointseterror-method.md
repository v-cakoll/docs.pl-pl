---
title: "ICorDebugManagedCallback::BreakpointSetError — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.BreakpointSetError
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d8d75261a0ac1211ec54252b698a2a1b17ccac2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="bec2e-102">ICorDebugManagedCallback::BreakpointSetError — Metoda</span><span class="sxs-lookup"><span data-stu-id="bec2e-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="bec2e-103">Powiadamia debugera, że środowisko uruchomieniowe języka wspólnego nie może powiązać dokładnie punkt przerwania ustawiony przed funkcją just-in-time (JIT) skompilowany.</span><span class="sxs-lookup"><span data-stu-id="bec2e-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bec2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bec2e-104">Syntax</span></span>  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bec2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bec2e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bec2e-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, która zawiera niezwiązanego punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="bec2e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="bec2e-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, który zawiera niezwiązanego punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="bec2e-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="bec2e-108">[in] Wskaźnik do obiektu ICorDebugBreakpoint, który reprezentuje niezwiązanego punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="bec2e-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="bec2e-109">[in] Liczba całkowita, która wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="bec2e-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bec2e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bec2e-110">Remarks</span></span>  
 <span data-ttu-id="bec2e-111">Podany punkt przerwania nigdy nie zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="bec2e-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="bec2e-112">Debuger należy go najpierw dezaktywować i ponownie ją powiązać.</span><span class="sxs-lookup"><span data-stu-id="bec2e-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bec2e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bec2e-113">Requirements</span></span>  
 <span data-ttu-id="bec2e-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bec2e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bec2e-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bec2e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bec2e-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bec2e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bec2e-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bec2e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec2e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bec2e-118">See Also</span></span>  
 [<span data-ttu-id="bec2e-119">ICorDebugManagedCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="bec2e-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
