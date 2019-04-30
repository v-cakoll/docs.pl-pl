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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749270"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="c6010-102">ICorDebugController::IsRunning — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6010-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="c6010-103">Pobiera wartość wskazującą, czy wątki w procesie są aktualnie uruchomione za darmo.</span><span class="sxs-lookup"><span data-stu-id="c6010-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6010-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6010-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6010-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6010-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="c6010-106">[out] Wskaźnik do wartości, która jest `true` wątki w procesie uruchamiania swobodnie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="c6010-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6010-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6010-107">Requirements</span></span>  
 <span data-ttu-id="c6010-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6010-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6010-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6010-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6010-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6010-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6010-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6010-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6010-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6010-112">See also</span></span>
