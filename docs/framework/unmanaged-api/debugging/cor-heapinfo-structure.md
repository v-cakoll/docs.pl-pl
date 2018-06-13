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
ms.openlocfilehash: 8fb1ae367c30bb038bfe25961e91f02f172f486c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405759"
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="c5396-102">COR_HEAPINFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="c5396-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="c5396-103">Ogólne informacje dotyczące odzyskiwania pamięci sterty kolekcji, także wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="c5396-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5396-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5396-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c5396-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c5396-105">Members</span></span>  
  
|<span data-ttu-id="c5396-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c5396-106">Member</span></span>|<span data-ttu-id="c5396-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c5396-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="c5396-108">`true` Jeśli odzyskiwanie kolekcji struktury są prawidłowe i mogą być wyliczane stercie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="c5396-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="c5396-109">Rozmiar w bajtach wskaźników architektury docelowej.</span><span class="sxs-lookup"><span data-stu-id="c5396-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="c5396-110">Liczba logicznych pamięci sterty w procesie.</span><span class="sxs-lookup"><span data-stu-id="c5396-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="c5396-111">`TRUE` Jeśli są one jednoczesnych pamięci (w tle) jest włączona; w przeciwnym razie `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="c5396-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="c5396-112">Członek [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) wyliczenia, która wskazuje, czy moduł zbierający elementy bezużyteczne jest uruchomiona na serwerze lub stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="c5396-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5396-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5396-113">Remarks</span></span>  
 <span data-ttu-id="c5396-114">Wystąpienie `COR_HEAPINFO` struktury jest zwracany przez wywołanie metody [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c5396-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="c5396-115">Przed wyliczania obiektów na stercie kolekcji pamięci, należy zawsze sprawdzić `areGCStructuresValid` pola, aby upewnić się, że stos jest w stanie wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="c5396-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="c5396-116">Aby uzyskać więcej informacji, zobacz [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c5396-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5396-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5396-117">Requirements</span></span>  
 <span data-ttu-id="c5396-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5396-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5396-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5396-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5396-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5396-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5396-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5396-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5396-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5396-122">See Also</span></span>  
 [<span data-ttu-id="c5396-123">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="c5396-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="c5396-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c5396-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
