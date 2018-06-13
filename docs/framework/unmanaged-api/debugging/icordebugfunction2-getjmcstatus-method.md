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
ms.openlocfilehash: acf0ba3938568524479e12b93ae8cebbcf52f909
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411732"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="65fc6-102">ICorDebugFunction2::GetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="65fc6-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="65fc6-103">Pobiera wartość wskazującą, czy funkcja reprezentowanego przez ten obiekt ICorDebugFunction2 jest oznaczony jako kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="65fc6-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65fc6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65fc6-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65fc6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65fc6-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="65fc6-106">[out] Wskaźnik do wartość logiczna, która jest `true`, jeśli ta funkcja jest oznaczony jako kod użytkownika; w przeciwnym razie wartość jest `false`.</span><span class="sxs-lookup"><span data-stu-id="65fc6-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65fc6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65fc6-107">Remarks</span></span>  
 <span data-ttu-id="65fc6-108">Jeśli funkcja reprezentowany przez to `ICorDebugFunction2` nie można debugować `pbIsJustMyCode` zawsze będzie `false`.</span><span class="sxs-lookup"><span data-stu-id="65fc6-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65fc6-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65fc6-109">Requirements</span></span>  
 <span data-ttu-id="65fc6-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65fc6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65fc6-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65fc6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65fc6-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65fc6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65fc6-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65fc6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
