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
ms.openlocfilehash: fa8c3160dc779b2475dec63be896af5283cf5346
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="287b2-102">ICorDebugGCReferenceEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="287b2-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="287b2-103">Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="287b2-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="287b2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="287b2-104">Methods</span></span>  
  
|<span data-ttu-id="287b2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="287b2-105">Method</span></span>|<span data-ttu-id="287b2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="287b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="287b2-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="287b2-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="287b2-108">Pobiera określoną liczbę [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) wystąpień, które zawierają informacje o obiektach, które mają być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="287b2-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="287b2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="287b2-109">Remarks</span></span>  
 <span data-ttu-id="287b2-110">`ICorDebugGCReferenceEnum` Interfejsu implementuje interfejs "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="287b2-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="287b2-111">`ICorDebugGCReferenceEnum` Wystąpień jest wypełniana [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) wystąpień przez wywołanie metody [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="287b2-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="287b2-112">[Cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekty mogą być wyliczane przez wywołanie metody [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="287b2-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="287b2-113">[Cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiektów z kolekcji wypełnione przez tę metodę reprezentowania trzy typy obiektów:</span><span class="sxs-lookup"><span data-stu-id="287b2-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
-   <span data-ttu-id="287b2-114">Obiekty z wszystkie zarządzane stosy.</span><span class="sxs-lookup"><span data-stu-id="287b2-114">Objects from all managed stacks.</span></span> <span data-ttu-id="287b2-115">Dotyczy to również na żywo odwołania z kodu zarządzanego, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="287b2-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="287b2-116">Obiekty z tabeli dojścia.</span><span class="sxs-lookup"><span data-stu-id="287b2-116">Objects from the handle table.</span></span> <span data-ttu-id="287b2-117">W tym silne odwołań (`HNDTYPE_STRONG` i `HNDTYPE_REFCOUNT`) i zmienne statyczne w module.</span><span class="sxs-lookup"><span data-stu-id="287b2-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="287b2-118">Obiekty w kolejce finalizatora.</span><span class="sxs-lookup"><span data-stu-id="287b2-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="287b2-119">Kolejce finalizatora katalogów głównych obiektów, do momentu finalizator zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="287b2-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="287b2-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="287b2-120">Requirements</span></span>  
 <span data-ttu-id="287b2-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="287b2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="287b2-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="287b2-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="287b2-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="287b2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="287b2-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="287b2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="287b2-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="287b2-125">See Also</span></span>  
 [<span data-ttu-id="287b2-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="287b2-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
