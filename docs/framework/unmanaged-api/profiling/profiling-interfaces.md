---
title: Interfejsy profilowania
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: 8b6b9acff2945e2d8fd684bfa31e4af086ea5ab9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868151"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="9a71c-102">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="9a71c-102">Profiling Interfaces</span></span>
<span data-ttu-id="9a71c-103">W tej sekcji opisano niezarządzane interfejsy, które umożliwiają profilowanie programu wykonywanego przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="9a71c-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a71c-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9a71c-104">In This Section</span></span>  
 [<span data-ttu-id="9a71c-105">ICLRProfiling, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-105">ICLRProfiling Interface</span></span>](iclrprofiling-interface.md)  
 <span data-ttu-id="9a71c-106">Udostępnia metodę [AttachProfiler —](iclrprofiling-attachprofiler-method.md) , która umożliwia profilerowi dołączenie do uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="9a71c-106">Provides the [AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="9a71c-107">ICorProfilerAssemblyReferenceProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="9a71c-108">Umożliwia programowi Profiler informowanie CLR o odwołaniach do zestawów, które Profiler doda do wywołania zwrotnego [ICorProfilerCallback:: ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9a71c-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="9a71c-109">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-109">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)  
 <span data-ttu-id="9a71c-110">Dostarcza metody, które są używane przez środowisko CLR do powiadamiania profilera kodu o wystąpieniu zdarzeń subskrybowanych przez profiler.</span><span class="sxs-lookup"><span data-stu-id="9a71c-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="9a71c-111">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-111">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)  
 <span data-ttu-id="9a71c-112">Rozszerza interfejs `ICorProfilerCallback` z wywołaniami zwrotnymi obsługiwanymi w .NET Framework 2,0 i nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="9a71c-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="9a71c-113">ICorProfilerCallback3, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-113">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)  
 <span data-ttu-id="9a71c-114">Zapewnia metody wywołania zwrotnego używane przez środowisko CLR do przekazywania informacji o stanie dołączania i odłączania do profilera.</span><span class="sxs-lookup"><span data-stu-id="9a71c-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="9a71c-115">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-115">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)  
 <span data-ttu-id="9a71c-116">Zapewnia metody wywołania zwrotnego używane przez środowisko CLR do przekazywania informacji do profilera.</span><span class="sxs-lookup"><span data-stu-id="9a71c-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="9a71c-117">ICorProfilerCallback5, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-117">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)  
 <span data-ttu-id="9a71c-118">Zapewnia metodę, która identyfikuje przechodnie zamknięcie obiektów, do których odwołują się katalogi główne wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9a71c-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="9a71c-119">ICorProfilerCallback6, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-119">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)  
 <span data-ttu-id="9a71c-120">Zapewnia metodę wywołania zwrotnego używaną przez środowisko CLR do powiadomienia profilera o ładowaniu zestawu.</span><span class="sxs-lookup"><span data-stu-id="9a71c-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="9a71c-121">ICorProfilerCallback7, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-121">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)  
 <span data-ttu-id="9a71c-122">Zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o aktualizowaniu strumienia symboli skojarzonego z modułem w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9a71c-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="9a71c-123">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)  
<span data-ttu-id="9a71c-124">Zapewnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o rozpoczęciu i zakończeniu kompilacji JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="9a71c-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="9a71c-125">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-125">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)  
<span data-ttu-id="9a71c-126">Zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadomienia profilera, że metoda dynamiczna jest odzyskiwana, a następnie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="9a71c-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="9a71c-127">ICorProfilerFunctionControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-127">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="9a71c-128">Dostarcza metody, które umożliwiają profilerowi kodu komunikowanie się z środowiskiem CLR w celu kontrolowania sposobu generowania kodu przez kompilator JIT podczas ponownego kompilowania określonej metody.</span><span class="sxs-lookup"><span data-stu-id="9a71c-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="9a71c-129">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-129">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="9a71c-130">Zapewnia metody sekwencyjnej iteracji przez kolekcję funkcji w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="9a71c-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="9a71c-131">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)  
 <span data-ttu-id="9a71c-132">Zapewnia metody do użycia przez program Code profilowas do komunikowania się z środowiskiem CLR w celu kontrolowania informacji o monitorowaniu zdarzeń i żądaniu.</span><span class="sxs-lookup"><span data-stu-id="9a71c-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="9a71c-133">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-133">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)  
 <span data-ttu-id="9a71c-134">Rozszerza interfejs `ICorProfilerInfo` z metodami obsługiwanymi w .NET Framework 2,0 i nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="9a71c-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="9a71c-135">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-135">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)  
 <span data-ttu-id="9a71c-136">Rozszerza interfejs `ICorProfilerInfo2` z metodami obsługiwanymi w .NET Framework 4 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="9a71c-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="9a71c-137">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-137">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)  
 <span data-ttu-id="9a71c-138">Dostarcza metody, których program codeer używa do komunikacji z środowiskiem CLR w celu kontrolowania monitorowania zdarzeń oraz żądania informacji.</span><span class="sxs-lookup"><span data-stu-id="9a71c-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="9a71c-139">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-139">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)  
 <span data-ttu-id="9a71c-140">Zapewnia metody do użycia przez program Code profilowas do komunikowania się z środowiskiem CLR w celu kontrolowania monitorowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9a71c-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="9a71c-141">ICorProfilerInfo6, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-141">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)  
 <span data-ttu-id="9a71c-142">Dostarcza moduł wyliczający do wszystkich metod, które należą do danego modułu NGen i są zawarte w treści danej metody.</span><span class="sxs-lookup"><span data-stu-id="9a71c-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="9a71c-143">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-143">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)  
 <span data-ttu-id="9a71c-144">Zapewnia metodę zastosowania nowo zdefiniowanych metadanych do modułu, który zapewnia dostęp do strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9a71c-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="9a71c-145">ICorProfilerModuleEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-145">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="9a71c-146">Dostarcza metody sekwencyjnie iteracji przez kolekcję modułów ładowanych przez aplikację lub profiler.</span><span class="sxs-lookup"><span data-stu-id="9a71c-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="9a71c-147">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-147">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="9a71c-148">Zapewnia metody sekwencyjnej iteracji przez kolekcję zamrożonych obiektów, które są generowane przez program [Ngen. exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="9a71c-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="9a71c-149">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-149">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="9a71c-150">Zapewnia metody sekwencyjnej iteracji przez kolekcję wątków w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="9a71c-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="9a71c-151">IMethodMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a71c-151">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)  
 <span data-ttu-id="9a71c-152">Udostępnia metodę [Alloc](imethodmalloc-alloc-method.md) do przydzielania pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a71c-152">Provides the [Alloc](imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a71c-153">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9a71c-153">Related Sections</span></span>  
 [<span data-ttu-id="9a71c-154">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="9a71c-154">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="9a71c-155">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="9a71c-155">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="9a71c-156">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9a71c-156">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="9a71c-157">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="9a71c-157">Profiling Structures</span></span>](profiling-structures.md)
