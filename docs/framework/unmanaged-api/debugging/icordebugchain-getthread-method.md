---
title: ICorDebugChain::GetThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
ms.openlocfilehash: 28b54026c8743f31a420e164944f60709e2e271b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894372"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="3d45c-102">ICorDebugChain::GetThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="3d45c-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="3d45c-103">Pobiera wątek fizyczny, do którego należy ten łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="3d45c-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d45c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d45c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d45c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d45c-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="3d45c-106">określoną Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek fizyczny, do którego należy ten łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="3d45c-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d45c-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d45c-107">Requirements</span></span>  
 <span data-ttu-id="3d45c-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d45c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d45c-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3d45c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d45c-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3d45c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d45c-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d45c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
