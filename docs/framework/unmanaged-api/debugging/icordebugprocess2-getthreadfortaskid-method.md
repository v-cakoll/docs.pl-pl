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
ms.openlocfilehash: 11acf997b2efd74bc8394d830f36d3acbd1eef56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137201"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="c0cab-102">ICorDebugProcess2::GetThreadForTaskID — Metoda</span><span class="sxs-lookup"><span data-stu-id="c0cab-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="c0cab-103">Pobiera wątek, w którym wykonywane jest zadanie o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="c0cab-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0cab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0cab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0cab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0cab-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="c0cab-106">podczas Identyfikator zadania.</span><span class="sxs-lookup"><span data-stu-id="c0cab-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="c0cab-107">określoną Wskaźnik do adresu obiektu ICorDebugThread2, który reprezentuje wątek do pobrania.</span><span class="sxs-lookup"><span data-stu-id="c0cab-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0cab-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0cab-108">Remarks</span></span>  
 <span data-ttu-id="c0cab-109">Na hoście można ustawić identyfikator zadania za pomocą metody [ICLRTask:: SetTaskIdentifier —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c0cab-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0cab-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0cab-110">Requirements</span></span>  
 <span data-ttu-id="c0cab-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0cab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0cab-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c0cab-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0cab-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c0cab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0cab-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0cab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
