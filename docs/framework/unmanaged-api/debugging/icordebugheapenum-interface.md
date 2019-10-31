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
ms.openlocfilehash: e8d1948a7d0ff23410ba8670628424a4067fb47d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138487"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="41c58-102">ICorDebugHeapEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="41c58-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="41c58-103">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="41c58-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="41c58-104">Ten interfejs jest podklasą interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="41c58-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41c58-105">Metody</span><span class="sxs-lookup"><span data-stu-id="41c58-105">Methods</span></span>  
  
|<span data-ttu-id="41c58-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="41c58-106">Method</span></span>|<span data-ttu-id="41c58-107">Opis</span><span class="sxs-lookup"><span data-stu-id="41c58-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41c58-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="41c58-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="41c58-109">Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , które zawierają informacje o obiektach na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="41c58-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41c58-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41c58-110">Remarks</span></span>  
 <span data-ttu-id="41c58-111">Interfejs `ICorDebugHeapEnum` implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="41c58-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="41c58-112">Wystąpienie `ICorDebugHeapEnum` jest wypełniane wystąpieniami [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) przez wywołanie metody [ICorDebugProcess5:: EnumerateHeap —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="41c58-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="41c58-113">Każde wystąpienie [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) w kolekcji reprezentuje obiekt na żywo na stercie lub obiekt, który nie jest odblokowany przez żaden obiekt, ale nie został jeszcze zebrany przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="41c58-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="41c58-114">Obiekty [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugHeapEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="41c58-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c58-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41c58-115">Requirements</span></span>  
 <span data-ttu-id="41c58-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41c58-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c58-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41c58-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41c58-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41c58-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41c58-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c58-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c58-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41c58-120">See also</span></span>

- [<span data-ttu-id="41c58-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="41c58-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
