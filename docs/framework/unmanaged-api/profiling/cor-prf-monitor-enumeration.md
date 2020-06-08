---
title: COR_PRF_MONITOR — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
ms.openlocfilehash: 1ff167121a5bb752c70edd2c5901133503326bea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500809"
---
# <a name="cor_prf_monitor-enumeration"></a><span data-ttu-id="653c8-102">COR_PRF_MONITOR — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="653c8-102">COR_PRF_MONITOR Enumeration</span></span>
<span data-ttu-id="653c8-103">Zawiera wartości, które są używane do określania zachowania, możliwości lub zdarzeń, do których profiler chce subskrybować.</span><span class="sxs-lookup"><span data-stu-id="653c8-103">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="653c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="653c8-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="653c8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="653c8-105">Members</span></span>  
 <span data-ttu-id="653c8-106">W poniższych sekcjach wymieniono `COR_PRF_MONITOR` elementy członkowskie wyliczenia według kategorii.</span><span class="sxs-lookup"><span data-stu-id="653c8-106">The following sections list `COR_PRF_MONITOR` enumeration members by category.</span></span> <span data-ttu-id="653c8-107">Kategorie są następujące:</span><span class="sxs-lookup"><span data-stu-id="653c8-107">The categories are:</span></span>  
  
- [<span data-ttu-id="653c8-108">Nie ustawiono flag</span><span class="sxs-lookup"><span data-stu-id="653c8-108">No flags set</span></span>](#None)  
  
- [<span data-ttu-id="653c8-109">Flagi wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="653c8-109">Callback flags</span></span>](#Callback)  
  
- [<span data-ttu-id="653c8-110">Flagi włączające funkcję</span><span class="sxs-lookup"><span data-stu-id="653c8-110">Feature-enabling flags</span></span>](#Feature)  
  
- [<span data-ttu-id="653c8-111">Flagi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="653c8-111">Configuration flags</span></span>](#Config)  
  
- [<span data-ttu-id="653c8-112">Flagi złożone</span><span class="sxs-lookup"><span data-stu-id="653c8-112">Composite flags</span></span>](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a><span data-ttu-id="653c8-113">Nie ustawiono flag</span><span class="sxs-lookup"><span data-stu-id="653c8-113">No flags set</span></span>  
  
|<span data-ttu-id="653c8-114">Członek</span><span class="sxs-lookup"><span data-stu-id="653c8-114">Member</span></span>|<span data-ttu-id="653c8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="653c8-115">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|<span data-ttu-id="653c8-116">Nie ustawiono żadnych flag.</span><span class="sxs-lookup"><span data-stu-id="653c8-116">No flags are set.</span></span>|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a><span data-ttu-id="653c8-117">Flagi wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="653c8-117">Callback flags</span></span>  
  
|<span data-ttu-id="653c8-118">Członek</span><span class="sxs-lookup"><span data-stu-id="653c8-118">Member</span></span>|<span data-ttu-id="653c8-119">Opis</span><span class="sxs-lookup"><span data-stu-id="653c8-119">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="653c8-120">Włącza wszystkie zdarzenia wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="653c8-120">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|<span data-ttu-id="653c8-121">Kontroluje `AppDomainCreation*` `AppDomainShutdown*` wywołania zwrotne i w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-121">Controls the `AppDomainCreation*` and `AppDomainShutdown*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|<span data-ttu-id="653c8-122">Kontroluje `AssemblyLoad*` `AssemblyUnload*` wywołania zwrotne i w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-122">Controls the `AssemblyLoad*` and `AssemblyUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|<span data-ttu-id="653c8-123">Steruje `JITCachedFunctionSearch*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-123">Controls the `JITCachedFunctionSearch*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span><br /><br /> <span data-ttu-id="653c8-124">Zachowanie tej flagi zostanie zmienione w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="653c8-124">The behavior of this flag is changed in the .NET Framework version 2.0.</span></span>|  
|`COR_PRF_MONITOR_CCW`|<span data-ttu-id="653c8-125">Steruje `COMClassicVTable*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-125">Controls the `COMClassicVTable*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLASS_LOADS`|<span data-ttu-id="653c8-126">Kontroluje `ClassLoad*` `ClassUnload*` wywołania zwrotne i w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-126">Controls the `ClassLoad*` and `ClassUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|<span data-ttu-id="653c8-127">Steruje `ExceptionCLRCatcher*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-127">Controls the `ExceptionCLRCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|<span data-ttu-id="653c8-128">Kontroluje wywołania zwrotne [UnmanagedToManagedTransition —](icorprofilercallback-unmanagedtomanagedtransition-method.md) i [ManagedToUnmanagedTransition —](icorprofilercallback-managedtounmanagedtransition-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="653c8-128">Controls the [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) and [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface</span></span>|  
|`COR_PRF_MONITOR_ENTERLEAVE`|<span data-ttu-id="653c8-129">Steruje `FunctionEnter*` `FunctionLeave*` `FunctionTailCall*` [globalnymi funkcjami statycznymi](profiling-global-static-functions.md), i profilowania.</span><span class="sxs-lookup"><span data-stu-id="653c8-129">Controls the `FunctionEnter*`,  `FunctionLeave*`, and `FunctionTailCall*`[profiling global static functions](profiling-global-static-functions.md).</span></span>|  
|`COR_PRF_MONITOR_EXCEPTIONS`|<span data-ttu-id="653c8-130">Steruje [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) wywołaniem zwrotnym ExceptionThrown — `ExceptionSearch*` oraz `ExceptionOSHandler*` `ExceptionUnwind*` `ExceptionCatcher*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-130">Controls the [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) callback and the `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, and `ExceptionCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|<span data-ttu-id="653c8-131">Steruje wywołaniem zwrotnym [FunctionUnloadStarted —](icorprofilercallback-functionunloadstarted-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-131">Controls the [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_GC`|<span data-ttu-id="653c8-132">Kontroluje [GarbageCollectionStarted —](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences —](icorprofilercallback-movedreferences-method.md), [MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences —](icorprofilercallback2-survivingreferences-method.md), SurvivingReferences2 — [,](icorprofilercallback4-survivingreferences2-method.md) [ObjectReferences —](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass —](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences —](icorprofilercallback-rootreferences-method.md), [RootReferences2 —](icorprofilercallback2-rootreferences2-method.md), [HandleCreated —](icorprofilercallback2-handlecreated-method.md)i HandleDestroyed — [wywołania](icorprofilercallback2-handledestroyed-method.md)zwrotne [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) w `ICorProfilerCallback*` interfejsach.</span><span class="sxs-lookup"><span data-stu-id="653c8-132">Controls the [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md),   [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md),  [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md),    [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md),  [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md),   [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md),  [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md),  [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), and [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) callbacks in the `ICorProfilerCallback*` interfaces.</span></span> <span data-ttu-id="653c8-133">Gdy `COR_PRF_MONITOR_GC` jest przydzielono, współbieżne wyrzucanie elementów bezużytecznych jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="653c8-133">When `COR_PRF_MONITOR_GC` is allocated, concurrent garbage collection is turned off.</span></span>|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|<span data-ttu-id="653c8-134">Kontroluje `JITCompilation*` wywołania zwrotne, [JITFunctionPitched —](icorprofilercallback-jitfunctionpitched-method.md)i [JITInlining —](icorprofilercallback-jitinlining-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-134">Controls the `JITCompilation*`, [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md), and [JITInlining](icorprofilercallback-jitinlining-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_MODULE_LOADS`|<span data-ttu-id="653c8-135">Kontroluje `ModuleLoad*` `ModuleUnload*` wywołania zwrotne, i [ModuleAttachedToAssembly —](icorprofilercallback-moduleattachedtoassembly-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-135">Controls the `ModuleLoad*`,  `ModuleUnload*`, and [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|<span data-ttu-id="653c8-136">Steruje wywołaniem zwrotnym [ObjectAllocated —](icorprofilercallback-objectallocated-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-136">Controls the [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING`|<span data-ttu-id="653c8-137">Steruje `Remoting*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-137">Controls the `Remoting*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|<span data-ttu-id="653c8-138">Określa, czy `Remoting*` wywołania zwrotne będą monitorować zdarzenia asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="653c8-138">Controls whether the `Remoting*` callbacks will monitor asynchronous events.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|<span data-ttu-id="653c8-139">Określa, czy plik cookie jest przesyłany do `Remoting*` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="653c8-139">Controls whether a cookie is passed to the `Remoting*` callbacks.</span></span>|  
|`COR_PRF_MONITOR_SUSPENDS`|<span data-ttu-id="653c8-140">Kontroluje `RuntimeSuspend*` `RuntimeResume*` wywołania zwrotne,, [RuntimeThreadSuspended —](icorprofilercallback-runtimethreadsuspended-method.md)i [RuntimeThreadResumed —](icorprofilercallback-runtimethreadresumed-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-140">Controls the `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md), and [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_THREADS`|<span data-ttu-id="653c8-141">Kontroluje wywołania zwrotne [ThreadCreated —](icorprofilercallback-threadcreated-method.md), [ThreadDestroyed —](icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread —](icorprofilercallback-threadassignedtoosthread-method.md)i [ThreadNameChanged —](icorprofilercallback2-threadnamechanged-method.md) w interfejsach [ICorProfilerCallback](icorprofilercallback-interface.md) i [ICorProfilerCallback2](icorprofilercallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-141">Controls the [ThreadCreated](icorprofilercallback-threadcreated-method.md),  [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md),  [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md), and [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) and [ICorProfilerCallback2](icorprofilercallback2-interface.md) interfaces.</span></span>|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a><span data-ttu-id="653c8-142">Flagi włączające funkcję</span><span class="sxs-lookup"><span data-stu-id="653c8-142">Feature-enabling flags</span></span>  
  
|<span data-ttu-id="653c8-143">Członek</span><span class="sxs-lookup"><span data-stu-id="653c8-143">Member</span></span>|<span data-ttu-id="653c8-144">Opis</span><span class="sxs-lookup"><span data-stu-id="653c8-144">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|<span data-ttu-id="653c8-145">Włącza pobieranie dokładne `ClassID` dla funkcji ogólnej przez wywołanie metody [GetFunctionInfo2 —](icorprofilerinfo2-getfunctioninfo2-method.md) z `COR_PRF_FRAME_INFO` wartością zwracaną przez wywołanie zwrotne [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-145">Enables the retrieval of an exact `ClassID` for a generic function by calling the [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method with a `COR_PRF_FRAME_INFO` value returned by the [FunctionEnter2](functionenter2-function.md) callback.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|<span data-ttu-id="653c8-146">Włącza śledzenie argumentów przy użyciu wywołania zwrotnego [FunctionEnter2](functionenter2-function.md) lub wywołania zwrotnego [FunctionEnter3WithInfo](functionenter3withinfo-function.md) i metody [GetFunctionEnter3Info —](icorprofilerinfo3-getfunctionenter3info-method.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-146">Enables argument tracing using the [FunctionEnter2](functionenter2-function.md) callback or the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) callback and the [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|<span data-ttu-id="653c8-147">Włącza śledzenie wartości zwracanych przy użyciu wywołania zwrotnego [FunctionLeave2](functionleave2-function.md) lub metody wywołania zwrotnego [FunctionLeave3WithInfo](functionleave3withinfo-function.md) i [GetFunctionLeave3Info —](icorprofilerinfo3-getfunctionleave3info-method.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-147">Enables tracing of return values by using the [FunctionLeave2](functionleave2-function.md) callback or the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) callback and [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|<span data-ttu-id="653c8-148">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="653c8-148">Deprecated.</span></span><br /><br /> <span data-ttu-id="653c8-149">Debugowanie procesu nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="653c8-149">In process debugging is not supported.</span></span> <span data-ttu-id="653c8-150">Ta flaga nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="653c8-150">This flag has no effect.</span></span>|  
|`COR_PRF_ENABLE_JIT_MAPS`|<span data-ttu-id="653c8-151">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="653c8-151">Deprecated.</span></span><br /><br /> <span data-ttu-id="653c8-152">Umożliwia programowi Profiler uzyskanie map IL-to-native przy użyciu [GetILToNativeMapping —](icorprofilerinfo-getiltonativemapping-method.md).</span><span class="sxs-lookup"><span data-stu-id="653c8-152">Allows the profiler to obtain IL-to-native maps by using [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span></span> <span data-ttu-id="653c8-153">Począwszy od .NET Framework 2,0, środowisko uruchomieniowe zawsze śledzi mapowania IL-to-natywne; w związku z tym Flaga ta jest zawsze uznawana za ustawioną.</span><span class="sxs-lookup"><span data-stu-id="653c8-153">Starting with the .NET Framework 2.0, the runtime always tracks IL-to-native maps; therefore, this flag is always considered to be set.</span></span>|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|<span data-ttu-id="653c8-154">Informuje środowisko uruchomieniowe, że profiler może chcieć otrzymywać powiadomienia dotyczące alokacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="653c8-154">Informs the runtime that the profiler may want object allocation notifications.</span></span> <span data-ttu-id="653c8-155">Ta flaga musi być ustawiona podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="653c8-155">This flag must be set during initialization.</span></span> <span data-ttu-id="653c8-156">Umożliwia profilerowi użycie `COR_PRF_MONITOR_OBJECT_ALLOCATED` flagi, aby otrzymać wywołania zwrotne [ObjectAllocated —](icorprofilercallback-objectallocated-method.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-156">It allows the profiler to subsequently use the `COR_PRF_MONITOR_OBJECT_ALLOCATED` flag to receive [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callbacks.</span></span>|  
|`COR_PRF_ENABLE_REJIT`|<span data-ttu-id="653c8-157">Włącza wywołania metod [RequestReJIT —](icorprofilerinfo4-requestrejit-method.md) i [RequestRevert —](icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-157">Enables calls to the [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) and [RequestRevert](icorprofilerinfo4-requestrevert-method.md) methods.</span></span> <span data-ttu-id="653c8-158">Profiler musi ustawić tę flagę podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="653c8-158">The profiler must set this flag on startup.</span></span>  <span data-ttu-id="653c8-159">Jeśli profiler określa tę flagę, musi także określić `COR_PRF_DISABLE_ALL_NGEN_IMAGES` .</span><span class="sxs-lookup"><span data-stu-id="653c8-159">If the profiler specifies this flag, it must also specify `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span></span>|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|<span data-ttu-id="653c8-160">Włącza wywołania metody [DoStackSnapshot —](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="653c8-160">Enables calls to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a><span data-ttu-id="653c8-161">Flagi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="653c8-161">Configuration flags</span></span>  
  
|<span data-ttu-id="653c8-162">Członek</span><span class="sxs-lookup"><span data-stu-id="653c8-162">Member</span></span>|<span data-ttu-id="653c8-163">Opis</span><span class="sxs-lookup"><span data-stu-id="653c8-163">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|<span data-ttu-id="653c8-164">Zapobiega ładowaniu wszystkich obrazów natywnych (w tym obrazów ulepszonych profilera).</span><span class="sxs-lookup"><span data-stu-id="653c8-164">Prevents all native images (including profiler-enhanced images) from loading.</span></span>  <span data-ttu-id="653c8-165">Jeśli ta flaga i `COR_PRF_USE_PROFILE_IMAGES` Flaga są określone, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jest używana.</span><span class="sxs-lookup"><span data-stu-id="653c8-165">If this flag and the `COR_PRF_USE_PROFILE_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
|`COR_PRF_DISABLE_INLINING`|<span data-ttu-id="653c8-166">Wyłącza wszystkie znaki wykreślania.</span><span class="sxs-lookup"><span data-stu-id="653c8-166">Disables all inlining.</span></span>|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|<span data-ttu-id="653c8-167">Wyłącza wszystkie optymalizacje kodu.</span><span class="sxs-lookup"><span data-stu-id="653c8-167">Disables all code optimizations.</span></span>|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|<span data-ttu-id="653c8-168">Wyłącza kontrole przezroczystości zabezpieczeń, które zwykle są wykonywane podczas kompilacji w czasie just-in-Time (JIT) i załadowanie klasy dla zestawów o pełnym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="653c8-168">Disables security transparency checks that are normally done during just-in-time (JIT) compilation and class loading for full-trust assemblies.</span></span> <span data-ttu-id="653c8-169">Może to ułatwić wykonywanie niektórych Instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="653c8-169">This can make some instrumentation easier to perform.</span></span>|  
|`COR_PRF_USE_PROFILE_IMAGES`|<span data-ttu-id="653c8-170">Powoduje, że wyszukiwanie obrazów natywnych jest wyszukiwane w obrazach z ulepszonym profilerem.</span><span class="sxs-lookup"><span data-stu-id="653c8-170">Causes the native image search to look for profiler-enhanced images.</span></span> <span data-ttu-id="653c8-171">Jeśli dla danego zestawu nie zostanie znaleziony obraz z ulepszonym profilerem, środowisko uruchomieniowe języka wspólnego powróci do trybu JIT dla tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="653c8-171">If no profiler-enhanced image is found for a given assembly, the common language runtime falls back to JIT for that assembly.</span></span> <span data-ttu-id="653c8-172">Jeśli ta flaga i `COR_PRF_DISABLE_ALL_NGEN_IMAGES` Flaga są określone, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jest używana.</span><span class="sxs-lookup"><span data-stu-id="653c8-172">If this flag and the `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a><span data-ttu-id="653c8-173">Flagi złożone</span><span class="sxs-lookup"><span data-stu-id="653c8-173">Composite flags</span></span>  
  
|<span data-ttu-id="653c8-174">Członek</span><span class="sxs-lookup"><span data-stu-id="653c8-174">Member</span></span>|<span data-ttu-id="653c8-175">Opis</span><span class="sxs-lookup"><span data-stu-id="653c8-175">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ALL`|<span data-ttu-id="653c8-176">Reprezentuje wszystkie `COR_PRF_MONITOR` wartości flag.</span><span class="sxs-lookup"><span data-stu-id="653c8-176">Represents all `COR_PRF_MONITOR` flag values.</span></span>|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="653c8-177">Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które można ustawić po dołączeniu profilera do uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="653c8-177">Represents all `COR_PRF_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span> <span data-ttu-id="653c8-178">Sekcja składnia wskazuje poszczególne flagi, które znajdują się w tej masce bitowej.</span><span class="sxs-lookup"><span data-stu-id="653c8-178">The syntax section indicates the individual flags that are present in this bitmask.</span></span>|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="653c8-179">Włącza wszystkie zdarzenia wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="653c8-179">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_IMMUTABLE`|<span data-ttu-id="653c8-180">Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które można ustawić tylko podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="653c8-180">Represents all `COR_PRF_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="653c8-181">Próba zmiany którejkolwiek z tych flag po inicjalizacji zwróci `HRESULT` wartość wskazującą niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="653c8-181">Trying to change any of these flags after initialization returns an `HRESULT` value that indicates failure.</span></span>|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="653c8-182">Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które wymagają obrazów z rozszerzonym profilem.</span><span class="sxs-lookup"><span data-stu-id="653c8-182">Represents all `COR_PRF_MONITOR` flags that require profile-enhanced images.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="653c8-183">Uwagi</span><span class="sxs-lookup"><span data-stu-id="653c8-183">Remarks</span></span>  
 <span data-ttu-id="653c8-184">`COR_PRF_MONITOR`Wartość jest używana z metodami [ICorProfilerInfo:: GetEventMask —](icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) do definiowania powiadomień o zdarzeniach, które środowisko uruchomieniowe języka wspólnego zapewnia Profiler.</span><span class="sxs-lookup"><span data-stu-id="653c8-184">A `COR_PRF_MONITOR` value is used with the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods to define the event notifications that the common language runtime makes to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="653c8-185">Wymagania</span><span class="sxs-lookup"><span data-stu-id="653c8-185">Requirements</span></span>  
 <span data-ttu-id="653c8-186">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="653c8-186">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="653c8-187">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="653c8-187">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="653c8-188">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="653c8-188">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="653c8-189">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="653c8-189">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653c8-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="653c8-190">See also</span></span>

- [<span data-ttu-id="653c8-191">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="653c8-191">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="653c8-192">GetEventMask, metoda</span><span class="sxs-lookup"><span data-stu-id="653c8-192">GetEventMask Method</span></span>](icorprofilerinfo-geteventmask-method.md)
- [<span data-ttu-id="653c8-193">SetEventMask, metoda</span><span class="sxs-lookup"><span data-stu-id="653c8-193">SetEventMask Method</span></span>](icorprofilerinfo-seteventmask-method.md)
