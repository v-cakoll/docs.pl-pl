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
ms.openlocfilehash: 6c5e5d1c9f734e097fc9e871d7a0cffdc9bb9138
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791122"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="9533c-102">ICorDebugValue2::GetExactType — Metoda</span><span class="sxs-lookup"><span data-stu-id="9533c-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="9533c-103">Pobiera wskaźnik interfejsu do obiektu "ICorDebugType", który reprezentuje <xref:System.Type> tej wartości.</span><span class="sxs-lookup"><span data-stu-id="9533c-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9533c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9533c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9533c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9533c-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="9533c-106">określoną Wskaźnik do adresu `ICorDebugType` obiektu, który reprezentuje <xref:System.Type> wartości reprezentowanej przez ten obiekt "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="9533c-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9533c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9533c-107">Remarks</span></span>  
 <span data-ttu-id="9533c-108">Metoda `GetExactType` opartej na typach ogólnych zastępuje zarówno metody [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) , jak i [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) , z których każdy zwraca informacje o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="9533c-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9533c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9533c-109">Requirements</span></span>  
 <span data-ttu-id="9533c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9533c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9533c-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9533c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9533c-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9533c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9533c-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9533c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9533c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9533c-114">See also</span></span>
