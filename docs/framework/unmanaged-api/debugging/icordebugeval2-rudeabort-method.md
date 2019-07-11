---
title: ICorDebugEval2::RudeAbort — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a1adb79e5081fc909d0cd180d8161eccea7e58e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754348"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="62525-102">ICorDebugEval2::RudeAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="62525-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="62525-103">Przerywa obliczeń że `ICorDebugEval2` Trwa wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="62525-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62525-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62525-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="62525-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62525-105">Remarks</span></span>  
 <span data-ttu-id="62525-106">`RudeAbort` nie spowoduje zwolnienia żadnych blokad, które przechowuje ewaluatora, więc pozostawia sesji debugowania w stanie niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="62525-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="62525-107">Wywołaj tę metodę z najwyższą ostrożnością.</span><span class="sxs-lookup"><span data-stu-id="62525-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62525-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62525-108">Requirements</span></span>  
 <span data-ttu-id="62525-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62525-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62525-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62525-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62525-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62525-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62525-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62525-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
