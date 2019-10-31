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
ms.openlocfilehash: 5a07550d44857526e8ab4ded9f1827ef12e3bba4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192138"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="2826f-102">ICorDebugChain::GetCaller — Metoda</span><span class="sxs-lookup"><span data-stu-id="2826f-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="2826f-103">Pobiera łańcuch, który wywołał ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="2826f-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2826f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2826f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2826f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2826f-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="2826f-106">określoną Wskaźnik do adresu obiektu ICorDebugChain, który reprezentuje łańcuch wywoływania.</span><span class="sxs-lookup"><span data-stu-id="2826f-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="2826f-107">Jeśli ten łańcuch został wywołany spontanicznie (tak jak w przypadku tego łańcucha lub debugera zainicjował stos wywołań), `ppChain` będzie miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="2826f-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2826f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2826f-108">Remarks</span></span>  
 <span data-ttu-id="2826f-109">Łańcuch wywołujący może znajdować się w innym wątku, jeśli wywołanie zostało zorganizowane między wątkami.</span><span class="sxs-lookup"><span data-stu-id="2826f-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2826f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2826f-110">Requirements</span></span>  
 <span data-ttu-id="2826f-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2826f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2826f-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2826f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2826f-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2826f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2826f-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2826f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
