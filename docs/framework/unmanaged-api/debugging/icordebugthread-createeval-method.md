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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e2d99d85a6e6b09558e5941d08a7f522aaf66cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421820"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="ddff1-102">ICorDebugThread::CreateEval — Metoda</span><span class="sxs-lookup"><span data-stu-id="ddff1-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="ddff1-103">Tworzy obiekt ICorDebugEval, który zbiera i udostępnia funkcje tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="ddff1-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddff1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddff1-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddff1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddff1-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="ddff1-106">[out] Wskaźnik do adresu `ICorDebugEval` obiektu, który zbiera i udostępnia funkcje tego wątku.</span><span class="sxs-lookup"><span data-stu-id="ddff1-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddff1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddff1-107">Remarks</span></span>  
 <span data-ttu-id="ddff1-108">Obiekt oceny przeprowadzi wypychanie nowy łańcuch w wątku, przed wykonaniem jego obliczeń.</span><span class="sxs-lookup"><span data-stu-id="ddff1-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="ddff1-109">To przerwania obliczenia aktualnie wykonywane w wątku dopiero po zakończeniu oceny.</span><span class="sxs-lookup"><span data-stu-id="ddff1-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddff1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddff1-110">Requirements</span></span>  
 <span data-ttu-id="ddff1-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddff1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddff1-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ddff1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ddff1-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddff1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddff1-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddff1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
