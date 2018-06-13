---
title: Profilowanie — Wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 996352637f34b0b6c0d12e611a6d9e70ab85230e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461763"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="2daaf-102">Profilowanie — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2daaf-102">Profiling Enumerations</span></span>
<span data-ttu-id="2daaf-103">W tej sekcji opisano niezarządzane wyliczenia, które używa interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="2daaf-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2daaf-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2daaf-104">In This Section</span></span>  
 [<span data-ttu-id="2daaf-105">COR_PRF_CLAUSE_TYPE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="2daaf-106">Wskazuje typ klauzuli wyjątek, który właśnie wprowadzony kod lub w lewo.</span><span class="sxs-lookup"><span data-stu-id="2daaf-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="2daaf-107">COR_PRF_CODEGEN_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="2daaf-108">Określa flagi generowania kodu, które można ustawić za pomocą [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2daaf-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="2daaf-109">COR_PRF_FINALIZER_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="2daaf-110">W tym artykule opisano finalizatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="2daaf-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="2daaf-111">COR_PRF_GC_GENERATION, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="2daaf-112">Określa Generowanie kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="2daaf-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="2daaf-113">COR_PRF_GC_REASON, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="2daaf-114">Wskazuje Przyczyna występuje wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2daaf-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="2daaf-115">COR_PRF_GC_ROOT_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="2daaf-116">Wskazuje właściwości główny moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="2daaf-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="2daaf-117">COR_PRF_GC_ROOT_KIND, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="2daaf-118">Wskazuje typ modułu zbierającego elementy bezużyteczne głównego, który jest udostępniany przez [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2daaf-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="2daaf-119">Wyliczenie COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="2daaf-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="2daaf-120">Udostępnia flagi oprócz występujące w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia, które można określić profilera [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody podczas jego ładowania.</span><span class="sxs-lookup"><span data-stu-id="2daaf-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="2daaf-121">COR_PRF_JIT_CACHE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="2daaf-122">Wskazuje wynik wyszukiwania funkcji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2daaf-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="2daaf-123">COR_PRF_MISC, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="2daaf-124">Zawiera stałe wartości, które określają specjalne identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="2daaf-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="2daaf-125">COR_PRF_MODULE_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="2daaf-126">Określa właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="2daaf-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="2daaf-127">COR_PRF_MONITOR, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="2daaf-128">Zawiera wartości, które są używane do określania zachowania, funkcji lub zdarzeń do których chce subskrypcji profilera.</span><span class="sxs-lookup"><span data-stu-id="2daaf-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="2daaf-129">COR_PRF_RUNTIME_TYPE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="2daaf-130">Zawiera wartości, które wskazują wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="2daaf-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="2daaf-131">COR_PRF_SNAPSHOT_INFO, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="2daaf-132">Określa, ile kopii danych do przekazania z migawki w każdym wywołaniu profilera stosu `StackSnapshotCallback` funkcji.</span><span class="sxs-lookup"><span data-stu-id="2daaf-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="2daaf-133">COR_PRF_STATIC_TYPE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="2daaf-134">Wskazuje, czy pole jest statyczny, a jeśli tak, statyczne jakości dotyczący pola.</span><span class="sxs-lookup"><span data-stu-id="2daaf-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="2daaf-135">COR_PRF_SUSPEND_REASON, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="2daaf-136">Wskazuje przyczynę zawieszenia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2daaf-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="2daaf-137">COR_PRF_TRANSITION_REASON, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2daaf-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="2daaf-138">Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="2daaf-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2daaf-139">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2daaf-139">Related Sections</span></span>  
 [<span data-ttu-id="2daaf-140">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="2daaf-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="2daaf-141">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="2daaf-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="2daaf-142">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="2daaf-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="2daaf-143">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="2daaf-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
