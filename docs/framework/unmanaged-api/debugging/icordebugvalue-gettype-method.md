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
ms.openlocfilehash: 0fc0dd03abc1adb8eeea76a1053fb4d58de4ecf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419835"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="4d4f1-102">ICorDebugValue::GetType — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d4f1-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="4d4f1-103">Pobiera pierwotny typ obiektu "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="4d4f1-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d4f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d4f1-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d4f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d4f1-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="4d4f1-106">[out] Wskaźnik do wartości wyliczenia "CorElementType", który wskazuje typ tej wartości.</span><span class="sxs-lookup"><span data-stu-id="4d4f1-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d4f1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d4f1-107">Remarks</span></span>  
 <span data-ttu-id="4d4f1-108">Jeśli obiekt jest typem złożonym czasu wykonywania, tego typu mogą być zbadane za pomocą odpowiednich podklasy `ICorDebugValue` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4d4f1-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="4d4f1-109">Na przykład "ICorDebugObjectValue", która dziedziczy od `ICorDebugValue`, reprezentuje typ złożony.</span><span class="sxs-lookup"><span data-stu-id="4d4f1-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="4d4f1-110">`GetType` i [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) metody każdego zwracają informacje o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="4d4f1-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="4d4f1-111">Zostały one zarówno zastąpione ogólne aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4d4f1-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d4f1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d4f1-112">Requirements</span></span>  
 <span data-ttu-id="4d4f1-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d4f1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d4f1-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d4f1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d4f1-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d4f1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d4f1-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d4f1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d4f1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d4f1-117">See Also</span></span>  
 
