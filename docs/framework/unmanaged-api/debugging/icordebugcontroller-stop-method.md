---
title: ICorDebugController::Stop — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 724db8c5c8dbb5bf3ff8bc7202a60397180b7b38
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183394"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="3198b-102">ICorDebugController::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="3198b-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="3198b-103">Wykonuje wspólne stop we wszystkich wątkach, na których uruchomiono kod zarządzany w procesie.</span><span class="sxs-lookup"><span data-stu-id="3198b-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3198b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3198b-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3198b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3198b-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="3198b-106">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="3198b-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3198b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3198b-107">Remarks</span></span>  
 `Stop` <span data-ttu-id="3198b-108">wykonuje kod zatrzymania współpracy na wszystkie wątki uruchomione zarządzanych w procesie.</span><span class="sxs-lookup"><span data-stu-id="3198b-108">performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="3198b-109">Podczas sesji debugowania tylko do zarządzanych niezarządzanych wątków może kontynuować działanie (ale będą blokowane podczas próby wywołania kodu zarządzanego).</span><span class="sxs-lookup"><span data-stu-id="3198b-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="3198b-110">Podczas debugowania międzyoperacyjnego sesji również zostaną zatrzymane niezarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="3198b-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="3198b-111">`dwTimeoutIgnored` Wartość aktualnie jest ignorowany i traktowany jako NIESKOŃCZONE (-1).</span><span class="sxs-lookup"><span data-stu-id="3198b-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="3198b-112">Jeśli współpracy stop zakończy się niepowodzeniem z powodu zakleszczenia, wszystkie wątki są wstrzymywane i E_TIMEOUT jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="3198b-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  `Stop` <span data-ttu-id="3198b-113">jest tylko synchroniczne metody w interfejsie API debugowania.</span><span class="sxs-lookup"><span data-stu-id="3198b-113">is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="3198b-114">Gdy `Stop` zwraca wartość S_OK, proces został zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="3198b-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="3198b-115">Nie wywołania zwrotnego otrzymuje o ogranicznika.</span><span class="sxs-lookup"><span data-stu-id="3198b-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="3198b-116">Debuger musi wywołać [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) umożliwia wznowienie procesu.</span><span class="sxs-lookup"><span data-stu-id="3198b-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="3198b-117">Debuger obsługuje licznika zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="3198b-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="3198b-118">Gdy licznik zbliża się do zera, jest wznawiany kontrolera.</span><span class="sxs-lookup"><span data-stu-id="3198b-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="3198b-119">Każde wywołanie `Stop` lub każdego wysłane wywołanie zwrotne zwiększa wartość licznika.</span><span class="sxs-lookup"><span data-stu-id="3198b-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="3198b-120">Każde wywołanie `ICorDebugController::Continue` zmniejsza wartość licznika.</span><span class="sxs-lookup"><span data-stu-id="3198b-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3198b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3198b-121">Requirements</span></span>  
 <span data-ttu-id="3198b-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3198b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3198b-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3198b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3198b-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3198b-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3198b-125">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3198b-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3198b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3198b-126">See also</span></span>
