---
title: "COR_TYPEID — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPEID
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPEID
helpviewer_keywords: COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 795dea77ac8dac1e1d22574c23f1e1c13344a71a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cortypeid-structure"></a><span data-ttu-id="b6607-102">COR_TYPEID — Struktura</span><span class="sxs-lookup"><span data-stu-id="b6607-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="b6607-103">Zawiera identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="b6607-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6607-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6607-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="b6607-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b6607-105">Members</span></span>  
  
|<span data-ttu-id="b6607-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b6607-106">Member</span></span>|<span data-ttu-id="b6607-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b6607-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="b6607-108">Pierwszy token.</span><span class="sxs-lookup"><span data-stu-id="b6607-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="b6607-109">Drugiego tokena.</span><span class="sxs-lookup"><span data-stu-id="b6607-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6607-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6607-110">Remarks</span></span>  
 <span data-ttu-id="b6607-111">`COR_TYPEID` Struktury jest zwracany przez liczbę metod debugowania, które zawierają informacje o obiektach być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="b6607-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="b6607-112">Go można następnie przekazać jako argument do innych metod debugowania, które znajdują się dodatkowe informacje o tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="b6607-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="b6607-113">Na przykład, wyliczając [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu, możesz pobrać poszczególnych [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów, które reprezentują poszczególnych obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="b6607-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="b6607-114">Można następnie przekazać `COR_TYPEID` wartość z `COR_HEAPOBJECT.type` do [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metoda pobierania obiektu ICorDebugType, który zawiera typ informacji o obiekcie.</span><span class="sxs-lookup"><span data-stu-id="b6607-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="b6607-115">A `COR_TYPEID` obiektu ma być nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="b6607-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="b6607-116">Nie można uzyskać dostępu do lub modyfikowany w zakresie poszczególnych pól.</span><span class="sxs-lookup"><span data-stu-id="b6607-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="b6607-117">Jest jego wyłącznie do użytku jako identyfikatora, który został dostarczony jako `out` parametr w wywołaniu metody i który może z kolei można przekazać do innych metod, aby podać dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="b6607-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6607-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6607-118">Requirements</span></span>  
 <span data-ttu-id="b6607-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6607-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6607-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6607-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6607-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6607-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6607-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6607-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6607-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6607-123">See Also</span></span>  
 [<span data-ttu-id="b6607-124">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="b6607-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="b6607-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b6607-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
