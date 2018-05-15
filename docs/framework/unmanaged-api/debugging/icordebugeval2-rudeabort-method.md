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
ms.openlocfilehash: 0aabff090634f1ecdeec5636336ad1fb77b8b81c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="af8d8-102">ICorDebugEval2::RudeAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="af8d8-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="af8d8-103">Przerywa obliczenia tego `ICorDebugEval2` wykonuje obecnie.</span><span class="sxs-lookup"><span data-stu-id="af8d8-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af8d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af8d8-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="af8d8-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af8d8-105">Remarks</span></span>  
 <span data-ttu-id="af8d8-106">`RudeAbort` nie zwalnia wszystkie blokady, które przechowuje ewaluatora, więc pozostawia sesji debugowania w stanie niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="af8d8-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="af8d8-107">Wywołanie tej metody za pomocą najwyższą ostrożność.</span><span class="sxs-lookup"><span data-stu-id="af8d8-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af8d8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af8d8-108">Requirements</span></span>  
 <span data-ttu-id="af8d8-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af8d8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af8d8-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af8d8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af8d8-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af8d8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af8d8-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af8d8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
