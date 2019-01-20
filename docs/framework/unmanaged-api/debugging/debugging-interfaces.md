---
title: Debugowanie — Interfejsy
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b6d00d17615769a5d03d58e0eda5af62ca58368
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415965"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="b7141-102">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b7141-102">Debugging Interfaces</span></span>
<span data-ttu-id="b7141-103">W tej sekcji opisano niezarządzane interfejsy obsługujące debugowanie programu wykonywanego w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="b7141-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7141-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b7141-104">In This Section</span></span>  
 [<span data-ttu-id="b7141-105">ICLRDataEnumMemoryRegions, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-105">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 <span data-ttu-id="b7141-106">Zapewnia metodę pozwalającą wyliczyć obszary pamięci, które są określone przez obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="b7141-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 [<span data-ttu-id="b7141-107">ICLRDataEnumMemoryRegionsCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-107">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 <span data-ttu-id="b7141-108">Zapewnia metodę wywołania zwrotnego dla `EnumMemoryRegions` do zgłaszania do debugera wyniku próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="b7141-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 [<span data-ttu-id="b7141-109">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-109">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 <span data-ttu-id="b7141-110">Zapewnia metody interakcji z obiektem docelowym procesu CLR.</span><span class="sxs-lookup"><span data-stu-id="b7141-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 [<span data-ttu-id="b7141-111">ICLRDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-111">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 <span data-ttu-id="b7141-112">Podklasa klasy `ICLRDataTarget` używany przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="b7141-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 [<span data-ttu-id="b7141-113">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-113">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 <span data-ttu-id="b7141-114">Podklasa klasy [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , który zapewnia dostęp do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b7141-114">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 [<span data-ttu-id="b7141-115">ICLRDebugging, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-115">ICLRDebugging Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 <span data-ttu-id="b7141-116">Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b7141-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 [<span data-ttu-id="b7141-117">ICLRDebuggingLibraryProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-117">ICLRDebuggingLibraryProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 <span data-ttu-id="b7141-118">Obejmuje [providelibrary — metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metody, która pobiera interfejs wywołania zwrotnego, która umożliwia języka wspólnego bibliotek debugowania specyficznych dla wersji środowiska uruchomieniowego lokalizowanie i ładowanie na żądanie dostawcy biblioteki.</span><span class="sxs-lookup"><span data-stu-id="b7141-118">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 [<span data-ttu-id="b7141-119">ICLRMetadataLocator, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-119">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 <span data-ttu-id="b7141-120">Interfejs używany przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="b7141-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 [<span data-ttu-id="b7141-121">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 <span data-ttu-id="b7141-122">Dostarcza metody, które umożliwiają programistom debugowanie aplikacji w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="b7141-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="b7141-123">ICorDebugAppDomain, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-123">ICorDebugAppDomain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 <span data-ttu-id="b7141-124">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b7141-124">Provides methods for debugging application domains.</span></span>  
  
 [<span data-ttu-id="b7141-125">ICorDebugAppDomain2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-125">ICorDebugAppDomain2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 <span data-ttu-id="b7141-126">Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami ByRef.</span><span class="sxs-lookup"><span data-stu-id="b7141-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="b7141-127">Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b7141-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 [<span data-ttu-id="b7141-128">ICorDebugAppDomain3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-128">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 <span data-ttu-id="b7141-129">Dostarcza metody do pracy z [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b7141-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="b7141-130">Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` i `ICorDebugAppDomain2` interfejsów.</span><span class="sxs-lookup"><span data-stu-id="b7141-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 [<span data-ttu-id="b7141-131">ICorDebugAppDomain4, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-131">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 <span data-ttu-id="b7141-132">Rozszerza logicznie [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interfejsu można pobrać obiektu zarządzanego z wywołalne opakowanie COM.</span><span class="sxs-lookup"><span data-stu-id="b7141-132">Logically extends the [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 [<span data-ttu-id="b7141-133">ICorDebugAppDomainEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-133">ICorDebugAppDomainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 <span data-ttu-id="b7141-134">Dostarcza metodę, która zwraca określoną liczbę `ICorDebugAppDomain` wartości, zaczynając od następnej pozycji w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="b7141-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 [<span data-ttu-id="b7141-135">ICorDebugArrayValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-135">ICorDebugArrayValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 <span data-ttu-id="b7141-136">Podklasa klasy `ICorDebugHeapValue` reprezentująca tablicę jednowymiarową lub wielowymiarową.</span><span class="sxs-lookup"><span data-stu-id="b7141-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 [<span data-ttu-id="b7141-137">ICorDebugAssembly, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-137">ICorDebugAssembly Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 <span data-ttu-id="b7141-138">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="b7141-138">Represents an assembly.</span></span>  
  
 [<span data-ttu-id="b7141-139">ICorDebugAssembly2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-139">ICorDebugAssembly2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 <span data-ttu-id="b7141-140">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="b7141-140">Represents an assembly.</span></span> <span data-ttu-id="b7141-141">Ten interfejs jest rozszerzeniem `ICorDebugAssembly` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b7141-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 [<span data-ttu-id="b7141-142">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-142">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 <span data-ttu-id="b7141-143">Rozszerza logicznie [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interfejs w celu zapewnienia obsługi kontenerów zestawów i ich zestawy zawarte.</span><span class="sxs-lookup"><span data-stu-id="b7141-143">Logically extends the [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="b7141-144">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-144">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-145">ICorDebugAssemblyEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-145">ICorDebugAssemblyEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 <span data-ttu-id="b7141-146">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugAssembly` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-147">ICorDebugBlockingObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-147">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 <span data-ttu-id="b7141-148">Dostarcza moduł wyliczający listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="b7141-148">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
 [<span data-ttu-id="b7141-149">ICorDebugBoxValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-149">ICorDebugBoxValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 <span data-ttu-id="b7141-150">Podklasa klasy `ICorDebugHeapValue` reprezentująca spakowany obiekt klasy wartości.</span><span class="sxs-lookup"><span data-stu-id="b7141-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 [<span data-ttu-id="b7141-151">ICorDebugBreakpoint, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-151">ICorDebugBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 <span data-ttu-id="b7141-152">Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.</span><span class="sxs-lookup"><span data-stu-id="b7141-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 [<span data-ttu-id="b7141-153">ICorDebugBreakpointEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-153">ICorDebugBreakpointEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 <span data-ttu-id="b7141-154">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugBreakpoint` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-155">ICorDebugChain, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-155">ICorDebugChain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 <span data-ttu-id="b7141-156">Reprezentuje segment stosu wywołań fizycznych lub logicznych.</span><span class="sxs-lookup"><span data-stu-id="b7141-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 [<span data-ttu-id="b7141-157">ICorDebugChainEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-157">ICorDebugChainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 <span data-ttu-id="b7141-158">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugChain` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-159">ICorDebugClass, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-159">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 <span data-ttu-id="b7141-160">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="b7141-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="b7141-161">Jeśli typ ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="b7141-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 [<span data-ttu-id="b7141-162">ICorDebugClass2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-162">ICorDebugClass2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 <span data-ttu-id="b7141-163">Reprezentuje klasą rodzajową lub klasy z parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="b7141-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="b7141-164">Ten interfejs rozszerza `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="b7141-164">This interface extends `ICorDebugClass`.</span></span>  
  
 [<span data-ttu-id="b7141-165">ICorDebugCode, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-165">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 <span data-ttu-id="b7141-166">Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="b7141-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 [<span data-ttu-id="b7141-167">ICorDebugCode2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-167">ICorDebugCode2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 <span data-ttu-id="b7141-168">Udostępnia metody, które rozszerzają możliwości `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="b7141-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 [<span data-ttu-id="b7141-169">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-169">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 <span data-ttu-id="b7141-170">Dostarcza metodę, która rozszerza [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) i [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) aby podać informacje o zarządzaniu wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="b7141-170">Provides a method that extends [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) and [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 [<span data-ttu-id="b7141-171">ICorDebugCode4, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-171">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 <span data-ttu-id="b7141-172">Dostarcza metodę, która umożliwia debugera wyliczanie zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="b7141-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="b7141-173">ICorDebugCodeEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-173">ICorDebugCodeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 <span data-ttu-id="b7141-174">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugCode` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-175">ICorDebugComObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-175">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 <span data-ttu-id="b7141-176">Dostarcza metody pobierania obiektów interfejsu w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b7141-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 [<span data-ttu-id="b7141-177">ICorDebugContext, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-177">ICorDebugContext Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 <span data-ttu-id="b7141-178">Reprezentuje obiekt kontekstu.</span><span class="sxs-lookup"><span data-stu-id="b7141-178">Represents a context object.</span></span> <span data-ttu-id="b7141-179">Ten Interfejs nie został jeszcze implementowany.</span><span class="sxs-lookup"><span data-stu-id="b7141-179">This interface has not been implemented yet.</span></span>  
  
 [<span data-ttu-id="b7141-180">ICorDebugController, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-180">ICorDebugController Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 <span data-ttu-id="b7141-181">Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, wykonanie kodu, które mogą być kontrolowane kontekstu.</span><span class="sxs-lookup"><span data-stu-id="b7141-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 [<span data-ttu-id="b7141-182">ICorDebugDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-182">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 <span data-ttu-id="b7141-183">Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="b7141-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 [<span data-ttu-id="b7141-184">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-184">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 <span data-ttu-id="b7141-185">Rozszerza logicznie [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b7141-185">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="b7141-186">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-186">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-187">ICorDebugDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-187">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 <span data-ttu-id="b7141-188">Rozszerza logicznie [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów.</span><span class="sxs-lookup"><span data-stu-id="b7141-188">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="b7141-189">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-189">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-190">ICorDebugDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-190">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 <span data-ttu-id="b7141-191">Definiuje interfejs podstawowy, z którym wszystkie `ICorDebug` pochodzić zdarzeń debugowania.</span><span class="sxs-lookup"><span data-stu-id="b7141-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="b7141-192">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-192">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-193">ICorDebugEditAndContinueErrorInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-193">ICorDebugEditAndContinueErrorInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 <span data-ttu-id="b7141-194">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="b7141-194">Obsolete.</span></span> <span data-ttu-id="b7141-195">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b7141-195">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="b7141-196">ICorDebugEditAndContinueSnapshot, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-196">ICorDebugEditAndContinueSnapshot Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 <span data-ttu-id="b7141-197">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="b7141-197">Obsolete.</span></span> <span data-ttu-id="b7141-198">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b7141-198">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="b7141-199">ICorDebugEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-199">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 <span data-ttu-id="b7141-200">Służy jako abstrakcyjny interfejs podstawowy do debugowania modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="b7141-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 [<span data-ttu-id="b7141-201">ICorDebugErrorInfoEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-201">ICorDebugErrorInfoEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 <span data-ttu-id="b7141-202">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="b7141-202">Obsolete.</span></span> <span data-ttu-id="b7141-203">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b7141-203">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="b7141-204">ICorDebugEval, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-204">ICorDebugEval Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 <span data-ttu-id="b7141-205">Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="b7141-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 [<span data-ttu-id="b7141-206">ICorDebugEval2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-206">ICorDebugEval2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 <span data-ttu-id="b7141-207">Rozszerza `ICorDebugEval` celu zapewnienia obsługi typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="b7141-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 [<span data-ttu-id="b7141-208">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-208">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 <span data-ttu-id="b7141-209">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń dotyczących wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b7141-209">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="b7141-210">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-210">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-211">ICorDebugExceptionObjectCallStackEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-211">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 <span data-ttu-id="b7141-212">Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b7141-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 [<span data-ttu-id="b7141-213">ICorDebugExceptionObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-213">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 <span data-ttu-id="b7141-214">Rozszerza [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interfejsu, aby zapewnić informacje śledzenia stosu z zarządzanego obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b7141-214">Extends the [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 [<span data-ttu-id="b7141-215">ICorDebugFrame, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-215">ICorDebugFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 <span data-ttu-id="b7141-216">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="b7141-216">Represents a frame on the current stack.</span></span>  
  
 [<span data-ttu-id="b7141-217">ICorDebugFrameEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-217">ICorDebugFrameEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 <span data-ttu-id="b7141-218">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugFrame` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-219">ICorDebugFunction, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-219">ICorDebugFunction Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 <span data-ttu-id="b7141-220">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="b7141-220">Represents a managed function or method.</span></span>  
  
 [<span data-ttu-id="b7141-221">ICorDebugFunction2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-221">ICorDebugFunction2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 <span data-ttu-id="b7141-222">Rozszerza logicznie `ICorDebugFunction` zapewnia obsługę debugowania tylko mój kod krokowym.</span><span class="sxs-lookup"><span data-stu-id="b7141-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 [<span data-ttu-id="b7141-223">ICorDebugFunction3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-223">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 <span data-ttu-id="b7141-224">Rozszerza logicznie [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interfejsu, aby zapewnić dostęp do kodu z żądaniem ReJIT.</span><span class="sxs-lookup"><span data-stu-id="b7141-224">Logically extends the [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 [<span data-ttu-id="b7141-225">ICorDebugFunctionBreakpoint, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-225">ICorDebugFunctionBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 <span data-ttu-id="b7141-226">Rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w obrębie funkcji.</span><span class="sxs-lookup"><span data-stu-id="b7141-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 [<span data-ttu-id="b7141-227">ICorDebugGCReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-227">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 <span data-ttu-id="b7141-228">Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="b7141-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 [<span data-ttu-id="b7141-229">ICorDebugGenericValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-229">ICorDebugGenericValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 <span data-ttu-id="b7141-230">Podklasa klasy `ICorDebugValue` która odnosi się do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="b7141-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="b7141-231">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="b7141-231">This interface provides Get and Set methods for the value.</span></span>  
  
 [<span data-ttu-id="b7141-232">ICorDebugGuidToTypeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-232">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 <span data-ttu-id="b7141-233">Dostarcza moduł wyliczający dla obiektu, który mapuje identyfikatory GUID i odpowiednie `ICorDebugType` obiektów.</span><span class="sxs-lookup"><span data-stu-id="b7141-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 [<span data-ttu-id="b7141-234">ICorDebugHandleValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-234">ICorDebugHandleValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 <span data-ttu-id="b7141-235">Podklasa klasy `ICorDebugReferenceValue` reprezentująca wartość odniesienia, do której debuger utworzył procedurę obsługi do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b7141-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 [<span data-ttu-id="b7141-236">ICorDebugHeapEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-236">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 <span data-ttu-id="b7141-237">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="b7141-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 [<span data-ttu-id="b7141-238">ICorDebugHeapSegmentEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-238">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 <span data-ttu-id="b7141-239">Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="b7141-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 [<span data-ttu-id="b7141-240">ICorDebugHeapValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-240">ICorDebugHeapValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 <span data-ttu-id="b7141-241">Podklasa klasy `ICorDebugValue` reprezentująca obiekt, który został zebrany przez moduł odśmiecania pamięci CLR.</span><span class="sxs-lookup"><span data-stu-id="b7141-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 [<span data-ttu-id="b7141-242">ICorDebugHeapValue2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-242">ICorDebugHeapValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 <span data-ttu-id="b7141-243">Rozszerzenie `ICorDebugHeapValue` który zapewnia obsługę dla obsługi środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b7141-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 [<span data-ttu-id="b7141-244">ICorDebugHeapValue3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-244">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 <span data-ttu-id="b7141-245">Udostępnia właściwości blokady monitora obiektów.</span><span class="sxs-lookup"><span data-stu-id="b7141-245">Exposes the monitor lock properties of objects.</span></span>  
  
 [<span data-ttu-id="b7141-246">ICorDebugILCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-246">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 <span data-ttu-id="b7141-247">Reprezentuje segment kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="b7141-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 [<span data-ttu-id="b7141-248">ICorDebugILCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-248">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 <span data-ttu-id="b7141-249">Rozszerza logicznie [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interfejsu podania metod, które zwracają token do funkcji lokalnej zmiennej podpisu i mapy, program profilujący instrumentowanych języka pośredniego (IL) przesuwa się do oryginalnej metody IL przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="b7141-249">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 [<span data-ttu-id="b7141-250">ICorDebugILFrame, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-250">ICorDebugILFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 <span data-ttu-id="b7141-251">Reprezentuje ramkę stosu kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="b7141-251">Represents a stack frame of MSIL code.</span></span>  
  
 [<span data-ttu-id="b7141-252">ICorDebugILFrame2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-252">ICorDebugILFrame2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 <span data-ttu-id="b7141-253">Logiczne rozszerzenie `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="b7141-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 [<span data-ttu-id="b7141-254">ICorDebugILFrame3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-254">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 <span data-ttu-id="b7141-255">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="b7141-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 [<span data-ttu-id="b7141-256">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-256">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 <span data-ttu-id="b7141-257">Udostępnia metody, które umożliwiają dostęp do zmiennych lokalnych i kod w ramce stosu kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="b7141-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="b7141-258">Parametr określa, czy narzędzie debuger ma dostęp do zmiennych i kodzie dodanym w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="b7141-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="b7141-259">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-259">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 <span data-ttu-id="b7141-260">Reprezentuje informacji dotyczących symboli debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b7141-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="b7141-261">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-261">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-262">ICorDebugInternalFrame, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-262">ICorDebugInternalFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 <span data-ttu-id="b7141-263">Identyfikuje typy ramek dla debugera.</span><span class="sxs-lookup"><span data-stu-id="b7141-263">Identifies frame types for the debugger.</span></span>  
  
 [<span data-ttu-id="b7141-264">ICorDebugInternalFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-264">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 <span data-ttu-id="b7141-265">Zawiera informacje o ramkach wewnętrznych, łącznie z adresem stosu i pozycją w odniesieniu do [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="b7141-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objects.</span></span>  
  
 [<span data-ttu-id="b7141-266">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-266">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 <span data-ttu-id="b7141-267">Zawiera informacje dotyczące załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="b7141-267">Provides information about a loaded module.</span></span> <span data-ttu-id="b7141-268">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-268">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-269">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-269">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 <span data-ttu-id="b7141-270">Dostarcza metody do przetwarzania wywołań zwrotnych debugera.</span><span class="sxs-lookup"><span data-stu-id="b7141-270">Provides methods to process debugger callbacks.</span></span>  
  
 [<span data-ttu-id="b7141-271">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-271">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 <span data-ttu-id="b7141-272">Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="b7141-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="b7141-273">`ICorDebugManagedCallback2` jest logicznym rozszerzeniem `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="b7141-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 [<span data-ttu-id="b7141-274">ICorDebugManagedCallback3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-274">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 <span data-ttu-id="b7141-275">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="b7141-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 [<span data-ttu-id="b7141-276">ICorDebugMDA, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-276">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 <span data-ttu-id="b7141-277">Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="b7141-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 [<span data-ttu-id="b7141-278">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-278">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 <span data-ttu-id="b7141-279">Reprezentuje buforów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b7141-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="b7141-280">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-280">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-281">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-281">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 <span data-ttu-id="b7141-282">Zawiera informacje o zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="b7141-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="b7141-283">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-283">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-284">ICorDebugMetaDataLocator, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-284">ICorDebugMetaDataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 <span data-ttu-id="b7141-285">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="b7141-285">Provides metadata information to the debugger.</span></span>  
  
 [<span data-ttu-id="b7141-286">ICorDebugModule, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-286">ICorDebugModule Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 <span data-ttu-id="b7141-287">Reprezentuje moduł CLR, który jest albo plikiem wykonywalnym lub biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="b7141-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 [<span data-ttu-id="b7141-288">ICorDebugModule2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-288">ICorDebugModule2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 <span data-ttu-id="b7141-289">Służy jako logiczne rozszerzenie `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="b7141-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 [<span data-ttu-id="b7141-290">ICorDebugModule3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-290">ICorDebugModule3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 <span data-ttu-id="b7141-291">Tworzy czytnik symbolu dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="b7141-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 [<span data-ttu-id="b7141-292">ICorDebugModuleBreakpoint, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-292">ICorDebugModuleBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 <span data-ttu-id="b7141-293">Rozszerza `ICorDebugBreakpoint` zapewnienie dostępu do konkretnych modułów.</span><span class="sxs-lookup"><span data-stu-id="b7141-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 [<span data-ttu-id="b7141-294">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-294">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 <span data-ttu-id="b7141-295">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="b7141-295">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="b7141-296">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-296">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-297">ICorDebugModuleEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-297">ICorDebugModuleEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 <span data-ttu-id="b7141-298">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugModule` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-299">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-299">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 <span data-ttu-id="b7141-300">Rozszerza [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu do obsługi danych modyfikowalnych elementów docelowych.</span><span class="sxs-lookup"><span data-stu-id="b7141-300">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 [<span data-ttu-id="b7141-301">ICorDebugNativeFrame, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-301">ICorDebugNativeFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 <span data-ttu-id="b7141-302">Wyspecjalizowana implementacja `ICorDebugFrame` wykorzystywana do ramek natywnych.</span><span class="sxs-lookup"><span data-stu-id="b7141-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 [<span data-ttu-id="b7141-303">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-303">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 <span data-ttu-id="b7141-304">Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.</span><span class="sxs-lookup"><span data-stu-id="b7141-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 [<span data-ttu-id="b7141-305">ICorDebugObjectEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-305">ICorDebugObjectEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 <span data-ttu-id="b7141-306">Implementuje `ICorDebugEnum` metod i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="b7141-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 [<span data-ttu-id="b7141-307">ICorDebugObjectValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-307">ICorDebugObjectValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 <span data-ttu-id="b7141-308">Podklasa klasy `ICorDebugValue` reprezentująca wartość, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="b7141-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 [<span data-ttu-id="b7141-309">ICorDebugObjectValue2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-309">ICorDebugObjectValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 <span data-ttu-id="b7141-310">Rozszerza `ICorDebugObjectValue` do obsługi dziedziczenia i zastępowania.</span><span class="sxs-lookup"><span data-stu-id="b7141-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 [<span data-ttu-id="b7141-311">ICorDebugProcess, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-311">ICorDebugProcess Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 <span data-ttu-id="b7141-312">Reprezentuje proces, który wykonuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="b7141-312">Represents a process that is executing managed code.</span></span>  
  
 [<span data-ttu-id="b7141-313">ICorDebugProcess2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-313">ICorDebugProcess2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 <span data-ttu-id="b7141-314">Logiczne rozszerzenie `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="b7141-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 [<span data-ttu-id="b7141-315">ICorDebugProcess3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-315">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 <span data-ttu-id="b7141-316">Steruje niestandardowymi powiadomieniami debugera.</span><span class="sxs-lookup"><span data-stu-id="b7141-316">Controls custom debugger notifications.</span></span>  
  
 [<span data-ttu-id="b7141-317">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-317">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 <span data-ttu-id="b7141-318">Rozszerza [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) obsługiwany dostęp do zarządzanej sterty, do dostarczania informacji dotyczących wyrzucania elementów bezużytecznych obiektów zarządzanych i określenia, czy debuger wczytuje obrazy z aplikacji przez interfejs użytkownika lokalnego pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="b7141-318">Extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 [<span data-ttu-id="b7141-319">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-319">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 <span data-ttu-id="b7141-320">Rozszerza logicznie [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interfejsu, aby włączyć funkcje, takie jak dekodowanie zdarzenia debugowania zarządzanego, które są kodowane w zdarzeń debugowania natywnych wyjątków oraz wirtualnego modułu dzielenia.</span><span class="sxs-lookup"><span data-stu-id="b7141-320">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="b7141-321">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-321">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-322">ICorDebugProcess7, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-322">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 <span data-ttu-id="b7141-323">Dostarcza metodę, która umożliwia skonfigurowanie debuger mógł obsłużyć aktualizacji metadanych w pamięci w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="b7141-323">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 [<span data-ttu-id="b7141-324">ICorDebugProcess8, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-324">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 <span data-ttu-id="b7141-325">Rozszerza logicznie [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interfejsu, aby włączyć lub wyłączyć niektórych rodzajów [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) wywołań zwrotnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b7141-325">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 [<span data-ttu-id="b7141-326">ICorDebugProcessEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-326">ICorDebugProcessEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 <span data-ttu-id="b7141-327">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugProcess` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-327">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-328">ICorDebugReferenceValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-328">ICorDebugReferenceValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 <span data-ttu-id="b7141-329">Podklasa klasy `ICorDebugValue` obsługuje typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="b7141-329">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 [<span data-ttu-id="b7141-330">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-330">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 <span data-ttu-id="b7141-331">Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="b7141-331">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 [<span data-ttu-id="b7141-332">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-332">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 <span data-ttu-id="b7141-333">Rozszerza możliwości `ICorDebugRegisterSet` dla platform sprzętowych, które mają więcej niż 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="b7141-333">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 [<span data-ttu-id="b7141-334">ICorDebugRemote, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-334">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 <span data-ttu-id="b7141-335">Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="b7141-335">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 [<span data-ttu-id="b7141-336">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-336">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 <span data-ttu-id="b7141-337">Dostarcza metody, które umożliwiają debugowania aplikacji opartych na dodatku Silverlight w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="b7141-337">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="b7141-338">ICorDebugRuntimeUnwindableFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-338">ICorDebugRuntimeUnwindableFrame Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 <span data-ttu-id="b7141-339">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="b7141-339">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 [<span data-ttu-id="b7141-340">ICorDebugStackWalk, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-340">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 <span data-ttu-id="b7141-341">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="b7141-341">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 [<span data-ttu-id="b7141-342">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-342">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 <span data-ttu-id="b7141-343">Reprezentuje informacji dotyczących symboli debugowania dla pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="b7141-343">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="b7141-344">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-344">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-345">ICorDebugStepper, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-345">ICorDebugStepper Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 <span data-ttu-id="b7141-346">Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.</span><span class="sxs-lookup"><span data-stu-id="b7141-346">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 [<span data-ttu-id="b7141-347">ICorDebugStepper2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-347">ICorDebugStepper2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 <span data-ttu-id="b7141-348">Zapewnia obsługę debugowania Tylko mój kod (JMC).</span><span class="sxs-lookup"><span data-stu-id="b7141-348">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 [<span data-ttu-id="b7141-349">ICorDebugStepperEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-349">ICorDebugStepperEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 <span data-ttu-id="b7141-350">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugStepper` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-350">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-351">ICorDebugStringValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-351">ICorDebugStringValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 <span data-ttu-id="b7141-352">Podklasa klasy `ICorDebugHeapValue` która odnosi się do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="b7141-352">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 [<span data-ttu-id="b7141-353">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-353">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 <span data-ttu-id="b7141-354">Udostępnia metody, które mogą służyć do pobierania informacji dotyczących symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="b7141-354">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="b7141-355">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-355">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-356">ICorDebugSymbolProvider2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-356">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 <span data-ttu-id="b7141-357">Rozszerza logicznie [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interfejsu można pobrać informacji dotyczących symboli debugowania dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="b7141-357">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="b7141-358">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-358">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-359">ICorDebugThread, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-359">ICorDebugThread Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 <span data-ttu-id="b7141-360">Reprezentuje wątek w procesie.</span><span class="sxs-lookup"><span data-stu-id="b7141-360">Represents a thread in a process.</span></span> <span data-ttu-id="b7141-361">Okres istnienia `ICorDebugThread` wystąpienie jest taki sam, jak okres istnienia wątku, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="b7141-361">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 [<span data-ttu-id="b7141-362">ICorDebugThread2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-362">ICorDebugThread2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 <span data-ttu-id="b7141-363">Służy jako logiczne rozszerzenie `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="b7141-363">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 [<span data-ttu-id="b7141-364">ICorDebugThread3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-364">ICorDebugThread3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 <span data-ttu-id="b7141-365">Zapewnia punkt wejścia do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) i odpowiednich interfejsów.</span><span class="sxs-lookup"><span data-stu-id="b7141-365">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 [<span data-ttu-id="b7141-366">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-366">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 <span data-ttu-id="b7141-367">Dostarcza informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="b7141-367">Provides thread blocking information.</span></span>  
  
 [<span data-ttu-id="b7141-368">ICorDebugThreadEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-368">ICorDebugThreadEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 <span data-ttu-id="b7141-369">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugThread` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-369">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-370">ICorDebugType, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-370">ICorDebugType Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 <span data-ttu-id="b7141-371">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="b7141-371">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="b7141-372">Jeśli typ ogólny, `ICorDebugType` reprezentuje typ ogólny z wystąpieniami.</span><span class="sxs-lookup"><span data-stu-id="b7141-372">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 [<span data-ttu-id="b7141-373">ICorDebugType2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-373">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 <span data-ttu-id="b7141-374">Rozszerza [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interfejsu, aby pobrać identyfikator typu Typ podstawowy lub złożony (typ zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="b7141-374">Extends the [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 [<span data-ttu-id="b7141-375">ICorDebugTypeEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="b7141-375">ICorDebugTypeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 <span data-ttu-id="b7141-376">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugType` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-376">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-377">ICorDebugUnmanagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-377">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 <span data-ttu-id="b7141-378">Zapewnia powiadomienie macierzystych zdarzeń, które nie dotyczą bezpośrednio środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b7141-378">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="b7141-379">"ICorDebugValue"</span><span class="sxs-lookup"><span data-stu-id="b7141-379">"ICorDebugValue"</span></span>  
 <span data-ttu-id="b7141-380">Reprezentuje wartość odczytu lub zapisu w procesie debugowania.</span><span class="sxs-lookup"><span data-stu-id="b7141-380">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="b7141-381">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="b7141-381">"ICorDebugValue2"</span></span>  
 <span data-ttu-id="b7141-382">Rozszerza `ICorDebugValue` aby zapewnić obsługę `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="b7141-382">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 [<span data-ttu-id="b7141-383">ICorDebugValue3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-383">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 <span data-ttu-id="b7141-384">Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic, które są większe niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="b7141-384">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="b7141-385">"ICorDebugValueBreakpoint"</span><span class="sxs-lookup"><span data-stu-id="b7141-385">"ICorDebugValueBreakpoint"</span></span>  
 <span data-ttu-id="b7141-386">Rozszerza `ICorDebugBreakpoint` zapewniać dostęp do określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="b7141-386">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="b7141-387">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="b7141-387">"ICorDebugValueEnum"</span></span>  
 <span data-ttu-id="b7141-388">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugValue` tablic.</span><span class="sxs-lookup"><span data-stu-id="b7141-388">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 [<span data-ttu-id="b7141-389">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-389">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 <span data-ttu-id="b7141-390">Reprezentuje zmiennej lokalnej lub argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="b7141-390">Represents a local variable or argument of a function.</span></span>  
  
 [<span data-ttu-id="b7141-391">ICorDebugVariableHomeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-391">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 <span data-ttu-id="b7141-392">Dostarcza moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="b7141-392">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="b7141-393">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-393">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 <span data-ttu-id="b7141-394">Umożliwia pobranie informacji dotyczących symboli debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b7141-394">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="b7141-395">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-395">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-396">ICorDebugVirtualUnwinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-396">ICorDebugVirtualUnwinder Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 <span data-ttu-id="b7141-397">Dostarcza metody pomagające w wykonywania operacji odwijania stosu.</span><span class="sxs-lookup"><span data-stu-id="b7141-397">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="b7141-398">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="b7141-398">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="b7141-399">ICorPublish, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-399">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 <span data-ttu-id="b7141-400">Służy jako ogólny interfejs dla procesów publikowania.</span><span class="sxs-lookup"><span data-stu-id="b7141-400">Serves as the general interface for the publishing processes.</span></span>  
  
 [<span data-ttu-id="b7141-401">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-401">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 <span data-ttu-id="b7141-402">Reprezentuje i dostarcza informacje dotyczące domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b7141-402">Represents and provides information about an application domain.</span></span>  
  
 [<span data-ttu-id="b7141-403">ICorPublishAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-403">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 <span data-ttu-id="b7141-404">Udostępnia metody, które przemierzają kolekcję `ICorPublishAppDomain` obiekty, które obecnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b7141-404">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 [<span data-ttu-id="b7141-405">ICorPublishEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-405">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 <span data-ttu-id="b7141-406">Służy jako abstrakcyjna podstawowa do publikowania modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="b7141-406">Serves as the abstract base for publishing enumerators.</span></span>  
  
 [<span data-ttu-id="b7141-407">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-407">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 <span data-ttu-id="b7141-408">Dostarcza metody, które mają dostęp do informacji dotyczących procesu.</span><span class="sxs-lookup"><span data-stu-id="b7141-408">Provides methods that access information about a process.</span></span>  
  
 [<span data-ttu-id="b7141-409">ICorPublishProcessEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7141-409">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 <span data-ttu-id="b7141-410">Udostępnia metody, które przemierzają kolekcję `ICorPublishProcess` obiektów.</span><span class="sxs-lookup"><span data-stu-id="b7141-410">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="b7141-411">[Interfejs ISOSDacInterface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) zapewnia metody pomocnika dostępu do danych z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="b7141-411">[ISOSDacInterface Interface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="b7141-412">[Interfejs IXCLRDataMethodDefinition](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) udostępnia metody do wykonywania zapytań o definicję metody.</span><span class="sxs-lookup"><span data-stu-id="b7141-412">[IXCLRDataMethodDefinition Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="b7141-413">[Interfejs IXCLRDataMethodInstance](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) udostępnia metody do wykonywania zapytań o wystąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="b7141-413">[IXCLRDataMethodInstance Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="b7141-414">[Interfejs IXCLRDataModule](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) udostępnia metody do wykonywania zapytań o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="b7141-414">[IXCLRDataModule Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="b7141-415">[Interfejs IXCLRDataProcess](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) udostępnia metody do wykonywania zapytań informacji dotyczących procesu.</span><span class="sxs-lookup"><span data-stu-id="b7141-415">[IXCLRDataProcess Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="b7141-416">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b7141-416">Related Sections</span></span>  
 [<span data-ttu-id="b7141-417">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="b7141-417">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="b7141-418">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="b7141-418">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="b7141-419">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b7141-419">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="b7141-420">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="b7141-420">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
