---
title: "ICorDebugController::Stop — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Stop
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b92d07f8d162123d20c6861d204d73789060906
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="bb7fd-102">ICorDebugController::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb7fd-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="bb7fd-103">Wykonuje wspólne Zatrzymaj wszystkie wątki uruchomione kodu zarządzanego w procesie.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb7fd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb7fd-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb7fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb7fd-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="bb7fd-106">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb7fd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb7fd-107">Remarks</span></span>  
 <span data-ttu-id="bb7fd-108">`Stop`wykonuje kod stop współpracy na wszystkie wątki uruchomione zarządzanych w procesie.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="bb7fd-109">Podczas sesji debugowania tylko do zarządzanych wątków niezarządzane może kontynuować działanie (ale będą blokowane podczas próby wywołania kodu zarządzanego).</span><span class="sxs-lookup"><span data-stu-id="bb7fd-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="bb7fd-110">Podczas sesji debugowania interop również zostaną zatrzymane niezarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="bb7fd-111">`dwTimeoutIgnored` Wartość jest obecnie zignorowana i potraktowana jako INFINITE (-1).</span><span class="sxs-lookup"><span data-stu-id="bb7fd-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="bb7fd-112">Jeśli współpracy stop zakończy się niepowodzeniem z powodu zakleszczenia, wszystkie wątki są wstrzymane i E_TIMEOUT jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb7fd-113">`Stop`jest to tylko synchroniczne metoda w interfejsie API debugowania.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="bb7fd-114">Gdy `Stop` zwraca wartość S_OK, proces został zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="bb7fd-115">Bez wywołania zwrotnego ma nadane uprawnienia do powiadamiania słuchaczy ogranicznika.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="bb7fd-116">Debuger musi wywołać [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) umożliwia wznowienie procesu.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="bb7fd-117">Debuger obsługuje licznika stop.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="bb7fd-118">Gdy licznik przechodzi do zera, kontrolerem jest wznawiana.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="bb7fd-119">Każde wywołanie `Stop` lub każdego wysyłanego wywołania zwrotnego zwiększa licznik.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="bb7fd-120">Każde wywołanie `ICorDebugController::Continue` zmniejsza licznika.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb7fd-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb7fd-121">Requirements</span></span>  
 <span data-ttu-id="bb7fd-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb7fd-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb7fd-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb7fd-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb7fd-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb7fd-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb7fd-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb7fd-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb7fd-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb7fd-126">See Also</span></span>  
 
