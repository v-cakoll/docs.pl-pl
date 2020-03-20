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
ms.openlocfilehash: 8a267ec7123edb73ad51f0781a78344119ec6f21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178897"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="25907-102">ICorDebugHeapSegmentEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="25907-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="25907-103">Pobiera określoną liczbę [COR_HEAPOBJECT](cor-heapobject-structure.md) wystąpień, które zawierają informacje o regionach pamięci zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="25907-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25907-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25907-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25907-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25907-105">Parameters</span></span>  
 <span data-ttu-id="25907-106">Celt</span><span class="sxs-lookup"><span data-stu-id="25907-106">celt</span></span>  
 <span data-ttu-id="25907-107">[w] Liczba segmentów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="25907-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="25907-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="25907-108">segments</span></span>  
 <span data-ttu-id="25907-109">[na zewnątrz] Tablica wskaźników, z których każdy wskazuje [na obiekt COR_HEAPOBJECT,](cor-heapobject-structure.md) który zawiera informacje o regionie pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="25907-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="25907-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="25907-110">pceltFetched</span></span>  
 <span data-ttu-id="25907-111">[na zewnątrz] Wskaźnik do liczby [obiektów COR_HEAPOBJECT](cor-heapobject-structure.md) faktycznie zwróconych `segments`w .</span><span class="sxs-lookup"><span data-stu-id="25907-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="25907-112">Ta wartość `null` może `celt` być, jeśli jest 1.</span><span class="sxs-lookup"><span data-stu-id="25907-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25907-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25907-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25907-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25907-114">Requirements</span></span>  
 <span data-ttu-id="25907-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25907-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25907-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25907-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25907-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25907-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25907-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25907-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25907-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25907-119">See also</span></span>

- [<span data-ttu-id="25907-120">ICorDebugHeapSegmentEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="25907-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="25907-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="25907-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
