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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83265c4f6dffed76f1710378cf5293aac7020ef2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119356"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="0b0af-102">ICorDebugValue::GetType — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b0af-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="0b0af-103">Pobiera typ pierwotny obiekt "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="0b0af-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b0af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b0af-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b0af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b0af-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="0b0af-106">[out] Wskaźnik do wartości wyliczenia "Corelementtype —", który wskazuje typ tej wartości.</span><span class="sxs-lookup"><span data-stu-id="0b0af-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b0af-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b0af-107">Remarks</span></span>  
 <span data-ttu-id="0b0af-108">Jeśli obiekt jest złożonych typów w czasie wykonywania, tego typu może być sprawdzane w drodze odpowiednie podklasy `ICorDebugValue` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0b0af-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="0b0af-109">Na przykład "ICorDebugObjectValue", która dziedziczy z `ICorDebugValue`, reprezentuje typ złożony.</span><span class="sxs-lookup"><span data-stu-id="0b0af-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="0b0af-110">`GetType` i [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) każdego zwracają informacje o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="0b0af-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="0b0af-111">Zostały one zarówno zastąpione świadomy rodzajowo [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="0b0af-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b0af-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b0af-112">Requirements</span></span>  
 <span data-ttu-id="0b0af-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b0af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b0af-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b0af-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b0af-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b0af-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b0af-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b0af-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b0af-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b0af-117">See also</span></span>
