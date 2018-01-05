---
title: "ICorDebugChain::GetCaller — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetCaller
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17c55358a1d502ce5946617556222282ac4c4fca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="7c417-102">ICorDebugChain::GetCaller — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c417-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="7c417-103">Pobiera łańcuch, który wywołuje ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="7c417-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c417-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c417-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c417-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c417-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="7c417-106">[out] Wskaźnik do adresu ICorDebugChain obiekt, który reprezentuje łańcucha wywołania.</span><span class="sxs-lookup"><span data-stu-id="7c417-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="7c417-107">Jeśli ten łańcuch samorzutnie została wywołana (jak byłoby, jeśli ten łańcuch lub debuger zainicjowany stosu wywołań), `ppChain` będzie mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="7c417-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c417-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c417-108">Remarks</span></span>  
 <span data-ttu-id="7c417-109">Łańcucha wywołania może być w innym wątku, jeśli wywołanie zostało organizowanego między wątkami.</span><span class="sxs-lookup"><span data-stu-id="7c417-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c417-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c417-110">Requirements</span></span>  
 <span data-ttu-id="7c417-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c417-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c417-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c417-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c417-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c417-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c417-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c417-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
