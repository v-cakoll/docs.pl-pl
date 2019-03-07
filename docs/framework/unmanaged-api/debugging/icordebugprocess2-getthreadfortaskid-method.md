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
ms.openlocfilehash: aa1f6852544dddcdf514b14710ade3949818c93e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487322"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="46332-102">ICorDebugProcess2::GetThreadForTaskID — Metoda</span><span class="sxs-lookup"><span data-stu-id="46332-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="46332-103">Pobiera wątku, na którym jest wykonywane zadanie o podanym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="46332-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46332-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="46332-104">Syntax</span></span>  
  
```  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46332-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46332-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="46332-106">[in] Identyfikator zadania.</span><span class="sxs-lookup"><span data-stu-id="46332-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="46332-107">[out] Wskaźnik na adres icordebugthread2 — obiekt, który reprezentuje wątków, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="46332-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46332-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46332-108">Remarks</span></span>  
 <span data-ttu-id="46332-109">Hosta można ustawić identyfikator zadania przy użyciu [iclrtask::settaskidentifier —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="46332-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46332-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46332-110">Requirements</span></span>  
 <span data-ttu-id="46332-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46332-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46332-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46332-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46332-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46332-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46332-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46332-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
