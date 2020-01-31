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
ms.openlocfilehash: 89ce4eafa46be3e9ba7cdb06884034a521e43bca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777535"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="f977b-102">ICorDebugHeapSegmentEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="f977b-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="f977b-103">Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](cor-heapobject-structure.md) zawierających informacje o regionach pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="f977b-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f977b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f977b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f977b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f977b-105">Parameters</span></span>  
 <span data-ttu-id="f977b-106">celt</span><span class="sxs-lookup"><span data-stu-id="f977b-106">celt</span></span>  
 <span data-ttu-id="f977b-107">podczas Liczba segmentów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="f977b-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="f977b-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="f977b-108">segments</span></span>  
 <span data-ttu-id="f977b-109">określoną Tablica wskaźników, z których każdy wskazuje obiekt [COR_HEAPOBJECT](cor-heapobject-structure.md) , który zawiera informacje o regionie pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="f977b-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="f977b-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="f977b-110">pceltFetched</span></span>  
 <span data-ttu-id="f977b-111">określoną Wskaźnik do liczby obiektów [COR_HEAPOBJECT](cor-heapobject-structure.md) faktycznie zwróconych w `segments`.</span><span class="sxs-lookup"><span data-stu-id="f977b-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="f977b-112">Ta wartość może być `null`, jeśli `celt` wynosi 1.</span><span class="sxs-lookup"><span data-stu-id="f977b-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f977b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f977b-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f977b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f977b-114">Requirements</span></span>  
 <span data-ttu-id="f977b-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f977b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f977b-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f977b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f977b-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f977b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f977b-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f977b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f977b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f977b-119">See also</span></span>

- [<span data-ttu-id="f977b-120">ICorDebugHeapSegmentEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="f977b-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="f977b-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f977b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
