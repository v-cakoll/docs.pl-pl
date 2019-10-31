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
ms.openlocfilehash: 84b5da043f9bd437ee9099135ba865c1ab23bb9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129666"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="5d8ac-102">ICorDebugProcess5::EnumerateGCReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="5d8ac-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="5d8ac-103">Pobiera moduł wyliczający dla wszystkich obiektów, które mają być zbierane jako elementy bezużyteczne w procesie.</span><span class="sxs-lookup"><span data-stu-id="5d8ac-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d8ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d8ac-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d8ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d8ac-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="5d8ac-106">podczas Wartość logiczna wskazująca, czy słabe odwołania są również wyliczane.</span><span class="sxs-lookup"><span data-stu-id="5d8ac-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="5d8ac-107">Jeśli `enumerateWeakReferences` jest `true`, moduł wyliczający `ppEnum` zawiera zarówno silne odwołania, jak i słabe odwołania.</span><span class="sxs-lookup"><span data-stu-id="5d8ac-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="5d8ac-108">Jeśli `enumerateWeakReferences` jest `false`, moduł wyliczający zawiera tylko silne odwołania.</span><span class="sxs-lookup"><span data-stu-id="5d8ac-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="5d8ac-109">określoną Wskaźnik na adres elementu [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) , który jest modułem wyliczającym dla obiektów, które mają być zbierane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="5d8ac-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d8ac-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d8ac-110">Remarks</span></span>  
 <span data-ttu-id="5d8ac-111">Ta metoda umożliwia określenie pełnego łańcucha katalogów głównych dla dowolnego obiektu zarządzanego w procesie i może służyć do określenia, dlaczego obiekt jest nadal aktywny.</span><span class="sxs-lookup"><span data-stu-id="5d8ac-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d8ac-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d8ac-112">Requirements</span></span>  
 <span data-ttu-id="5d8ac-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d8ac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d8ac-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5d8ac-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d8ac-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5d8ac-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d8ac-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d8ac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d8ac-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d8ac-117">See also</span></span>

- [<span data-ttu-id="5d8ac-118">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="5d8ac-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="5d8ac-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5d8ac-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
