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
ms.openlocfilehash: b905d3b5de39057cba384ea7bca917bc3476623f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700653"
---
# <a name="cortypeid-structure"></a><span data-ttu-id="76f29-102">COR_TYPEID — Struktura</span><span class="sxs-lookup"><span data-stu-id="76f29-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="76f29-103">Zawiera identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="76f29-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76f29-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="76f29-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="76f29-105">Members</span></span>  
  
|<span data-ttu-id="76f29-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="76f29-106">Member</span></span>|<span data-ttu-id="76f29-107">Opis</span><span class="sxs-lookup"><span data-stu-id="76f29-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="76f29-108">Pierwszy token.</span><span class="sxs-lookup"><span data-stu-id="76f29-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="76f29-109">Drugiego tokena.</span><span class="sxs-lookup"><span data-stu-id="76f29-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76f29-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76f29-110">Remarks</span></span>  
 <span data-ttu-id="76f29-111">`COR_TYPEID` Struktury jest zwracany przez szereg metod debugowania, które zawierają informacje dotyczące obiektów zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="76f29-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="76f29-112">Go może być następnie przekazywany jako argument do innych metod debugowania, które zapewniają dodatkowe informacje na temat tego elementu.</span><span class="sxs-lookup"><span data-stu-id="76f29-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="76f29-113">Na przykład, wyliczając [icordebugheapenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu, możesz pobrać poszczególne [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektami, które reprezentują poszczególne obiekty na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="76f29-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="76f29-114">Możesz następnie przekazać `COR_TYPEID` wartość z `COR_HEAPOBJECT.type` pole [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metodę, aby pobrać obiekt ICorDebugType, który zawiera informacje o typie o obiekcie.</span><span class="sxs-lookup"><span data-stu-id="76f29-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="76f29-115">A `COR_TYPEID` obiekt ma być nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="76f29-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="76f29-116">Nie należy uzyskać dostępu do ani modyfikować jego poszczególne pola.</span><span class="sxs-lookup"><span data-stu-id="76f29-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="76f29-117">Jej jedyny użycie jest jako identyfikator, który jest dostarczana jako `out` parametr w wywołaniu metody i który może z kolei można przekazać do innych metod, aby podać dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="76f29-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76f29-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76f29-118">Requirements</span></span>  
 <span data-ttu-id="76f29-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76f29-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76f29-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76f29-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76f29-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76f29-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76f29-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76f29-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f29-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76f29-123">See also</span></span>
- [<span data-ttu-id="76f29-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="76f29-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="76f29-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="76f29-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
