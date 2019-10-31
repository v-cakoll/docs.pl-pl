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
ms.openlocfilehash: ab3819d5c33f090fda1ca9c3dccb5d08ab8f84cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131457"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="ce8a6-102">ICorDebugManagedCallback2::MDANotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce8a6-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="ce8a6-103">Zapewnia powiadomienie, że wykonanie kodu napotkało asystenta zarządzanego debugowania (MDA) w debugowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce8a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce8a6-104">Syntax</span></span>  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce8a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce8a6-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="ce8a6-106">podczas Wskaźnik do interfejsu ICorDebugController, który uwidacznia proces lub domenę aplikacji, w której wystąpiło zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="ce8a6-107">Debuger nie powinien wprowadzać żadnych założeń dotyczących tego, czy kontroler jest procesem czy domeną aplikacji, chociaż zawsze może wysyłać zapytania do interfejsu w celu określenia.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ce8a6-108">podczas Wskaźnik do interfejsu ICorDebugThread, który uwidacznia zarządzany wątek, w którym wystąpiło zdarzenie debugowania.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="ce8a6-109">Jeśli zdarzenie MDA wystąpił w niezarządzanym wątku, wartość `pThread` będzie równa null.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="ce8a6-110">Musisz uzyskać identyfikator wątku systemu operacyjnego (OS) z samego obiektu MDA.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="ce8a6-111">podczas Wskaźnik do interfejsu [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) , który UWIDACZNIA informacje MDA.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce8a6-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce8a6-112">Remarks</span></span>  
 <span data-ttu-id="ce8a6-113">MDA jest ostrzeżeniem heurystycznym i nie wymaga żadnej jawnej akcji debugera z wyjątkiem wywołania [ICorDebugController:: Kontynuuj](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby wznowić wykonywanie debugowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="ce8a6-114">Środowisko uruchomieniowe języka wspólnego (CLR) może określić, które MDA są wywoływane i które dane znajdują się w dowolnym punkcie.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="ce8a6-115">W związku z tym debugery nie powinny kompilować żadnej funkcjonalności wymagającej określonych wzorców MDA.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="ce8a6-116">MDA może zostać umieszczona w kolejce i wyzwolona wkrótce po wystąpieniu MDA.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="ce8a6-117">Taka sytuacja może wystąpić, jeśli środowisko uruchomieniowe musi czekać, aż osiągnie bezpieczny punkt do uruchomienia MDA, zamiast wyzwalać zdarzenie MDA po jego napotkaniu.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="ce8a6-118">Oznacza to również, że środowisko uruchomieniowe może uruchamiać wiele MDA w jednym zestawie wywołań zwrotnych umieszczonych w kolejce (podobnie jak w przypadku operacji "Attach").</span><span class="sxs-lookup"><span data-stu-id="ce8a6-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="ce8a6-119">Debuger powinien zwolnić odwołanie do wystąpienia `ICorDebugMDA` natychmiast po powrocie z wywołania zwrotnego `MDANotification`, aby umożliwić środowisku CLR odtwarzanie pamięci używanej przez zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="ce8a6-120">Zwolnienie wystąpienia może zwiększyć wydajność w przypadku uruchamiania wielu MDA.</span><span class="sxs-lookup"><span data-stu-id="ce8a6-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce8a6-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce8a6-121">Requirements</span></span>  
 <span data-ttu-id="ce8a6-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce8a6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce8a6-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ce8a6-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce8a6-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ce8a6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce8a6-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce8a6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8a6-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce8a6-126">See also</span></span>

- [<span data-ttu-id="ce8a6-127">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ce8a6-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ce8a6-128">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce8a6-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="ce8a6-129">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce8a6-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
