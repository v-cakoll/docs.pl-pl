---
title: "ICorDebugHeapValue::IsValid — Metoda"
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
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f4f356c953feaf0e6597983f431222a469e90c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="83ad4-102">ICorDebugHeapValue::IsValid — Metoda</span><span class="sxs-lookup"><span data-stu-id="83ad4-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="83ad4-103">Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten ICorDebugHeapValue jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="83ad4-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="83ad4-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="83ad4-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ad4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="83ad4-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83ad4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="83ad4-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="83ad4-107">[out] Wskaźnik na wartość logiczną, wskazującą, czy ta wartość na stercie jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="83ad4-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83ad4-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83ad4-108">Remarks</span></span>  
 <span data-ttu-id="83ad4-109">Wartość jest nieprawidłowa, jeśli ma zostać odzyskana przez moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="83ad4-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="83ad4-110">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="83ad4-110">This method has been deprecated.</span></span> <span data-ttu-id="83ad4-111">W .NET Framework 2.0, wszystkie wartości są prawidłowe do [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) jest wywołana, w których wartości są nieważne.</span><span class="sxs-lookup"><span data-stu-id="83ad4-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83ad4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83ad4-112">Requirements</span></span>  
 <span data-ttu-id="83ad4-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83ad4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83ad4-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83ad4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83ad4-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83ad4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83ad4-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83ad4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
