---
title: COR_SEGMENT — Struktura
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
ms.openlocfilehash: 0370c74bde9ca5bdbd0fd03515f4b174ddd0a39a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132318"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="e2341-102">COR_SEGMENT — Struktura</span><span class="sxs-lookup"><span data-stu-id="e2341-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="e2341-103">Zawiera informacje o regionie pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="e2341-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2341-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2341-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="e2341-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e2341-105">Members</span></span>  
  
|<span data-ttu-id="e2341-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e2341-106">Member</span></span>|<span data-ttu-id="e2341-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e2341-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="e2341-108">Adres początkowy regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="e2341-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="e2341-109">Adres końcowy regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="e2341-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="e2341-110">Element członkowski wyliczenia [CorDebugGenerationTypes —](cordebuggenerationtypes-enumeration.md) wskazujący generowanie regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="e2341-110">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="e2341-111">Numer sterty, w której znajduje się region pamięci.</span><span class="sxs-lookup"><span data-stu-id="e2341-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="e2341-112">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="e2341-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2341-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2341-113">Remarks</span></span>  
 <span data-ttu-id="e2341-114">Struktura `COR_SEGMENTS` reprezentuje region pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="e2341-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="e2341-115">obiekty `COR_SEGMENTS` są elementami członkowskimi obiektu kolekcji [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) , który jest wypełniany przez wywołanie metody [ICorDebugProcess5:: EnumerateHeapRegions —](icordebugprocess5-enumerateheapregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e2341-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="e2341-116">Pole `heap` jest numerem procesora, który odpowiada zgłaszanej stercie.</span><span class="sxs-lookup"><span data-stu-id="e2341-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="e2341-117">W przypadku modułów bezużytecznych stacji roboczej jego wartość jest zawsze zerowa, ponieważ stacje robocze mają tylko jedną stertę odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="e2341-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="e2341-118">W przypadku modułów wyrzucających elementy bezużyteczne serwera jego wartość odpowiada procesorowi, do którego jest dołączona sterta.</span><span class="sxs-lookup"><span data-stu-id="e2341-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="e2341-119">Należy zauważyć, że może być więcej lub mniej sterty wyrzucania elementów bezużytecznych, ponieważ istnieją rzeczywiste procesory ze względu na szczegóły implementacji modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e2341-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2341-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2341-120">Requirements</span></span>  
 <span data-ttu-id="e2341-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2341-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2341-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e2341-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2341-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e2341-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2341-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2341-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2341-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2341-125">See also</span></span>

- [<span data-ttu-id="e2341-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="e2341-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e2341-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e2341-127">Debugging</span></span>](index.md)
