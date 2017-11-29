---
title: "ICorDebugProcess5::EnumerateHandles — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHandles
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5377f4ce0571cdb1de6c338f4bbb87d6a589aaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="17b53-102">ICorDebugProcess5::EnumerateHandles — Metoda</span><span class="sxs-lookup"><span data-stu-id="17b53-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="17b53-103">Pobiera moduł wyliczający dla obiekt dojść w procesie.</span><span class="sxs-lookup"><span data-stu-id="17b53-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17b53-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17b53-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17b53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17b53-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="17b53-106">[in] Bitowe połączenie [corgcreferencetype —](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartości, które określają typ dojścia do uwzględnienia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="17b53-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="17b53-107">[out] Wskaźnik do adresu [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) czyli moduł wyliczający dla obiektów być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="17b53-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17b53-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17b53-108">Remarks</span></span>  
 <span data-ttu-id="17b53-109">`EnumerateHandles`to funkcja pomocnika obsługującą kontroli tabeli dojścia.</span><span class="sxs-lookup"><span data-stu-id="17b53-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="17b53-110">Jest podobna do [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metody, z wyjątkiem zamiast wypełnianie [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) kolekcji ze wszystkimi obiektami być zbierane odzyskiwanie go obejmuje tylko te obiekty, które mają uchwyty z tabeli dojścia.</span><span class="sxs-lookup"><span data-stu-id="17b53-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="17b53-111">`types` Parametr określa typ dojścia do uwzględnienia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="17b53-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="17b53-112">`types`Możesz użyć dowolnej z następujących trzech elementów członkowskich [corgcreferencetype —](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wyliczenie:</span><span class="sxs-lookup"><span data-stu-id="17b53-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
-   <span data-ttu-id="17b53-113">`CorHandleStrongOnly`(dojść tylko silne odwołania).</span><span class="sxs-lookup"><span data-stu-id="17b53-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
-   <span data-ttu-id="17b53-114">`CorHandleWeakOnly`(dojść tylko słabego odwołania).</span><span class="sxs-lookup"><span data-stu-id="17b53-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
-   <span data-ttu-id="17b53-115">`CorHandleAll`(wszystkie dojścia).</span><span class="sxs-lookup"><span data-stu-id="17b53-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17b53-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="17b53-116">Requirements</span></span>  
 <span data-ttu-id="17b53-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17b53-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17b53-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17b53-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17b53-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17b53-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17b53-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17b53-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b53-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17b53-121">See Also</span></span>  
 [<span data-ttu-id="17b53-122">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="17b53-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="17b53-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="17b53-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
