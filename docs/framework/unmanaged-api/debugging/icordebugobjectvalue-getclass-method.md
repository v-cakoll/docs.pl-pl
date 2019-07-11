---
title: ICorDebugObjectValue::GetClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a20ab7a7ecb5d01351d0c912e08955f44b26d5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756997"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="860d0-102">ICorDebugObjectValue::GetClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="860d0-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="860d0-103">Pobiera klasę wartość tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="860d0-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="860d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="860d0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="860d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="860d0-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="860d0-106">[out] Wskaźnik na adres obiektu "ICorDebugClass", który reprezentuje klasę wartości obiektu reprezentowanego przez ten obiekt "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="860d0-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="860d0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="860d0-107">Remarks</span></span>  
 <span data-ttu-id="860d0-108">`GetClass` i [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) metody zwracają informacje o typie wartości; zostały one zarówno zastąpione świadomy rodzajowo [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="860d0-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="860d0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="860d0-109">Requirements</span></span>  
 <span data-ttu-id="860d0-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="860d0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="860d0-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="860d0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="860d0-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="860d0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="860d0-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="860d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="860d0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="860d0-114">See also</span></span>
