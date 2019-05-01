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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 682d6684b6c86485530b9e5283d843f3b2eb7e46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995998"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="0c5be-102">ICorDebugEval::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c5be-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="0c5be-103">Przerywa obliczeń, który wykonuje obecnie ten obiekt ICorDebugEval.</span><span class="sxs-lookup"><span data-stu-id="0c5be-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c5be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c5be-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0c5be-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c5be-105">Remarks</span></span>  
 <span data-ttu-id="0c5be-106">Jeśli ocena jest zagnieżdżony, a nie jest ostatnim zadaniem `Abort` metoda może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0c5be-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c5be-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c5be-107">Requirements</span></span>  
 <span data-ttu-id="0c5be-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c5be-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c5be-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c5be-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c5be-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c5be-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c5be-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c5be-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
