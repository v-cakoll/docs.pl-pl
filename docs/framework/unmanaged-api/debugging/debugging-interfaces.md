---
title: Debugowanie — Interfejsy
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 07b39666637628102e9ffafd2c059ba0d4b51b92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097199"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="d5968-102">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d5968-102">Debugging Interfaces</span></span>
<span data-ttu-id="d5968-103">W tej sekcji opisano niezarządzane interfejsy obsługujące debugowanie programu wykonywanego w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d5968-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5968-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d5968-104">In This Section</span></span>  
 <span data-ttu-id="d5968-105">[ICLRDataEnumMemoryRegions\ interfejsu](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)\</span></span>
 <span data-ttu-id="d5968-106">Zapewnia metodę pozwalającą wyliczyć obszary pamięci, które są określone przez obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="d5968-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="d5968-107">[ICLRDataEnumMemoryRegionsCallback\ interfejsu](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)\</span></span>
 <span data-ttu-id="d5968-108">Zapewnia metodę wywołania zwrotnego dla `EnumMemoryRegions`, aby zgłosić do debugera, wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="d5968-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="d5968-109">[ICLRDataTarget\ interfejsu](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)\</span></span>
 <span data-ttu-id="d5968-110">Zapewnia metody interakcji z obiektem docelowym procesu CLR.</span><span class="sxs-lookup"><span data-stu-id="d5968-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="d5968-111">[ICLRDataTarget2\ interfejsu](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)\</span></span>
 <span data-ttu-id="d5968-112">Podklasa `ICLRDataTarget`, która jest używana przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="d5968-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="d5968-113">[ICLRDataTarget3\ interfejsu](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)\</span></span>
 <span data-ttu-id="d5968-114">Podklasa elementu [ICLRDataTarget2](iclrdatatarget2-interface.md) , która zapewnia dostęp do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d5968-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="d5968-115">[ICLRDebugging\ interfejsu](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-115">[ICLRDebugging Interface](iclrdebugging-interface.md)\</span></span>
 <span data-ttu-id="d5968-116">Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.</span><span class="sxs-lookup"><span data-stu-id="d5968-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="d5968-117">[ICLRDebuggingLibraryProvider\ interfejsu](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)\</span></span>
 <span data-ttu-id="d5968-118">Obejmuje metodę [metody ProvideLibrary —](iclrdebugginglibraryprovider-providelibrary-method.md) , która pobiera interfejs wywołania zwrotnego dostawcy biblioteki, który umożliwia zlokalizowanie i załadowanie bibliotek debugowania specyficznych dla wersji środowiska uruchomieniowego języka wspólnego na żądanie.</span><span class="sxs-lookup"><span data-stu-id="d5968-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="d5968-119">[ICLRMetadataLocator\ interfejsu](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)\</span></span>
 <span data-ttu-id="d5968-120">Interfejs używany przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="d5968-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="d5968-121">[ICorDebug\ interfejsu](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-121">[ICorDebug Interface](icordebug-interface.md)\</span></span>
 <span data-ttu-id="d5968-122">Dostarcza metody, które umożliwiają programistom debugowanie aplikacji w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="d5968-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="d5968-123">[ICorDebugAppDomain\ interfejsu](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)\</span></span>
 <span data-ttu-id="d5968-124">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5968-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="d5968-125">[ICorDebugAppDomain2\ interfejsu](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\</span></span>
 <span data-ttu-id="d5968-126">Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami ByRef.</span><span class="sxs-lookup"><span data-stu-id="d5968-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="d5968-127">Ten interfejs jest rozszerzeniem interfejsu `ICorDebugAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="d5968-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="d5968-128">[ICorDebugAppDomain3\ interfejsu](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\</span></span>
 <span data-ttu-id="d5968-129">Zapewnia metody do pracy z typami środowisko wykonawcze systemu Windows w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5968-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="d5968-130">Ten interfejs jest rozszerzeniem interfejsów `ICorDebugAppDomain` i `ICorDebugAppDomain2`.</span><span class="sxs-lookup"><span data-stu-id="d5968-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="d5968-131">[ICorDebugAppDomain4\ interfejsu](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\</span></span>
 <span data-ttu-id="d5968-132">Logicznie rozszerza interfejs [ICorDebugAppDomain](icordebugappdomain-interface.md) w celu uzyskania obiektu zarządzanego z przywywoływanej otoki com.</span><span class="sxs-lookup"><span data-stu-id="d5968-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="d5968-133">[ICorDebugAppDomainEnum\ interfejsu](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-134">Zapewnia metodę, która zwraca określoną liczbę `ICorDebugAppDomain` wartości, rozpoczynając od następnej lokalizacji w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="d5968-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="d5968-135">[ICorDebugArrayValue\ interfejsu](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)\</span></span>
 <span data-ttu-id="d5968-136">Podklasa `ICorDebugHeapValue`, która reprezentuje tablicę jednowymiarową lub wielowymiarową.</span><span class="sxs-lookup"><span data-stu-id="d5968-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="d5968-137">[ICorDebugAssembly\ interfejsu](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)\</span></span>
 <span data-ttu-id="d5968-138">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="d5968-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="d5968-139">[ICorDebugAssembly2\ interfejsu](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)\</span></span>
 <span data-ttu-id="d5968-140">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="d5968-140">Represents an assembly.</span></span> <span data-ttu-id="d5968-141">Ten interfejs jest rozszerzeniem interfejsu `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="d5968-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="d5968-142">[ICorDebugAssembly3\ interfejsu](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)\</span></span>
 <span data-ttu-id="d5968-143">Logicznie rozszerza interfejs [ICorDebugAssembly](icordebugassembly-interface.md) w celu zapewnienia obsługi zestawów kontenerów i zawartych w nich zestawów.</span><span class="sxs-lookup"><span data-stu-id="d5968-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="d5968-144">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-145">[ICorDebugAssemblyEnum\ interfejsu](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-146">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugAssembly` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="d5968-147">[ICorDebugBlockingObjectEnum\ interfejsu](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-148">Dostarcza moduł wyliczający listę struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="d5968-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="d5968-149">[ICorDebugBoxValue\ interfejsu](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)\</span></span>
 <span data-ttu-id="d5968-150">Podklasa `ICorDebugHeapValue`, która reprezentuje obiekt klasy wartości w ramce.</span><span class="sxs-lookup"><span data-stu-id="d5968-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="d5968-151">[ICorDebugBreakpoint\ interfejsu](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)\</span></span>
 <span data-ttu-id="d5968-152">Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.</span><span class="sxs-lookup"><span data-stu-id="d5968-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="d5968-153">[ICorDebugBreakpointEnum\ interfejsu](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-154">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugBreakpoint` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="d5968-155">[ICorDebugChain\ interfejsu](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-155">[ICorDebugChain Interface](icordebugchain-interface.md)\</span></span>
 <span data-ttu-id="d5968-156">Reprezentuje segment stosu wywołań fizycznych lub logicznych.</span><span class="sxs-lookup"><span data-stu-id="d5968-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="d5968-157">[ICorDebugChainEnum\ interfejsu](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-158">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugChain` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="d5968-159">[ICorDebugClass\ interfejsu](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-159">[ICorDebugClass Interface](icordebugclass-interface.md)\</span></span>
 <span data-ttu-id="d5968-160">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="d5968-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="d5968-161">Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="d5968-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="d5968-162">[ICorDebugClass2\ interfejsu](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)\</span></span>
 <span data-ttu-id="d5968-163">Reprezentuje klasę generyczną lub klasę z parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="d5968-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="d5968-164">Ten interfejs rozszerza `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="d5968-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="d5968-165">[ICorDebugCode\ interfejsu](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-165">[ICorDebugCode Interface](icordebugcode-interface1.md)\</span></span>
 <span data-ttu-id="d5968-166">Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="d5968-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="d5968-167">[ICorDebugCode2\ interfejsu](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)\</span></span>
 <span data-ttu-id="d5968-168">Dostarcza metody, które zwiększają możliwości `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="d5968-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="d5968-169">[ICorDebugCode3\ interfejsu](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)\</span></span>
 <span data-ttu-id="d5968-170">Zapewnia metodę, która rozszerza [ICorDebugCode](icordebugcode-interface1.md) i [ICorDebugCode2](icordebugcode2-interface.md) , aby zapewnić informacje o zarządzanej wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="d5968-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="d5968-171">[ICorDebugCode4\ interfejsu](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)\</span></span>
 <span data-ttu-id="d5968-172">Zapewnia metodę, która umożliwia debugerowi Wyliczenie zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="d5968-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="d5968-173">[ICorDebugCodeEnum\ interfejsu](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-174">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugCode` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="d5968-175">[ICorDebugComObjectValue\ interfejsu](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\</span></span>
 <span data-ttu-id="d5968-176">Dostarcza metody pobierania obiektów interfejsu w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d5968-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="d5968-177">[Icordebugcontext —\ interfejsu](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-177">[ICorDebugContext Interface](icordebugcontext-interface.md)\</span></span>
 <span data-ttu-id="d5968-178">Reprezentuje obiekt kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d5968-178">Represents a context object.</span></span> <span data-ttu-id="d5968-179">Ten Interfejs nie został jeszcze implementowany.</span><span class="sxs-lookup"><span data-stu-id="d5968-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="d5968-180">[ICorDebugController\ interfejsu](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-180">[ICorDebugController Interface](icordebugcontroller-interface.md)\</span></span>
 <span data-ttu-id="d5968-181">Reprezentuje zakres, <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, w którym można kontrolować kontekst wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="d5968-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="d5968-182">[ICorDebugDataTarget\ interfejsu](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)\</span></span>
 <span data-ttu-id="d5968-183">Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d5968-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="d5968-184">[Metoda icordebugdatatarget2\ interfejsu](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)\</span></span>
 <span data-ttu-id="d5968-185">Logicznie rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d5968-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="d5968-186">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-187">[ICorDebugDataTarget3\ interfejsu](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\</span></span>
 <span data-ttu-id="d5968-188">Logicznie rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) w celu dostarczenia informacji o załadowanych modułach.</span><span class="sxs-lookup"><span data-stu-id="d5968-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="d5968-189">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-190">[ICorDebugDebugEvent\ interfejsu](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)\</span></span>
 <span data-ttu-id="d5968-191">Definiuje interfejs podstawowy, z którego pochodzą wszystkie zdarzenia debugowania `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="d5968-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="d5968-192">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-193">[ICorDebugEditAndContinueErrorInfo\ interfejsu](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\</span></span>
 <span data-ttu-id="d5968-194">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="d5968-194">Obsolete.</span></span> <span data-ttu-id="d5968-195">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d5968-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="d5968-196">[ICorDebugEditAndContinueSnapshot\ interfejsu](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)\</span></span>
 <span data-ttu-id="d5968-197">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="d5968-197">Obsolete.</span></span> <span data-ttu-id="d5968-198">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d5968-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="d5968-199">[ICorDebugEnum\ interfejsu](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)\</span></span>
 <span data-ttu-id="d5968-200">Służy jako abstrakcyjny interfejs podstawowy do debugowania modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="d5968-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="d5968-201">[ICorDebugErrorInfoEnum\ interfejsu](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-202">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="d5968-202">Obsolete.</span></span> <span data-ttu-id="d5968-203">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d5968-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="d5968-204">[ICorDebugEval\ interfejsu](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-204">[ICorDebugEval Interface](icordebugeval-interface.md)\</span></span>
 <span data-ttu-id="d5968-205">Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="d5968-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="d5968-206">[ICorDebugEval2\ interfejsu](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)\</span></span>
 <span data-ttu-id="d5968-207">Rozszerza `ICorDebugEval`, aby zapewnić obsługę typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="d5968-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="d5968-208">[ICorDebugExceptionDebugEvent\ interfejsu](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)\</span></span>
 <span data-ttu-id="d5968-209">Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) w celu obsługi zdarzeń wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d5968-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="d5968-210">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-211">[ICorDebugExceptionObjectCallStackEnum\ interfejsu](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-212">Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d5968-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="d5968-213">[ICorDebugExceptionObjectValue\ interfejsu](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)\</span></span>
 <span data-ttu-id="d5968-214">Rozszerza interfejs [ICorDebugObjectValue](icordebugobjectvalue-interface.md) w celu udostępnienia informacji o śledzeniu stosu z obiektu wyjątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d5968-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="d5968-215">[ICorDebugFrame\ interfejsu](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-215">[ICorDebugFrame Interface](icordebugframe-interface.md)\</span></span>
 <span data-ttu-id="d5968-216">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="d5968-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="d5968-217">[ICorDebugFrameEnum\ interfejsu](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-218">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugFrame` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="d5968-219">[ICorDebugFunction\ interfejsu](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)\</span></span>
 <span data-ttu-id="d5968-220">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="d5968-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="d5968-221">[ICorDebugFunction2\ interfejsu](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)\</span></span>
 <span data-ttu-id="d5968-222">Logicznie rozszerza `ICorDebugFunction`, aby zapewnić obsługę Tylko mój kod debugowania krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="d5968-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="d5968-223">[ICorDebugFunction3\ interfejsu](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)\</span></span>
 <span data-ttu-id="d5968-224">Logicznie rozszerza interfejs [ICorDebugFunction](icordebugfunction-interface1.md) w celu zapewnienia dostępu do kodu z żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="d5968-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="d5968-225">[ICorDebugFunctionBreakpoint\ interfejsu](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)\</span></span>
 <span data-ttu-id="d5968-226">Rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="d5968-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="d5968-227">[ICorDebugGCReferenceEnum\ interfejsu](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-228">Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="d5968-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="d5968-229">[ICorDebugGenericValue\ interfejsu](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)\</span></span>
 <span data-ttu-id="d5968-230">Podklasa `ICorDebugValue`, która ma zastosowanie do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="d5968-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="d5968-231">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="d5968-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="d5968-232">[ICorDebugGuidToTypeEnum\ interfejsu](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-233">Dostarcza moduł wyliczający dla obiektu, który mapuje identyfikatory GUID i odpowiadające im obiekty `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="d5968-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="d5968-234">[ICorDebugHandleValue\ interfejsu](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)\</span></span>
 <span data-ttu-id="d5968-235">Podklasa `ICorDebugReferenceValue`, która reprezentuje wartość odniesienia, do której debuger utworzył dojście do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d5968-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="d5968-236">[ICorDebugHeapEnum\ interfejsu](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-237">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="d5968-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="d5968-238">[ICorDebugHeapSegmentEnum\ interfejsu](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-239">Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="d5968-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="d5968-240">[ICorDebugHeapValue\ interfejsu](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)\</span></span>
 <span data-ttu-id="d5968-241">Podklasa `ICorDebugValue`, która reprezentuje obiekt, który został zebrany przez moduł wyrzucania elementów bezużytecznych CLR.</span><span class="sxs-lookup"><span data-stu-id="d5968-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="d5968-242">[ICorDebugHeapValue2\ interfejsu](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)\</span></span>
 <span data-ttu-id="d5968-243">Rozszerzenie `ICorDebugHeapValue`, które zapewnia obsługę uchwytów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d5968-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="d5968-244">[ICorDebugHeapValue3\ interfejsu](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)\</span></span>
 <span data-ttu-id="d5968-245">Udostępnia właściwości blokady monitora obiektów.</span><span class="sxs-lookup"><span data-stu-id="d5968-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="d5968-246">[ICorDebugILCode\ interfejsu](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)\</span></span>
 <span data-ttu-id="d5968-247">Reprezentuje segment kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="d5968-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="d5968-248">[ICorDebugILCode2\ interfejsu](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)\</span></span>
 <span data-ttu-id="d5968-249">Logicznie rozszerza interfejs [ICorDebugILCode](icordebugilcode-interface.md) w celu zapewnienia metod, które zwracają token dla sygnatury zmiennej lokalnej funkcji, i mapuje przesunięcia języka pośredniego (IL) narzędzia profilera do oryginalnej metody do przesunięcia Il.</span><span class="sxs-lookup"><span data-stu-id="d5968-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="d5968-250">[ICorDebugILFrame\ interfejsu](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)\</span></span>
 <span data-ttu-id="d5968-251">Reprezentuje ramkę stosu kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="d5968-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="d5968-252">[ICorDebugILFrame2\ interfejsu](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)\</span></span>
 <span data-ttu-id="d5968-253">Logiczne rozszerzenie `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="d5968-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="d5968-254">[ICorDebugILFrame3\ interfejsu](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)\</span></span>
 <span data-ttu-id="d5968-255">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="d5968-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="d5968-256">[Metoda icordebugilframe4\ interfejsu](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)\</span></span>
 <span data-ttu-id="d5968-257">Zapewnia metody umożliwiające dostęp do zmiennych lokalnych i kodu w ramce stosu kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="d5968-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="d5968-258">Parametr określa, czy debuger ma dostęp do zmiennych i kodu dodanych w Instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="d5968-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="d5968-259">[ICorDebugInstanceFieldSymbol\ interfejsu](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\</span></span>
 <span data-ttu-id="d5968-260">Przedstawia informacje o symbolu debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d5968-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="d5968-261">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-262">[ICorDebugInternalFrame\ interfejsu](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)\</span></span>
 <span data-ttu-id="d5968-263">Identyfikuje typy ramek dla debugera.</span><span class="sxs-lookup"><span data-stu-id="d5968-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="d5968-264">[ICorDebugInternalFrame2\ interfejsu](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)\</span></span>
 <span data-ttu-id="d5968-265">Zawiera informacje o ramkach wewnętrznych, łącznie z adresem stosu i pozycją w odniesieniu do obiektów [ICorDebugFrame](icordebugframe-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d5968-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="d5968-266">[ICorDebugLoadedModule\ interfejsu](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)\</span></span>
 <span data-ttu-id="d5968-267">Zawiera informacje o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="d5968-267">Provides information about a loaded module.</span></span> <span data-ttu-id="d5968-268">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-269">[ICorDebugManagedCallback\ interfejsu](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\</span></span>
 <span data-ttu-id="d5968-270">Dostarcza metody do przetwarzania wywołań zwrotnych debugera.</span><span class="sxs-lookup"><span data-stu-id="d5968-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="d5968-271">[ICorDebugManagedCallback2\ interfejsu](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\</span></span>
 <span data-ttu-id="d5968-272">Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="d5968-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="d5968-273">`ICorDebugManagedCallback2` jest logicznym rozszerzeniem `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="d5968-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="d5968-274">[ICorDebugManagedCallback3\ interfejsu](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\</span></span>
 <span data-ttu-id="d5968-275">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="d5968-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="d5968-276">[ICorDebugMDA\ interfejsu](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-276">[ICorDebugMDA Interface](icordebugmda-interface.md)\</span></span>
 <span data-ttu-id="d5968-277">Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="d5968-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="d5968-278">[ICorDebugMemoryBuffer\ interfejsu](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)\</span></span>
 <span data-ttu-id="d5968-279">Reprezentuje bufor w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d5968-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="d5968-280">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-281">[ICorDebugMergedAssemblyRecord\ interfejsu](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)\</span></span>
 <span data-ttu-id="d5968-282">Zawiera informacje o scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="d5968-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="d5968-283">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-284">[ICorDebugMetaDataLocator\ interfejsu](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\</span></span>
 <span data-ttu-id="d5968-285">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="d5968-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="d5968-286">[ICorDebugModule\ interfejsu](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-286">[ICorDebugModule Interface](icordebugmodule-interface.md)\</span></span>
 <span data-ttu-id="d5968-287">Reprezentuje moduł CLR, który jest albo plikiem wykonywalnym lub biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="d5968-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="d5968-288">[ICorDebugModule2\ interfejsu](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)\</span></span>
 <span data-ttu-id="d5968-289">Służy jako logiczne rozszerzenie do `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="d5968-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="d5968-290">[ICorDebugModule3\ interfejsu](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)\</span></span>
 <span data-ttu-id="d5968-291">Tworzy czytnik symbolu dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="d5968-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="d5968-292">[ICorDebugModuleBreakpoint\ interfejsu](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\</span></span>
 <span data-ttu-id="d5968-293">Rozszerza `ICorDebugBreakpoint`, aby zapewnić dostęp do określonych modułów.</span><span class="sxs-lookup"><span data-stu-id="d5968-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="d5968-294">[ICorDebugModuleDebugEvent\ interfejsu](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)\</span></span>
 <span data-ttu-id="d5968-295">Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) w celu obsługi zdarzeń na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="d5968-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="d5968-296">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-297">[ICorDebugModuleEnum\ interfejsu](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-298">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugModule` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="d5968-299">[ICorDebugMutableDataTarget\ interfejsu](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\</span></span>
 <span data-ttu-id="d5968-300">Rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) w celu obsługi modyfikowalnych obiektów docelowych danych.</span><span class="sxs-lookup"><span data-stu-id="d5968-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="d5968-301">[ICorDebugNativeFrame\ interfejsu](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)\</span></span>
 <span data-ttu-id="d5968-302">Wyspecjalizowana implementacja `ICorDebugFrame` używana w przypadku ramek natywnych.</span><span class="sxs-lookup"><span data-stu-id="d5968-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="d5968-303">[ICorDebugNativeFrame2\ interfejsu](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)\</span></span>
 <span data-ttu-id="d5968-304">Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.</span><span class="sxs-lookup"><span data-stu-id="d5968-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="d5968-305">[ICorDebugObjectEnum\ interfejsu](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-306">Implementuje metody `ICorDebugEnum` i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="d5968-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="d5968-307">[ICorDebugObjectValue\ interfejsu](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)\</span></span>
 <span data-ttu-id="d5968-308">Podklasa `ICorDebugValue`, która reprezentuje wartość, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="d5968-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="d5968-309">[ICorDebugObjectValue2\ interfejsu](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)\</span></span>
 <span data-ttu-id="d5968-310">Rozszerza `ICorDebugObjectValue` do obsługi dziedziczenia i zastąpień.</span><span class="sxs-lookup"><span data-stu-id="d5968-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="d5968-311">[ICorDebugProcess\ interfejsu](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)\</span></span>
 <span data-ttu-id="d5968-312">Reprezentuje proces, który wykonuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="d5968-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="d5968-313">[ICorDebugProcess2\ interfejsu](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)\</span></span>
 <span data-ttu-id="d5968-314">Logiczne rozszerzenie `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="d5968-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="d5968-315">[ICorDebugProcess3\ interfejsu](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)\</span></span>
 <span data-ttu-id="d5968-316">Steruje niestandardowymi powiadomieniami debugera.</span><span class="sxs-lookup"><span data-stu-id="d5968-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="d5968-317">[ICorDebugProcess4\ interfejsu](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)\</span></span>
 <span data-ttu-id="d5968-318">Zapewnia obsługę kontroli wykonywania poza procesem.</span><span class="sxs-lookup"><span data-stu-id="d5968-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="d5968-319">[ICorDebugProcess5\ interfejsu](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)\</span></span>
 <span data-ttu-id="d5968-320">Rozszerza interfejs [ICorDebugProcess](icordebugprocess-interface.md) w celu obsługi dostępu do zarządzanej sterty, zapewnia informacje o wyrzucaniu elementów bezużytecznych obiektów zarządzanych i określa, czy debuger ładuje obrazy z lokalnej pamięci podręcznej obrazów natywnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5968-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="d5968-321">[Metoda icordebugprocess6\ interfejsu](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)\</span></span>
 <span data-ttu-id="d5968-322">Logicznie rozszerza interfejs [ICorDebugProcess](icordebugprocess-interface.md) w celu włączenia takich funkcji, jak dekodowanie zdarzeń debugowania zarządzanego, które są kodowane w natywnych zdarzeniach debugowania wyjątków i dzielenia modułu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="d5968-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="d5968-323">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-324">[ICorDebugProcess7\ interfejsu](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)\</span></span>
 <span data-ttu-id="d5968-325">Zapewnia metodę, która umożliwia skonfigurowanie debugera do obsługi aktualizacji metadanych w pamięci w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="d5968-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="d5968-326">[ICorDebugProcess8\ interfejsu](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)\</span></span>
 <span data-ttu-id="d5968-327">Logicznie rozszerza interfejs [ICorDebugProcess](icordebugprocess-interface.md) w celu włączenia lub wyłączenia niektórych typów wywołań zwrotnych wyjątków [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d5968-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="d5968-328">[ICorDebugProcessEnum\ interfejsu](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-329">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugProcess` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="d5968-330">[ICorDebugReferenceValue\ interfejsu](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)\</span></span>
 <span data-ttu-id="d5968-331">Podklasa `ICorDebugValue`, która obsługuje typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="d5968-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="d5968-332">[ICorDebugRegisterSet\ interfejsu](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)\</span></span>
 <span data-ttu-id="d5968-333">Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="d5968-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="d5968-334">[ICorDebugRegisterSet2\ interfejsu](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)\</span></span>
 <span data-ttu-id="d5968-335">Rozszerza możliwości `ICorDebugRegisterSet` dla platform sprzętowych, które mają więcej niż 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="d5968-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="d5968-336">[ICorDebugRemote\ interfejsu](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-336">[ICorDebugRemote Interface](icordebugremote-interface.md)\</span></span>
 <span data-ttu-id="d5968-337">Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="d5968-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="d5968-338">[ICorDebugRemoteTarget\ interfejsu](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)\</span></span>
 <span data-ttu-id="d5968-339">Dostarcza metody, które umożliwiają debugowania aplikacji opartych na dodatku Silverlight w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="d5968-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="d5968-340">[ICorDebugRuntimeUnwindableFrame\ interfejsu](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)\</span></span>
 <span data-ttu-id="d5968-341">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="d5968-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="d5968-342">[ICorDebugStackWalk\ interfejsu](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)\</span></span>
 <span data-ttu-id="d5968-343">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="d5968-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="d5968-344">[ICorDebugStaticFieldSymbol\ interfejsu](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)\</span></span>
 <span data-ttu-id="d5968-345">Przedstawia informacje o symbolu debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="d5968-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="d5968-346">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-347">[ICorDebugStepper\ interfejsu](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)\</span></span>
 <span data-ttu-id="d5968-348">Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.</span><span class="sxs-lookup"><span data-stu-id="d5968-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="d5968-349">[ICorDebugStepper2\ interfejsu](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)\</span></span>
 <span data-ttu-id="d5968-350">Zapewnia obsługę debugowania Tylko mój kod (JMC).</span><span class="sxs-lookup"><span data-stu-id="d5968-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="d5968-351">[ICorDebugStepperEnum\ interfejsu](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-352">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugStepper` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="d5968-353">[ICorDebugStringValue\ interfejsu](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)\</span></span>
 <span data-ttu-id="d5968-354">Podklasa `ICorDebugHeapValue`, która ma zastosowanie do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="d5968-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="d5968-355">[ICorDebugSymbolProvider\ interfejsu](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)\</span></span>
 <span data-ttu-id="d5968-356">Dostarcza metody, których można użyć do pobrania informacji o symbolach debugowania.</span><span class="sxs-lookup"><span data-stu-id="d5968-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="d5968-357">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-358">[ICorDebugSymbolProvider2\ interfejsu](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)\</span></span>
 <span data-ttu-id="d5968-359">Logicznie rozszerza interfejs [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) w celu pobrania dodatkowych informacji o symbolach debugowania.</span><span class="sxs-lookup"><span data-stu-id="d5968-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="d5968-360">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-361">[ICorDebugThread\ interfejsu](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-361">[ICorDebugThread Interface](icordebugthread-interface.md)\</span></span>
 <span data-ttu-id="d5968-362">Reprezentuje wątek w procesie.</span><span class="sxs-lookup"><span data-stu-id="d5968-362">Represents a thread in a process.</span></span> <span data-ttu-id="d5968-363">Okres istnienia wystąpienia `ICorDebugThread` jest taki sam jak okres istnienia wątku, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="d5968-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="d5968-364">[ICorDebugThread2\ interfejsu](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)\</span></span>
 <span data-ttu-id="d5968-365">Służy jako logiczne rozszerzenie do `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="d5968-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="d5968-366">[ICorDebugThread3\ interfejsu](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)\</span></span>
 <span data-ttu-id="d5968-367">Udostępnia punkt wejścia do [ICorDebugStackWalk](icordebugstackwalk-interface.md) i odpowiednich interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d5968-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="d5968-368">[ICorDebugThread4\ interfejsu](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)\</span></span>
 <span data-ttu-id="d5968-369">Dostarcza informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="d5968-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="d5968-370">[ICorDebugThreadEnum\ interfejsu](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)\</span></span>
 <span data-ttu-id="d5968-371">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugThread` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="d5968-372">[ICorDebugType\ interfejsu](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-372">[ICorDebugType Interface](icordebugtype-interface.md)\</span></span>
 <span data-ttu-id="d5968-373">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="d5968-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="d5968-374">Jeśli typ jest ogólny, `ICorDebugType` reprezentuje typ ogólny wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d5968-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="d5968-375">[ICorDebugType2\ interfejsu](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)\</span></span>
 <span data-ttu-id="d5968-376">Rozszerza interfejs [ICorDebugType](icordebugtype-interface.md) w celu pobrania identyfikatora typu podstawowego lub złożonego (zdefiniowanego przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="d5968-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="d5968-377">[ICorDebugTypeEnum\ interfejsu](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-378">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugType` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="d5968-379">[ICorDebugUnmanagedCallback\ interfejsu](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)\</span></span>
 <span data-ttu-id="d5968-380">Zapewnia powiadomienie macierzystych zdarzeń, które nie dotyczą bezpośrednio środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d5968-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="d5968-381">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="d5968-382">Reprezentuje wartość odczytu lub zapisu w procesie debugowania.</span><span class="sxs-lookup"><span data-stu-id="d5968-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="d5968-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="d5968-384">Rozszerza `ICorDebugValue`, aby zapewnić obsługę `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="d5968-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="d5968-385">[ICorDebugValue3\ interfejsu](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)\</span></span>
 <span data-ttu-id="d5968-386">Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic o rozmiarze większym niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="d5968-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="d5968-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="d5968-388">Rozszerza `ICorDebugBreakpoint`, aby zapewnić dostęp do określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="d5968-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="d5968-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="d5968-390">Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugValue` tablice.</span><span class="sxs-lookup"><span data-stu-id="d5968-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="d5968-391">[ICorDebugVariableHome\ interfejsu](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)\</span></span>
 <span data-ttu-id="d5968-392">Reprezentuje zmienną lokalną lub argument funkcji.</span><span class="sxs-lookup"><span data-stu-id="d5968-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="d5968-393">[ICorDebugVariableHomeEnum\ interfejsu](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-394">Dostarcza moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="d5968-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="d5968-395">[ICorDebugVariableSymbol\ interfejsu](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)\</span></span>
 <span data-ttu-id="d5968-396">Pobiera informacje o symbolach debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d5968-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="d5968-397">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-398">[ICorDebugVirtualUnwinder\ interfejsu](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)\</span></span>
 <span data-ttu-id="d5968-399">Zapewnia metody pomagające w rozwinięcia stosu.</span><span class="sxs-lookup"><span data-stu-id="d5968-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="d5968-400">**Dostępne tylko .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="d5968-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="d5968-401">[ICorPublish\ interfejsu](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-401">[ICorPublish Interface](icorpublish-interface.md)\</span></span>
 <span data-ttu-id="d5968-402">Służy jako ogólny interfejs dla procesów publikowania.</span><span class="sxs-lookup"><span data-stu-id="d5968-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="d5968-403">[ICorPublishAppDomain\ interfejsu](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)\</span></span>
 <span data-ttu-id="d5968-404">Reprezentuje i dostarcza informacje dotyczące domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5968-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="d5968-405">[ICorPublishAppDomainEnum\ interfejsu](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-406">Dostarcza metody, które przechodzą przez kolekcję `ICorPublishAppDomain` obiektów, które aktualnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d5968-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="d5968-407">[ICorPublishEnum\ interfejsu](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-408">Służy jako abstrakcyjna podstawowa do publikowania modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="d5968-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="d5968-409">[ICorPublishProcess\ interfejsu](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)\</span></span>
 <span data-ttu-id="d5968-410">Dostarcza metody, które mają dostęp do informacji dotyczących procesu.</span><span class="sxs-lookup"><span data-stu-id="d5968-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="d5968-411">[ICorPublishProcessEnum\ interfejsu](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)\</span></span>
 <span data-ttu-id="d5968-412">Dostarcza metody, które przechodzą przez kolekcję obiektów `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="d5968-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="d5968-413">[ISOSDacInterface\ interfejsu](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)\</span></span>
 <span data-ttu-id="d5968-414">Zapewnia metody pomocnika do uzyskiwania dostępu do danych z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="d5968-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="d5968-415">[IXCLRDataMethodDefinition\ interfejsu](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)\</span></span>
 <span data-ttu-id="d5968-416">Zapewnia metody wykonywania zapytań dotyczących informacji o definicji metody.</span><span class="sxs-lookup"><span data-stu-id="d5968-416">Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="d5968-417">[IXCLRDataMethodInstance\ interfejsu](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)\</span></span>
 <span data-ttu-id="d5968-418">Zapewnia metody wykonywania zapytań dotyczących informacji o wystąpieniu metody.</span><span class="sxs-lookup"><span data-stu-id="d5968-418">Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="d5968-419">[IXCLRDataModule\ interfejsu](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)\</span></span>
 <span data-ttu-id="d5968-420">Zapewnia metody wykonywania zapytania o informacje o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="d5968-420">Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="d5968-421">[IXCLRDataProcess\ interfejsu](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)\</span></span>
 <span data-ttu-id="d5968-422">Dostarcza metody do wykonywania zapytań dotyczących informacji o procesie.</span><span class="sxs-lookup"><span data-stu-id="d5968-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="d5968-423">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d5968-423">Related Sections</span></span>  
 <span data-ttu-id="d5968-424">[Klasy coclass debugowania](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="d5968-425">[Debugowanie globalnych funkcji statycznych](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="d5968-426">\ [wyliczeń debugowania](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-426">[Debugging Enumerations](debugging-enumerations.md)\</span></span>
 <span data-ttu-id="d5968-427">[Struktury debugowania](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="d5968-427">[Debugging Structures](debugging-structures.md)</span></span>\
