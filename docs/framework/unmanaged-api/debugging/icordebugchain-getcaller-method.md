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
ms.openlocfilehash: a6d26924773e6ad505975402ec3ace150d02cc3a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894612"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="9c594-102">ICorDebugChain::GetCaller — Metoda</span><span class="sxs-lookup"><span data-stu-id="9c594-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="9c594-103">Pobiera łańcuch, który wywołał ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="9c594-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c594-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c594-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c594-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c594-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="9c594-106">określoną Wskaźnik do adresu obiektu ICorDebugChain, który reprezentuje łańcuch wywoływania.</span><span class="sxs-lookup"><span data-stu-id="9c594-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="9c594-107">Jeśli ten łańcuch został wywołany spontanicznie (tak jak w przypadku, gdy ten łańcuch lub debuger zainicjował stos wywołań), `ppChain` będzie miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="9c594-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c594-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c594-108">Remarks</span></span>  
 <span data-ttu-id="9c594-109">Łańcuch wywołujący może znajdować się w innym wątku, jeśli wywołanie zostało zorganizowane między wątkami.</span><span class="sxs-lookup"><span data-stu-id="9c594-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c594-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9c594-110">Requirements</span></span>  
 <span data-ttu-id="9c594-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c594-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c594-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9c594-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c594-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9c594-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c594-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c594-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
