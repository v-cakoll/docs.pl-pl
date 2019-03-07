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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d23a0a489cfe13201b7798920feb3528db3b0709
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494613"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="a2f47-102">ICorDebugFunction2::GetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2f47-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="a2f47-103">Pobiera wartość wskazującą, czy funkcja, która jest reprezentowany przez ten obiekt icordebugfunction2 — jest oznaczony jako kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a2f47-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2f47-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2f47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2f47-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="a2f47-106">[out] Wskaźnik na wartość logiczną, która jest `true`, jeśli ta funkcja jest oznaczona jako kod użytkownika; w przeciwnym razie wartość to `false`.</span><span class="sxs-lookup"><span data-stu-id="a2f47-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2f47-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2f47-107">Remarks</span></span>  
 <span data-ttu-id="a2f47-108">Jeśli funkcja reprezentowany przez ten `ICorDebugFunction2` nie można debugować, `pbIsJustMyCode` zawsze będzie `false`.</span><span class="sxs-lookup"><span data-stu-id="a2f47-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2f47-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2f47-109">Requirements</span></span>  
 <span data-ttu-id="a2f47-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2f47-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2f47-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2f47-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2f47-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2f47-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2f47-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2f47-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
