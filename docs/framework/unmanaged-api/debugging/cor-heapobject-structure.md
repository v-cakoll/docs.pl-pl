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
ms.openlocfilehash: 270360a8950197eca14e02a60554659e5ac7b91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099075"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="70948-102">COR_HEAPOBJECT — Struktura</span><span class="sxs-lookup"><span data-stu-id="70948-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="70948-103">Zawiera informacje o obiekcie na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="70948-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70948-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70948-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="70948-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="70948-105">Members</span></span>  
  
|<span data-ttu-id="70948-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="70948-106">Member</span></span>|<span data-ttu-id="70948-107">Opis</span><span class="sxs-lookup"><span data-stu-id="70948-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="70948-108">Adres obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="70948-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="70948-109">Łączny rozmiar obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="70948-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="70948-110">Token [COR_TYPEID](cor-typeid-structure.md) , który reprezentuje typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="70948-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70948-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70948-111">Remarks</span></span>  
 <span data-ttu-id="70948-112">wystąpienia `COR_HEAPOBJECT` mogą być pobierane przez Wyliczenie obiektu interfejsu [ICorDebugHeapEnum](icordebugheapenum-interface.md) , który jest wypełniany przez wywołanie metody [ICorDebugProcess5:: EnumerateHeap —](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="70948-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="70948-113">Wystąpienie `COR_HEAPOBJECT` zawiera informacje o obiekcie aktywnym na zarządzanym stosie lub o obiekcie, który nie jest odblokowany przez żaden obiekt, ale nie został jeszcze zebrany przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="70948-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="70948-114">W celu uzyskania lepszej wydajności pole `COR_HEAPOBJECT.address` jest wartością `CORDB_ADDRESS`, a nie wartością interfejsu ICorDebugValue używaną w większości interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="70948-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="70948-115">Aby uzyskać obiekt ICorDebugValue dla danego adresu obiektu, można przekazać wartość `CORDB_ADDRESS` do metody [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="70948-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="70948-116">W celu uzyskania lepszej wydajności pole `COR_HEAPOBJECT.type` jest wartością `COR_TYPEID`, a nie wartością interfejsu ICorDebugType używaną w większości interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="70948-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="70948-117">Aby uzyskać obiekt ICorDebugType dla danego identyfikatora typu, można przekazać wartość `COR_TYPEID` do metody [ICorDebugProcess5:: GetTypeForTypeID —](icordebugprocess5-gettypefortypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="70948-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="70948-118">Struktura `COR_HEAPOBJECT` obejmuje interfejs COM liczony z odwołaniami.</span><span class="sxs-lookup"><span data-stu-id="70948-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="70948-119">Jeśli pobierzesz wystąpienie `COR_HEAPOBJECT` z modułu wyliczającego, wywołując metodę [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) , należy następnie zwolnić odwołanie.</span><span class="sxs-lookup"><span data-stu-id="70948-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70948-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70948-120">Requirements</span></span>  
 <span data-ttu-id="70948-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70948-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70948-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="70948-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70948-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="70948-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70948-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70948-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70948-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70948-125">See also</span></span>

- [<span data-ttu-id="70948-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="70948-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="70948-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="70948-127">Debugging</span></span>](index.md)
