---
title: ICorDebugEval::CreateValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
ms.openlocfilehash: 55888786fdd8ff2b1d5610a74ee729db0d4fcfde
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976255"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="926a9-102">ICorDebugEval::CreateValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="926a9-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="926a9-103">Tworzy wartość określonego typu z początkową wartością zero lub null.</span><span class="sxs-lookup"><span data-stu-id="926a9-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="926a9-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="926a9-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="926a9-105">Zamiast tego użyj [ICorDebugEval2:: CreateValueForType —](icordebugeval2-createvaluefortype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="926a9-105">Use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="926a9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="926a9-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="926a9-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="926a9-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="926a9-108">podczas Wartość wyliczenia [CorElementType —](../metadata/corelementtype-enumeration.md) , która określa typ wartości.</span><span class="sxs-lookup"><span data-stu-id="926a9-108">[in] A value of the [CorElementType](../metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="926a9-109">podczas Wskaźnik do obiektu [ICorDebugClass](icordebugclass-interface.md) , który określa klasę wartości, jeśli typ nie jest typem pierwotnym.</span><span class="sxs-lookup"><span data-stu-id="926a9-109">[in] Pointer to an [ICorDebugClass](icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="926a9-110">określoną Wskaźnik na adres obiektu "ICorDebugValue", który reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="926a9-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="926a9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="926a9-111">Remarks</span></span>  
 <span data-ttu-id="926a9-112">`CreateValue`tworzy `ICorDebugValue` obiekt danego typu jako jedyny cel użycia go w ocenie funkcji.</span><span class="sxs-lookup"><span data-stu-id="926a9-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="926a9-113">Ten obiekt wartości może służyć do przekazywania stałych użytkowników jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="926a9-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="926a9-114">Jeśli typ wartości jest typem pierwotnym, jego wartość początkowa wynosi zero lub ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="926a9-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="926a9-115">Użyj [ICorDebugGenericValue:: SetValue](icordebuggenericvalue-setvalue-method.md) , aby ustawić wartość typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="926a9-115">Use [ICorDebugGenericValue::SetValue](icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="926a9-116">Jeśli wartość `elementType` jest ELEMENT_TYPE_CLASS, otrzymujesz "ICorDebugReferenceValue" (zwrócony w `ppValue`) reprezentujący odwołanie do obiektu o wartości null.</span><span class="sxs-lookup"><span data-stu-id="926a9-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="926a9-117">Można użyć tego obiektu, aby przekazać wartość null do oceny funkcji, która ma parametry odwołania obiektu.</span><span class="sxs-lookup"><span data-stu-id="926a9-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="926a9-118">Nie można ustawić elementów `ICorDebugValue` na wszystkie; zawsze pozostaje puste.</span><span class="sxs-lookup"><span data-stu-id="926a9-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="926a9-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="926a9-119">Requirements</span></span>  
 <span data-ttu-id="926a9-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="926a9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="926a9-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="926a9-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="926a9-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="926a9-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="926a9-123">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="926a9-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="926a9-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="926a9-124">See also</span></span>

- [<span data-ttu-id="926a9-125">CreateValueForType, metoda</span><span class="sxs-lookup"><span data-stu-id="926a9-125">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="926a9-126">ICorDebugEval, interfejs</span><span class="sxs-lookup"><span data-stu-id="926a9-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
