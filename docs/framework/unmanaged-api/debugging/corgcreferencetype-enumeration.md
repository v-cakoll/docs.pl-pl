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
ms.openlocfilehash: d156f103c3812c91da380e722a1c6c95d621df4c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860919"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="b2917-102">CorGCReferenceType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b2917-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="b2917-103">Określa źródło obiektu, które ma zostać pobrane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="b2917-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2917-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2917-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="b2917-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b2917-105">Members</span></span>  
  
|<span data-ttu-id="b2917-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="b2917-106">Member name</span></span>|<span data-ttu-id="b2917-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b2917-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="b2917-108">Dojście do silnego odwołania z tabeli uchwytów obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2917-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="b2917-109">Dojście do przypiętego silnego odwołania z tabeli uchwytów obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2917-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="b2917-110">Dojście do słabego odwołania z tabeli uchwytów obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2917-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="b2917-111">Dojście do słabego odwołującego się obiektu z tabeli uchwytów obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2917-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="b2917-112">Dojście do obiektu zliczanego odwołań z tabeli uchwytów obiektu.</span><span class="sxs-lookup"><span data-stu-id="b2917-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="b2917-113">Dojście do obiektu zależnego z tabeli uchwytów obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2917-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="b2917-114">Asynchroniczny obiekt przypięty z tabeli uchwytów obiektu.</span><span class="sxs-lookup"><span data-stu-id="b2917-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="b2917-115">Silne dojście, które utrzymuje przybliżony rozmiar całego rozłącznego zamykania wszystkich obiektów i katalogów głównych obiektów w czasie odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="b2917-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="b2917-116">Odwołanie z zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="b2917-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="b2917-117">Odwołanie z kolejki finalizatora.</span><span class="sxs-lookup"><span data-stu-id="b2917-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="b2917-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="b2917-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="b2917-119">Zwróć tylko silne odwołania z tabeli uchwytów.</span><span class="sxs-lookup"><span data-stu-id="b2917-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="b2917-120">Ta wartość jest używana tylko przez metodę [ICorDebugProcess5:: EnumerateHandles —](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b2917-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="b2917-121">Zwróć tylko słabe odwołania z tabeli dojścia.</span><span class="sxs-lookup"><span data-stu-id="b2917-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="b2917-122">Ta wartość jest używana tylko przez metodę [ICorDebugProcess5:: EnumerateHandles —](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b2917-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="b2917-123">Zwróć wszystkie odwołania z tabeli uchwytów.</span><span class="sxs-lookup"><span data-stu-id="b2917-123">Return all references from the handle table.</span></span> <span data-ttu-id="b2917-124">Ta wartość jest używana tylko przez metodę [ICorDebugProcess5:: EnumerateHandles —](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b2917-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2917-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2917-125">Remarks</span></span>  
 <span data-ttu-id="b2917-126">`CorGCReferenceType` Wyliczenie jest używane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b2917-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="b2917-127">Jako wartość `type` pola struktury [COR_GC_REFERENCE](cor-gc-reference-structure.md) wskazuje Źródło odwołania lub dojścia.</span><span class="sxs-lookup"><span data-stu-id="b2917-127">As the value of the `type` field of the [COR_GC_REFERENCE](cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="b2917-128">Jako `types` argument metody [ICorDebugProcess5:: EnumerateHandles —](icordebugprocess5-enumeratehandles-method.md) określa typy dojść do uwzględnienia w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="b2917-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2917-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2917-129">Requirements</span></span>  
 <span data-ttu-id="b2917-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2917-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2917-131">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2917-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2917-132">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b2917-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2917-133">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2917-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2917-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2917-134">See also</span></span>

- [<span data-ttu-id="b2917-135">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b2917-135">Debugging Enumerations</span></span>](debugging-enumerations.md)
