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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757576"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="a4d6c-102">Profilowanie — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a4d6c-102">Profiling Enumerations</span></span>
<span data-ttu-id="a4d6c-103">W tej sekcji opisano niezarządzane wyliczenia, których używa interfejs profilowania API.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4d6c-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a4d6c-104">In This Section</span></span>  
 [<span data-ttu-id="a4d6c-105">COR_PRF_CLAUSE_TYPE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="a4d6c-106">Wskazuje typ klauzuli wyjątek, który po prostu wprowadzony kod lub po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="a4d6c-107">COR_PRF_CODEGEN_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="a4d6c-108">Określa flagi generowania kodu, które można ustawić za pomocą [icorprofilerfunctioncontrol::setcodegenflags —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="a4d6c-109">COR_PRF_FINALIZER_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="a4d6c-110">W tym artykule opisano finalizatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="a4d6c-111">COR_PRF_GC_GENERATION, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="a4d6c-112">Identyfikuje generacjach wyrzucania.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="a4d6c-113">COR_PRF_GC_REASON, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="a4d6c-114">Wskazuje powód, że odbywa się wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="a4d6c-115">COR_PRF_GC_ROOT_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="a4d6c-116">Określa właściwości głównego modułu zbierającego elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="a4d6c-117">COR_PRF_GC_ROOT_KIND, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="a4d6c-118">Wskazuje rodzaj głównego modułu odśmiecania pamięci, który jest udostępniany przez [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="a4d6c-119">Wyliczenie COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="a4d6c-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="a4d6c-120">Zawiera flagi, oprócz tych dostępnych w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenie, które można określić profiler [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metodą podczas wczytywania.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="a4d6c-121">COR_PRF_JIT_CACHE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="a4d6c-122">Wskazuje wynik wyszukiwania funkcję pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="a4d6c-123">COR_PRF_MISC, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="a4d6c-124">Zawiera wartości stałych, które określają specjalne identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="a4d6c-125">COR_PRF_MODULE_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="a4d6c-126">Określa właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="a4d6c-127">COR_PRF_MONITOR, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="a4d6c-128">Zawiera wartości, które są używane do określania zachowania, funkcji lub zdarzeń do których program profilujący chce subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="a4d6c-129">COR_PRF_RUNTIME_TYPE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="a4d6c-130">Zawiera wartości, które wskazują wersję środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="a4d6c-131">COR_PRF_SNAPSHOT_INFO, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="a4d6c-132">Określa, ile danych do przekazania z powrotem przy użyciu migawek w każdym wywołaniu do programu profilującego stosu `StackSnapshotCallback` funkcji.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="a4d6c-133">COR_PRF_STATIC_TYPE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="a4d6c-134">Wskazuje, czy pole jest statyczna, a jeśli tak, statycznej jakości, która odnosi się do pola.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="a4d6c-135">COR_PRF_SUSPEND_REASON, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="a4d6c-136">Wskazuje powód, że środowisko uruchomieniowe zostało wstrzymane.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="a4d6c-137">COR_PRF_TRANSITION_REASON, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a4d6c-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="a4d6c-138">Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="a4d6c-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a4d6c-139">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a4d6c-139">Related Sections</span></span>  
 [<span data-ttu-id="a4d6c-140">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="a4d6c-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="a4d6c-141">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a4d6c-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="a4d6c-142">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="a4d6c-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="a4d6c-143">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="a4d6c-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
