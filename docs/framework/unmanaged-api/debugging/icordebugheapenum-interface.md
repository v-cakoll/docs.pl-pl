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
ms.openlocfilehash: 9e9f58a0bc51e8a22672df6ab9bd94009c00f9bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688083"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="db72e-102">ICorDebugHeapEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="db72e-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="db72e-103">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="db72e-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="db72e-104">Ten interfejs jest podklasą icordebugenum — interfejs.</span><span class="sxs-lookup"><span data-stu-id="db72e-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db72e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="db72e-105">Methods</span></span>  
  
|<span data-ttu-id="db72e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="db72e-106">Method</span></span>|<span data-ttu-id="db72e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="db72e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db72e-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="db72e-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="db72e-109">Pobiera określoną liczbę [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obiektów na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="db72e-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db72e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db72e-110">Remarks</span></span>  
 <span data-ttu-id="db72e-111">`ICorDebugHeapEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="db72e-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="db72e-112">`ICorDebugHeapEnum` Wystąpień jest wypełniana przy użyciu [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, wywołując [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="db72e-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="db72e-113">Każdy [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpienia w kolekcji reprezentuje obiekt na żywo na stosie albo obiekt, który nie jest ścieżką przez dowolny obiekt, ale jeszcze nie został zebrany przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="db72e-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="db72e-114">[Cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="db72e-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db72e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db72e-115">Requirements</span></span>  
 <span data-ttu-id="db72e-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db72e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db72e-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db72e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db72e-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db72e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db72e-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db72e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db72e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db72e-120">See also</span></span>
- [<span data-ttu-id="db72e-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="db72e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
