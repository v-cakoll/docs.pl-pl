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
ms.openlocfilehash: d0845165e3200d7a5e14715cbe116ea5255aa021
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178896"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="a7fc9-102">ICorDebugProcess5::EnumerateGCReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7fc9-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="a7fc9-103">Pobiera moduł wyliczający dla wszystkich obiektów, które mają być jesdnostką zbierającą śmieci w procesie.</span><span class="sxs-lookup"><span data-stu-id="a7fc9-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7fc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7fc9-104">Syntax</span></span>  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7fc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7fc9-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="a7fc9-106">[in] Wartość logiczna wskazująca, czy słabe odwołania są także do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a7fc9-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="a7fc9-107">Jeśli `enumerateWeakReferences` jest `true`, `ppEnum` modułu wyliczającego zawiera odwołań do silnych i słabe odwołania.</span><span class="sxs-lookup"><span data-stu-id="a7fc9-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="a7fc9-108">Jeśli `enumerateWeakReferences` jest `false`, moduł wyliczający obejmuje tylko silne odwołania.</span><span class="sxs-lookup"><span data-stu-id="a7fc9-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="a7fc9-109">[out] Wskaźnik na adres [icordebuggcreferenceenum —](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) oznacza to moduł wyliczający dla obiektów jako zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a7fc9-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7fc9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7fc9-110">Remarks</span></span>  
 <span data-ttu-id="a7fc9-111">Ta metoda zapewnia możliwość określenia pełnego łańcucha umieszczania dla dowolnego obiektu zarządzanego w procesie i może służyć do ustalenia, dlaczego obiekt jest nadal aktywne.</span><span class="sxs-lookup"><span data-stu-id="a7fc9-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7fc9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7fc9-112">Requirements</span></span>  
 <span data-ttu-id="a7fc9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7fc9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7fc9-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7fc9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7fc9-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7fc9-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a7fc9-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a7fc9-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a7fc9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7fc9-117">See also</span></span>

- [<span data-ttu-id="a7fc9-118">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7fc9-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="a7fc9-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a7fc9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
