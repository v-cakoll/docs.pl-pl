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
ms.openlocfilehash: 2a1653055a3834ce1bed0e7de7877b255bea0c38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792429"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="792af-102">ICorDebugProcess5::EnumerateHandles — Metoda</span><span class="sxs-lookup"><span data-stu-id="792af-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="792af-103">Pobiera moduł wyliczający dla dojść do obiektów w procesie.</span><span class="sxs-lookup"><span data-stu-id="792af-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="792af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="792af-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="792af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="792af-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="792af-106">podczas Bitowa kombinacja wartości [CorGCReferenceType](corgcreferencetype-enumeration.md) , która określa typ dojść do uwzględnienia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="792af-106">[in] A bitwise combination of [CorGCReferenceType](corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="792af-107">określoną Wskaźnik na adres elementu [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) , który jest modułem wyliczającym dla obiektów, które mają być zbierane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="792af-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="792af-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="792af-108">Remarks</span></span>  
 <span data-ttu-id="792af-109">`EnumerateHandles` jest funkcją pomocnika, która obsługuje inspekcję tabeli dojścia.</span><span class="sxs-lookup"><span data-stu-id="792af-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="792af-110">Jest podobna do metody [ICorDebugProcess5:: EnumerateGCReferences —](icordebugprocess5-enumerategcreferences-method.md) , z wyjątkiem tego, że zamiast wypełniania kolekcji [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) wszystkie obiekty, które mają być zbierane jako elementy bezużyteczne, zawiera tylko te obiekty, które mają uchwyty z tabeli uchwytów.</span><span class="sxs-lookup"><span data-stu-id="792af-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="792af-111">`types` parametr określa typy dojść do uwzględnienia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="792af-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="792af-112">`types` może być jednym z trzech następujących elementów członkowskich wyliczenia [CorGCReferenceType](corgcreferencetype-enumeration.md) :</span><span class="sxs-lookup"><span data-stu-id="792af-112">`types` can be any of the following three members of the [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="792af-113">`CorHandleStrongOnly` (obsługuje tylko silne odwołania).</span><span class="sxs-lookup"><span data-stu-id="792af-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="792af-114">`CorHandleWeakOnly` (obsługuje tylko słabe odwołania).</span><span class="sxs-lookup"><span data-stu-id="792af-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="792af-115">`CorHandleAll` (wszystkie uchwyty).</span><span class="sxs-lookup"><span data-stu-id="792af-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="792af-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="792af-116">Requirements</span></span>  
 <span data-ttu-id="792af-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="792af-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="792af-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="792af-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="792af-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="792af-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="792af-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="792af-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792af-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="792af-121">See also</span></span>

- [<span data-ttu-id="792af-122">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="792af-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="792af-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="792af-123">Debugging</span></span>](index.md)
