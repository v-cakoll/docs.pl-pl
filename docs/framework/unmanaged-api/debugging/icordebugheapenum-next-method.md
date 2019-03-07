---
title: ICorDebugHeapEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a9e423a35ba8c592bbfd806f9087a88ee251e76
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502292"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="ed373-102">ICorDebugHeapEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed373-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="ed373-103">Pobiera określoną liczbę [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obiektów na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="ed373-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed373-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed373-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed373-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed373-105">Parameters</span></span>  
 <span data-ttu-id="ed373-106">celt</span><span class="sxs-lookup"><span data-stu-id="ed373-106">celt</span></span>  
 <span data-ttu-id="ed373-107">[in] Liczba obiektów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="ed373-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="ed373-108"> — obiekty</span><span class="sxs-lookup"><span data-stu-id="ed373-108">objects</span></span>  
 <span data-ttu-id="ed373-109">[out] Tablica wskaźników, z których każdy wskazuje [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektu, który zawiera informacje dotyczące obiektu na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="ed373-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="ed373-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="ed373-110">pceltFetched</span></span>  
 <span data-ttu-id="ed373-111">[out] Wskaźnik do liczby [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiekty, które faktycznie są zwracane w `objects`.</span><span class="sxs-lookup"><span data-stu-id="ed373-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="ed373-112">Ta wartość może być `null` Jeśli `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="ed373-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed373-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed373-113">Remarks</span></span>  
 <span data-ttu-id="ed373-114">`COR_HEAPOBJECT.type` Pola jest identyfikatorem zagnieżdżonego interfejsu COM zliczonych odwołań.</span><span class="sxs-lookup"><span data-stu-id="ed373-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="ed373-115">Ta dokumentacja muszą zostać zwolnione przez obiekt wywołujący `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="ed373-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed373-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed373-116">Requirements</span></span>  
 <span data-ttu-id="ed373-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed373-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed373-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed373-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed373-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed373-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed373-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed373-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed373-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed373-121">See also</span></span>
- [<span data-ttu-id="ed373-122">ICorDebugHeapEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed373-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [<span data-ttu-id="ed373-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ed373-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
