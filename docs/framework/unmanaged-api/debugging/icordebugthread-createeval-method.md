---
title: ICorDebugThread::CreateEval — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
ms.openlocfilehash: 0c622e0eba27f501446d2b7d9d264ee0834e869c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133618"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="c2f30-102">ICorDebugThread::CreateEval — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2f30-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="c2f30-103">Tworzy obiekt ICorDebugEval, który zbiera i udostępnia funkcje tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c2f30-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f30-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2f30-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2f30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2f30-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="c2f30-106">określoną Wskaźnik do adresu obiektu `ICorDebugEval`, który zbiera i udostępnia funkcje tego wątku.</span><span class="sxs-lookup"><span data-stu-id="c2f30-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2f30-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2f30-107">Remarks</span></span>  
 <span data-ttu-id="c2f30-108">Obiekt oceny wypycha nowy łańcuch w wątku przed wykonaniem jego obliczenia.</span><span class="sxs-lookup"><span data-stu-id="c2f30-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="c2f30-109">Spowoduje to przerwanie obliczeń aktualnie wykonywanych na wątku do momentu zakończenia szacowania.</span><span class="sxs-lookup"><span data-stu-id="c2f30-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2f30-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2f30-110">Requirements</span></span>  
 <span data-ttu-id="c2f30-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2f30-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2f30-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c2f30-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2f30-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2f30-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2f30-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2f30-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
