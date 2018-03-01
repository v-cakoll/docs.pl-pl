---
title: "ICorDebugThread2::GetTaskID — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1b94478a0dfb8cc4d90dea611620238024634799
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="8a559-102">ICorDebugThread2::GetTaskID — Metoda</span><span class="sxs-lookup"><span data-stu-id="8a559-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="8a559-103">Pobiera identyfikator zadania uruchomione w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="8a559-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a559-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a559-104">Syntax</span></span>  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a559-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a559-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="8a559-106">[out] Wskaźnik do identyfikatora zadania uruchamiane w wątku reprezentowany przez ten obiekt ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="8a559-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a559-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a559-107">Remarks</span></span>  
 <span data-ttu-id="8a559-108">Zadanie może być uruchomiony tylko w wątku, jeśli wątek jest skojarzone z połączeniem.</span><span class="sxs-lookup"><span data-stu-id="8a559-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="8a559-109">`GetTaskID`Zwraca zero `pTaskId` Jeśli wątek nie jest skojarzone z połączeniem.</span><span class="sxs-lookup"><span data-stu-id="8a559-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a559-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a559-110">Requirements</span></span>  
 <span data-ttu-id="8a559-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a559-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a559-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a559-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a559-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a559-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a559-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a559-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
