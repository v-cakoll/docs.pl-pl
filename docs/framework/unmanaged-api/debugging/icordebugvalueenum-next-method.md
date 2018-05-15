---
title: ICorDebugValueEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 433e387365834498203e444ed2f85889f8adde06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="2ce47-102">ICorDebugValueEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ce47-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="2ce47-103">Pobiera określoną liczbę wystąpień "ICorDebugValue" z wyliczenia, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="2ce47-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ce47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ce47-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ce47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ce47-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="2ce47-106">[in] Liczba `ICorDebugValue` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="2ce47-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="2ce47-107">[out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2ce47-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2ce47-108">[out] Wskaźnik do liczby `ICorDebugValue` wystąpienia faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="2ce47-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="2ce47-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="2ce47-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ce47-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ce47-110">Requirements</span></span>  
 <span data-ttu-id="2ce47-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ce47-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ce47-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ce47-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ce47-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ce47-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ce47-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ce47-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ce47-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ce47-115">See Also</span></span>  
    
 
