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
ms.openlocfilehash: d1bdb14e8c3a61a2b94cef778660eeb5c85c34df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149776"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="b6b24-102">ICorDebugManagedCallback::EditAndContinueRemap — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6b24-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="b6b24-103">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="b6b24-103">This method has been deprecated.</span></span> <span data-ttu-id="b6b24-104">Powiadomi użytkownika debugera, zdarzenia ponowne mapowanie została wysłana do zintegrowanego środowiska programistycznego (IDE).</span><span class="sxs-lookup"><span data-stu-id="b6b24-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b24-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6b24-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b6b24-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6b24-106">Remarks</span></span>  
 <span data-ttu-id="b6b24-107">`EditAndContinueRemap` Metoda jest wywoływana, gdy podjęto próbę wykonania kodu w starszej wersji zaktualizowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="b6b24-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="b6b24-108">Środowisko uruchomieniowe wywołuje języka wspólnego `EditAndContinueRemap` metodę, aby wysłać zdarzenie ponowne mapowanie środowiska IDE.</span><span class="sxs-lookup"><span data-stu-id="b6b24-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b24-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6b24-109">Requirements</span></span>  
 <span data-ttu-id="b6b24-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6b24-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6b24-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6b24-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6b24-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6b24-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b6b24-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b6b24-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b6b24-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6b24-114">See also</span></span>

- [<span data-ttu-id="b6b24-115">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b6b24-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
