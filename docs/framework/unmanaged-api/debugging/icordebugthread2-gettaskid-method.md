---
title: ICorDebugThread2::GetTaskID — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1272df17a9a9a500b84f62914811b8d109bf3cdd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768951"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="135e8-102">ICorDebugThread2::GetTaskID — Metoda</span><span class="sxs-lookup"><span data-stu-id="135e8-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="135e8-103">Pobiera identyfikator zadania uruchomione w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="135e8-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="135e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="135e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="135e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="135e8-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="135e8-106">[out] Wskaźnik do identyfikatora zadania uruchamiane w wątku, reprezentowane przez ten obiekt icordebugthread2 —.</span><span class="sxs-lookup"><span data-stu-id="135e8-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="135e8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="135e8-107">Remarks</span></span>  
 <span data-ttu-id="135e8-108">Zadanie może być uruchomiony tylko w wątku, jeśli wątek jest skojarzona z połączeniem.</span><span class="sxs-lookup"><span data-stu-id="135e8-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="135e8-109">`GetTaskID` Zwraca zero `pTaskId` Jeśli wątek nie jest skojarzona z połączeniem.</span><span class="sxs-lookup"><span data-stu-id="135e8-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="135e8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="135e8-110">Requirements</span></span>  
 <span data-ttu-id="135e8-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="135e8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="135e8-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="135e8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="135e8-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="135e8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="135e8-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="135e8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
