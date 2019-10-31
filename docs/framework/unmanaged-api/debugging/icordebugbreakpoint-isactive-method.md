---
title: ICorDebugBreakpoint::IsActive — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type:
- apiref
ms.openlocfilehash: 8df4e1df7836f340bb04fc47d1ca55e0fb7c9f0e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122768"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="b35c1-102">ICorDebugBreakpoint::IsActive — Metoda</span><span class="sxs-lookup"><span data-stu-id="b35c1-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="b35c1-103">Pobiera wartość wskazującą, czy ta `ICorDebugBreakpoint` jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="b35c1-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b35c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b35c1-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b35c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b35c1-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="b35c1-106">[out] `true`, jeśli ten punkt przerwania jest aktywny; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="b35c1-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b35c1-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b35c1-107">Requirements</span></span>  
 <span data-ttu-id="b35c1-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b35c1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b35c1-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b35c1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b35c1-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b35c1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b35c1-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b35c1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
