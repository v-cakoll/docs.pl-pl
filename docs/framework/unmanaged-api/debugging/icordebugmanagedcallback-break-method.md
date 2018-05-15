---
title: ICorDebugManagedCallback::Break — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7120e092b422b755ecbde9e48236b42e67636fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="177c7-102">ICorDebugManagedCallback::Break — Metoda</span><span class="sxs-lookup"><span data-stu-id="177c7-102">ICorDebugManagedCallback::Break Method</span></span>
<span data-ttu-id="177c7-103">Powiadamia debuger podczas <xref:System.Reflection.Emit.OpCodes.Break> wykonaniem instrukcji w strumieniu kodu.</span><span class="sxs-lookup"><span data-stu-id="177c7-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="177c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="177c7-104">Syntax</span></span>  
  
```  
HRESULT Break (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="177c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="177c7-105">Parameters</span></span>  
 `pAppDOmain`  
 <span data-ttu-id="177c7-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, która zawiera instrukcji break.</span><span class="sxs-lookup"><span data-stu-id="177c7-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>  
  
 `thread`  
 <span data-ttu-id="177c7-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, który zawiera instrukcji break.</span><span class="sxs-lookup"><span data-stu-id="177c7-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="177c7-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="177c7-108">Requirements</span></span>  
 <span data-ttu-id="177c7-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="177c7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="177c7-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="177c7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="177c7-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="177c7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="177c7-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="177c7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177c7-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="177c7-113">See Also</span></span>  
 [<span data-ttu-id="177c7-114">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="177c7-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
