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
ms.openlocfilehash: 6e5c29952fd300da1d7fb6b87a3287b34e76f863
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716257"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="beb73-102">ICorDebugHeapSegmentEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="beb73-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="beb73-103">Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="beb73-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="beb73-104">Ten interfejs jest podklasą icordebugenum — interfejs.</span><span class="sxs-lookup"><span data-stu-id="beb73-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="beb73-105">Metody</span><span class="sxs-lookup"><span data-stu-id="beb73-105">Methods</span></span>  
  
|<span data-ttu-id="beb73-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="beb73-106">Method</span></span>|<span data-ttu-id="beb73-107">Opis</span><span class="sxs-lookup"><span data-stu-id="beb73-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="beb73-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="beb73-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="beb73-109">Pobiera określoną liczbę [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje na temat regionów zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="beb73-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="beb73-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="beb73-110">Remarks</span></span>  
 <span data-ttu-id="beb73-111">`ICorDebugHeapSegmentEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="beb73-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="beb73-112">`ICorDebugHeapSegmentEnum` Wystąpień jest wypełniana przy użyciu [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, wywołując [icordebugprocess5::enumerateheapregions —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="beb73-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="beb73-113">[Cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="beb73-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="beb73-114">`ICorDebugHeapSegmentEnum` Obiekt kolekcji wylicza wszystkie regiony pamięci, które może zawierać obiekty zarządzane, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w tych regionach.</span><span class="sxs-lookup"><span data-stu-id="beb73-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="beb73-115">Może zawierać informacji na temat regionów pamięci puste lub zastrzeżonych.</span><span class="sxs-lookup"><span data-stu-id="beb73-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beb73-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="beb73-116">Requirements</span></span>  
 <span data-ttu-id="beb73-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beb73-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beb73-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="beb73-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="beb73-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="beb73-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="beb73-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beb73-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb73-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="beb73-121">See also</span></span>
- [<span data-ttu-id="beb73-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="beb73-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
