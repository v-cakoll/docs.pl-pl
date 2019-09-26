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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273993"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="fc51f-102">COR_TYPEID — Struktura</span><span class="sxs-lookup"><span data-stu-id="fc51f-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="fc51f-103">Zawiera identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="fc51f-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc51f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc51f-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="fc51f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fc51f-105">Members</span></span>  
  
|<span data-ttu-id="fc51f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fc51f-106">Member</span></span>|<span data-ttu-id="fc51f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fc51f-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="fc51f-108">Pierwszy token.</span><span class="sxs-lookup"><span data-stu-id="fc51f-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="fc51f-109">Drugi token.</span><span class="sxs-lookup"><span data-stu-id="fc51f-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc51f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc51f-110">Remarks</span></span>  
 <span data-ttu-id="fc51f-111">`COR_TYPEID` Struktura jest zwracana przez wiele metod debugowania, które dostarczają informacji o obiektach, które mają być zbierane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="fc51f-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="fc51f-112">Następnie można przekazać jako argument do innych metod debugowania, które zawierają dodatkowe informacje na temat tego elementu.</span><span class="sxs-lookup"><span data-stu-id="fc51f-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="fc51f-113">Na przykład przez Wyliczenie obiektu [ICorDebugHeapEnum](icordebugheapenum-interface.md) można pobrać pojedyncze obiekty [COR_HEAPOBJECT](cor-heapobject-structure.md) , które reprezentują poszczególne obiekty na stercie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="fc51f-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="fc51f-114">Następnie można przekazać `COR_TYPEID` wartość `COR_HEAPOBJECT.type` z pola do metody [ICorDebugProcess5:: GetTypeForTypeID —](icordebugprocess5-gettypefortypeid-method.md) , aby pobrać obiekt ICorDebugType, który zawiera informacje o typie obiektu.</span><span class="sxs-lookup"><span data-stu-id="fc51f-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="fc51f-115">`COR_TYPEID` Obiekt ma być nieprzezroczysty.</span><span class="sxs-lookup"><span data-stu-id="fc51f-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="fc51f-116">Nie można uzyskać dostępu do poszczególnych pól ani manipulować nimi.</span><span class="sxs-lookup"><span data-stu-id="fc51f-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="fc51f-117">Jego jedynym zastosowaniem jest jako identyfikator, który jest dostarczany jako `out` parametr w wywołaniu metody i który może z kolei być przekazywany do innych metod w celu dostarczenia dodatkowych informacji.</span><span class="sxs-lookup"><span data-stu-id="fc51f-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc51f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc51f-118">Requirements</span></span>  
 <span data-ttu-id="fc51f-119">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc51f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc51f-120">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc51f-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc51f-121">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc51f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc51f-122">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc51f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc51f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc51f-123">See also</span></span>

- [<span data-ttu-id="fc51f-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="fc51f-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="fc51f-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="fc51f-125">Debugging</span></span>](index.md)
