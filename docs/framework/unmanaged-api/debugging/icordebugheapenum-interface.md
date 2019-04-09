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
ms.openlocfilehash: 79ef77e52e14fede9949121e7ec4575d10b820c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135853"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="8c274-102">ICorDebugHeapEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8c274-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="8c274-103">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="8c274-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="8c274-104">Ten interfejs jest podklasą icordebugenum — interfejs.</span><span class="sxs-lookup"><span data-stu-id="8c274-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c274-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8c274-105">Methods</span></span>  
  
|<span data-ttu-id="8c274-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8c274-106">Method</span></span>|<span data-ttu-id="8c274-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8c274-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c274-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="8c274-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="8c274-109">Pobiera określoną liczbę [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obiektów na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="8c274-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c274-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c274-110">Remarks</span></span>  
 <span data-ttu-id="8c274-111">`ICorDebugHeapEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="8c274-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="8c274-112">`ICorDebugHeapEnum` Wystąpień jest wypełniana przy użyciu [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, wywołując [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8c274-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="8c274-113">Każdy [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpienia w kolekcji reprezentuje obiekt na żywo na stosie albo obiekt, który nie jest ścieżką przez dowolny obiekt, ale jeszcze nie został zebrany przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c274-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="8c274-114">[Cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8c274-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c274-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c274-115">Requirements</span></span>  
 <span data-ttu-id="8c274-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c274-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c274-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c274-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c274-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c274-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8c274-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8c274-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8c274-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c274-120">See also</span></span>

- [<span data-ttu-id="8c274-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8c274-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
