---
title: "ICorDebugChain::GetActiveFrame — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5de327c1579d05f6ae4a440fc76a3fb9ee99b13
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="4a091-102">ICorDebugChain::GetActiveFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a091-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="4a091-103">Pobiera aktywny (to znaczy najnowszych) ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="4a091-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a091-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a091-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a091-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a091-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="4a091-106">[out] Wskaźnik do adresu ICorDebugFrame obiekt, który reprezentuje aktywne (oznacza to, że najnowsze) ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="4a091-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a091-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a091-107">Remarks</span></span>  
 <span data-ttu-id="4a091-108">Jeśli nie jest dostępne nie ramki stosu zarządzanych `ppFrame` jest ustawiony na wartość null.</span><span class="sxs-lookup"><span data-stu-id="4a091-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="4a091-109">Jeśli aktywną ramkę nie jest dostępny, połączenie powiedzie się i `ppFrame` będzie mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="4a091-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="4a091-110">Aktywne ramek nie będą dostępne, łańcuchy inicjowane z powodu CHAIN_ENTER_UNMANAGED i niektóre łańcuchów inicjowane z powodu CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="4a091-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="4a091-111">Zobacz cordebugchainreason — wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="4a091-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a091-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a091-112">Requirements</span></span>  
 <span data-ttu-id="4a091-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a091-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a091-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a091-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a091-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a091-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a091-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a091-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
