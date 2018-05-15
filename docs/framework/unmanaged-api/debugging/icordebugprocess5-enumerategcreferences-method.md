---
title: ICorDebugProcess5::EnumerateGCReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b5f66099eb4b1cb84d9911567cac4255bf20480
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="0281d-102">ICorDebugProcess5::EnumerateGCReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="0281d-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="0281d-103">Pobiera moduł wyliczający dla wszystkich obiektów, które mają być zbierane pamięci w procesie.</span><span class="sxs-lookup"><span data-stu-id="0281d-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0281d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0281d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0281d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0281d-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="0281d-106">[in] Wartość logiczna wskazująca, czy słabe odwołania są również mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="0281d-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="0281d-107">Jeśli `enumerateWeakReferences` jest `true`, `ppEnum` modułu wyliczającego zawiera odwołań silne i słabe odwołania.</span><span class="sxs-lookup"><span data-stu-id="0281d-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="0281d-108">Jeśli `enumerateWeakReferences` jest `false`, moduł wyliczający zawiera tylko silne odwołania.</span><span class="sxs-lookup"><span data-stu-id="0281d-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="0281d-109">[out] Wskaźnik do adresu [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) czyli moduł wyliczający dla obiektów być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="0281d-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0281d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0281d-110">Remarks</span></span>  
 <span data-ttu-id="0281d-111">Ta metoda zapewnia możliwość określenia całego łańcucha umieszczania na dowolnym obiektem zarządzanym w procesie i może służyć do ustalenia, dlaczego obiektu jest nadal aktywna.</span><span class="sxs-lookup"><span data-stu-id="0281d-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0281d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0281d-112">Requirements</span></span>  
 <span data-ttu-id="0281d-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0281d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0281d-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0281d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0281d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0281d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0281d-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0281d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0281d-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0281d-117">See Also</span></span>  
 [<span data-ttu-id="0281d-118">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="0281d-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="0281d-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0281d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
