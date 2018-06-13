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
ms.openlocfilehash: f1f8292a6964a6b25e228fcd07ab21a7ee5f5a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423335"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="1ddc2-102">ICorDebugValue2::GetExactType — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ddc2-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="1ddc2-103">Pobiera wskaźnika interfejsu do obiektu "ICorDebugType", który reprezentuje <xref:System.Type> tej wartości.</span><span class="sxs-lookup"><span data-stu-id="1ddc2-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ddc2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ddc2-104">Syntax</span></span>  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ddc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ddc2-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="1ddc2-106">[out] Wskaźnik do adresu `ICorDebugType` obiekt, który reprezentuje <xref:System.Type> wartości reprezentowany przez ten obiekt "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="1ddc2-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ddc2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ddc2-107">Remarks</span></span>  
 <span data-ttu-id="1ddc2-108">Ogólne aware `GetExactType` metoda zastępuje zarówno [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) i [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) metod, każdy z których zwracany informacji na temat typu wartości .</span><span class="sxs-lookup"><span data-stu-id="1ddc2-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ddc2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ddc2-109">Requirements</span></span>  
 <span data-ttu-id="1ddc2-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ddc2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ddc2-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ddc2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ddc2-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ddc2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ddc2-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ddc2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ddc2-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ddc2-114">See Also</span></span>  
 
