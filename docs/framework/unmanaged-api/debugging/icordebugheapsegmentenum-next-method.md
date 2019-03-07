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
ms.openlocfilehash: 3c3b99936315c949fa9920c7d17dc01d9bcc53b2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485047"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="f16e5-102">ICorDebugHeapSegmentEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="f16e5-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="f16e5-103">Pobiera określoną liczbę [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="f16e5-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f16e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f16e5-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f16e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f16e5-105">Parameters</span></span>  
 <span data-ttu-id="f16e5-106">celt</span><span class="sxs-lookup"><span data-stu-id="f16e5-106">celt</span></span>  
 <span data-ttu-id="f16e5-107">[in] Liczba segmentów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="f16e5-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="f16e5-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="f16e5-108">segments</span></span>  
 <span data-ttu-id="f16e5-109">[out] Tablica wskaźników, z których każdy wskazuje [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektu, który dostarcza informacji na temat region pamięci w stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="f16e5-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="f16e5-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="f16e5-110">pceltFetched</span></span>  
 <span data-ttu-id="f16e5-111">[out] Wskaźnik do liczby [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiekty, które faktycznie są zwracane w `segments`.</span><span class="sxs-lookup"><span data-stu-id="f16e5-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="f16e5-112">Ta wartość może być `null` Jeśli `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="f16e5-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f16e5-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f16e5-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f16e5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f16e5-114">Requirements</span></span>  
 <span data-ttu-id="f16e5-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f16e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f16e5-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f16e5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f16e5-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f16e5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f16e5-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f16e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f16e5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f16e5-119">See also</span></span>
- [<span data-ttu-id="f16e5-120">ICorDebugHeapSegmentEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="f16e5-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="f16e5-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f16e5-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
