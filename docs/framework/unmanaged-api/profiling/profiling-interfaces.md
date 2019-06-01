---
title: Interfejsy profilowania
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d97960a43e1d7ce625d96755a7c597a0425d0911
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457462"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="03920-102">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="03920-102">Profiling Interfaces</span></span>
<span data-ttu-id="03920-103">W tej sekcji opisano niezarządzane interfejsy, które umożliwiają profilowanie program, który jest wykonywany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="03920-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="03920-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="03920-104">In This Section</span></span>  
 [<span data-ttu-id="03920-105">ICLRProfiling, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="03920-106">Udostępnia [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metody, która umożliwia programowi profilującemu dołączanie do uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="03920-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="03920-107">ICorProfilerAssemblyReferenceProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="03920-108">Włącza program profilujący do informowania CLR odwołania do zestawów, które doda profilera w [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="03920-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="03920-109">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="03920-110">Udostępnia metody, które są używane przez środowisko CLR, aby powiadomić profiler kodu po wystąpieniu zdarzenia, dla których zostały zasubskrybowane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="03920-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="03920-111">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="03920-112">Rozszerza `ICorProfilerCallback` interfejs za pomocą wywołania zwrotne obsługiwane w programie .NET Framework 2.0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="03920-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="03920-113">ICorProfilerCallback3, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="03920-114">Udostępnia metody wywołania zwrotnego, które środowisko CLR używa do komunikowania się dołączania i odłączania informacje o stanie do programu profilującego.</span><span class="sxs-lookup"><span data-stu-id="03920-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="03920-115">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="03920-116">Udostępnia metody wywołania zwrotnego, które środowisko CLR używa do przekazywania informacji do programu profilującego.</span><span class="sxs-lookup"><span data-stu-id="03920-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="03920-117">ICorProfilerCallback5, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="03920-118">Dostarcza metodę, która identyfikuje przechodnie zamknięcia obiektów, które odwołują się obiekty główne kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="03920-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="03920-119">ICorProfilerCallback6, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="03920-120">Zapewnia metodę wywołania zwrotnego, która używa środowiska CLR, aby powiadomić profiler, która jest ładowana zestawu.</span><span class="sxs-lookup"><span data-stu-id="03920-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="03920-121">ICorProfilerCallback7, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="03920-122">Zapewnia metodę wywołania zwrotnego, która środowiska uruchomieniowego języka wspólnego używa powiadomić profiler, że strumień symbol skojarzone z modułem w pamięci jest aktualizowana.</span><span class="sxs-lookup"><span data-stu-id="03920-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="03920-123">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-123">ICorProfilerCallback8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
<span data-ttu-id="03920-124">Udostępnia metody wywołania zwrotnego, używanych przez środowisko uruchomieniowe języka wspólnego powiadomić profiler, który kompilację JIT metoda dynamiczna ma rozpoczęcia i zakończenia.</span><span class="sxs-lookup"><span data-stu-id="03920-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="03920-125">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-125">ICorProfilerCallback9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
<span data-ttu-id="03920-126">Zapewnia metodę wywołania zwrotnego, który środowiska uruchomieniowego języka wspólnego używa powiadomić profiler, która metoda dynamiczna jest pamięci zbierane i następnie zwolnione.</span><span class="sxs-lookup"><span data-stu-id="03920-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="03920-127">ICorProfilerFunctionControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-127">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="03920-128">Udostępnia metody, które umożliwiają programowi profilującemu kodu komunikować się z CLR do kontrolowania, jak kompilator JIT ma generować kod ponownej kompilacji określonej metody.</span><span class="sxs-lookup"><span data-stu-id="03920-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="03920-129">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-129">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="03920-130">Udostępnia metody do sekwencyjnie iteracji przez kolekcję funkcji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="03920-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="03920-131">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-131">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="03920-132">Udostępnia metody do użycia przez profilery kodu do komunikowania się z CLR do kontrolowania, monitorowanie zdarzeń i zażądać informacji.</span><span class="sxs-lookup"><span data-stu-id="03920-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="03920-133">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-133">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="03920-134">Rozszerza `ICorProfilerInfo` interfejs za pomocą metod obsługiwanych w programie .NET Framework 2.0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="03920-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="03920-135">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-135">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="03920-136">Rozszerza `ICorProfilerInfo2` interfejs za pomocą metod obsługiwanych w programie .NET Framework 4 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="03920-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="03920-137">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-137">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="03920-138">Zawiera metody, które profilery kodu używają do komunikacji z CLR do kontrolowania, monitorowanie zdarzeń i żądania informacji.</span><span class="sxs-lookup"><span data-stu-id="03920-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="03920-139">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-139">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="03920-140">Udostępnia metody do użycia przez profilery kodu do komunikowania się z CLR do kontrolowania, monitorowanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="03920-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="03920-141">ICorProfilerInfo6, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-141">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="03920-142">Dostarcza moduł wyliczający dla wszystkich metod należących do danego modułu NGen i są śródwierszowe w treści danej metody.</span><span class="sxs-lookup"><span data-stu-id="03920-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="03920-143">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-143">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="03920-144">Zapewnia metody do stosowania w nowo zdefiniowane metadane do modułu i który zapewnia dostęp do strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="03920-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="03920-145">ICorProfilerModuleEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-145">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="03920-146">Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji moduły załadowane przez program profilujący lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03920-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="03920-147">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-147">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="03920-148">Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji zamrożone obiekty, które są generowane przez [Ngen.exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="03920-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="03920-149">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-149">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="03920-150">Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji wątków w CLR.</span><span class="sxs-lookup"><span data-stu-id="03920-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="03920-151">IMethodMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="03920-151">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="03920-152">Udostępnia [alokacji](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) metoda można przydzielić pamięci dla nowej treści funkcji Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="03920-152">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="03920-153">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="03920-153">Related Sections</span></span>  
 [<span data-ttu-id="03920-154">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="03920-154">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="03920-155">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="03920-155">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="03920-156">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="03920-156">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="03920-157">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="03920-157">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
