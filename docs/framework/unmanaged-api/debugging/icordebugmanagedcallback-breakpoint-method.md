---
title: ICorDebugManagedCallback::Breakpoint — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Breakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Breakpoint
helpviewer_keywords:
- ICorDebugManagedCallback::Breakpoint method [.NET Framework debugging]
- Breakpoint method [.NET Framework debugging]
ms.assetid: 60b279b0-a726-46d2-8c53-76986a007ebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 381fdecfb2cb194cd1eb00a5b55db6fb89eeebbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="bcf72-102">ICorDebugManagedCallback::Breakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="bcf72-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="bcf72-103">Powiadamia debugera w przypadku napotkania punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="bcf72-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcf72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bcf72-104">Syntax</span></span>  
  
```  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcf72-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcf72-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bcf72-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, która zawiera punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="bcf72-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="bcf72-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, który zawiera punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="bcf72-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="bcf72-108">[in] Wskaźnik do obiektu ICorDebugBreakpoint, który reprezentuje punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="bcf72-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcf72-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bcf72-109">Requirements</span></span>  
 <span data-ttu-id="bcf72-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcf72-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcf72-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcf72-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcf72-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcf72-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcf72-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcf72-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcf72-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bcf72-114">See Also</span></span>  
 [<span data-ttu-id="bcf72-115">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="bcf72-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
