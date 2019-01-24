---
title: ICorDebugValue2::GetExactType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 982af81f8f3886ae26b56114cc36374279c07593
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656352"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="a9378-102">ICorDebugValue2::GetExactType — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9378-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="a9378-103">Pobiera wskaźnik interfejsu do obiektu "ICorDebugType", który reprezentuje <xref:System.Type> tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a9378-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9378-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9378-104">Syntax</span></span>  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9378-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9378-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="a9378-106">[out] Wskaźnik na adres `ICorDebugType` obiekt, który reprezentuje <xref:System.Type> wartości reprezentowany przez ten obiekt "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="a9378-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9378-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9378-107">Remarks</span></span>  
 <span data-ttu-id="a9378-108">Świadomy rodzajowo `GetExactType` metoda zastępuje zarówno [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) i [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) metod, każda z których informacje zwrotne o typie wartości .</span><span class="sxs-lookup"><span data-stu-id="a9378-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9378-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9378-109">Requirements</span></span>  
 <span data-ttu-id="a9378-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9378-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9378-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9378-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9378-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9378-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9378-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9378-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9378-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9378-114">See also</span></span>

