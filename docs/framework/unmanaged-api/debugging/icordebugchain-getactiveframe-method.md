---
title: ICorDebugChain::GetActiveFrame — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c14b48a29993a65a0a0ab9fcb63bcb1e0d882042
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645373"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="1294c-102">ICorDebugChain::GetActiveFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="1294c-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="1294c-103">Pobiera aktywny (oznacza to, najbardziej aktualną) ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="1294c-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1294c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1294c-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1294c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1294c-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="1294c-106">[out] Wskaźnik na adres ICorDebugFrame obiekt, który reprezentuje aktywny (oznacza to, najbardziej aktualną) ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="1294c-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1294c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1294c-107">Remarks</span></span>  
 <span data-ttu-id="1294c-108">Jeśli nie ramki zarządzanego stosu jest dostępna, `ppFrame` jest ustawiona na wartość null.</span><span class="sxs-lookup"><span data-stu-id="1294c-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="1294c-109">Jeśli aktywnej ramki jest niedostępny, wywołanie zostanie wykonane pomyślnie i `ppFrame` będzie miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="1294c-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="1294c-110">Aktywne ramek nie będą dostępne, łańcuchy inicjowane z powodu CHAIN_ENTER_UNMANAGED i niektóre łańcuchów inicjowane z powodu CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="1294c-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="1294c-111">Zobacz cordebugchainreason — wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="1294c-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1294c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1294c-112">Requirements</span></span>  
 <span data-ttu-id="1294c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1294c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1294c-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1294c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1294c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1294c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1294c-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1294c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
