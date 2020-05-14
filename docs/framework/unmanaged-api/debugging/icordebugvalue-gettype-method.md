---
title: ICorDebugValue::GetType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: a3cd62384ad87d072cd715d23d0e9ee9dac23270
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396740"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="c5912-102">ICorDebugValue::GetType — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5912-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="c5912-103">Pobiera typ pierwotny tego obiektu "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="c5912-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5912-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5912-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5912-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5912-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="c5912-106">określoną Wskaźnik do wartości wyliczenia "CorElementType —", która wskazuje typ wartości.</span><span class="sxs-lookup"><span data-stu-id="c5912-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5912-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5912-107">Remarks</span></span>  
 <span data-ttu-id="c5912-108">Jeśli obiekt jest złożonym typem czasu wykonywania, ten typ może być badany za pomocą odpowiednich podklas `ICorDebugValue` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c5912-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="c5912-109">Na przykład "ICorDebugObjectValue", który dziedziczy po `ICorDebugValue` , reprezentuje typ złożony.</span><span class="sxs-lookup"><span data-stu-id="c5912-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="c5912-110">`GetType`Metody i [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) każda zwracają informacje o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="c5912-110">The `GetType` and [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="c5912-111">Są one zastępowane przez metodę [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) z uwzględnieniem typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="c5912-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5912-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5912-112">Requirements</span></span>  
 <span data-ttu-id="c5912-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5912-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5912-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c5912-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5912-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c5912-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5912-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5912-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5912-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5912-117">See also</span></span>
