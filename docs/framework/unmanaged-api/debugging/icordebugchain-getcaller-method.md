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
ms.openlocfilehash: d11693473dc4ed4438bbcad7f95c1b20adc1062b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744972"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="bcc5c-102">ICorDebugChain::GetCaller — Metoda</span><span class="sxs-lookup"><span data-stu-id="bcc5c-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="bcc5c-103">Pobiera łańcucha, który wywołuje ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="bcc5c-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc5c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bcc5c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcc5c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcc5c-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="bcc5c-106">[out] Wskaźnik na adres icordebugchain — obiekt, który reprezentuje łańcucha wywołania.</span><span class="sxs-lookup"><span data-stu-id="bcc5c-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="bcc5c-107">Jeśli ten łańcuch spontanicznie została wywołana (tak jak w przypadku gdy ten łańcuch lub debuger zainicjowano stosu wywołań), `ppChain` będzie miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="bcc5c-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcc5c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bcc5c-108">Remarks</span></span>  
 <span data-ttu-id="bcc5c-109">Łańcucha wywołania może być w innym wątku, jeśli połączenie zostało organizowane przez wątków.</span><span class="sxs-lookup"><span data-stu-id="bcc5c-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcc5c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bcc5c-110">Requirements</span></span>  
 <span data-ttu-id="bcc5c-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcc5c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcc5c-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcc5c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcc5c-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcc5c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcc5c-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcc5c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
