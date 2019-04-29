---
title: COR_HEAPOBJECT — Struktura
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f179b58ff8eb51e2843780d3212cf38ed7d13216
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609453"
---
# <a name="corheapobject-structure"></a><span data-ttu-id="092af-102">COR_HEAPOBJECT — Struktura</span><span class="sxs-lookup"><span data-stu-id="092af-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="092af-103">Zawiera informacje dotyczące obiektu na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="092af-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="092af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="092af-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="092af-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="092af-105">Members</span></span>  
  
|<span data-ttu-id="092af-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="092af-106">Member</span></span>|<span data-ttu-id="092af-107">Opis</span><span class="sxs-lookup"><span data-stu-id="092af-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="092af-108">Adres obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="092af-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="092af-109">Całkowity rozmiar obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="092af-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="092af-110">A [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, który reprezentuje typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="092af-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="092af-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="092af-111">Remarks</span></span>  
 <span data-ttu-id="092af-112">`COR_HEAPOBJECT` wystąpienia mogą być pobierane według wyliczania [icordebugheapenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu interfejsu, który jest wypełniana przez wywołanie metody [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="092af-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="092af-113">A `COR_HEAPOBJECT` wystąpienie zawiera informacje o obiekt na żywo w zarządzanym stosie albo o obiekt, który nie jest ścieżką przez dowolny obiekt, ale jeszcze nie został zebrany przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="092af-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="092af-114">Aby uzyskać lepszą wydajność `COR_HEAPOBJECT.address` pole jest `CORDB_ADDRESS` wartość, a nie icordebugvalue — interfejs wartość używana przez wiele interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="092af-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="092af-115">Aby uzyskać obiekt ICorDebugValue adresu podanego obiektu, można przekazać `CORDB_ADDRESS` wartość, która [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="092af-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="092af-116">Aby uzyskać lepszą wydajność `COR_HEAPOBJECT.type` pole jest `COR_TYPEID` wartość, a nie icordebugtype — interfejs wartość używana przez wiele interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="092af-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="092af-117">Aby uzyskać obiekt ICorDebugType dla Identyfikatora danego typu, możesz przekazać `COR_TYPEID` wartość, która [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="092af-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="092af-118">`COR_HEAPOBJECT` Struktura zawiera interfejsu COM zliczonych odwołań.</span><span class="sxs-lookup"><span data-stu-id="092af-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="092af-119">Jeśli pobierasz `COR_HEAPOBJECT` wystąpienia z modułu wyliczającego, wywołując [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metody, należy następnie zwolnij odwołanie.</span><span class="sxs-lookup"><span data-stu-id="092af-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="092af-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="092af-120">Requirements</span></span>  
 <span data-ttu-id="092af-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="092af-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="092af-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="092af-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="092af-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="092af-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="092af-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="092af-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="092af-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="092af-125">See also</span></span>

- [<span data-ttu-id="092af-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="092af-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="092af-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="092af-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
