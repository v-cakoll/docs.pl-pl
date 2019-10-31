---
title: ICorDebugChain::GetPrevious — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
ms.openlocfilehash: c7598a9d93631ca93187886fd8929ba10726dad7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124738"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="16d0e-102">ICorDebugChain::GetPrevious — Metoda</span><span class="sxs-lookup"><span data-stu-id="16d0e-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="16d0e-103">Pobiera poprzedni łańcuch ramek dla wątku.</span><span class="sxs-lookup"><span data-stu-id="16d0e-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16d0e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16d0e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16d0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16d0e-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="16d0e-106">określoną Wskaźnik do adresu obiektu ICorDebugChain, który reprezentuje poprzedni łańcuch ramek dla tego wątku.</span><span class="sxs-lookup"><span data-stu-id="16d0e-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="16d0e-107">Jeśli ten łańcuch jest pierwszym łańcuchem, `ppChain` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="16d0e-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16d0e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16d0e-108">Requirements</span></span>  
 <span data-ttu-id="16d0e-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16d0e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16d0e-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16d0e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16d0e-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="16d0e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16d0e-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16d0e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
