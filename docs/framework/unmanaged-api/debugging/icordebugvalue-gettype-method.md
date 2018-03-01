---
title: "ICorDebugValue::GetType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a79ef332361fdaa3a23cc4e13daa8b4a8303d2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="e09de-102">ICorDebugValue::GetType — Metoda</span><span class="sxs-lookup"><span data-stu-id="e09de-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="e09de-103">Pobiera pierwotny typ obiektu "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="e09de-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e09de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e09de-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e09de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e09de-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="e09de-106">[out] Wskaźnik do wartości wyliczenia "CorElementType", który wskazuje typ tej wartości.</span><span class="sxs-lookup"><span data-stu-id="e09de-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e09de-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e09de-107">Remarks</span></span>  
 <span data-ttu-id="e09de-108">Jeśli obiekt jest typem złożonym czasu wykonywania, tego typu mogą być zbadane za pomocą odpowiednich podklasy `ICorDebugValue` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e09de-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="e09de-109">Na przykład "ICorDebugObjectValue", która dziedziczy od `ICorDebugValue`, reprezentuje typ złożony.</span><span class="sxs-lookup"><span data-stu-id="e09de-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="e09de-110">`GetType` i [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) metody każdego zwracają informacje o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="e09de-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="e09de-111">Zostały one zarówno zastąpione ogólne aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e09de-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e09de-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e09de-112">Requirements</span></span>  
 <span data-ttu-id="e09de-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e09de-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e09de-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e09de-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e09de-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e09de-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e09de-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e09de-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e09de-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e09de-117">See Also</span></span>  
 
