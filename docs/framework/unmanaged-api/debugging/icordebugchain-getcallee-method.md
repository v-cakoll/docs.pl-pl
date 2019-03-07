---
title: ICorDebugChain::GetCallee — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed5a7657affde335acf79952d77bbdb7ac42c7a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490466"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="578a8-102">ICorDebugChain::GetCallee — Metoda</span><span class="sxs-lookup"><span data-stu-id="578a8-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="578a8-103">Pobiera łańcucha, który został wywołany przez tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="578a8-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="578a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="578a8-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="578a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="578a8-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="578a8-106">[out] Wskaźnik na adres icordebugchain — obiekt, który reprezentuje o nazwie łańcucha.</span><span class="sxs-lookup"><span data-stu-id="578a8-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="578a8-107">Jeśli ta sieć jest w trakcie wykonywania (to znaczy, jeśli ten łańcuch nie oczekuje na o nazwie łańcuch do zwrócenia), `ppChain` będzie miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="578a8-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="578a8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="578a8-108">Remarks</span></span>  
 <span data-ttu-id="578a8-109">Ten łańcuch będzie czekać na o nazwie łańcuch do zwrócenia przed jego wznawia działanie.</span><span class="sxs-lookup"><span data-stu-id="578a8-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="578a8-110">Łańcuch o nazwie może znajdować się na inny wątek w przypadku międzyprocesowe między wątkami.</span><span class="sxs-lookup"><span data-stu-id="578a8-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="578a8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="578a8-111">Requirements</span></span>  
 <span data-ttu-id="578a8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="578a8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="578a8-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="578a8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="578a8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="578a8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="578a8-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="578a8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
