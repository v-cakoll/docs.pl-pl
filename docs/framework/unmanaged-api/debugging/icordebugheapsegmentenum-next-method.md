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
ms.openlocfilehash: 3d4e44eefaf99a40b9c4f1c45e7dd81192f8b607
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904276"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="c2ace-102">ICorDebugHeapSegmentEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2ace-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="c2ace-103">Pobiera określoną liczbę wystąpień [COR_SEGMENT](cor-segment-structure.md) zawierających informacje o regionach pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="c2ace-103">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2ace-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2ace-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2ace-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2ace-105">Parameters</span></span>  
 <span data-ttu-id="c2ace-106">celt</span><span class="sxs-lookup"><span data-stu-id="c2ace-106">celt</span></span>  
 <span data-ttu-id="c2ace-107">podczas Liczba segmentów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="c2ace-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="c2ace-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="c2ace-108">segments</span></span>  
 <span data-ttu-id="c2ace-109">określoną Tablica wskaźników, z których każdy wskazuje obiekt [COR_SEGMENT](cor-segment-structure.md) , który zawiera informacje o regionie pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="c2ace-109">[out] An array of pointers, each of which points to a [COR_SEGMENT](cor-segment-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="c2ace-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="c2ace-110">pceltFetched</span></span>  
 <span data-ttu-id="c2ace-111">określoną Wskaźnik do liczby obiektów [COR_SEGMENT](cor-segment-structure.md) faktycznie zwróconych w `segments` .</span><span class="sxs-lookup"><span data-stu-id="c2ace-111">[out] A pointer to the number of [COR_SEGMENT](cor-segment-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="c2ace-112">Ta wartość może być równa `null` `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="c2ace-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2ace-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2ace-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2ace-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2ace-114">Requirements</span></span>  
 <span data-ttu-id="c2ace-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2ace-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2ace-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c2ace-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2ace-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2ace-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2ace-118">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2ace-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ace-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2ace-119">See also</span></span>

- [<span data-ttu-id="c2ace-120">ICorDebugHeapSegmentEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c2ace-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="c2ace-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c2ace-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
