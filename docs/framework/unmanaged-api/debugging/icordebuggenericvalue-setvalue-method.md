---
title: ICorDebugGenericValue::SetValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b6907cdf78fc70c75ddd711cd8593427857b172
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756890"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="33eb3-102">ICorDebugGenericValue::SetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="33eb3-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="33eb3-103">Kopiuje nowej wartości z określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="33eb3-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33eb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33eb3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33eb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33eb3-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="33eb3-106">[in] Wskaźnik do buforu z którego można skopiować wartości.</span><span class="sxs-lookup"><span data-stu-id="33eb3-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33eb3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33eb3-107">Remarks</span></span>  
 <span data-ttu-id="33eb3-108">Dla typów odwołań wartość jest odwołanie, nie element.</span><span class="sxs-lookup"><span data-stu-id="33eb3-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33eb3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33eb3-109">Requirements</span></span>  
 <span data-ttu-id="33eb3-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33eb3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33eb3-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33eb3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33eb3-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33eb3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33eb3-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33eb3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
