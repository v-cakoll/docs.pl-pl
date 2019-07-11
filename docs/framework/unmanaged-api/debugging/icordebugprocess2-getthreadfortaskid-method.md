---
title: ICorDebugProcess2::GetThreadForTaskID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85040a31966a92ead6ca4786f62852f17923056
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736922"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="e22c5-102">ICorDebugProcess2::GetThreadForTaskID — Metoda</span><span class="sxs-lookup"><span data-stu-id="e22c5-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="e22c5-103">Pobiera wątku, na którym jest wykonywane zadanie o podanym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="e22c5-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e22c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e22c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e22c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e22c5-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="e22c5-106">[in] Identyfikator zadania.</span><span class="sxs-lookup"><span data-stu-id="e22c5-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="e22c5-107">[out] Wskaźnik na adres icordebugthread2 — obiekt, który reprezentuje wątków, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="e22c5-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e22c5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e22c5-108">Remarks</span></span>  
 <span data-ttu-id="e22c5-109">Hosta można ustawić identyfikator zadania przy użyciu [iclrtask::settaskidentifier —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e22c5-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e22c5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e22c5-110">Requirements</span></span>  
 <span data-ttu-id="e22c5-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e22c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e22c5-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e22c5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e22c5-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e22c5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e22c5-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e22c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
