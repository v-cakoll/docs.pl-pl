---
title: "ICorDebugHeapEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9869542b04b26fdf343b4112c2f84a26a3061c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="159c4-102">ICorDebugHeapEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="159c4-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="159c4-103">Pobiera określoną liczbę [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="159c4-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="159c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="159c4-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="159c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="159c4-105">Parameters</span></span>  
 <span data-ttu-id="159c4-106">celt</span><span class="sxs-lookup"><span data-stu-id="159c4-106">celt</span></span>  
 <span data-ttu-id="159c4-107">[in] Liczba obiektów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="159c4-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="159c4-108">— obiekty</span><span class="sxs-lookup"><span data-stu-id="159c4-108">objects</span></span>  
 <span data-ttu-id="159c4-109">[out] Tablicy wskaźników, z których każdy wskazuje [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektu, który zawiera informacje o obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="159c4-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="159c4-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="159c4-110">pceltFetched</span></span>  
 <span data-ttu-id="159c4-111">[out] Wskaźnik do liczby [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiekty zwrócone faktycznie w `objects`.</span><span class="sxs-lookup"><span data-stu-id="159c4-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="159c4-112">Ta wartość może być `null` Jeśli `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="159c4-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="159c4-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="159c4-113">Remarks</span></span>  
 <span data-ttu-id="159c4-114">`COR_HEAPOBJECT.type` Pole jest identyfikatorem zagnieżdżonego interfejsu COM zliczane odwołania.</span><span class="sxs-lookup"><span data-stu-id="159c4-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="159c4-115">To odwołanie musi zostać zwolniona przez obiekt wywołujący `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="159c4-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="159c4-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="159c4-116">Requirements</span></span>  
 <span data-ttu-id="159c4-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="159c4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="159c4-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="159c4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="159c4-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="159c4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="159c4-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="159c4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="159c4-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="159c4-121">See Also</span></span>  
 [<span data-ttu-id="159c4-122">ICorDebugHeapEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="159c4-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 [<span data-ttu-id="159c4-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="159c4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
