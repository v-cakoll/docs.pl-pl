---
title: ICorDebugType::GetClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 878a57514af34730049864f17f4853c1237904c2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379962"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="4c76d-102">ICorDebugType::GetClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c76d-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="4c76d-103">Pobiera wskaźnik interfejsu do ICorDebugClass, który reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="4c76d-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c76d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c76d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c76d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c76d-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="4c76d-106">określoną Wskaźnik do adresu `ICorDebugClass` interfejsu, który reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="4c76d-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c76d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c76d-107">Remarks</span></span>  
 <span data-ttu-id="4c76d-108">`GetClass`może być wywoływana tylko w określonych warunkach.</span><span class="sxs-lookup"><span data-stu-id="4c76d-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="4c76d-109">Wywołaj metodę [ICorDebugType:: GetType](icordebugtype-gettype-method.md) przed wywołaniem metody `GetClass` .</span><span class="sxs-lookup"><span data-stu-id="4c76d-109">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="4c76d-110">Jeśli `ICorDebugType::GetType` zwraca wartość CorElementType —, która jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, `GetClass` można wywołać, aby uzyskać typ nieskonkretyzowany dla typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="4c76d-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c76d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c76d-111">Requirements</span></span>  
 <span data-ttu-id="4c76d-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c76d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c76d-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4c76d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c76d-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4c76d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c76d-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c76d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
