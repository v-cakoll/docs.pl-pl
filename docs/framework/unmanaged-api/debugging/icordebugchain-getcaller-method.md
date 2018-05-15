---
title: ICorDebugChain::GetCaller — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0b5d702e9718ce6ac537beae67fc190b152b9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="d011d-102">ICorDebugChain::GetCaller — Metoda</span><span class="sxs-lookup"><span data-stu-id="d011d-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="d011d-103">Pobiera łańcuch, który wywołuje ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="d011d-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d011d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d011d-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d011d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d011d-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="d011d-106">[out] Wskaźnik do adresu ICorDebugChain obiekt, który reprezentuje łańcucha wywołania.</span><span class="sxs-lookup"><span data-stu-id="d011d-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="d011d-107">Jeśli ten łańcuch samorzutnie została wywołana (jak byłoby, jeśli ten łańcuch lub debuger zainicjowany stosu wywołań), `ppChain` będzie mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="d011d-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d011d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d011d-108">Remarks</span></span>  
 <span data-ttu-id="d011d-109">Łańcucha wywołania może być w innym wątku, jeśli wywołanie zostało organizowanego między wątkami.</span><span class="sxs-lookup"><span data-stu-id="d011d-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d011d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d011d-110">Requirements</span></span>  
 <span data-ttu-id="d011d-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d011d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d011d-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d011d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d011d-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d011d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d011d-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d011d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
