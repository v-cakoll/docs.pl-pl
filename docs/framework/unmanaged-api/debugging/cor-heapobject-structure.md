---
title: "COR_HEAPOBJECT — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_HEAPOBJECT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_HEAPOBJECT
helpviewer_keywords: COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bcd971853707349bf0d60459cb46b0fea1e8a97b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corheapobject-structure"></a><span data-ttu-id="19ec5-102">COR_HEAPOBJECT — Struktura</span><span class="sxs-lookup"><span data-stu-id="19ec5-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="19ec5-103">Zawiera informacje dotyczące obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="19ec5-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19ec5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19ec5-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="19ec5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="19ec5-105">Members</span></span>  
  
|<span data-ttu-id="19ec5-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="19ec5-106">Member</span></span>|<span data-ttu-id="19ec5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="19ec5-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="19ec5-108">Adres obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="19ec5-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="19ec5-109">Całkowity rozmiar obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="19ec5-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="19ec5-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, który reprezentuje typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="19ec5-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19ec5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19ec5-111">Remarks</span></span>  
 <span data-ttu-id="19ec5-112">`COR_HEAPOBJECT`wystąpienia mogą zostać pobrane przez wyliczania [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu interfejsu, który jest wypełniana przez wywołanie metody [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="19ec5-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="19ec5-113">A `COR_HEAPOBJECT` wystąpienia zawiera informacje dotyczące obiektu na żywo na stercie zarządzanej lub o obiekt, który nie jest ścieżką przez dowolny obiekt, ale nie ma jeszcze zbierane przez moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="19ec5-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="19ec5-114">W celu poprawy wydajności `COR_HEAPOBJECT.address` pole jest `CORDB_ADDRESS` wartość zamiast ICorDebugValue interfejsu wartość używana w bardzo interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="19ec5-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="19ec5-115">Aby uzyskać obiekt ICorDebugValue dla danego obiektu adresu, można przekazać `CORDB_ADDRESS` do wartości [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="19ec5-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="19ec5-116">W celu poprawy wydajności `COR_HEAPOBJECT.type` pole jest `COR_TYPEID` wartość zamiast ICorDebugType interfejsu wartość używana w bardzo interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="19ec5-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="19ec5-117">Aby uzyskać obiekt ICorDebugType o identyfikatorze danego typu, można przekazać `COR_TYPEID` do wartości [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="19ec5-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="19ec5-118">`COR_HEAPOBJECT` Struktura zawiera interfejsu COM zliczane odwołania.</span><span class="sxs-lookup"><span data-stu-id="19ec5-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="19ec5-119">Po pobraniu `COR_HEAPOBJECT` wystąpienia z modułu wyliczającego, wywołując [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metody, należy następnie zwolnij odwołanie.</span><span class="sxs-lookup"><span data-stu-id="19ec5-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19ec5-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19ec5-120">Requirements</span></span>  
 <span data-ttu-id="19ec5-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19ec5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19ec5-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19ec5-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19ec5-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19ec5-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19ec5-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19ec5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19ec5-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19ec5-125">See Also</span></span>  
 [<span data-ttu-id="19ec5-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="19ec5-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="19ec5-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="19ec5-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
