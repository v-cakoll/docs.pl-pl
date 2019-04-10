---
title: CorGCReferenceType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a673c98b11fbca5f66e9e1ae61f224448c20797
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207152"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="6a22a-102">CorGCReferenceType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6a22a-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="6a22a-103">Określa źródło obiektu zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6a22a-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a22a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a22a-104">Syntax</span></span>  
  
```  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="6a22a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6a22a-105">Members</span></span>  
  
|<span data-ttu-id="6a22a-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="6a22a-106">Member name</span></span>|<span data-ttu-id="6a22a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6a22a-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="6a22a-108">Dojście do silne odwołanie z tabeli uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a22a-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="6a22a-109">Dojście do przypiętych silne odwołanie z tabeli uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a22a-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="6a22a-110">Dojście do słabe odwołanie z tabeli uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a22a-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="6a22a-111">Dojście do obiektu słabe zliczonych odwołań z tabeli uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a22a-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="6a22a-112">Dojście do obiektu zliczonych odwołań z tabeli uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a22a-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="6a22a-113">Dojście do obiektu zależnego od tabelę uchwytów obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a22a-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="6a22a-114">Asynchroniczny obiekt przypięte z tabelę uchwytów obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a22a-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="6a22a-115">Silne dojście, który utrzymuje Przybliżony rozmiar zbiorowe zamknięcia wszystkich obiektów i korzenie obiektów w czasie kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="6a22a-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="6a22a-116">Odwołanie z zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="6a22a-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="6a22a-117">Odwołanie; kolejka finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="6a22a-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="6a22a-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="6a22a-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="6a22a-119">Zwróć tabelę uchwytów tylko silne odwołania.</span><span class="sxs-lookup"><span data-stu-id="6a22a-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="6a22a-120">Ta wartość jest używana przez [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) tylko metody.</span><span class="sxs-lookup"><span data-stu-id="6a22a-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="6a22a-121">Zwróć tabelę uchwytów jedynie słabe odwołania.</span><span class="sxs-lookup"><span data-stu-id="6a22a-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="6a22a-122">Ta wartość jest używana przez [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) tylko metody.</span><span class="sxs-lookup"><span data-stu-id="6a22a-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="6a22a-123">Zwraca wszystkie odwołania z tabeli dojście.</span><span class="sxs-lookup"><span data-stu-id="6a22a-123">Return all references from the handle table.</span></span> <span data-ttu-id="6a22a-124">Ta wartość jest używana przez [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) tylko metody.</span><span class="sxs-lookup"><span data-stu-id="6a22a-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a22a-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a22a-125">Remarks</span></span>  
 <span data-ttu-id="6a22a-126">`CorGCReferenceType` Wyliczenie jest używane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6a22a-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
-   <span data-ttu-id="6a22a-127">Jako wartość `type` pole [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) struktury, oznacza to źródło odniesienia lub uchwyt.</span><span class="sxs-lookup"><span data-stu-id="6a22a-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
-   <span data-ttu-id="6a22a-128">Jako `types` argument [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) metody Określa typy dojścia do uwzględnienia w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="6a22a-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a22a-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a22a-129">Requirements</span></span>  
 <span data-ttu-id="6a22a-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a22a-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a22a-131">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a22a-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a22a-132">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a22a-132">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6a22a-133">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6a22a-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6a22a-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a22a-134">See also</span></span>

- [<span data-ttu-id="6a22a-135">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6a22a-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
