---
title: "ICorDebugHeapEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapEnum
helpviewer_keywords: ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbc97aec2fc9758df17767188c6b4d044b5016fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="fee8f-102">ICorDebugHeapEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fee8f-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="fee8f-103">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="fee8f-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="fee8f-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="fee8f-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fee8f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fee8f-105">Methods</span></span>  
  
|<span data-ttu-id="fee8f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fee8f-106">Method</span></span>|<span data-ttu-id="fee8f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fee8f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fee8f-108">Next — metoda</span><span class="sxs-lookup"><span data-stu-id="fee8f-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="fee8f-109">Pobiera określoną liczbę [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="fee8f-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fee8f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fee8f-110">Remarks</span></span>  
 <span data-ttu-id="fee8f-111">`ICorDebugHeapEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="fee8f-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="fee8f-112">`ICorDebugHeapEnum` Wystąpień jest wypełniana [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień przez wywołanie metody [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fee8f-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="fee8f-113">Każdy [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) reprezentuje wystąpienie w kolekcji na żywo obiektów na stercie lub obiekt, który nie jest ścieżką przez dowolny obiekt, ale nie ma jeszcze zbierane przez moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="fee8f-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="fee8f-114">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) mogą być wyliczane obiektów w kolekcji, wywołując [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fee8f-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee8f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fee8f-115">Requirements</span></span>  
 <span data-ttu-id="fee8f-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fee8f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee8f-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fee8f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fee8f-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fee8f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fee8f-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee8f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee8f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fee8f-120">See Also</span></span>  
 [<span data-ttu-id="fee8f-121">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="fee8f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
