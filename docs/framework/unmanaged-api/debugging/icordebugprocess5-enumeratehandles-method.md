---
title: ICorDebugProcess5::EnumerateHandles — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b3cc158c48e8bb9f833429bbddaa74ed459f1b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108835"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="d26a9-102">ICorDebugProcess5::EnumerateHandles — Metoda</span><span class="sxs-lookup"><span data-stu-id="d26a9-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="d26a9-103">Pobiera moduł wyliczający dla obiektu uchwytów w procesie.</span><span class="sxs-lookup"><span data-stu-id="d26a9-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d26a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d26a9-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d26a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d26a9-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="d26a9-106">[in] Bitowa kombinacja [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartości, które określa typ dojścia do uwzględnienia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d26a9-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="d26a9-107">[out] Wskaźnik na adres [icordebuggcreferenceenum —](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) oznacza to moduł wyliczający dla obiektów jako zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d26a9-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d26a9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d26a9-108">Remarks</span></span>  
 `EnumerateHandles` <span data-ttu-id="d26a9-109">jest funkcja pomocnicza, która obsługuje inspekcji tabelę uchwytów.</span><span class="sxs-lookup"><span data-stu-id="d26a9-109">is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="d26a9-110">Jest on podobny do [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metody, chyba że zamiast wypełnianie [icordebuggcreferenceenum —](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) kolekcji ze wszystkimi obiektami jako zebranych elementów bezużytecznych go zawiera tylko te obiekty, które mają dojścia stałe od tabelę uchwytów.</span><span class="sxs-lookup"><span data-stu-id="d26a9-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="d26a9-111">`types` Parametr określa typ dojścia do uwzględnienia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d26a9-111">The `types` parameter specifies the handle types to include in the collection.</span></span> `types` <span data-ttu-id="d26a9-112">może być dowolną z następujących trzech członków [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="d26a9-112">can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
-   `CorHandleStrongOnly` <span data-ttu-id="d26a9-113">(obsługuje tylko silne odwołania).</span><span class="sxs-lookup"><span data-stu-id="d26a9-113">(handles to strong references only).</span></span>  
  
-   `CorHandleWeakOnly` <span data-ttu-id="d26a9-114">(obsługuje wyłącznie słabe odwołania).</span><span class="sxs-lookup"><span data-stu-id="d26a9-114">(handles to weak references only).</span></span>  
  
-   `CorHandleAll` <span data-ttu-id="d26a9-115">(wszystkie uchwyty).</span><span class="sxs-lookup"><span data-stu-id="d26a9-115">(all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d26a9-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d26a9-116">Requirements</span></span>  
 <span data-ttu-id="d26a9-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d26a9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d26a9-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d26a9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d26a9-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d26a9-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d26a9-120">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d26a9-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d26a9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d26a9-121">See also</span></span>

- [<span data-ttu-id="d26a9-122">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="d26a9-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="d26a9-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d26a9-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
