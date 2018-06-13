---
title: ICorDebugHeapEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25f352a3a6dfae69116d6cda2497d55485b951cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417066"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="58694-102">ICorDebugHeapEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="58694-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="58694-103">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="58694-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="58694-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="58694-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58694-105">Metody</span><span class="sxs-lookup"><span data-stu-id="58694-105">Methods</span></span>  
  
|<span data-ttu-id="58694-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="58694-106">Method</span></span>|<span data-ttu-id="58694-107">Opis</span><span class="sxs-lookup"><span data-stu-id="58694-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58694-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="58694-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="58694-109">Pobiera określoną liczbę [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="58694-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58694-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58694-110">Remarks</span></span>  
 <span data-ttu-id="58694-111">`ICorDebugHeapEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="58694-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="58694-112">`ICorDebugHeapEnum` Wystąpień jest wypełniana [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień przez wywołanie metody [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="58694-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="58694-113">Każdy [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) reprezentuje wystąpienie w kolekcji na żywo obiektów na stercie lub obiekt, który nie jest ścieżką przez dowolny obiekt, ale nie ma jeszcze zbierane przez moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="58694-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="58694-114">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) mogą być wyliczane obiektów w kolekcji, wywołując [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="58694-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58694-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58694-115">Requirements</span></span>  
 <span data-ttu-id="58694-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58694-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58694-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58694-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58694-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58694-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58694-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58694-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58694-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58694-120">See Also</span></span>  
 [<span data-ttu-id="58694-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="58694-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
