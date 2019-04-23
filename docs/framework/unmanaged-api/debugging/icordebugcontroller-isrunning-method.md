---
title: ICorDebugController::IsRunning — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5eae9e14bcd0ca430f03a873818246896438463
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227096"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="43361-102">ICorDebugController::IsRunning — Metoda</span><span class="sxs-lookup"><span data-stu-id="43361-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="43361-103">Pobiera wartość wskazującą, czy wątki w procesie są aktualnie uruchomione za darmo.</span><span class="sxs-lookup"><span data-stu-id="43361-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43361-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43361-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43361-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43361-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="43361-106">[out] Wskaźnik do wartości, która jest `true` wątki w procesie uruchamiania swobodnie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="43361-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43361-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43361-107">Requirements</span></span>  
 <span data-ttu-id="43361-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43361-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43361-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43361-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43361-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43361-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43361-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43361-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43361-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43361-112">See also</span></span>
