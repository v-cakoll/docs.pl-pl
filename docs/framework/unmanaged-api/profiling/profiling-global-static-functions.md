---
title: Profilowanie statycznych funkcji globalnych
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 20ee2a9e045d839aa8ac043e035c438986b987ef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860869"
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="106f6-102">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="106f6-102">Profiling Global Static Functions</span></span>
<span data-ttu-id="106f6-103">W tej sekcji opisano niezarządzane funkcje API, które są używane przez interfejs API profilowania.</span><span class="sxs-lookup"><span data-stu-id="106f6-103">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="106f6-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="106f6-104">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="106f6-105">Funkcje profilowania .NET Framework w wersji 1</span><span class="sxs-lookup"><span data-stu-id="106f6-105">.NET Framework version 1 Profiling Functions</span></span>  
 [<span data-ttu-id="106f6-106">FunctionEnter, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-106">FunctionEnter Function</span></span>](functionenter-function.md)  
 <span data-ttu-id="106f6-107">Powiadamia profiler, że sterowanie jest przesyłane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="106f6-107">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="106f6-108">Przestarzałe w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="106f6-108">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="106f6-109">FunctionLeave, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-109">FunctionLeave Function</span></span>](functionleave-function.md)  
 <span data-ttu-id="106f6-110">Powiadamia profiler, że funkcja ma zwrócić do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="106f6-110">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="106f6-111">Przestarzałe w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="106f6-111">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="106f6-112">FunctionTailcall, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-112">FunctionTailcall Function</span></span>](functiontailcall-function.md)  
 <span data-ttu-id="106f6-113">Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji.</span><span class="sxs-lookup"><span data-stu-id="106f6-113">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="106f6-114">Przestarzałe w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="106f6-114">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="106f6-115">Funkcje profilowania .NET Framework w wersji 2</span><span class="sxs-lookup"><span data-stu-id="106f6-115">.NET Framework version 2 Profiling Functions</span></span>  
 [<span data-ttu-id="106f6-116">FunctionIDMapper, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-116">FunctionIDMapper Function</span></span>](functionidmapper-function.md)  
 <span data-ttu-id="106f6-117">Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)i [FunctionTailcall2](functiontailcall2-function.md) dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="106f6-117">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="106f6-118">Umożliwia również profilerowi wskazanie, czy chce otrzymywać wywołania zwrotne dla tej funkcji</span><span class="sxs-lookup"><span data-stu-id="106f6-118">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="106f6-119">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-119">FunctionEnter2 Function</span></span>](functionenter2-function.md)  
 <span data-ttu-id="106f6-120">Powiadamia profiler, że sterowanie jest przesyłane do funkcji i zawiera informacje na temat ramki stosu i argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="106f6-120">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="106f6-121">Przestarzałe w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="106f6-121">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="106f6-122">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-122">FunctionLeave2 Function</span></span>](functionleave2-function.md)  
 <span data-ttu-id="106f6-123">Powiadamia program profilujący, że funkcja ma zwrócić do obiektu wywołującego i zawiera informacje na temat ramki stosu i wartości zwracanej przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="106f6-123">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="106f6-124">Przestarzałe w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="106f6-124">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="106f6-125">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-125">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)  
 <span data-ttu-id="106f6-126">Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji i zawiera informacje na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="106f6-126">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="106f6-127">Przestarzałe w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="106f6-127">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="106f6-128">StackSnapshotCallback, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-128">StackSnapshotCallback Function</span></span>](stacksnapshotcallback-function.md)  
 <span data-ttu-id="106f6-129">Zapewnia profilerowi informacje o każdej zarządzanej ramce i każdym uruchomieniu niezarządzanych ramek na stosie podczas przechodzenia stosu, który jest inicjowany przez [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="106f6-129">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="106f6-130">Funkcje profilowania .NET Framework w wersji 4</span><span class="sxs-lookup"><span data-stu-id="106f6-130">.NET Framework version 4 Profiling Functions</span></span>  
 [<span data-ttu-id="106f6-131">FunctionIDMapper2, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-131">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)  
 <span data-ttu-id="106f6-132">Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)i [FunctionTailcall3](functiontailcall3-function.md), lub[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)i [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="106f6-132">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="106f6-133">Umożliwia również profilerowi określenie, czy chce otrzymywać wywołania zwrotne dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="106f6-133">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="106f6-134">`FunctionIDMapper2` rozszerza funkcję [FunctionIDMapper](functionidmapper-function.md) z parametrem `clientData`, którego mogą używać pliki do rozróżniania między środowiskami uruchomieniowymi.</span><span class="sxs-lookup"><span data-stu-id="106f6-134">`FunctionIDMapper2` extends the [FunctionIDMapper](functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="106f6-135">FunctionEnter3, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-135">FunctionEnter3 Function</span></span>](functionenter3-function.md)  
 <span data-ttu-id="106f6-136">Powiadamia profiler, że sterowanie jest przesyłane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="106f6-136">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="106f6-137">FunctionEnter3WithInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-137">FunctionEnter3WithInfo Function</span></span>](functionenter3withinfo-function.md)  
 <span data-ttu-id="106f6-138">Powiadamia program profilujący, że formant jest przesyłany do funkcji i udostępnia dojście, które może być przekazane do [ICorProfilerInfo3:: GetFunctionEnter3Info —](icorprofilerinfo3-getfunctionenter3info-method.md) w celu pobrania ramki stosu i argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="106f6-138">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="106f6-139">FunctionLeave3, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-139">FunctionLeave3 Function</span></span>](functionleave3-function.md)  
 <span data-ttu-id="106f6-140">Powiadamia profiler, że formant jest zwracany przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="106f6-140">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="106f6-141">FunctionLeave3WithInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-141">FunctionLeave3WithInfo Function</span></span>](functionleave3withinfo-function.md)  
 <span data-ttu-id="106f6-142">Powiadamia profiler, że formant jest zwracany przez funkcję i udostępnia dojście, które można przesłać do [ICorProfilerInfo3:: GetFunctionLeave3Info —](icorprofilerinfo3-getfunctionleave3info-method.md) , aby pobrać ramkę stosu i wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="106f6-142">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="106f6-143">FunctionTailcall3, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-143">FunctionTailcall3 Function</span></span>](functiontailcall3-function.md)  
 <span data-ttu-id="106f6-144">Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji.</span><span class="sxs-lookup"><span data-stu-id="106f6-144">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="106f6-145">FunctionTailcall3WithInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="106f6-145">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)  
 <span data-ttu-id="106f6-146">Powiadamia program profilujący, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji i udostępnia dojście, które może zostać przesłane do [ICorProfilerInfo3:: GetFunctionTailcall3Info —](icorprofilerinfo3-getfunctiontailcall3info-method.md) w celu pobrania ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="106f6-146">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="106f6-147">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="106f6-147">Related Sections</span></span>  
 [<span data-ttu-id="106f6-148">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="106f6-148">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="106f6-149">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="106f6-149">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="106f6-150">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="106f6-150">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="106f6-151">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="106f6-151">Profiling Structures</span></span>](profiling-structures.md)
