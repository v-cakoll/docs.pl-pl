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
ms.openlocfilehash: c59ddec655f3127e8dab8d8c41543f03a896cf63
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274035"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="6d5f2-102">COR_HEAPOBJECT — Struktura</span><span class="sxs-lookup"><span data-stu-id="6d5f2-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="6d5f2-103">Zawiera informacje o obiekcie na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="6d5f2-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d5f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d5f2-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="6d5f2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6d5f2-105">Members</span></span>  
  
|<span data-ttu-id="6d5f2-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6d5f2-106">Member</span></span>|<span data-ttu-id="6d5f2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6d5f2-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="6d5f2-108">Adres obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6d5f2-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="6d5f2-109">Łączny rozmiar obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="6d5f2-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="6d5f2-110">Token [COR_TYPEID](cor-typeid-structure.md) , który reprezentuje typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="6d5f2-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d5f2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d5f2-111">Remarks</span></span>  
 <span data-ttu-id="6d5f2-112">`COR_HEAPOBJECT`wystąpienia mogą być pobierane przez Wyliczenie obiektu interfejsu [ICorDebugHeapEnum](icordebugheapenum-interface.md) , który jest wypełniany przez wywołanie metody [ICorDebugProcess5:: EnumerateHeap —](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6d5f2-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="6d5f2-113">`COR_HEAPOBJECT` Wystąpienie zawiera informacje dotyczące aktywnego obiektu na zarządzanym stosie lub o obiekcie, który nie jest odblokowany przez żaden obiekt, ale nie został jeszcze zebrany przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6d5f2-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="6d5f2-114">W celu uzyskania lepszej wydajności `COR_HEAPOBJECT.address` pole `CORDB_ADDRESS` to wartość, a nie wartość interfejsu ICorDebugValue użyta w większości interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="6d5f2-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="6d5f2-115">Aby uzyskać obiekt ICorDebugValue dla danego adresu obiektu, można przekazać `CORDB_ADDRESS` wartość do metody [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6d5f2-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="6d5f2-116">W celu uzyskania lepszej wydajności `COR_HEAPOBJECT.type` pole `COR_TYPEID` to wartość, a nie wartość interfejsu ICorDebugType użyta w większości interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="6d5f2-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="6d5f2-117">Aby uzyskać obiekt ICorDebugType dla danego identyfikatora typu, można przekazać `COR_TYPEID` wartość do metody [ICorDebugProcess5:: GetTypeForTypeID —](icordebugprocess5-gettypefortypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6d5f2-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="6d5f2-118">`COR_HEAPOBJECT` Struktura zawiera interfejs com liczony z odwołaniami.</span><span class="sxs-lookup"><span data-stu-id="6d5f2-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="6d5f2-119">Jeśli pobrano `COR_HEAPOBJECT` wystąpienie z modułu wyliczającego, wywołując metodę [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) , należy następnie zwolnić odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6d5f2-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d5f2-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d5f2-120">Requirements</span></span>  
 <span data-ttu-id="6d5f2-121">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d5f2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d5f2-122">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d5f2-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d5f2-123">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d5f2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d5f2-124">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d5f2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d5f2-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d5f2-125">See also</span></span>

- [<span data-ttu-id="6d5f2-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="6d5f2-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="6d5f2-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6d5f2-127">Debugging</span></span>](index.md)
