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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ecb4f8a5519fb819161ed917ad03d2537bd9551
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645243"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="cecc8-102">ICorDebugChain::GetNext — Metoda</span><span class="sxs-lookup"><span data-stu-id="cecc8-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="cecc8-103">Pobiera łańcuch następnej ramki dla wątku.</span><span class="sxs-lookup"><span data-stu-id="cecc8-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cecc8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cecc8-104">Syntax</span></span>  
  
```  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cecc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cecc8-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="cecc8-106">[out] Wskaźnik na adres icordebugchain — obiekt, który reprezentuje łańcuch następnej ramki dla wątku.</span><span class="sxs-lookup"><span data-stu-id="cecc8-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="cecc8-107">Jeśli ten łańcuch jest ostatni łańcucha `ppChain` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="cecc8-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cecc8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cecc8-108">Requirements</span></span>  
 <span data-ttu-id="cecc8-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cecc8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cecc8-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cecc8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cecc8-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cecc8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cecc8-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cecc8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
