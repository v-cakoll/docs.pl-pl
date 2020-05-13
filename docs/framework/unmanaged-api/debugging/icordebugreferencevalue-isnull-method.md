---
title: ICorDebugReferenceValue::IsNull — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: e8b778c0880040f5ffd639a445fd5663ce493219
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379082"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="9daff-102">ICorDebugReferenceValue::IsNull — Metoda</span><span class="sxs-lookup"><span data-stu-id="9daff-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="9daff-103">Pobiera wartość wskazującą, czy ta ICorDebugReferenceValue jest wartością null, w której przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.</span><span class="sxs-lookup"><span data-stu-id="9daff-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9daff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9daff-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9daff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9daff-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="9daff-106">określoną Wskaźnik do wartości logicznej, która jest, `true` Jeśli ten `ICorDebugReferenceValue` obiekt ma wartość null; w przeciwnym razie `pbNull` jest `false` .</span><span class="sxs-lookup"><span data-stu-id="9daff-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9daff-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9daff-107">Requirements</span></span>  
 <span data-ttu-id="9daff-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9daff-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9daff-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9daff-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9daff-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9daff-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9daff-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9daff-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
