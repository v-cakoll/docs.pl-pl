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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f83d2ac9ca96145fa89b283fec42c71858097f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651626"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="bd682-102">ICorDebugGCReferenceEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bd682-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="bd682-103">Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="bd682-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd682-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bd682-104">Methods</span></span>  
  
|<span data-ttu-id="bd682-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd682-105">Method</span></span>|<span data-ttu-id="bd682-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bd682-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd682-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="bd682-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="bd682-108">Pobiera określoną liczbę [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) wystąpień, które zawierają informacje o obiektach, których będzie jesdnostką zbierającą śmieci.</span><span class="sxs-lookup"><span data-stu-id="bd682-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd682-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd682-109">Remarks</span></span>  
 <span data-ttu-id="bd682-110">`ICorDebugGCReferenceEnum` Interfejsu implementuje interfejs "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="bd682-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="bd682-111">`ICorDebugGCReferenceEnum` Wystąpień jest wypełniana przy użyciu [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) wystąpień, wywołując [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="bd682-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="bd682-112">[Cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekty mogą być wyliczane przez wywołanie metody [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="bd682-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="bd682-113">[Cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiektów kolekcji wypełnione przez tę metodę reprezentowania trzy rodzaje obiektów:</span><span class="sxs-lookup"><span data-stu-id="bd682-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="bd682-114">Obiekty z wszystkie stosy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="bd682-114">Objects from all managed stacks.</span></span> <span data-ttu-id="bd682-115">Obejmuje to odwołań na żywo w kodzie zarządzanym, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="bd682-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="bd682-116">Obiekty z tabeli dojście.</span><span class="sxs-lookup"><span data-stu-id="bd682-116">Objects from the handle table.</span></span> <span data-ttu-id="bd682-117">Obejmuje to odwołań do silnych (`HNDTYPE_STRONG` i `HNDTYPE_REFCOUNT`) i zmiennych statycznych w module.</span><span class="sxs-lookup"><span data-stu-id="bd682-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="bd682-118">Obiekty z; kolejka finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="bd682-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="bd682-119">Elementy główne obiektów; kolejka finalizatorów, aż finalizator zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="bd682-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd682-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd682-120">Requirements</span></span>  
 <span data-ttu-id="bd682-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd682-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd682-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd682-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd682-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd682-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd682-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd682-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd682-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd682-125">See also</span></span>

- [<span data-ttu-id="bd682-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bd682-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
