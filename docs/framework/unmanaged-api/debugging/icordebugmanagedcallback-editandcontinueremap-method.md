---
title: ICorDebugManagedCallback::EditAndContinueRemap — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e8aa71a79bee45d5a8e1f3448c781e6ba1ec605
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414141"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="6b030-102">ICorDebugManagedCallback::EditAndContinueRemap — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b030-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="6b030-103">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="6b030-103">This method has been deprecated.</span></span> <span data-ttu-id="6b030-104">Powiadamia debugera, że zdarzenie ponownego mapowania zostało wysłane do zintegrowanego środowiska projektowego (IDE).</span><span class="sxs-lookup"><span data-stu-id="6b030-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b030-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b030-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b030-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b030-106">Remarks</span></span>  
 <span data-ttu-id="6b030-107">`EditAndContinueRemap` Metoda jest wywoływana, gdy podjęto próbę wykonania kodu w starszej wersji zaktualizowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="6b030-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="6b030-108">Typowe wywołania środowiska uruchomieniowego języka `EditAndContinueRemap` do wysyłania zdarzeń ponownego mapowania do środowiska IDE.</span><span class="sxs-lookup"><span data-stu-id="6b030-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b030-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b030-109">Requirements</span></span>  
 <span data-ttu-id="6b030-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b030-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b030-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b030-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b030-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b030-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b030-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b030-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b030-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b030-114">See Also</span></span>  
 [<span data-ttu-id="6b030-115">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b030-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
