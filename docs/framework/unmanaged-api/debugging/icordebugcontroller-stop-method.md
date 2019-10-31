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
ms.openlocfilehash: c8c6b40f7a9c63a577140209eed65436040addcb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125388"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="f9e56-102">ICorDebugController::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9e56-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="f9e56-103">Wykonuje przerwanie w ramach wszystkich wątków, które uruchamiają kod zarządzany w procesie.</span><span class="sxs-lookup"><span data-stu-id="f9e56-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e56-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9e56-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9e56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9e56-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="f9e56-106">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="f9e56-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9e56-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9e56-107">Remarks</span></span>  
 <span data-ttu-id="f9e56-108">`Stop` wykonuje przerwanie w ramach wszystkich wątków uruchamiających kod zarządzany w procesie.</span><span class="sxs-lookup"><span data-stu-id="f9e56-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="f9e56-109">W trakcie sesji debugowania tylko zarządzanej wątki niezarządzane mogą nadal działać (ale będą blokowane podczas próby wywołania kodu zarządzanego).</span><span class="sxs-lookup"><span data-stu-id="f9e56-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="f9e56-110">W trakcie sesji debugowania międzyoperacyjności wątki niezarządzane również zostaną zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="f9e56-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="f9e56-111">Wartość `dwTimeoutIgnored` jest obecnie ignorowana i traktowana jako NIESKOŃCZONa (-1).</span><span class="sxs-lookup"><span data-stu-id="f9e56-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="f9e56-112">Jeśli z powodu zakleszczenia nie powiedzie się, wszystkie wątki są zawieszone i zwracany jest E_TIMEOUT.</span><span class="sxs-lookup"><span data-stu-id="f9e56-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9e56-113">`Stop` jest jedyną metodą synchroniczną w interfejsie API debugowania.</span><span class="sxs-lookup"><span data-stu-id="f9e56-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="f9e56-114">Gdy `Stop` zwraca S_OK, proces jest zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="f9e56-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="f9e56-115">Nie podano wywołania zwrotnego, aby powiadomić detektory zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="f9e56-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="f9e56-116">Debuger musi wywołać [ICorDebugController:: Kontynuuj](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby umożliwić wznowienie procesu.</span><span class="sxs-lookup"><span data-stu-id="f9e56-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="f9e56-117">Debuger zachowuje licznik zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="f9e56-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="f9e56-118">Gdy licznik spadnie do zera, kontroler zostanie wznowiony.</span><span class="sxs-lookup"><span data-stu-id="f9e56-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="f9e56-119">Każde wywołanie `Stop` lub każdego wysłanego wywołania zwrotnego zwiększa licznik.</span><span class="sxs-lookup"><span data-stu-id="f9e56-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="f9e56-120">Każde wywołanie `ICorDebugController::Continue` zmniejsza licznik.</span><span class="sxs-lookup"><span data-stu-id="f9e56-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9e56-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9e56-121">Requirements</span></span>  
 <span data-ttu-id="f9e56-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9e56-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9e56-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f9e56-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9e56-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f9e56-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9e56-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9e56-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e56-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9e56-126">See also</span></span>
