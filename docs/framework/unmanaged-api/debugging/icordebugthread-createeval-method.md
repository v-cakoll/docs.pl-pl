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
ms.openlocfilehash: f66ef88646c314502dcb610cec8ce822cab1fca2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379285"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="59ad3-102">ICorDebugThread::CreateEval — Metoda</span><span class="sxs-lookup"><span data-stu-id="59ad3-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="59ad3-103">Tworzy obiekt ICorDebugEval, który zbiera i udostępnia funkcje tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="59ad3-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ad3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59ad3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59ad3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="59ad3-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="59ad3-106">określoną Wskaźnik do adresu `ICorDebugEval` obiektu, który zbiera i udostępnia funkcjonalność tego wątku.</span><span class="sxs-lookup"><span data-stu-id="59ad3-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59ad3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59ad3-107">Remarks</span></span>  
 <span data-ttu-id="59ad3-108">Obiekt oceny wypycha nowy łańcuch w wątku przed wykonaniem jego obliczenia.</span><span class="sxs-lookup"><span data-stu-id="59ad3-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="59ad3-109">Spowoduje to przerwanie obliczeń aktualnie wykonywanych na wątku do momentu zakończenia szacowania.</span><span class="sxs-lookup"><span data-stu-id="59ad3-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ad3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59ad3-110">Requirements</span></span>  
 <span data-ttu-id="59ad3-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59ad3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ad3-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="59ad3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59ad3-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="59ad3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59ad3-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59ad3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
