---
title: ICorDebugChain::GetCallee — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: ba9a4e32216fd6fad285397bfc48fbc54f602b88
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894649"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="861e5-102">ICorDebugChain::GetCallee — Metoda</span><span class="sxs-lookup"><span data-stu-id="861e5-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="861e5-103">Pobiera łańcuch, który został wywołany przez ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="861e5-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="861e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="861e5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="861e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="861e5-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="861e5-106">określoną Wskaźnik do adresu obiektu ICorDebugChain, który reprezentuje wywołany łańcuch.</span><span class="sxs-lookup"><span data-stu-id="861e5-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="861e5-107">Jeśli ten łańcuch jest obecnie wykonywany (oznacza to, że jeśli ten łańcuch nie oczekuje na zwrócenie wywołanego łańcucha), `ppChain` będzie miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="861e5-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="861e5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="861e5-108">Remarks</span></span>  
 <span data-ttu-id="861e5-109">Ten łańcuch będzie czekał na zwrócenie wywoływanego łańcucha przed wznowieniem wykonywania.</span><span class="sxs-lookup"><span data-stu-id="861e5-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="861e5-110">Wywołany łańcuch może znajdować się w innym wątku w przypadku wywołań zorganizowanych między wątkami.</span><span class="sxs-lookup"><span data-stu-id="861e5-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="861e5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="861e5-111">Requirements</span></span>  
 <span data-ttu-id="861e5-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="861e5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="861e5-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="861e5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="861e5-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="861e5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="861e5-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="861e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
