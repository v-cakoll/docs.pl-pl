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
ms.openlocfilehash: 7edf0065fa7eb39dada167a682f2b634a438f1f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138398"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="0bdb6-102">ICorDebugHeapValue::IsValid — Metoda</span><span class="sxs-lookup"><span data-stu-id="0bdb6-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="0bdb6-103">Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten ICorDebugHeapValue jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="0bdb6-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="0bdb6-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="0bdb6-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bdb6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0bdb6-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bdb6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bdb6-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="0bdb6-107">określoną Wskaźnik do wartości logicznej wskazującej, czy ta wartość w stercie jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="0bdb6-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bdb6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0bdb6-108">Remarks</span></span>  
 <span data-ttu-id="0bdb6-109">Wartość jest nieprawidłowa, jeśli została odinicjowana przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0bdb6-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="0bdb6-110">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="0bdb6-110">This method has been deprecated.</span></span> <span data-ttu-id="0bdb6-111">W .NET Framework 2,0 wszystkie wartości są ważne do momentu wywołania metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , podczas gdy wartości są unieważnione.</span><span class="sxs-lookup"><span data-stu-id="0bdb6-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bdb6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0bdb6-112">Requirements</span></span>  
 <span data-ttu-id="0bdb6-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bdb6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bdb6-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0bdb6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bdb6-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0bdb6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bdb6-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bdb6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
