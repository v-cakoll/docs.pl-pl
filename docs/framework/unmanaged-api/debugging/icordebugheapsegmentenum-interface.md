---
title: "ICorDebugHeapSegmentEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHealRegionEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum
helpviewer_keywords: ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b477631b5920401127d34b2304485bd32c3d78f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="b7710-102">ICorDebugHeapSegmentEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b7710-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="b7710-103">Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="b7710-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="b7710-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="b7710-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7710-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b7710-105">Methods</span></span>  
  
|<span data-ttu-id="b7710-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b7710-106">Method</span></span>|<span data-ttu-id="b7710-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b7710-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7710-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="b7710-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="b7710-109">Pobiera określoną liczbę [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje na temat regionów sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="b7710-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7710-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7710-110">Remarks</span></span>  
 <span data-ttu-id="b7710-111">`ICorDebugHeapSegmentEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="b7710-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="b7710-112">`ICorDebugHeapSegmentEnum` Wystąpień jest wypełniana [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień przez wywołanie metody [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b7710-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="b7710-113">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) mogą być wyliczane obiektów w kolekcji, wywołując [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b7710-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="b7710-114">`ICorDebugHeapSegmentEnum` Obiektu kolekcji wylicza wszystkie regiony pamięci, które mogą zawierać obiektów zarządzanych, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w regionach.</span><span class="sxs-lookup"><span data-stu-id="b7710-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="b7710-115">Mogą one obejmować informacji o regionach pamięci pusty lub zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="b7710-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7710-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7710-116">Requirements</span></span>  
 <span data-ttu-id="b7710-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7710-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7710-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7710-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7710-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7710-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7710-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7710-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7710-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7710-121">See Also</span></span>  
 [<span data-ttu-id="b7710-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b7710-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
