---
title: ICorDebugCode::GetILToNativeMapping — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c9e2bb9ef97326c3d11553b6cabd0de0fd6e495
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747508"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="d124d-102">ICorDebugCode::GetILToNativeMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="d124d-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="d124d-103">Pobiera tablicę wystąpień "cor_debug_il_to_native_map —", które reprezentują mapowań od przesunięcia języka pośredniego (MSIL) firmy Microsoft do natywnych przesunięć.</span><span class="sxs-lookup"><span data-stu-id="d124d-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d124d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d124d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d124d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d124d-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="d124d-106">[in] Rozmiar `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d124d-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="d124d-107">[out] Wskaźnik do rzeczywistej liczby elementów zwracanych w `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d124d-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="d124d-108">[out] Tablica `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z których każdy reprezentuje mapowanie z przesunięcia MSIL na przesunięciu macierzystym.</span><span class="sxs-lookup"><span data-stu-id="d124d-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="d124d-109">Nie ma żadnych kolejności do tablicy elementów zwracanych.</span><span class="sxs-lookup"><span data-stu-id="d124d-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d124d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d124d-110">Remarks</span></span>  
 <span data-ttu-id="d124d-111">`GetILToNativeMapping` Metoda zwraca znaczące wyniki tylko wtedy, gdy to wystąpienie "ICorDebugCode" reprezentuje kodu macierzystego, który był just-in-time (JIT) skompilowane z kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="d124d-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d124d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d124d-112">Requirements</span></span>  
 <span data-ttu-id="d124d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d124d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d124d-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d124d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d124d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d124d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d124d-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d124d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d124d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d124d-117">See also</span></span>

- [<span data-ttu-id="d124d-118">Icordebugcode — interfejs</span><span class="sxs-lookup"><span data-stu-id="d124d-118">ICorDebugCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
