---
title: "ICorDebugValueEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a497488c06dd387f65182318c22f3189dfd7725
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="c07f5-102">ICorDebugValueEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="c07f5-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="c07f5-103">Pobiera określoną liczbę wystąpień "ICorDebugValue" z wyliczenia, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="c07f5-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c07f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c07f5-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c07f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c07f5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c07f5-106">[in] Liczba `ICorDebugValue` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="c07f5-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="c07f5-107">[out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c07f5-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c07f5-108">[out] Wskaźnik do liczby `ICorDebugValue` wystąpienia faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="c07f5-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="c07f5-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="c07f5-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c07f5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c07f5-110">Requirements</span></span>  
 <span data-ttu-id="c07f5-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c07f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c07f5-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c07f5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c07f5-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c07f5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c07f5-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c07f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07f5-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c07f5-115">See Also</span></span>  
    
 
