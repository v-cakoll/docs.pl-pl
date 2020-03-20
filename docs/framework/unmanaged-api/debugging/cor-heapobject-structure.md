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
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179337"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="96717-102">COR_HEAPOBJECT — Struktura</span><span class="sxs-lookup"><span data-stu-id="96717-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="96717-103">Zawiera informacje o obiekcie na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="96717-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96717-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="96717-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="96717-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="96717-105">Members</span></span>  
  
|<span data-ttu-id="96717-106">Członek</span><span class="sxs-lookup"><span data-stu-id="96717-106">Member</span></span>|<span data-ttu-id="96717-107">Opis</span><span class="sxs-lookup"><span data-stu-id="96717-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="96717-108">Adres obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="96717-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="96717-109">Całkowity rozmiar obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="96717-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="96717-110">Token [COR_TYPEID](cor-typeid-structure.md) reprezentujący typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="96717-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96717-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96717-111">Remarks</span></span>  
 <span data-ttu-id="96717-112">`COR_HEAPOBJECT`instancje można pobrać, wyliczając obiekt interfejsu [ICorDebugHeapEnum,](icordebugheapenum-interface.md) który jest wypełniany przez [wywołanie metody ICorDebugProcess5::EnumerateHeap.](icordebugprocess5-enumerateheap-method.md)</span><span class="sxs-lookup"><span data-stu-id="96717-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="96717-113">Wystąpienie `COR_HEAPOBJECT` zawiera informacje o obiektie na żywo na zarządzanym stercie lub o obiekcie, który nie jest zakorzeniony przez żaden obiekt, ale nie został jeszcze zebrany przez moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="96717-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="96717-114">Aby uzyskać lepszą `COR_HEAPOBJECT.address` wydajność, `CORDB_ADDRESS` pole jest wartością, a nie wartością interfejsu ICorDebugValue używaną w większości interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="96717-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="96717-115">Aby uzyskać ICorDebugValue obiektu dla danego adresu obiektu, można przekazać `CORDB_ADDRESS` wartość do [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="96717-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="96717-116">Aby uzyskać lepszą `COR_HEAPOBJECT.type` wydajność, `COR_TYPEID` pole jest wartością, a nie wartością interfejsu ICorDebugType używaną w większości interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="96717-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="96717-117">Aby uzyskać obiekt ICorDebugType dla danego identyfikatora typu, można przekazać `COR_TYPEID` wartość do metody [ICorDebugProcess5::GetTypeForTypeID.](icordebugprocess5-gettypefortypeid-method.md)</span><span class="sxs-lookup"><span data-stu-id="96717-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="96717-118">Struktura `COR_HEAPOBJECT` zawiera interfejs COM z liczonych odwołaniemi.</span><span class="sxs-lookup"><span data-stu-id="96717-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="96717-119">Jeśli pobierasz `COR_HEAPOBJECT` wystąpienie z wyliczacza, wywołując [metodę ICorDebugHeapEnum::Next,](icordebugheapenum-next-method.md) należy następnie zwolnić odwołanie.</span><span class="sxs-lookup"><span data-stu-id="96717-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96717-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96717-120">Requirements</span></span>  
 <span data-ttu-id="96717-121">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96717-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96717-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96717-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96717-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96717-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96717-124">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96717-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96717-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96717-125">See also</span></span>

- [<span data-ttu-id="96717-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="96717-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="96717-127">Debugging</span><span class="sxs-lookup"><span data-stu-id="96717-127">Debugging</span></span>](index.md)
