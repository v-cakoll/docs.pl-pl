---
title: "COR_SEGMENT — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9414aa1c36ba059d9ee1101f6183dc8a669f9e6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corsegment-structure"></a><span data-ttu-id="ad60c-102">COR_SEGMENT — Struktura</span><span class="sxs-lookup"><span data-stu-id="ad60c-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="ad60c-103">Zawiera informacje na temat obszar pamięci sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="ad60c-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad60c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad60c-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="ad60c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ad60c-105">Members</span></span>  
  
|<span data-ttu-id="ad60c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ad60c-106">Member</span></span>|<span data-ttu-id="ad60c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ad60c-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="ad60c-108">Adres początkowy obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad60c-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="ad60c-109">Końcowy adres regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad60c-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="ad60c-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) element członkowski wyliczenia wskazująca generacji regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad60c-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="ad60c-111">Liczba stosu, w której znajduje się obszar pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad60c-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="ad60c-112">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="ad60c-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad60c-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad60c-113">Remarks</span></span>  
 <span data-ttu-id="ad60c-114">`COR_SEGMENTS` Struktury reprezentuje obszar pamięci sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="ad60c-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="ad60c-115">`COR_SEGMENTS`obiekty są członkami [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiektu kolekcji, która jest wypełniana przez wywołanie metody[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ad60c-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="ad60c-116">`heap` Pole jest numer procesora, co odpowiada sterty zgłaszają.</span><span class="sxs-lookup"><span data-stu-id="ad60c-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="ad60c-117">Moduły zbierające elementy bezużyteczne stacji roboczej jego wartość jest zawsze zero, ponieważ stacje robocze mają tylko jeden sterty kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad60c-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="ad60c-118">Dla modułów zbierających dane pamięci serwera jego wartość odpowiada procesora, której jest dołączona sterty.</span><span class="sxs-lookup"><span data-stu-id="ad60c-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="ad60c-119">Należy pamiętać, że może istnieć więcej lub mniej pamięci sterty, niż rzeczywista procesory z powodu szczegóły implementacji moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="ad60c-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad60c-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad60c-120">Requirements</span></span>  
 <span data-ttu-id="ad60c-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad60c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad60c-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad60c-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad60c-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad60c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad60c-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad60c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad60c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad60c-125">See Also</span></span>  
 [<span data-ttu-id="ad60c-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="ad60c-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="ad60c-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ad60c-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
