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
ms.openlocfilehash: 09394acb07b8595f99d9ecc873eb0985cdd79316
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134595"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="7aed8-102">ICorDebugValueEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="7aed8-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="7aed8-103">Pobiera określoną liczbę wystąpień "ICorDebugValue" z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="7aed8-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aed8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7aed8-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aed8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7aed8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7aed8-106">podczas Liczba wystąpień `ICorDebugValue` do pobrania.</span><span class="sxs-lookup"><span data-stu-id="7aed8-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="7aed8-107">określoną Tablica wskaźników, z których każdy wskazuje obiekt `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="7aed8-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7aed8-108">określoną Wskaźnik do liczby zwróconych wystąpień `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="7aed8-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="7aed8-109">Ta wartość może być równa null, jeśli `celt` to jeden.</span><span class="sxs-lookup"><span data-stu-id="7aed8-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aed8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7aed8-110">Requirements</span></span>  
 <span data-ttu-id="7aed8-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aed8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aed8-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7aed8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7aed8-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7aed8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aed8-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aed8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aed8-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7aed8-115">See also</span></span>
