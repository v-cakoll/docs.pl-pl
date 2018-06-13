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
ms.openlocfilehash: 13ec60999db88b9d7191a3866fcebe8098b4edee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411389"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="0a0e1-102">ICorDebugCode::GetILToNativeMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="0a0e1-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="0a0e1-103">Pobiera tablicę wystąpień "cor_debug_il_to_native_map —", które reprezentują mapowania od przesunięcia języka pośredniego (MSIL) firmy Microsoft do natywnej przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a0e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a0e1-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a0e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a0e1-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="0a0e1-106">[in] Rozmiar `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="0a0e1-107">[out] Wskaźnik do rzeczywistą liczbę zwracanych w elementów `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="0a0e1-108">[out] Tablica `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, z których każdy reprezentuje mapowanie z przesunięciem MSIL do natywnej przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="0a0e1-109">Nie ma żadnych porządkowanie tablicy zwracane elementy.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a0e1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a0e1-110">Remarks</span></span>  
 <span data-ttu-id="0a0e1-111">`GetILToNativeMapping` Metoda zwraca wyniki znaczenie tylko wtedy, gdy to wystąpienie "ICorDebugCode" reprezentuje kodu macierzystego, który był just-in-time (JIT) skompilowana z kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a0e1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a0e1-112">Requirements</span></span>  
 <span data-ttu-id="0a0e1-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a0e1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a0e1-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a0e1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a0e1-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a0e1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a0e1-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a0e1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a0e1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a0e1-117">See Also</span></span>  
 [<span data-ttu-id="0a0e1-118">ICorDebugCode, interfejs1</span><span class="sxs-lookup"><span data-stu-id="0a0e1-118">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
