---
title: ICorDebugChain::GetNext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
ms.openlocfilehash: 47a90ed63ae217cb150f392ad9196f8d0d5764e3
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894642"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="d5c94-102">ICorDebugChain::GetNext — Metoda</span><span class="sxs-lookup"><span data-stu-id="d5c94-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="d5c94-103">Pobiera następny łańcuch ramek dla wątku.</span><span class="sxs-lookup"><span data-stu-id="d5c94-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c94-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5c94-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5c94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5c94-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="d5c94-106">określoną Wskaźnik do adresu obiektu ICorDebugChain, który reprezentuje następny łańcuch ramek dla wątku.</span><span class="sxs-lookup"><span data-stu-id="d5c94-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="d5c94-107">Jeśli ten łańcuch jest ostatnim łańcuchem, `ppChain` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="d5c94-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c94-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5c94-108">Requirements</span></span>  
 <span data-ttu-id="d5c94-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5c94-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5c94-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5c94-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5c94-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d5c94-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5c94-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c94-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
