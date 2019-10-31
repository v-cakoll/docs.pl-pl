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
ms.openlocfilehash: 3fd1686eb268b9d4e347fe28e067a5321327dbd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137385"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="c75d8-102">ICorDebugManagedCallback::EditAndContinueRemap — Metoda</span><span class="sxs-lookup"><span data-stu-id="c75d8-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="c75d8-103">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="c75d8-103">This method has been deprecated.</span></span> <span data-ttu-id="c75d8-104">Powiadamia on debuger o wysłaniu zdarzenia ponownego mapowania do zintegrowanego środowiska programistycznego (IDE).</span><span class="sxs-lookup"><span data-stu-id="c75d8-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c75d8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c75d8-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c75d8-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c75d8-106">Remarks</span></span>  
 <span data-ttu-id="c75d8-107">Metoda `EditAndContinueRemap` jest wywoływana, gdy podjęto próbę wykonania kodu w starej wersji zaktualizowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c75d8-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="c75d8-108">Środowisko uruchomieniowe języka wspólnego wywołuje metodę `EditAndContinueRemap`, aby wysłać zdarzenie ponownego mapowania do środowiska IDE.</span><span class="sxs-lookup"><span data-stu-id="c75d8-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c75d8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c75d8-109">Requirements</span></span>  
 <span data-ttu-id="c75d8-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c75d8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c75d8-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c75d8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c75d8-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c75d8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c75d8-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c75d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75d8-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c75d8-114">See also</span></span>

- [<span data-ttu-id="c75d8-115">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c75d8-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
