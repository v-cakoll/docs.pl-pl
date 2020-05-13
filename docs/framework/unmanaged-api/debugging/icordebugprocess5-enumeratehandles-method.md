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
ms.openlocfilehash: 291b384d6f0c8c1404b380c653693ec65fcfc960
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213416"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="6b953-102">ICorDebugProcess5::EnumerateHandles — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b953-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="6b953-103">Pobiera moduł wyliczający dla dojść do obiektów w procesie.</span><span class="sxs-lookup"><span data-stu-id="6b953-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b953-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b953-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b953-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b953-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="6b953-106">podczas Bitowa kombinacja wartości [CorGCReferenceType](corgcreferencetype-enumeration.md) , która określa typ dojść do uwzględnienia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6b953-106">[in] A bitwise combination of [CorGCReferenceType](corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="6b953-107">określoną Wskaźnik na adres elementu [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) , który jest modułem wyliczającym dla obiektów, które mają być zbierane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="6b953-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b953-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b953-108">Remarks</span></span>  
 <span data-ttu-id="6b953-109">`EnumerateHandles`jest funkcją pomocnika, która obsługuje inspekcję tabeli dojścia.</span><span class="sxs-lookup"><span data-stu-id="6b953-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="6b953-110">Jest podobna do metody [ICorDebugProcess5:: EnumerateGCReferences —](icordebugprocess5-enumerategcreferences-method.md) , z wyjątkiem tego, że zamiast wypełniania kolekcji [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) wszystkie obiekty, które mają być zbierane jako elementy bezużyteczne, zawiera tylko te obiekty, które mają uchwyty z tabeli uchwytów.</span><span class="sxs-lookup"><span data-stu-id="6b953-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="6b953-111">`types`Parametr określa typy dojść do uwzględnienia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6b953-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="6b953-112">`types`może to być dowolny z następujących trzech elementów członkowskich wyliczenia [CorGCReferenceType](corgcreferencetype-enumeration.md) :</span><span class="sxs-lookup"><span data-stu-id="6b953-112">`types` can be any of the following three members of the [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="6b953-113">`CorHandleStrongOnly`(obsługuje tylko silne odwołania).</span><span class="sxs-lookup"><span data-stu-id="6b953-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="6b953-114">`CorHandleWeakOnly`(obsługuje tylko słabe odwołania).</span><span class="sxs-lookup"><span data-stu-id="6b953-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="6b953-115">`CorHandleAll`(wszystkie uchwyty).</span><span class="sxs-lookup"><span data-stu-id="6b953-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b953-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b953-116">Requirements</span></span>  
 <span data-ttu-id="6b953-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b953-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b953-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6b953-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b953-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6b953-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b953-120">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b953-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b953-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b953-121">See also</span></span>

- [<span data-ttu-id="6b953-122">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="6b953-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="6b953-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6b953-123">Debugging</span></span>](index.md)
