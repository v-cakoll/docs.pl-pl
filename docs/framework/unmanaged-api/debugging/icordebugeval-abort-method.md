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
ms.openlocfilehash: 78402e5e099815fe309618e692285de91b8b29f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124236"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="32a06-102">ICorDebugEval::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="32a06-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="32a06-103">Przerywa obliczenia wykonywane przez ten obiekt ICorDebugEval.</span><span class="sxs-lookup"><span data-stu-id="32a06-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32a06-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="32a06-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32a06-105">Remarks</span></span>  
 <span data-ttu-id="32a06-106">Jeśli ocena jest zagnieżdżona i nie jest to najnowsza wartość, Metoda `Abort` może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="32a06-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32a06-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32a06-107">Requirements</span></span>  
 <span data-ttu-id="32a06-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32a06-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a06-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32a06-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32a06-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="32a06-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32a06-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a06-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
