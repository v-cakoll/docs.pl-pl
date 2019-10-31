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
ms.openlocfilehash: 441d225dadbbca09ab27c8ccd70debe32f4c12da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140254"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="010a9-102">ICorDebugValue2::GetExactType — Metoda</span><span class="sxs-lookup"><span data-stu-id="010a9-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="010a9-103">Pobiera wskaźnik interfejsu do obiektu "ICorDebugType", który reprezentuje <xref:System.Type> tej wartości.</span><span class="sxs-lookup"><span data-stu-id="010a9-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="010a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="010a9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="010a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="010a9-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="010a9-106">określoną Wskaźnik do adresu `ICorDebugType` obiektu, który reprezentuje <xref:System.Type> wartości reprezentowanej przez ten obiekt "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="010a9-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="010a9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="010a9-107">Remarks</span></span>  
 <span data-ttu-id="010a9-108">Metoda `GetExactType` opartej na typach ogólnych zastępuje zarówno metody [ICorDebugObjectValue:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) , jak i [ICorDebugValue:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) , z których każdy zwraca informacje o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="010a9-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="010a9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="010a9-109">Requirements</span></span>  
 <span data-ttu-id="010a9-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="010a9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="010a9-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="010a9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="010a9-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="010a9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="010a9-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="010a9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="010a9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="010a9-114">See also</span></span>
