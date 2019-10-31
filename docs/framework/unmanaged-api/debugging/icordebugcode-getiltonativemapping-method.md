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
ms.openlocfilehash: 011da6aacbf4c40420329952f47b1fabdfc2c1a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125632"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="04ba3-102">ICorDebugCode::GetILToNativeMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="04ba3-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="04ba3-103">Pobiera tablicę wystąpień "COR_DEBUG_IL_TO_NATIVE_MAP", które reprezentują mapowania z przesunięcia języka pośredniego firmy Microsoft (MSIL) do natywnych przesunięć.</span><span class="sxs-lookup"><span data-stu-id="04ba3-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ba3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04ba3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04ba3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04ba3-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="04ba3-106">podczas Rozmiar tablicy `map`.</span><span class="sxs-lookup"><span data-stu-id="04ba3-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="04ba3-107">określoną Wskaźnik do rzeczywistej liczby elementów zwracanych w tablicy `map`.</span><span class="sxs-lookup"><span data-stu-id="04ba3-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="04ba3-108">określoną Tablica struktur `COR_DEBUG_IL_TO_NATIVE_MAP`, z których każdy reprezentuje mapowanie z przesunięcia MSIL do natywnego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="04ba3-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="04ba3-109">Nie istnieje porządkowanie do tablicy zwracanych elementów.</span><span class="sxs-lookup"><span data-stu-id="04ba3-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04ba3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04ba3-110">Remarks</span></span>  
 <span data-ttu-id="04ba3-111">Metoda `GetILToNativeMapping` zwraca znaczące wyniki tylko wtedy, gdy to wystąpienie "ICorDebugCode" reprezentuje kod natywny, który był wcześniej (JIT) skompilowany na podstawie kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="04ba3-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ba3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04ba3-112">Requirements</span></span>  
 <span data-ttu-id="04ba3-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04ba3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04ba3-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="04ba3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04ba3-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="04ba3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04ba3-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04ba3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ba3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04ba3-117">See also</span></span>

- [<span data-ttu-id="04ba3-118">ICorDebugCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="04ba3-118">ICorDebugCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
