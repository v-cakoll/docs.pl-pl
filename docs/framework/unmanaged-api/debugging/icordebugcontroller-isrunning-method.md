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
ms.openlocfilehash: 89ea9f221ad55063e4186cc27cc8038334d800d4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892878"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="f95d9-102">ICorDebugController::IsRunning — Metoda</span><span class="sxs-lookup"><span data-stu-id="f95d9-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="f95d9-103">Pobiera wartość wskazującą, czy wątki w procesie są obecnie uruchomione swobodnie.</span><span class="sxs-lookup"><span data-stu-id="f95d9-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f95d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f95d9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f95d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f95d9-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="f95d9-106">określoną Wskaźnik do wartości, która jest `true` , jeśli wątki w procesie działają swobodnie; w przeciwnym `false`razie.</span><span class="sxs-lookup"><span data-stu-id="f95d9-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f95d9-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f95d9-107">Requirements</span></span>  
 <span data-ttu-id="f95d9-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f95d9-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f95d9-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f95d9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f95d9-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f95d9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f95d9-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f95d9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f95d9-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f95d9-112">See also</span></span>
