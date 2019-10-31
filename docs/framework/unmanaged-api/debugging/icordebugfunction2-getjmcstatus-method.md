---
title: ICorDebugFunction2::GetJMCStatus — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 360434fe6e08804d8c80c4ea36d585209cc6761a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137817"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="294a5-102">ICorDebugFunction2::GetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="294a5-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="294a5-103">Pobiera wartość wskazującą, czy funkcja reprezentowana przez ten obiekt ICorDebugFunction2 jest oznaczona jako kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="294a5-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="294a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="294a5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="294a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="294a5-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="294a5-106">określoną Wskaźnik do wartości logicznej, która jest `true`, jeśli ta funkcja jest oznaczona jako kod użytkownika; w przeciwnym razie wartość jest `false`.</span><span class="sxs-lookup"><span data-stu-id="294a5-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="294a5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="294a5-107">Remarks</span></span>  
 <span data-ttu-id="294a5-108">Jeśli funkcja reprezentowana przez tę `ICorDebugFunction2` nie może być debugowana, `pbIsJustMyCode` będzie zawsze `false`.</span><span class="sxs-lookup"><span data-stu-id="294a5-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="294a5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="294a5-109">Requirements</span></span>  
 <span data-ttu-id="294a5-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="294a5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="294a5-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="294a5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="294a5-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="294a5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="294a5-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="294a5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
