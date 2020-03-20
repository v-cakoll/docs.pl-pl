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
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179310"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="56fdd-102">COR_HEAPINFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="56fdd-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="56fdd-103">Zawiera ogólne informacje na temat sterty wyrzucania elementów bezużytecznych, w tym, czy jest wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="56fdd-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fdd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56fdd-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="56fdd-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="56fdd-105">Members</span></span>  
  
|<span data-ttu-id="56fdd-106">Członek</span><span class="sxs-lookup"><span data-stu-id="56fdd-106">Member</span></span>|<span data-ttu-id="56fdd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="56fdd-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="56fdd-108">`true`jeśli struktury wyrzucania elementów bezużytecznych są prawidłowe i sterty mogą być wyliczone; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="56fdd-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="56fdd-109">Rozmiar w bajtach wskaźników na architekturze docelowej.</span><span class="sxs-lookup"><span data-stu-id="56fdd-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="56fdd-110">Liczba logicznych sterty wyrzucania elementów bezużytecznych w procesie.</span><span class="sxs-lookup"><span data-stu-id="56fdd-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="56fdd-111">`TRUE`jeśli równoczesne (tło) wyrzucanie elementów bezużytecznych jest włączone; w `FALSE`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="56fdd-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="56fdd-112">Członek wyliczenia [CorDebugGCType,](cordebuggctype-enumeration.md) który wskazuje, czy moduł zbierający elementy bezużyteczne jest uruchomiony na stacji roboczej lub serwera.</span><span class="sxs-lookup"><span data-stu-id="56fdd-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56fdd-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56fdd-113">Remarks</span></span>  
 <span data-ttu-id="56fdd-114">Wystąpienie `COR_HEAPINFO` struktury jest zwracany przez wywołanie [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="56fdd-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="56fdd-115">Przed wyliczeniem obiektów na stercie wyrzucania `areGCStructuresValid` elementów bezużytecznych należy zawsze sprawdzić pole, aby upewnić się, że sterty jest w stanie wyliczalnym.</span><span class="sxs-lookup"><span data-stu-id="56fdd-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="56fdd-116">Aby uzyskać więcej informacji, zobacz [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="56fdd-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56fdd-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56fdd-117">Requirements</span></span>  
 <span data-ttu-id="56fdd-118">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56fdd-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fdd-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56fdd-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56fdd-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56fdd-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56fdd-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56fdd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fdd-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56fdd-122">See also</span></span>

- [<span data-ttu-id="56fdd-123">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="56fdd-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="56fdd-124">Debugging</span><span class="sxs-lookup"><span data-stu-id="56fdd-124">Debugging</span></span>](index.md)
