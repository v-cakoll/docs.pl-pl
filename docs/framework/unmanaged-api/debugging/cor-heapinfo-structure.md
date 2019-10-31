---
title: COR_HEAPINFO — Struktura
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: b6fd3682290c9752125aed7b9663c6704ade25de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132334"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="7abdb-102">COR_HEAPINFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="7abdb-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="7abdb-103">Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy są wyliczalne</span><span class="sxs-lookup"><span data-stu-id="7abdb-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7abdb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7abdb-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="7abdb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7abdb-105">Members</span></span>  
  
|<span data-ttu-id="7abdb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7abdb-106">Member</span></span>|<span data-ttu-id="7abdb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7abdb-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="7abdb-108">`true`, jeśli struktury wyrzucania elementów bezużytecznych są prawidłowe i można wyliczyć stertę; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="7abdb-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="7abdb-109">Rozmiar (w bajtach) wskaźników na architekturze docelowej.</span><span class="sxs-lookup"><span data-stu-id="7abdb-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="7abdb-110">Liczba sterty logicznego wyrzucania elementów bezużytecznych w procesie.</span><span class="sxs-lookup"><span data-stu-id="7abdb-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="7abdb-111">`TRUE`, jeśli jest włączone współbieżne wyrzucanie elementów bezużytecznych (w tle); w przeciwnym razie `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="7abdb-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="7abdb-112">Element członkowski wyliczenia [CorDebugGCType —](cordebuggctype-enumeration.md) , który wskazuje, czy moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej lub na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7abdb-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7abdb-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7abdb-113">Remarks</span></span>  
 <span data-ttu-id="7abdb-114">Wystąpienie struktury `COR_HEAPINFO` jest zwracane przez wywołanie metody [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7abdb-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="7abdb-115">Przed wyliczeniem obiektów na stercie wyrzucania elementów bezużytecznych należy zawsze sprawdzić pole `areGCStructuresValid`, aby upewnić się, że sterta jest w stanie wyliczalnym.</span><span class="sxs-lookup"><span data-stu-id="7abdb-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="7abdb-116">Aby uzyskać więcej informacji, zobacz metodę [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7abdb-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7abdb-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7abdb-117">Requirements</span></span>  
 <span data-ttu-id="7abdb-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7abdb-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7abdb-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7abdb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7abdb-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7abdb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7abdb-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7abdb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abdb-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7abdb-122">See also</span></span>

- [<span data-ttu-id="7abdb-123">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="7abdb-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="7abdb-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7abdb-124">Debugging</span></span>](index.md)
