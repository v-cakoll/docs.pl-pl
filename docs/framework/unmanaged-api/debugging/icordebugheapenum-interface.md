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
ms.openlocfilehash: ff290cd8ad331ff109c3bbbf87638d22b9b183bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208541"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="f6629-102">ICorDebugHeapEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f6629-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="f6629-103">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="f6629-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="f6629-104">Ten interfejs jest podklasą interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="f6629-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6629-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f6629-105">Methods</span></span>  
  
|<span data-ttu-id="f6629-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f6629-106">Method</span></span>|<span data-ttu-id="f6629-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f6629-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6629-108">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="f6629-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="f6629-109">Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](cor-heapobject-structure.md) , które zawierają informacje o obiektach na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="f6629-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6629-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6629-110">Remarks</span></span>  
 <span data-ttu-id="f6629-111">`ICorDebugHeapEnum`Interfejs implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="f6629-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="f6629-112">`ICorDebugHeapEnum`Wystąpienie jest wypełniane wystąpieniami [COR_HEAPOBJECT](cor-heapobject-structure.md) , wywołując metodę [ICorDebugProcess5:: EnumerateHeap —](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f6629-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="f6629-113">Każde wystąpienie [COR_HEAPOBJECT](cor-heapobject-structure.md) w kolekcji reprezentuje obiekt na żywo na stercie lub obiekt, który nie jest odblokowany przez żaden obiekt, ale nie został jeszcze zebrany przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f6629-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="f6629-114">[COR_HEAPOBJECT](cor-heapobject-structure.md) obiektów w kolekcji można wyliczyć, wywołując metodę [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f6629-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6629-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6629-115">Requirements</span></span>  
 <span data-ttu-id="f6629-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6629-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6629-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f6629-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6629-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f6629-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6629-119">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6629-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6629-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6629-120">See also</span></span>

- [<span data-ttu-id="f6629-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f6629-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
