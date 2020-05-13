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
ms.openlocfilehash: e774905939640d2748344ad3f6e12a96f9868d9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213806"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="ef9af-102">ICorDebugHeapValue::IsValid — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef9af-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="ef9af-103">Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten ICorDebugHeapValue jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ef9af-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="ef9af-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="ef9af-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef9af-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef9af-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef9af-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef9af-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="ef9af-107">określoną Wskaźnik do wartości logicznej wskazującej, czy ta wartość w stercie jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="ef9af-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef9af-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef9af-108">Remarks</span></span>  
 <span data-ttu-id="ef9af-109">Wartość jest nieprawidłowa, jeśli została odinicjowana przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ef9af-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="ef9af-110">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="ef9af-110">This method has been deprecated.</span></span> <span data-ttu-id="ef9af-111">W .NET Framework 2,0 wszystkie wartości są ważne do momentu wywołania metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , podczas gdy wartości są unieważnione.</span><span class="sxs-lookup"><span data-stu-id="ef9af-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef9af-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef9af-112">Requirements</span></span>  
 <span data-ttu-id="ef9af-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef9af-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef9af-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ef9af-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef9af-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ef9af-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef9af-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef9af-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
