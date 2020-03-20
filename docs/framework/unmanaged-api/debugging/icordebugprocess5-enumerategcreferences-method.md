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
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178620"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="1f7f6-102">ICorDebugProcess5::EnumerateGCReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f7f6-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="1f7f6-103">Pobiera moduł wyliczania dla wszystkich obiektów, które mają być zbierane śmieci w procesie.</span><span class="sxs-lookup"><span data-stu-id="1f7f6-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f7f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f7f6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f7f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f7f6-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="1f7f6-106">[w] Wartość logiczna, która wskazuje, czy słabe odwołania mają być również wyliczone.</span><span class="sxs-lookup"><span data-stu-id="1f7f6-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="1f7f6-107">Jeśli `enumerateWeakReferences` `true`jest `ppEnum` , wyliczacz zawiera zarówno silne odwołania i słabe odwołania.</span><span class="sxs-lookup"><span data-stu-id="1f7f6-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="1f7f6-108">Jeśli `enumerateWeakReferences` `false`jest , wyliczacz zawiera tylko silne odwołania.</span><span class="sxs-lookup"><span data-stu-id="1f7f6-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="1f7f6-109">[na zewnątrz] Wskaźnik do adresu [ICorDebugGCReferenceEnum,](icordebuggcreferenceenum-interface.md) który jest modułem wyliczacza dla obiektów, które mają być zbierane przez śmieci.</span><span class="sxs-lookup"><span data-stu-id="1f7f6-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f7f6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f7f6-110">Remarks</span></span>  
 <span data-ttu-id="1f7f6-111">Ta metoda umożliwia określenie pełnego łańcucha rootowania dla dowolnego obiektu zarządzanego w procesie i może służyć do określenia, dlaczego obiekt jest nadal żywy.</span><span class="sxs-lookup"><span data-stu-id="1f7f6-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f7f6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f7f6-112">Requirements</span></span>  
 <span data-ttu-id="1f7f6-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f7f6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f7f6-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f7f6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f7f6-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f7f6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f7f6-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f7f6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f7f6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f7f6-117">See also</span></span>

- [<span data-ttu-id="1f7f6-118">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f7f6-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="1f7f6-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1f7f6-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
