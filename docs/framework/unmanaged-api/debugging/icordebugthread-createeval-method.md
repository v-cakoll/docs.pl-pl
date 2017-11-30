---
title: "ICorDebugThread::CreateEval — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateEval
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aebabf12e6dcf12f0e1e1f24ec2ad69ea55ec86c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="01550-102">ICorDebugThread::CreateEval — Metoda</span><span class="sxs-lookup"><span data-stu-id="01550-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="01550-103">Tworzy obiekt ICorDebugEval, który zbiera i udostępnia funkcje tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="01550-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01550-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01550-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01550-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01550-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="01550-106">[out] Wskaźnik do adresu `ICorDebugEval` obiektu, który zbiera i udostępnia funkcje tego wątku.</span><span class="sxs-lookup"><span data-stu-id="01550-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01550-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01550-107">Remarks</span></span>  
 <span data-ttu-id="01550-108">Obiekt oceny przeprowadzi wypychanie nowy łańcuch w wątku, przed wykonaniem jego obliczeń.</span><span class="sxs-lookup"><span data-stu-id="01550-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="01550-109">To przerwania obliczenia aktualnie wykonywane w wątku dopiero po zakończeniu oceny.</span><span class="sxs-lookup"><span data-stu-id="01550-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01550-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01550-110">Requirements</span></span>  
 <span data-ttu-id="01550-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01550-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01550-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01550-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01550-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01550-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01550-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01550-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
