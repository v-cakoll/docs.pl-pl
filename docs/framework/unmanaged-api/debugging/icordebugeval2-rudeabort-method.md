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
ms.openlocfilehash: a486935d5d53a6fc7d862160ed1186c5774814c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084797"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="0ae6f-102">ICorDebugEval2::RudeAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="0ae6f-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="0ae6f-103">Przerywa Obliczanie wykonywane przez tę `ICorDebugEval2`.</span><span class="sxs-lookup"><span data-stu-id="0ae6f-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ae6f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ae6f-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0ae6f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ae6f-105">Remarks</span></span>  
 <span data-ttu-id="0ae6f-106">`RudeAbort` nie zwolni żadnych blokad, które są przechowywane przez ewaluatora, więc pozostawia sesję debugowania w stanie niebezpiecznym.</span><span class="sxs-lookup"><span data-stu-id="0ae6f-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="0ae6f-107">Wywołaj tę metodę z największą ostrożnością.</span><span class="sxs-lookup"><span data-stu-id="0ae6f-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ae6f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ae6f-108">Requirements</span></span>  
 <span data-ttu-id="0ae6f-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ae6f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ae6f-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0ae6f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ae6f-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0ae6f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ae6f-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ae6f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
