---
title: Interfejsy profilowania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5c0423f9c8b01c1289e1107c0c16c59968a6e2a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-interfaces"></a><span data-ttu-id="d9926-102">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="d9926-102">Profiling Interfaces</span></span>
<span data-ttu-id="d9926-103">W tej sekcji opisano niezarządzane interfejsy, które umożliwiają profilu program, który jest wykonywany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d9926-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9926-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d9926-104">In This Section</span></span>  
 [<span data-ttu-id="d9926-105">ICLRProfiling — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="d9926-106">Udostępnia [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metodę, która pozwala na dołączenie do uruchomionego procesu profilera.</span><span class="sxs-lookup"><span data-stu-id="d9926-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="d9926-107">Interfejs ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="d9926-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="d9926-108">Włącza profiler do informowania CLR odwołania do zestawów, które profilera doda w [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d9926-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="d9926-109">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="d9926-110">Udostępnia metody, które są używane przez środowisko CLR powiadomiono profilera kodu, w przypadku wystąpienia zdarzenia, do których subskrybowanych profilera.</span><span class="sxs-lookup"><span data-stu-id="d9926-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="d9926-111">ICorProfilerCallback2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="d9926-112">Rozszerza `ICorProfilerCallback` interfejsu z wywołań zwrotnych obsługiwane w programie .NET Framework 2.0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="d9926-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="d9926-113">ICorProfilerCallback3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="d9926-114">Udostępnia metody wywołania zwrotnego, używanych do komunikacji CLR dołączania i odłączania informacje o stanie do profilera.</span><span class="sxs-lookup"><span data-stu-id="d9926-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="d9926-115">ICorProfilerCallback4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="d9926-116">Udostępnia metody wywołania zwrotnego, używanych do przekazywania informacji do profiler CLR.</span><span class="sxs-lookup"><span data-stu-id="d9926-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="d9926-117">ICorProfilerCallback5 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="d9926-118">Udostępnia metody, która identyfikuje przechodnie zamknięcia odwołuje certyfikaty główne kolekcji odzyskiwanie obiektów.</span><span class="sxs-lookup"><span data-stu-id="d9926-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="d9926-119">Interfejs ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="d9926-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="d9926-120">Udostępnia metody wywołania zwrotnego, która CLR używa powiadomiono profilera, który jest ładowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="d9926-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="d9926-121">Interfejs ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="d9926-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="d9926-122">Udostępnia metody wywołania zwrotnego, która środowisko uruchomieniowe języka wspólnego używa do powiadamiania profilera zaktualizowaniu strumienia symbol skojarzone z modułu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d9926-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
 [<span data-ttu-id="d9926-123">ICorProfilerFunctionControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-123">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="d9926-124">Udostępnia metody umożliwiające profilującego do komunikowania się z CLR, aby kontrolować sposób przy użyciu kompilatora JIT powinna generować kod ponowną kompilację określonej metody.</span><span class="sxs-lookup"><span data-stu-id="d9926-124">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="d9926-125">ICorProfilerFunctionEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-125">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="d9926-126">Udostępnia metody sekwencyjnie iterowania po kolekcji funkcji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d9926-126">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="d9926-127">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="d9926-128">Udostępnia metody do użycia przez profilery kodu do komunikowania się z CLR do kontrolowania, monitorowanie zdarzeń i żądań informacji.</span><span class="sxs-lookup"><span data-stu-id="d9926-128">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="d9926-129">ICorProfilerInfo2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-129">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="d9926-130">Rozszerza `ICorProfilerInfo` interfejsu z metod obsługiwanych w programie .NET Framework 2.0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="d9926-130">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="d9926-131">ICorProfilerInfo3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-131">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="d9926-132">Rozszerza `ICorProfilerInfo2` interfejsu z metod obsługiwanych w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="d9926-132">Extends the `ICorProfilerInfo2` interface with methods supported in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] and later versions.</span></span>  
  
 [<span data-ttu-id="d9926-133">ICorProfilerInfo4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-133">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="d9926-134">Udostępnia metody, które profilery kodu używają do komunikacji z CLR sterować monitorowaniem zdarzenia i żądania informacji.</span><span class="sxs-lookup"><span data-stu-id="d9926-134">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="d9926-135">Interfejs ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="d9926-135">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="d9926-136">Udostępnia metody do użycia przez profilery kodu do komunikowania się z CLR do kontrolowania monitorowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d9926-136">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="d9926-137">Interfejs ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="d9926-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="d9926-138">Udostępnia moduł wyliczający do wszystkich metod należących do danego modułu NGen i które są wbudowane w treści danej metody.</span><span class="sxs-lookup"><span data-stu-id="d9926-138">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="d9926-139">Interfejs ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="d9926-139">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="d9926-140">Udostępnia metody do zastosowania w nowo zdefiniowane metadanych do modułu i który zapewnia dostęp do strumienia symbol w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d9926-140">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="d9926-141">ICorProfilerModuleEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-141">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="d9926-142">Udostępnia metody sekwencyjnie iterowania po kolekcji moduły załadowane przez profiler lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d9926-142">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="d9926-143">ICorProfilerObjectEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-143">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="d9926-144">Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji zablokowane obiekty, które są generowane przez [Ngen.exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="d9926-144">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="d9926-145">ICorProfilerThreadEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-145">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="d9926-146">Udostępnia metody sekwencyjnie iterowania po kolekcji wątki środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d9926-146">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="d9926-147">IMethodMalloc — interfejs</span><span class="sxs-lookup"><span data-stu-id="d9926-147">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="d9926-148">Udostępnia [alokacji](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) metody można przydzielić pamięci dla nowego treści funkcji języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d9926-148">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d9926-149">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d9926-149">Related Sections</span></span>  
 [<span data-ttu-id="d9926-150">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="d9926-150">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="d9926-151">Statyczne funkcje globalne profilowania</span><span class="sxs-lookup"><span data-stu-id="d9926-151">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="d9926-152">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d9926-152">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="d9926-153">Struktury profilowania</span><span class="sxs-lookup"><span data-stu-id="d9926-153">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
