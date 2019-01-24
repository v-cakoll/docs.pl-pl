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
ms.openlocfilehash: 90c805a5f1f1da990564034fc292562d5f933d71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608092"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="81785-102">ICorDebugManagedCallback2::MDANotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="81785-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="81785-103">Zapewnia powiadomienie napotkała wykonywania kodu zarządzanego Asystenta debugowania (MDA) w aplikacji, która jest debugowana.</span><span class="sxs-lookup"><span data-stu-id="81785-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81785-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81785-104">Syntax</span></span>  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81785-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81785-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="81785-106">[in] Wskaźnik do icordebugcontroller — interfejs, który przedstawia proces ani domeny aplikacji, w którym wystąpiło zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="81785-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="81785-107">Debuger nie powinna dokonywać żadnych założeń dotyczących tego, czy ma używać kontroler proces lub domenę aplikacji, mimo że zawsze można wykonać zapytanie interfejsu umożliwiają określenie.</span><span class="sxs-lookup"><span data-stu-id="81785-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="81785-108">[in] Wskaźnik do icordebugthread — interfejs, który udostępnia wątków zarządzanych, w którym wystąpiło zdarzenie debugowania.</span><span class="sxs-lookup"><span data-stu-id="81785-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="81785-109">Jeśli MDA wystąpił na niezarządzanych wątków, wartość `pThread` będzie miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="81785-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="81785-110">Identyfikator wątku systemu operacyjnego (OS) należy uzyskać od samego obiektu MDA.</span><span class="sxs-lookup"><span data-stu-id="81785-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="81785-111">[in] Wskaźnik do [icordebugmda —](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interfejsu, który udostępnia informacje MDA.</span><span class="sxs-lookup"><span data-stu-id="81785-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81785-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81785-112">Remarks</span></span>  
 <span data-ttu-id="81785-113">MDA heurystyczne ostrzeżenie i nie wymaga żadnych akcji jawne debugera, z wyjątkiem wywoływania [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) Aby wznowić wykonywanie aplikacji, która jest debugowana.</span><span class="sxs-lookup"><span data-stu-id="81785-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="81785-114">Środowisko uruchomieniowe języka wspólnego (CLR) można określić, które są uruchamiane mda i dane, które znajduje się w dowolnym danym MDA w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="81785-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="81785-115">W związku z tym debugery nie należy tworzyć żadnych funkcji wymagających określonych wzorców MDA.</span><span class="sxs-lookup"><span data-stu-id="81785-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="81785-116">MDA może być umieszczona w kolejce i uruchamiany wkrótce, po napotkaniu MDA.</span><span class="sxs-lookup"><span data-stu-id="81785-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="81785-117">Może się to zdarzyć, jeśli środowisko wykonawcze musi czekać, aż do napotkania punktu bezpieczne w celu wyzwalania MDA, zamiast wyzwalania MDA po napotkaniu go.</span><span class="sxs-lookup"><span data-stu-id="81785-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="81785-118">Oznacza to również, że środowisko uruchomieniowe może wyzwalać liczba mda w jednym zestawie umieszczonych w kolejce wywołania zwrotne (podobne do operacji zdarzeń "Dołącz").</span><span class="sxs-lookup"><span data-stu-id="81785-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="81785-119">Debuger powinien zwolnić odwołanie do `ICorDebugMDA` wystąpienia natychmiast po powrocie z `MDANotification` wywołanie zwrotne, aby umożliwić CLR odtwarzanie pamięci używane przez MDA.</span><span class="sxs-lookup"><span data-stu-id="81785-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="81785-120">Zwalnianie wystąpienie może zwiększyć wydajność, jeśli wiele mda są wyzwalania.</span><span class="sxs-lookup"><span data-stu-id="81785-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81785-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81785-121">Requirements</span></span>  
 <span data-ttu-id="81785-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81785-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81785-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81785-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81785-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81785-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81785-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81785-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81785-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81785-126">See also</span></span>
- [<span data-ttu-id="81785-127">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="81785-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="81785-128">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="81785-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="81785-129">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="81785-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
