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
ms.openlocfilehash: b0e8fd162ccc1cfc944fb870f493febfe2e5ef42
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207685"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="5e7cf-102">ICorDebugObjectValue::GetClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e7cf-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="5e7cf-103">Pobiera klasę tej wartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="5e7cf-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e7cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e7cf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e7cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e7cf-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="5e7cf-106">określoną Wskaźnik do adresu obiektu "ICorDebugClass", który reprezentuje klasę wartości obiektu reprezentowanej przez ten obiekt "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="5e7cf-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e7cf-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e7cf-107">Remarks</span></span>  
 <span data-ttu-id="5e7cf-108">`GetClass`Metody i [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) każda zwracają informacje o typie wartości; są one zastępowane przez ogólne [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="5e7cf-108">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e7cf-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e7cf-109">Requirements</span></span>  
 <span data-ttu-id="5e7cf-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e7cf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e7cf-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e7cf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e7cf-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5e7cf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e7cf-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e7cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e7cf-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e7cf-114">See also</span></span>
