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
ms.openlocfilehash: a5c743064b8ca645cf45d02b8800c88187bf4c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179286"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="3a480-102">COR_SEGMENT — Struktura</span><span class="sxs-lookup"><span data-stu-id="3a480-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="3a480-103">Zawiera informacje o regionie pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="3a480-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a480-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a480-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;
    CORDB_ADDRESS end;
    CorDebugGenerationTypes gen;
    ULONG heap;
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="3a480-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3a480-105">Members</span></span>  
  
|<span data-ttu-id="3a480-106">Członek</span><span class="sxs-lookup"><span data-stu-id="3a480-106">Member</span></span>|<span data-ttu-id="3a480-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3a480-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="3a480-108">Adres początkowy regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="3a480-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="3a480-109">Adres końcowy regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="3a480-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="3a480-110">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) element członkowski wyliczenia, który wskazuje generowanie regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="3a480-110">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="3a480-111">Numer sterty, w którym znajduje się region pamięci.</span><span class="sxs-lookup"><span data-stu-id="3a480-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="3a480-112">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="3a480-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a480-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a480-113">Remarks</span></span>  
 <span data-ttu-id="3a480-114">Struktura `COR_SEGMENTS` reprezentuje region pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="3a480-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="3a480-115">`COR_SEGMENTS`obiekty są członkami obiektu kolekcji [ICorDebugHeapRegionEnum,](icordebugheapsegmentenum-interface.md) który jest wypełniany przez [wywołanie metody ICorDebugProcess5::EnumerateHeapRegions.](icordebugprocess5-enumerateheapregions-method.md)</span><span class="sxs-lookup"><span data-stu-id="3a480-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="3a480-116">To `heap` pole jest numerem procesora, który odpowiada zgłoszonemu stercie.</span><span class="sxs-lookup"><span data-stu-id="3a480-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="3a480-117">Dla modułów zbierających elementy bezużyteczne stacji roboczej jego wartość jest zawsze równa zero, ponieważ stacje robocze mają tylko jedną stertę wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="3a480-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="3a480-118">W przypadku modułów zbierających elementy bezużyteczne serwera jego wartość odpowiada procesorowi, do którym jest dołączona sterta.</span><span class="sxs-lookup"><span data-stu-id="3a480-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="3a480-119">Należy zauważyć, że może być więcej lub mniej sterty wyrzucania elementów bezużytecznych niż istnieją rzeczywiste procesory ze względu na szczegóły implementacji modułu zbierającego elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="3a480-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a480-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a480-120">Requirements</span></span>  
 <span data-ttu-id="3a480-121">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a480-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a480-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a480-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a480-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a480-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a480-124">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a480-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a480-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a480-125">See also</span></span>

- [<span data-ttu-id="3a480-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="3a480-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="3a480-127">Debugging</span><span class="sxs-lookup"><span data-stu-id="3a480-127">Debugging</span></span>](index.md)
