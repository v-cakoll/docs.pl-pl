---
title: ICorDebugHeapValue::IsValid — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e1edb1d25a62a9a689c397339740e563d986c8b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478768"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="6ef81-102">ICorDebugHeapValue::IsValid — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ef81-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="6ef81-103">Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten ICorDebugHeapValue jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="6ef81-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="6ef81-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="6ef81-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ef81-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ef81-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ef81-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ef81-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="6ef81-107">[out] Wskaźnik na wartość logiczną, wskazującą, czy ta wartość na stosie jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="6ef81-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ef81-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ef81-108">Remarks</span></span>  
 <span data-ttu-id="6ef81-109">Wartość jest nieprawidłowa, jeśli został odzyskany przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="6ef81-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="6ef81-110">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="6ef81-110">This method has been deprecated.</span></span> <span data-ttu-id="6ef81-111">W programie .NET Framework 2.0, wszystkie wartości są ważne do [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) jest wywoływana, w których wartości są nieważne.</span><span class="sxs-lookup"><span data-stu-id="6ef81-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ef81-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ef81-112">Requirements</span></span>  
 <span data-ttu-id="6ef81-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ef81-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ef81-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ef81-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ef81-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ef81-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ef81-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ef81-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
