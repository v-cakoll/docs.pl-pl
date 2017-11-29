---
title: "COR_SEGMENT — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_SEGMENT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_SEGMENT
helpviewer_keywords: COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fc7a749f92149d7f0f5725aec6d90d72e0582c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corsegment-structure"></a><span data-ttu-id="f2eeb-102">COR_SEGMENT — Struktura</span><span class="sxs-lookup"><span data-stu-id="f2eeb-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="f2eeb-103">Zawiera informacje na temat obszar pamięci sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2eeb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2eeb-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="f2eeb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f2eeb-105">Members</span></span>  
  
|<span data-ttu-id="f2eeb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f2eeb-106">Member</span></span>|<span data-ttu-id="f2eeb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f2eeb-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="f2eeb-108">Adres początkowy obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="f2eeb-109">Końcowy adres regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="f2eeb-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) element członkowski wyliczenia wskazująca generacji regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="f2eeb-111">Liczba stosu, w której znajduje się obszar pamięci.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="f2eeb-112">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2eeb-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2eeb-113">Remarks</span></span>  
 <span data-ttu-id="f2eeb-114">`COR_SEGMENTS` Struktury reprezentuje obszar pamięci sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="f2eeb-115">`COR_SEGMENTS`obiekty są członkami [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiektu kolekcji, która jest wypełniana przez wywołanie metody[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="f2eeb-116">`heap` Pole jest numer procesora, co odpowiada sterty zgłaszają.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="f2eeb-117">Moduły zbierające elementy bezużyteczne stacji roboczej jego wartość jest zawsze zero, ponieważ stacje robocze mają tylko jeden sterty kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="f2eeb-118">Dla modułów zbierających dane pamięci serwera jego wartość odpowiada procesora, której jest dołączona sterty.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="f2eeb-119">Należy pamiętać, że może istnieć więcej lub mniej pamięci sterty, niż rzeczywista procesory z powodu szczegóły implementacji moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2eeb-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2eeb-120">Requirements</span></span>  
 <span data-ttu-id="f2eeb-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2eeb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2eeb-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2eeb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2eeb-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2eeb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2eeb-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2eeb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2eeb-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2eeb-125">See Also</span></span>  
 [<span data-ttu-id="f2eeb-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="f2eeb-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="f2eeb-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f2eeb-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
