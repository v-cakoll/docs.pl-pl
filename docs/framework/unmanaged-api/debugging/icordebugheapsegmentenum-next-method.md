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
ms.openlocfilehash: c9999961ec20a31cf82d5ad60104bcdd04c340d1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210179"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="1a451-102">ICorDebugHeapSegmentEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a451-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="1a451-103">Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](cor-heapobject-structure.md) zawierających informacje o regionach pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="1a451-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a451-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a451-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a451-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a451-105">Parameters</span></span>  
 <span data-ttu-id="1a451-106">celt</span><span class="sxs-lookup"><span data-stu-id="1a451-106">celt</span></span>  
 <span data-ttu-id="1a451-107">podczas Liczba segmentów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="1a451-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="1a451-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="1a451-108">segments</span></span>  
 <span data-ttu-id="1a451-109">określoną Tablica wskaźników, z których każdy wskazuje obiekt [COR_HEAPOBJECT](cor-heapobject-structure.md) , który zawiera informacje o regionie pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="1a451-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="1a451-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="1a451-110">pceltFetched</span></span>  
 <span data-ttu-id="1a451-111">określoną Wskaźnik do liczby obiektów [COR_HEAPOBJECT](cor-heapobject-structure.md) faktycznie zwróconych w `segments` .</span><span class="sxs-lookup"><span data-stu-id="1a451-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="1a451-112">Ta wartość może być równa `null` `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="1a451-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a451-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a451-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a451-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a451-114">Requirements</span></span>  
 <span data-ttu-id="1a451-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a451-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a451-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1a451-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a451-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1a451-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a451-118">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a451-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a451-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a451-119">See also</span></span>

- [<span data-ttu-id="1a451-120">ICorDebugHeapSegmentEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1a451-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="1a451-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1a451-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
