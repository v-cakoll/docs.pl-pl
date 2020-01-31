---
title: Profilowanie — Wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 1a9781fa1b4b608152faa7d5edc80bd4866f0c81
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868138"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="55d78-102">Profilowanie — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="55d78-102">Profiling Enumerations</span></span>
<span data-ttu-id="55d78-103">W tej sekcji opisano niezarządzane wyliczenia, które są używane przez interfejs API profilowania.</span><span class="sxs-lookup"><span data-stu-id="55d78-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55d78-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="55d78-104">In This Section</span></span>  
 [<span data-ttu-id="55d78-105">COR_PRF_CLAUSE_TYPE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="55d78-106">Wskazuje typ klauzuli wyjątku, który został właśnie wprowadzony lub pozostawiony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="55d78-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="55d78-107">COR_PRF_CODEGEN_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="55d78-108">Definiuje flagi generowania kodu, które można ustawić za pomocą metody [ICorProfilerFunctionControl:: SetCodegenFlags —](icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="55d78-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="55d78-109">COR_PRF_FINALIZER_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="55d78-110">Opisuje finalizator dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="55d78-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="55d78-111">COR_PRF_GC_GENERATION, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-111">COR_PRF_GC_GENERATION Enumeration</span></span>](cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="55d78-112">Identyfikuje generowanie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="55d78-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="55d78-113">COR_PRF_GC_REASON, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-113">COR_PRF_GC_REASON Enumeration</span></span>](cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="55d78-114">Wskazuje przyczynę wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="55d78-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="55d78-115">COR_PRF_GC_ROOT_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="55d78-116">Wskazuje właściwości elementu głównego modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="55d78-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="55d78-117">COR_PRF_GC_ROOT_KIND, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="55d78-118">Wskazuje rodzaj elementu głównego modułu wyrzucania elementów bezużytecznych, który jest udostępniany przez wywołanie zwrotne [ICorProfilerCallback2:: RootReferences2 —](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="55d78-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="55d78-119">Wyliczenie COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="55d78-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="55d78-120">Oferuje flagi oprócz tych, które znajdują się w wyliczeniu [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) , który profiler może określić do metody [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) podczas ładowania.</span><span class="sxs-lookup"><span data-stu-id="55d78-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="55d78-121">COR_PRF_JIT_CACHE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-121">COR_PRF_JIT_CACHE Enumeration</span></span>](cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="55d78-122">Wskazuje wynik funkcji wyszukiwania w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="55d78-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="55d78-123">COR_PRF_MISC, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-123">COR_PRF_MISC Enumeration</span></span>](cor-prf-misc-enumeration.md)  
 <span data-ttu-id="55d78-124">Zawiera wartości stałe, które określają identyfikatory specjalne.</span><span class="sxs-lookup"><span data-stu-id="55d78-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="55d78-125">COR_PRF_MODULE_FLAGS, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="55d78-126">Określa właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="55d78-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="55d78-127">COR_PRF_MONITOR, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-127">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="55d78-128">Zawiera wartości, które są używane do określania zachowania, możliwości lub zdarzeń, do których profiler chce subskrybować.</span><span class="sxs-lookup"><span data-stu-id="55d78-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="55d78-129">COR_PRF_RUNTIME_TYPE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="55d78-130">Zawiera wartości wskazujące wersję środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="55d78-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="55d78-131">COR_PRF_SNAPSHOT_INFO, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="55d78-132">Określa ilość danych, które mają zostać przekazane z migawki stosu w każdym wywołaniu funkcji `StackSnapshotCallback` profilera.</span><span class="sxs-lookup"><span data-stu-id="55d78-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="55d78-133">COR_PRF_STATIC_TYPE, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="55d78-134">Wskazuje, czy pole jest statyczne i, jeśli tak, statyczna jakość stosowana do pola.</span><span class="sxs-lookup"><span data-stu-id="55d78-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="55d78-135">COR_PRF_SUSPEND_REASON, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="55d78-136">Wskazuje przyczynę wstrzymania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="55d78-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="55d78-137">COR_PRF_TRANSITION_REASON, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55d78-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="55d78-138">Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="55d78-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="55d78-139">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="55d78-139">Related Sections</span></span>  
 [<span data-ttu-id="55d78-140">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="55d78-140">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="55d78-141">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="55d78-141">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="55d78-142">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="55d78-142">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="55d78-143">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="55d78-143">Profiling Structures</span></span>](profiling-structures.md)
