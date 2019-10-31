---
title: ICorDebugEval::GetThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
ms.openlocfilehash: 6a7d9465a454175b58bb7b9566d31f3c65420610
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085057"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="9d99f-102">ICorDebugEval::GetThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d99f-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="9d99f-103">Pobiera wątek, w którym ta Ocena wykonuje lub zostanie wykonana.</span><span class="sxs-lookup"><span data-stu-id="9d99f-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d99f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d99f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d99f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d99f-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="9d99f-106">określoną Wskaźnik do adresu obiektu ICorDebugThread, który reprezentuje wątek.</span><span class="sxs-lookup"><span data-stu-id="9d99f-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d99f-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d99f-107">Requirements</span></span>  
 <span data-ttu-id="9d99f-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d99f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d99f-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9d99f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d99f-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9d99f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d99f-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d99f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
