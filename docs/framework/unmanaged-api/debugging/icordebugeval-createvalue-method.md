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
ms.openlocfilehash: 4bb04ba090be9cab551bc39d8d9f1be974c747d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085132"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="f3217-102">ICorDebugEval::CreateValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3217-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="f3217-103">Tworzy wartość określonego typu z początkową wartością zero lub null.</span><span class="sxs-lookup"><span data-stu-id="f3217-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="f3217-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="f3217-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f3217-105">Zamiast tego użyj [ICorDebugEval2:: CreateValueForType —](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f3217-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3217-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3217-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3217-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3217-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="f3217-108">podczas Wartość wyliczenia [CorElementType —](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) , która określa typ wartości.</span><span class="sxs-lookup"><span data-stu-id="f3217-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="f3217-109">podczas Wskaźnik do obiektu [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) , który określa klasę wartości, jeśli typ nie jest typem pierwotnym.</span><span class="sxs-lookup"><span data-stu-id="f3217-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="f3217-110">określoną Wskaźnik na adres obiektu "ICorDebugValue", który reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="f3217-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3217-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3217-111">Remarks</span></span>  
 <span data-ttu-id="f3217-112">`CreateValue` tworzy obiekt `ICorDebugValue` danego typu jako jedyny cel użycia go w ocenie funkcji.</span><span class="sxs-lookup"><span data-stu-id="f3217-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="f3217-113">Ten obiekt wartości może służyć do przekazywania stałych użytkowników jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="f3217-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="f3217-114">Jeśli typ wartości jest typem pierwotnym, jego wartość początkowa wynosi zero lub ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="f3217-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="f3217-115">Użyj [ICorDebugGenericValue:: SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) , aby ustawić wartość typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="f3217-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="f3217-116">Jeśli wartość `elementType` to ELEMENT_TYPE_CLASS, otrzymujesz "ICorDebugReferenceValue" (zwrócony w `ppValue`) reprezentujący odwołanie do obiektu null.</span><span class="sxs-lookup"><span data-stu-id="f3217-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="f3217-117">Można użyć tego obiektu, aby przekazać wartość null do oceny funkcji, która ma parametry odwołania obiektu.</span><span class="sxs-lookup"><span data-stu-id="f3217-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="f3217-118">Nie można ustawić dla `ICorDebugValue` żadnych elementów. zawsze pozostaje puste.</span><span class="sxs-lookup"><span data-stu-id="f3217-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3217-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3217-119">Requirements</span></span>  
 <span data-ttu-id="f3217-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3217-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3217-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f3217-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3217-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f3217-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3217-123">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="f3217-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3217-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3217-124">See also</span></span>

- [<span data-ttu-id="f3217-125">CreateValueForType, metoda</span><span class="sxs-lookup"><span data-stu-id="f3217-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="f3217-126">ICorDebugEval, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3217-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
