---
title: ICorDebugHeapSegmentEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b63646b54b73c30abf0ddb9a06a982f1364ef87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="1ea2e-102">ICorDebugHeapSegmentEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ea2e-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="1ea2e-103">Pobiera określoną liczbę [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje o pamięci sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="1ea2e-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ea2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ea2e-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ea2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ea2e-105">Parameters</span></span>  
 <span data-ttu-id="1ea2e-106">celt</span><span class="sxs-lookup"><span data-stu-id="1ea2e-106">celt</span></span>  
 <span data-ttu-id="1ea2e-107">[in] Liczba segmentów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="1ea2e-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="1ea2e-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="1ea2e-108">segments</span></span>  
 <span data-ttu-id="1ea2e-109">[out] Tablicy wskaźników, z których każdy wskazuje [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektu, który zawiera informacje o obszar pamięci sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="1ea2e-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="1ea2e-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="1ea2e-110">pceltFetched</span></span>  
 <span data-ttu-id="1ea2e-111">[out] Wskaźnik do liczby [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiekty zwrócone faktycznie w `segments`.</span><span class="sxs-lookup"><span data-stu-id="1ea2e-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="1ea2e-112">Ta wartość może być `null` Jeśli `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="1ea2e-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ea2e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ea2e-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ea2e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ea2e-114">Requirements</span></span>  
 <span data-ttu-id="1ea2e-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ea2e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ea2e-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ea2e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ea2e-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ea2e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ea2e-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ea2e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea2e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ea2e-119">See Also</span></span>  
 [<span data-ttu-id="1ea2e-120">ICorDebugHeapSegmentEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ea2e-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 [<span data-ttu-id="1ea2e-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1ea2e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
