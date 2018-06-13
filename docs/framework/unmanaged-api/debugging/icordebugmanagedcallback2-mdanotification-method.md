---
title: ICorDebugManagedCallback2::MDANotification — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64b09c173e2f66d4c650083cc12f8a0ac2c92007
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417231"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="0005e-102">ICorDebugManagedCallback2::MDANotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="0005e-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="0005e-103">Zapewnia powiadomienie, że wykonywanie kodu napotkał zarządzany Asystent debugowania (MDA) w aplikacji, która jest debugowana.</span><span class="sxs-lookup"><span data-stu-id="0005e-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0005e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0005e-104">Syntax</span></span>  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0005e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0005e-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="0005e-106">[in] Wskaźnik do ICorDebugController — interfejs udostępniający procesu lub domena aplikacji, w którym wystąpił MDA.</span><span class="sxs-lookup"><span data-stu-id="0005e-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="0005e-107">Debuger nie należy podejmować żadnych założeń, czy kontroler jest procesem lub domena aplikacji, mimo że zawsze można wykonać kwerendy interfejs umożliwiający określenie.</span><span class="sxs-lookup"><span data-stu-id="0005e-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="0005e-108">[in] Wskaźnik do ICorDebugThread — interfejs udostępniający zarządzanego wątku, w którym wystąpiło zdarzenie debugowania.</span><span class="sxs-lookup"><span data-stu-id="0005e-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="0005e-109">Jeśli MDA wystąpił na niezarządzanego wątku, wartość `pThread` będzie mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="0005e-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="0005e-110">Od samego obiektu MDA, należy uzyskać identyfikator wątku systemu operacyjnego (systemu operacyjnego).</span><span class="sxs-lookup"><span data-stu-id="0005e-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="0005e-111">[in] Wskaźnik do [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interfejs, który opisuje informacje o MDA.</span><span class="sxs-lookup"><span data-stu-id="0005e-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0005e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0005e-112">Remarks</span></span>  
 <span data-ttu-id="0005e-113">MDA to ostrzeżenie heurystyczne i nie wymaga żadnych działań jawne debugera, z wyjątkiem wywołania [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) można wznowić wykonywania aplikacji, która jest debugowana.</span><span class="sxs-lookup"><span data-stu-id="0005e-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="0005e-114">Środowisko uruchomieniowe języka wspólnego (CLR) można określić, którego są uruchamiane mda i dane, które znajduje się w dowolnym danym MDA w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="0005e-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="0005e-115">W związku z tym debugery nie powinien utworzyć żadnej funkcji, które wymagają określonych wzorców MDA.</span><span class="sxs-lookup"><span data-stu-id="0005e-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="0005e-116">Mda mogą być umieszczone w kolejce i uruchamiany wkrótce po napotkaniu MDA.</span><span class="sxs-lookup"><span data-stu-id="0005e-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="0005e-117">Może to się zdarzyć, jeśli środowisko uruchomieniowe musi czekać, aż osiągnie punkt bezpieczne dla wyzwalania MDA, zamiast wyzwalania MDA po napotkaniu go.</span><span class="sxs-lookup"><span data-stu-id="0005e-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="0005e-118">Oznacza to również, że środowisko wykonawcze mogą wyzwalać liczba mda w pojedynczy zestaw umieszczonych w kolejce wywołania zwrotne (podobnie do operacji zdarzeń "Dołącz").</span><span class="sxs-lookup"><span data-stu-id="0005e-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="0005e-119">Debuger powinien zwolnienia odwołania do `ICorDebugMDA` wystąpienia natychmiast po powrocie ze `MDANotification` wywołania zwrotnego, aby umożliwić CLR do odtworzenia pamięci używane przez MDA.</span><span class="sxs-lookup"><span data-stu-id="0005e-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="0005e-120">Wydanie wystąpienia może zwiększyć wydajność, jeśli wiele mda są wyzwalania.</span><span class="sxs-lookup"><span data-stu-id="0005e-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0005e-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0005e-121">Requirements</span></span>  
 <span data-ttu-id="0005e-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0005e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0005e-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0005e-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0005e-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0005e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0005e-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0005e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0005e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0005e-126">See Also</span></span>  
 [<span data-ttu-id="0005e-127">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="0005e-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="0005e-128">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0005e-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="0005e-129">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="0005e-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
