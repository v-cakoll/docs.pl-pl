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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227096"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="8ef97-102">ICorDebugController::IsRunning — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ef97-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="8ef97-103">Pobiera wartość wskazującą, czy wątki w procesie są aktualnie uruchomione za darmo.</span><span class="sxs-lookup"><span data-stu-id="8ef97-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef97-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ef97-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ef97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ef97-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="8ef97-106">[out] Wskaźnik do wartości, która jest `true` wątki w procesie uruchamiania swobodnie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="8ef97-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef97-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ef97-107">Requirements</span></span>  
 <span data-ttu-id="8ef97-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef97-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef97-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ef97-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ef97-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ef97-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8ef97-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8ef97-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ef97-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ef97-112">See also</span></span>
