---
title: ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8cff277179be761bb0dc78b02702e7d35ad4b6a9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779248"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="f4047-102">ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda</span><span class="sxs-lookup"><span data-stu-id="f4047-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="f4047-103">Powiadamia program profilujący, że środowisko uruchomieniowe języka wspólnego (CLR) zostanie zwolnienia biblioteki DLL profilera.</span><span class="sxs-lookup"><span data-stu-id="f4047-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4047-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4047-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f4047-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f4047-105">Return Value</span></span>  
 <span data-ttu-id="f4047-106">Wartość zwrócona przez to wywołanie zwrotne jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="f4047-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4047-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4047-107">Remarks</span></span>  
 <span data-ttu-id="f4047-108">`ProfilerDetachSucceeded` Wywołanie zwrotne zostało wydane po zamknięciu wszystkich wątków programu profilującego kodu.</span><span class="sxs-lookup"><span data-stu-id="f4047-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="f4047-109">Gdy ta metoda jest wywoływana, program profilujący, należy wykonać wszelkie zadania ostatniej chwili, które nie są odpowiednie dla jego destruktor, takie jak jego interfejsu użytkownika lub składnik rejestrowania zgłaszające.</span><span class="sxs-lookup"><span data-stu-id="f4047-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="f4047-110">Jednakże program profilujący nie mogą wywoływać funkcje dla interfejsów, które są dostarczane przez środowisko CLR Podczas tego wywołania zwrotnego (takie jak [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) lub `IMetaData*` interfejsów).</span><span class="sxs-lookup"><span data-stu-id="f4047-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="f4047-111">Środowisko CLR tworzy wpis w dzienniku zdarzeń aplikacji Windows, aby wskazać, czy operacja odłączenia powiodła się.</span><span class="sxs-lookup"><span data-stu-id="f4047-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="f4047-112">Po profiler zwraca z to wywołanie zwrotne, środowisko CLR zwalnia obiekt profilera i wyładowuje profiler DLL.</span><span class="sxs-lookup"><span data-stu-id="f4047-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="f4047-113">W związku z tym program profilujący nie musi wykonywać wszystkie akcje, które mogłoby spowodować wykonanie zapytania wewnątrz biblioteki DLL profilera po zwraca od to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="f4047-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="f4047-114">Na przykład nie musi tworzyć wątków lub rejestrowanie wywołań zwrotnych czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f4047-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4047-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4047-115">Requirements</span></span>  
 <span data-ttu-id="f4047-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4047-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4047-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f4047-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f4047-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4047-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4047-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4047-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4047-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4047-120">See also</span></span>

- [<span data-ttu-id="f4047-121">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="f4047-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="f4047-122">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="f4047-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f4047-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f4047-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f4047-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="f4047-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
