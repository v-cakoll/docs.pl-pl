---
title: ICorDebugEval::Abort — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
ms.openlocfilehash: 98a9b285323bc3ad94b4f555e72a4b3242519801
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976294"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="94b6a-102">ICorDebugEval::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="94b6a-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="94b6a-103">Przerywa obliczenia wykonywane przez ten obiekt ICorDebugEval.</span><span class="sxs-lookup"><span data-stu-id="94b6a-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94b6a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94b6a-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="94b6a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94b6a-105">Remarks</span></span>  
 <span data-ttu-id="94b6a-106">Jeśli ocena jest zagnieżdżona i nie jest to najnowsza z nich, `Abort` Metoda może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="94b6a-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94b6a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94b6a-107">Requirements</span></span>  
 <span data-ttu-id="94b6a-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94b6a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94b6a-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="94b6a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94b6a-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="94b6a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94b6a-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94b6a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
