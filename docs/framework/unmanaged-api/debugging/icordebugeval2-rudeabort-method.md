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
ms.openlocfilehash: e901c65824ee8d6949c79c7778944148c0d9eb28
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976060"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="1c6df-102">ICorDebugEval2::RudeAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c6df-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="1c6df-103">Przerywa obliczenia, które `ICorDebugEval2` jest aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="1c6df-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c6df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c6df-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1c6df-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c6df-105">Remarks</span></span>  
 <span data-ttu-id="1c6df-106">`RudeAbort`nie zwalnia żadnych blokad, które są przechowywane przez ewaluatora, dlatego sesja debugowania jest pozostawiana w stanie niebezpiecznym.</span><span class="sxs-lookup"><span data-stu-id="1c6df-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="1c6df-107">Wywołaj tę metodę z największą ostrożnością.</span><span class="sxs-lookup"><span data-stu-id="1c6df-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c6df-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c6df-108">Requirements</span></span>  
 <span data-ttu-id="1c6df-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c6df-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c6df-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c6df-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c6df-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1c6df-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c6df-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c6df-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
