---
title: ICorDebugGCReferenceEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: 49f89f7d36e74b1fa5921230d7dc6d271d4c0883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134634"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="a58c6-102">ICorDebugGCReferenceEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a58c6-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="a58c6-103">Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="a58c6-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a58c6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a58c6-104">Methods</span></span>  
  
|<span data-ttu-id="a58c6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a58c6-105">Method</span></span>|<span data-ttu-id="a58c6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a58c6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a58c6-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="a58c6-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="a58c6-108">Pobiera określoną liczbę wystąpień [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) , które zawierają informacje o obiektach, które będą zbierane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="a58c6-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a58c6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a58c6-109">Remarks</span></span>  
 <span data-ttu-id="a58c6-110">Interfejs `ICorDebugGCReferenceEnum` implementuje interfejs "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="a58c6-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="a58c6-111">Wystąpienie `ICorDebugGCReferenceEnum` jest wypełniane wystąpieniami [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) przez wywołanie metody [ICorDebugProcess5:: EnumerateGCReferences —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a58c6-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="a58c6-112">Obiekty [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) można wyliczyć przez wywołanie metody [ICorDebugGCReference:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a58c6-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="a58c6-113">Obiekty [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) w kolekcji wypełnione przez tę metodę reprezentują trzy rodzaje obiektów:</span><span class="sxs-lookup"><span data-stu-id="a58c6-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="a58c6-114">Obiekty ze wszystkich zarządzanych stosów.</span><span class="sxs-lookup"><span data-stu-id="a58c6-114">Objects from all managed stacks.</span></span> <span data-ttu-id="a58c6-115">Obejmuje to dynamiczne odwołania w kodzie zarządzanym oraz obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="a58c6-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="a58c6-116">Obiekty z tabeli uchwytów.</span><span class="sxs-lookup"><span data-stu-id="a58c6-116">Objects from the handle table.</span></span> <span data-ttu-id="a58c6-117">Obejmuje to silne odwołania (`HNDTYPE_STRONG` i `HNDTYPE_REFCOUNT`) oraz zmienne statyczne w module.</span><span class="sxs-lookup"><span data-stu-id="a58c6-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="a58c6-118">Obiekty z kolejki finalizatora.</span><span class="sxs-lookup"><span data-stu-id="a58c6-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="a58c6-119">Obiekty główne kolejki finalizatora do momentu uruchomienia finalizatora.</span><span class="sxs-lookup"><span data-stu-id="a58c6-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a58c6-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a58c6-120">Requirements</span></span>  
 <span data-ttu-id="a58c6-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a58c6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a58c6-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a58c6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a58c6-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a58c6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a58c6-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a58c6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a58c6-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a58c6-125">See also</span></span>

- [<span data-ttu-id="a58c6-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a58c6-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
