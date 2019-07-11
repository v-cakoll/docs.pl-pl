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
ms.openlocfilehash: ed2364c7c47aed1430a86aeee3daabf6b94cbf3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754478"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="56fab-102">ICorDebugFunction2::GetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="56fab-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="56fab-103">Pobiera wartość wskazującą, czy funkcja, która jest reprezentowany przez ten obiekt icordebugfunction2 — jest oznaczony jako kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="56fab-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56fab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56fab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56fab-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="56fab-106">[out] Wskaźnik na wartość logiczną, która jest `true`, jeśli ta funkcja jest oznaczona jako kod użytkownika; w przeciwnym razie wartość to `false`.</span><span class="sxs-lookup"><span data-stu-id="56fab-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56fab-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56fab-107">Remarks</span></span>  
 <span data-ttu-id="56fab-108">Jeśli funkcja reprezentowany przez ten `ICorDebugFunction2` nie można debugować, `pbIsJustMyCode` zawsze będzie `false`.</span><span class="sxs-lookup"><span data-stu-id="56fab-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56fab-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56fab-109">Requirements</span></span>  
 <span data-ttu-id="56fab-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56fab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fab-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56fab-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56fab-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56fab-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56fab-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56fab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
