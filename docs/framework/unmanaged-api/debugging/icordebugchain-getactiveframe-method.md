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
ms.openlocfilehash: 2f67188539d5ad5523c255fbc663e990e1b8245f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894683"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="46802-102">ICorDebugChain::GetActiveFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="46802-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="46802-103">Pobiera aktywną (czyli ostatnią) ramkę w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="46802-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46802-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="46802-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46802-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46802-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="46802-106">określoną Wskaźnik do adresu obiektu ICorDebugFrame, który reprezentuje aktywną (czyli ostatnią) ramkę w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="46802-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46802-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46802-107">Remarks</span></span>  
 <span data-ttu-id="46802-108">Jeśli żadna ramka zarządzanego stosu nie jest dostępna `ppFrame` , jest ustawiona na wartość null.</span><span class="sxs-lookup"><span data-stu-id="46802-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="46802-109">Jeśli aktywna ramka jest niedostępna, wywołanie powiedzie się i `ppFrame` będzie miało wartość null.</span><span class="sxs-lookup"><span data-stu-id="46802-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="46802-110">Aktywne ramki nie będą dostępne dla łańcuchów inicjowanych z powodu CHAIN_ENTER_UNMANAGED, a w przypadku niektórych łańcuchów inicjowanych z powodu CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="46802-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="46802-111">Zobacz Wyliczenie CorDebugChainReason —.</span><span class="sxs-lookup"><span data-stu-id="46802-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46802-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46802-112">Requirements</span></span>  
 <span data-ttu-id="46802-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46802-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46802-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="46802-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46802-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="46802-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46802-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46802-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
