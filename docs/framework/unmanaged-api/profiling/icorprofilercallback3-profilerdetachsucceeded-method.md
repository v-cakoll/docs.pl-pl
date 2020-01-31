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
ms.openlocfilehash: b96a8930c24275546b0aac9fa650cf5447ef4ef2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865418"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="ac7d5-102">ICorProfilerCallback3::ProfilerDetachSucceeded — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac7d5-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="ac7d5-103">Powiadamia program profilujący, że aparat plików wykonywalnych języka wspólnego (CLR) ma zwolnić plik DLL profilera.</span><span class="sxs-lookup"><span data-stu-id="ac7d5-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac7d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac7d5-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ac7d5-105">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="ac7d5-105">Return Value</span></span>  
 <span data-ttu-id="ac7d5-106">Wartość zwracana z tego wywołania zwrotnego jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="ac7d5-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac7d5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac7d5-107">Remarks</span></span>  
 <span data-ttu-id="ac7d5-108">Wywołanie zwrotne `ProfilerDetachSucceeded` jest emitowane po zakończeniu przez wszystkie wątki kodu profilera.</span><span class="sxs-lookup"><span data-stu-id="ac7d5-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="ac7d5-109">Gdy ta metoda jest wywoływana, profiler powinien wykonać wszystkie ostatnie zadania, które nie są odpowiednie dla destruktora, takie jak powiadamianie jego interfejsu użytkownika lub składnika rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="ac7d5-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="ac7d5-110">Jednak Profiler nie może wywoływać funkcji w interfejsach, które są dostarczane przez środowisko CLR w trakcie tego wywołania zwrotnego (takiego jak interfejsy [ICorProfilerInfo](icorprofilerinfo-interface.md) lub `IMetaData*`).</span><span class="sxs-lookup"><span data-stu-id="ac7d5-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="ac7d5-111">Środowisko CLR tworzy wpis w dzienniku zdarzeń aplikacji systemu Windows, aby wskazać, że operacja odłączenia zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ac7d5-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="ac7d5-112">Po powrocie profilera z tego wywołania zwrotnego środowisko CLR zwalnia obiekt profilera i zwalnia plik Profiler DLL.</span><span class="sxs-lookup"><span data-stu-id="ac7d5-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="ac7d5-113">W związku z tym Profiler nie może wykonywać żadnych akcji, które mogłyby spowodować wystąpienie w pliku DLL profilera po powrocie z tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ac7d5-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="ac7d5-114">Na przykład nie może tworzyć wątków ani rejestrować wywołań zwrotnych czasomierza.</span><span class="sxs-lookup"><span data-stu-id="ac7d5-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac7d5-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac7d5-115">Requirements</span></span>  
 <span data-ttu-id="ac7d5-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac7d5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac7d5-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ac7d5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac7d5-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ac7d5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac7d5-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac7d5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac7d5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac7d5-120">See also</span></span>

- [<span data-ttu-id="ac7d5-121">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="ac7d5-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="ac7d5-122">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac7d5-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ac7d5-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="ac7d5-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ac7d5-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="ac7d5-124">Profiling</span></span>](index.md)
