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
ms.openlocfilehash: bed2871c46712490bc4b0520fa1ab8023dbab5cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794424"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="0546f-102">ICorDebugHeapEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0546f-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="0546f-103">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="0546f-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="0546f-104">Ten interfejs jest podklasą interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="0546f-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0546f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0546f-105">Methods</span></span>  
  
|<span data-ttu-id="0546f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0546f-106">Method</span></span>|<span data-ttu-id="0546f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0546f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0546f-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="0546f-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="0546f-109">Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](cor-heapobject-structure.md) , które zawierają informacje o obiektach na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="0546f-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0546f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0546f-110">Remarks</span></span>  
 <span data-ttu-id="0546f-111">Interfejs `ICorDebugHeapEnum` implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="0546f-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="0546f-112">Wystąpienie `ICorDebugHeapEnum` jest wypełniane wystąpieniami [COR_HEAPOBJECT](cor-heapobject-structure.md) przez wywołanie metody [ICorDebugProcess5:: EnumerateHeap —](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0546f-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="0546f-113">Każde wystąpienie [COR_HEAPOBJECT](cor-heapobject-structure.md) w kolekcji reprezentuje obiekt na żywo na stercie lub obiekt, który nie jest odblokowany przez żaden obiekt, ale nie został jeszcze zebrany przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0546f-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="0546f-114">[COR_HEAPOBJECT](cor-heapobject-structure.md) obiektów w kolekcji można wyliczyć, wywołując metodę [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0546f-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0546f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0546f-115">Requirements</span></span>  
 <span data-ttu-id="0546f-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0546f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0546f-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0546f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0546f-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0546f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0546f-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0546f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0546f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0546f-120">See also</span></span>

- [<span data-ttu-id="0546f-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0546f-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
