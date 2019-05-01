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
ms.openlocfilehash: 2016795e7b2c0588e2bd69e764fb96f7f90b24d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994074"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="30afb-102">ICorDebugThread::CreateEval — Metoda</span><span class="sxs-lookup"><span data-stu-id="30afb-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="30afb-103">Tworzy obiekt ICorDebugEval, który zbiera i udostępnia funkcje to ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="30afb-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30afb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="30afb-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30afb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30afb-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="30afb-106">[out] Wskaźnik na adres `ICorDebugEval` obiektu, który zbiera i udostępnia funkcje tego wątku.</span><span class="sxs-lookup"><span data-stu-id="30afb-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30afb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30afb-107">Remarks</span></span>  
 <span data-ttu-id="30afb-108">Obiekt oceny będzie umożliwiać wypychanie powiadomień nowy łańcuch w wątku, przed wykonaniem jego obliczeń.</span><span class="sxs-lookup"><span data-stu-id="30afb-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="30afb-109">Przerywa to działanie obliczeń obecnie wykonywane w wątku do chwili zakończenia oceny.</span><span class="sxs-lookup"><span data-stu-id="30afb-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30afb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="30afb-110">Requirements</span></span>  
 <span data-ttu-id="30afb-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30afb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30afb-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30afb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30afb-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30afb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30afb-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30afb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
