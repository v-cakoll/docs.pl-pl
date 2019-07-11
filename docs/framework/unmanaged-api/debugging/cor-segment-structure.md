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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eef2d75a2c8a3445c7f8666fec5be9e4d089e3cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740530"
---
# <a name="corsegment-structure"></a><span data-ttu-id="6f996-102">COR_SEGMENT — Struktura</span><span class="sxs-lookup"><span data-stu-id="6f996-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="6f996-103">Zawiera informacje o region pamięci w stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="6f996-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f996-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f996-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="6f996-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6f996-105">Members</span></span>  
  
|<span data-ttu-id="6f996-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6f996-106">Member</span></span>|<span data-ttu-id="6f996-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6f996-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="6f996-108">Adres początkowy regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f996-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="6f996-109">Końcowy adres regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f996-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="6f996-110">A [cordebuggenerationtypes —](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) składowej wyliczenia, która wskazuje Generowanie regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f996-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="6f996-111">Liczba sterty, w której znajduje się regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f996-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="6f996-112">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6f996-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f996-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f996-113">Remarks</span></span>  
 <span data-ttu-id="6f996-114">`COR_SEGMENTS` Struktury reprezentuje region pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="6f996-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="6f996-115">`COR_SEGMENTS` obiekty są członkami [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiekt kolekcji, który jest wypełniana przez wywołanie metody [icordebugprocess5::enumerateheapregions —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6f996-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="6f996-116">`heap` Pole jest numer procesora, który odnosi się do sterty zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="6f996-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="6f996-117">Na stacji roboczej wyrzucania elementów modułów zbierających dzienniki jego zawsze ma wartość zero, ponieważ stacje robocze mają tylko jeden stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f996-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="6f996-118">Dla moduły zbierające pamięci serwera jego wartość odpowiada procesora, której jest dołączona sterty.</span><span class="sxs-lookup"><span data-stu-id="6f996-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="6f996-119">Należy pamiętać, że może istnieć więcej lub mniej wyrzucania elementów bezużytecznych sterty, niż rzeczywista procesorów ze względu na szczegóły implementacji moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f996-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f996-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f996-120">Requirements</span></span>  
 <span data-ttu-id="6f996-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f996-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f996-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f996-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f996-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f996-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f996-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f996-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f996-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f996-125">See also</span></span>

- [<span data-ttu-id="6f996-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="6f996-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="6f996-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6f996-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
