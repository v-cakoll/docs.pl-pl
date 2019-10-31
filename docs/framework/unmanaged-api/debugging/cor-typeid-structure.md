---
title: COR_TYPEID — Struktura
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
ms.openlocfilehash: 4f6dbe8c17bd6a91078b87a87c1055fbf4977a88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132309"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="5cc0c-102">COR_TYPEID — Struktura</span><span class="sxs-lookup"><span data-stu-id="5cc0c-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="5cc0c-103">Zawiera identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="5cc0c-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc0c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cc0c-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="5cc0c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5cc0c-105">Members</span></span>  
  
|<span data-ttu-id="5cc0c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5cc0c-106">Member</span></span>|<span data-ttu-id="5cc0c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5cc0c-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="5cc0c-108">Pierwszy token.</span><span class="sxs-lookup"><span data-stu-id="5cc0c-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="5cc0c-109">Drugi token.</span><span class="sxs-lookup"><span data-stu-id="5cc0c-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cc0c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5cc0c-110">Remarks</span></span>  
 <span data-ttu-id="5cc0c-111">Struktura `COR_TYPEID` jest zwracana przez wiele metod debugowania, które zapewniają informacje o obiektach, które mają być zbierane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="5cc0c-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="5cc0c-112">Następnie można przekazać jako argument do innych metod debugowania, które zawierają dodatkowe informacje na temat tego elementu.</span><span class="sxs-lookup"><span data-stu-id="5cc0c-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="5cc0c-113">Na przykład przez Wyliczenie obiektu [ICorDebugHeapEnum](icordebugheapenum-interface.md) można pobrać pojedyncze obiekty [COR_HEAPOBJECT](cor-heapobject-structure.md) , które reprezentują poszczególne obiekty na stercie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="5cc0c-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="5cc0c-114">Następnie można przekazać wartość `COR_TYPEID` z pola `COR_HEAPOBJECT.type` do metody [ICorDebugProcess5:: GetTypeForTypeID —](icordebugprocess5-gettypefortypeid-method.md) , aby pobrać obiekt ICorDebugType, który zawiera informacje o typie obiektu.</span><span class="sxs-lookup"><span data-stu-id="5cc0c-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="5cc0c-115">Obiekt `COR_TYPEID` ma być nieprzezroczysty.</span><span class="sxs-lookup"><span data-stu-id="5cc0c-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="5cc0c-116">Nie można uzyskać dostępu do poszczególnych pól ani manipulować nimi.</span><span class="sxs-lookup"><span data-stu-id="5cc0c-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="5cc0c-117">Jego jedynym zastosowaniem jest jako identyfikator, który jest dostarczany jako parametr `out` w wywołaniu metody i który może z kolei być przekazywany do innych metod w celu dostarczenia dodatkowych informacji.</span><span class="sxs-lookup"><span data-stu-id="5cc0c-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cc0c-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5cc0c-118">Requirements</span></span>  
 <span data-ttu-id="5cc0c-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cc0c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cc0c-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5cc0c-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cc0c-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5cc0c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cc0c-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cc0c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc0c-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cc0c-123">See also</span></span>

- [<span data-ttu-id="5cc0c-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="5cc0c-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="5cc0c-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5cc0c-125">Debugging</span></span>](index.md)
