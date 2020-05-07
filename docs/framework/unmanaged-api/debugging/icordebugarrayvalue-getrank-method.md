---
title: ICorDebugArrayValue::GetRank — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type:
- apiref
ms.openlocfilehash: e6401731844f2ce7a1d9fec1c94019f763870fe7
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894991"
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="c22d2-102">ICorDebugArrayValue::GetRank — Metoda</span><span class="sxs-lookup"><span data-stu-id="c22d2-102">ICorDebugArrayValue::GetRank Method</span></span>
<span data-ttu-id="c22d2-103">Pobiera liczbę wymiarów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="c22d2-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c22d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c22d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c22d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c22d2-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="c22d2-106">określoną Wskaźnik do liczby wymiarów w tym `ICorDebugArrayValue` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="c22d2-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c22d2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c22d2-107">Requirements</span></span>  
 <span data-ttu-id="c22d2-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c22d2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c22d2-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c22d2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c22d2-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c22d2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c22d2-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c22d2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
