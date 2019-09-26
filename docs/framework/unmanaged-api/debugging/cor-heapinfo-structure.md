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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7b340a73aa9eaebca9c0d78563ae298557039b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274188"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="3d96b-102">COR_HEAPINFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="3d96b-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="3d96b-103">Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy są wyliczalne</span><span class="sxs-lookup"><span data-stu-id="3d96b-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d96b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d96b-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="3d96b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3d96b-105">Members</span></span>  
  
|<span data-ttu-id="3d96b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3d96b-106">Member</span></span>|<span data-ttu-id="3d96b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3d96b-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="3d96b-108">`true`Jeśli struktury wyrzucania elementów bezużytecznych są prawidłowe i sterta może zostać wyliczona; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="3d96b-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="3d96b-109">Rozmiar (w bajtach) wskaźników na architekturze docelowej.</span><span class="sxs-lookup"><span data-stu-id="3d96b-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="3d96b-110">Liczba sterty logicznego wyrzucania elementów bezużytecznych w procesie.</span><span class="sxs-lookup"><span data-stu-id="3d96b-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="3d96b-111">`TRUE`Jeśli włączono współbieżne (w tle) odzyskiwanie pamięci; w przeciwnym razie. `FALSE`</span><span class="sxs-lookup"><span data-stu-id="3d96b-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="3d96b-112">Element członkowski wyliczenia [CorDebugGCType —](cordebuggctype-enumeration.md) , który wskazuje, czy moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej lub na serwerze.</span><span class="sxs-lookup"><span data-stu-id="3d96b-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d96b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d96b-113">Remarks</span></span>  
 <span data-ttu-id="3d96b-114">Wystąpienie `COR_HEAPINFO` struktury jest zwracane przez wywołanie metody [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3d96b-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="3d96b-115">Przed wyliczeniem obiektów na stercie wyrzucania elementów bezużytecznych należy `areGCStructuresValid` zawsze zaznaczyć pole, aby upewnić się, że sterta jest w stanie wyliczalnym.</span><span class="sxs-lookup"><span data-stu-id="3d96b-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="3d96b-116">Aby uzyskać więcej informacji, zobacz metodę [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3d96b-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d96b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d96b-117">Requirements</span></span>  
 <span data-ttu-id="3d96b-118">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d96b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d96b-119">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d96b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d96b-120">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d96b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d96b-121">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d96b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d96b-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d96b-122">See also</span></span>

- [<span data-ttu-id="3d96b-123">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="3d96b-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="3d96b-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3d96b-124">Debugging</span></span>](index.md)
