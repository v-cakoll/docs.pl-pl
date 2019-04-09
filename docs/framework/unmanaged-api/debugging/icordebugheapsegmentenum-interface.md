---
title: ICorDebugHeapSegmentEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73036d1c12c46cbfda8031073a005bc9b376040e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137647"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="584f0-102">ICorDebugHeapSegmentEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="584f0-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="584f0-103">Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="584f0-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="584f0-104">Ten interfejs jest podklasą icordebugenum — interfejs.</span><span class="sxs-lookup"><span data-stu-id="584f0-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="584f0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="584f0-105">Methods</span></span>  
  
|<span data-ttu-id="584f0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="584f0-106">Method</span></span>|<span data-ttu-id="584f0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="584f0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="584f0-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="584f0-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="584f0-109">Pobiera określoną liczbę [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje na temat regionów zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="584f0-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="584f0-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="584f0-110">Remarks</span></span>  
 <span data-ttu-id="584f0-111">`ICorDebugHeapSegmentEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="584f0-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="584f0-112">`ICorDebugHeapSegmentEnum` Wystąpień jest wypełniana przy użyciu [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, wywołując [icordebugprocess5::enumerateheapregions —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="584f0-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="584f0-113">[Cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="584f0-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="584f0-114">`ICorDebugHeapSegmentEnum` Obiekt kolekcji wylicza wszystkie regiony pamięci, które może zawierać obiekty zarządzane, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w tych regionach.</span><span class="sxs-lookup"><span data-stu-id="584f0-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="584f0-115">Może zawierać informacji na temat regionów pamięci puste lub zastrzeżonych.</span><span class="sxs-lookup"><span data-stu-id="584f0-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="584f0-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="584f0-116">Requirements</span></span>  
 <span data-ttu-id="584f0-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="584f0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="584f0-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="584f0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="584f0-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="584f0-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="584f0-120">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="584f0-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="584f0-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="584f0-121">See also</span></span>

- [<span data-ttu-id="584f0-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="584f0-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
