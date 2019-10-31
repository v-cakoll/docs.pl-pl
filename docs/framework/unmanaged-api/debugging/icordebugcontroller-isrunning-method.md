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
ms.openlocfilehash: f24c07a654dc2345cb65226463573576a6fb3658
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125339"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="d7a31-102">ICorDebugController::IsRunning — Metoda</span><span class="sxs-lookup"><span data-stu-id="d7a31-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="d7a31-103">Pobiera wartość wskazującą, czy wątki w procesie są obecnie uruchomione swobodnie.</span><span class="sxs-lookup"><span data-stu-id="d7a31-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7a31-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7a31-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7a31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7a31-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="d7a31-106">określoną Wskaźnik do wartości, która jest `true`, jeśli wątki w procesie działają swobodnie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d7a31-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7a31-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7a31-107">Requirements</span></span>  
 <span data-ttu-id="d7a31-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7a31-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7a31-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d7a31-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7a31-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d7a31-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7a31-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7a31-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a31-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7a31-112">See also</span></span>
