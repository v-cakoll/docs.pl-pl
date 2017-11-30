---
title: "ICorDebugEval::CreateValue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CreateValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e7242e98a69083ca8d5a6d8d54e9b25279abb7bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="457d8-102">ICorDebugEval::CreateValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="457d8-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="457d8-103">Tworzy wartość określonego typu o wartości początkowej zero lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="457d8-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="457d8-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="457d8-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="457d8-105">Użyj [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="457d8-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="457d8-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="457d8-106">Syntax</span></span>  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="457d8-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="457d8-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="457d8-108">[in] Wartość [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) wyliczenia, która określa typ wartości.</span><span class="sxs-lookup"><span data-stu-id="457d8-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="457d8-109">[in] Wskaźnik do [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) obiekt, który określa klasę wartości, jeśli typ nie jest typem pierwotnym.</span><span class="sxs-lookup"><span data-stu-id="457d8-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="457d8-110">[out] Wskaźnik do obiektu "ICorDebugValue", który reprezentuje wartość adresu.</span><span class="sxs-lookup"><span data-stu-id="457d8-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="457d8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="457d8-111">Remarks</span></span>  
 <span data-ttu-id="457d8-112">`CreateValue`Tworzy `ICorDebugValue` obiekt danego typu wyłącznie w celu używania go w obliczania funkcji.</span><span class="sxs-lookup"><span data-stu-id="457d8-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="457d8-113">Ten obiekt wartość może służyć do przekazywania stałe użytkownika jako parametry.</span><span class="sxs-lookup"><span data-stu-id="457d8-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="457d8-114">Jeśli typ wartości jest typu pierwotnego, jego wartość początkowa to zero lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="457d8-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="457d8-115">Użyj [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) można ustawić wartości typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="457d8-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="457d8-116">Jeśli wartość `elementType` jest po elemencie ELEMENT_TYPE_CLASS, możesz uzyskać "ICorDebugReferenceValue" (zwracane w `ppValue`) reprezentujący odwołanie do obiektu o wartości null.</span><span class="sxs-lookup"><span data-stu-id="457d8-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="457d8-117">Ten obiekt służy do przekazania wartości null do obliczania funkcji z parametrami odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="457d8-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="457d8-118">Nie można ustawić `ICorDebugValue` na niczego; zawsze pozostaje wartości null.</span><span class="sxs-lookup"><span data-stu-id="457d8-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="457d8-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="457d8-119">Requirements</span></span>  
 <span data-ttu-id="457d8-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="457d8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="457d8-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="457d8-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="457d8-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="457d8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="457d8-123">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="457d8-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457d8-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="457d8-124">See Also</span></span>  
    
 [<span data-ttu-id="457d8-125">CreateValueForType — metoda</span><span class="sxs-lookup"><span data-stu-id="457d8-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)  
 <span data-ttu-id="457d8-126">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="457d8-126">ICorDebugValue</span></span>
