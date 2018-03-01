---
title: "ICorDebugValue2::GetExactType — Metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ad7d0e2ddcd8b66fd87cffa23204ae3b859f368c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="da6a0-102">ICorDebugValue2::GetExactType — Metoda</span><span class="sxs-lookup"><span data-stu-id="da6a0-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="da6a0-103">Pobiera wskaźnika interfejsu do obiektu "ICorDebugType", który reprezentuje <xref:System.Type> tej wartości.</span><span class="sxs-lookup"><span data-stu-id="da6a0-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da6a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da6a0-104">Syntax</span></span>  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da6a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da6a0-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="da6a0-106">[out] Wskaźnik do adresu `ICorDebugType` obiekt, który reprezentuje <xref:System.Type> wartości reprezentowany przez ten obiekt "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="da6a0-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da6a0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da6a0-107">Remarks</span></span>  
 <span data-ttu-id="da6a0-108">Ogólne aware `GetExactType` metoda zastępuje zarówno [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) i [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) metod, każdy z których zwracany informacji na temat typu wartości .</span><span class="sxs-lookup"><span data-stu-id="da6a0-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da6a0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da6a0-109">Requirements</span></span>  
 <span data-ttu-id="da6a0-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da6a0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da6a0-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da6a0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da6a0-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da6a0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da6a0-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da6a0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da6a0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da6a0-114">See Also</span></span>  
 
