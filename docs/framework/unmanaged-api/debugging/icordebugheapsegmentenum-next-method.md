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
ms.openlocfilehash: 897fb56cacb51e98cf8f1778c3529617decb5ecb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138444"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="5a8d6-102">ICorDebugHeapSegmentEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a8d6-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="5a8d6-103">Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , które zawierają informacje o regionach pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="5a8d6-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a8d6-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a8d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a8d6-105">Parameters</span></span>  
 <span data-ttu-id="5a8d6-106">celt</span><span class="sxs-lookup"><span data-stu-id="5a8d6-106">celt</span></span>  
 <span data-ttu-id="5a8d6-107">podczas Liczba segmentów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="5a8d6-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="5a8d6-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="5a8d6-108">segments</span></span>  
 <span data-ttu-id="5a8d6-109">określoną Tablica wskaźników, z których każdy wskazuje obiekt [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , który zawiera informacje o regionie pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="5a8d6-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="5a8d6-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="5a8d6-110">pceltFetched</span></span>  
 <span data-ttu-id="5a8d6-111">określoną Wskaźnik do liczby obiektów [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) faktycznie zwróconych w `segments`.</span><span class="sxs-lookup"><span data-stu-id="5a8d6-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="5a8d6-112">Ta wartość może być `null`, jeśli `celt` wynosi 1.</span><span class="sxs-lookup"><span data-stu-id="5a8d6-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a8d6-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a8d6-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a8d6-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a8d6-114">Requirements</span></span>  
 <span data-ttu-id="5a8d6-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a8d6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a8d6-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5a8d6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a8d6-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5a8d6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a8d6-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a8d6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8d6-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a8d6-119">See also</span></span>

- [<span data-ttu-id="5a8d6-120">ICorDebugHeapSegmentEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a8d6-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="5a8d6-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5a8d6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
