---
title: Debugowanie — Interfejsy
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d939063aaefb00d4db3de604df0dbd1b2175bf95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698424"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="87245-102">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="87245-102">Debugging Interfaces</span></span>
<span data-ttu-id="87245-103">W tej sekcji opisano niezarządzane interfejsy obsługujące debugowanie programu wykonywanego w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="87245-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87245-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="87245-104">In This Section</span></span>  
 <span data-ttu-id="87245-105">[Iclrdataenummemoryregions — interfejs](iclrdataenummemoryregions-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)\\</span></span>
 <span data-ttu-id="87245-106">Zapewnia metodę pozwalającą wyliczyć obszary pamięci, które są określone przez obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="87245-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="87245-107">[Iclrdataenummemoryregionscallback — interfejs](iclrdataenummemoryregionscallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)\\</span></span>
 <span data-ttu-id="87245-108">Zapewnia metodę wywołania zwrotnego dla `EnumMemoryRegions` do zgłaszania do debugera wyniku próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="87245-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="87245-109">[Iclrdatatarget — interfejs](iclrdatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)\\</span></span>
 <span data-ttu-id="87245-110">Zapewnia metody interakcji z obiektem docelowym procesu CLR.</span><span class="sxs-lookup"><span data-stu-id="87245-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="87245-111">[Iclrdatatarget2 — interfejs](iclrdatatarget2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)\\</span></span>
 <span data-ttu-id="87245-112">Podklasa klasy `ICLRDataTarget` używany przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="87245-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="87245-113">[ICLRDataTarget3, interfejs](iclrdatatarget3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)\\</span></span>
 <span data-ttu-id="87245-114">Podklasa klasy [ICLRDataTarget2](iclrdatatarget2-interface.md) , który zapewnia dostęp do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="87245-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="87245-115">[Iclrdebugging — interfejs](iclrdebugging-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-115">[ICLRDebugging Interface](iclrdebugging-interface.md)\\</span></span>
 <span data-ttu-id="87245-116">Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.</span><span class="sxs-lookup"><span data-stu-id="87245-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="87245-117">[Iclrdebugginglibraryprovider — interfejs](iclrdebugginglibraryprovider-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)\\</span></span>
 <span data-ttu-id="87245-118">Obejmuje [providelibrary — metoda](iclrdebugginglibraryprovider-providelibrary-method.md) metody, która pobiera interfejs wywołania zwrotnego, która umożliwia języka wspólnego bibliotek debugowania specyficznych dla wersji środowiska uruchomieniowego lokalizowanie i ładowanie na żądanie dostawcy biblioteki.</span><span class="sxs-lookup"><span data-stu-id="87245-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="87245-119">[Iclrmetadatalocator — interfejs](iclrmetadatalocator-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)\\</span></span>
 <span data-ttu-id="87245-120">Interfejs używany przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="87245-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="87245-121">[Icordebug — interfejs](icordebug-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-121">[ICorDebug Interface](icordebug-interface.md)\\</span></span>
 <span data-ttu-id="87245-122">Dostarcza metody, które umożliwiają programistom debugowanie aplikacji w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="87245-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="87245-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)\\</span></span>
 <span data-ttu-id="87245-124">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87245-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="87245-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\\</span></span>
 <span data-ttu-id="87245-126">Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami ByRef.</span><span class="sxs-lookup"><span data-stu-id="87245-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="87245-127">Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="87245-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="87245-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\\</span></span>
 <span data-ttu-id="87245-129">Dostarcza metody do pracy z [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87245-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="87245-130">Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` i `ICorDebugAppDomain2` interfejsów.</span><span class="sxs-lookup"><span data-stu-id="87245-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="87245-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\\</span></span>
 <span data-ttu-id="87245-132">Rozszerza logicznie [ICorDebugAppDomain](icordebugappdomain-interface.md) interfejsu można pobrać obiektu zarządzanego z wywołalne opakowanie COM.</span><span class="sxs-lookup"><span data-stu-id="87245-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="87245-133">[Icordebugappdomainenum — interfejs](icordebugappdomainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-134">Dostarcza metodę, która zwraca określoną liczbę `ICorDebugAppDomain` wartości, zaczynając od następnej pozycji w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="87245-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="87245-135">[Icordebugarrayvalue — interfejs](icordebugarrayvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-136">Podklasa klasy `ICorDebugHeapValue` reprezentująca tablicę jednowymiarową lub wielowymiarową.</span><span class="sxs-lookup"><span data-stu-id="87245-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="87245-137">[Icordebugassembly — interfejs](icordebugassembly-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)\\</span></span>
 <span data-ttu-id="87245-138">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="87245-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="87245-139">[Icordebugassembly2 — interfejs](icordebugassembly2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)\\</span></span>
 <span data-ttu-id="87245-140">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="87245-140">Represents an assembly.</span></span> <span data-ttu-id="87245-141">Ten interfejs jest rozszerzeniem `ICorDebugAssembly` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="87245-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="87245-142">[ICorDebugAssembly3, interfejs](icordebugassembly3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)\\</span></span>
 <span data-ttu-id="87245-143">Rozszerza logicznie [ICorDebugAssembly](icordebugassembly-interface.md) interfejs w celu zapewnienia obsługi kontenerów zestawów i ich zestawy zawarte.</span><span class="sxs-lookup"><span data-stu-id="87245-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="87245-144">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-145">[Icordebugassemblyenum — interfejs](icordebugassemblyenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-146">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugAssembly` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="87245-147">[Icordebugblockingobjectenum — interfejs](icordebugblockingobjectenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-148">Dostarcza moduł wyliczający listę [CorDebugBlockingObject](cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="87245-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="87245-149">[Icordebugboxvalue — interfejs](icordebugboxvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-150">Podklasa klasy `ICorDebugHeapValue` reprezentująca spakowany obiekt klasy wartości.</span><span class="sxs-lookup"><span data-stu-id="87245-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="87245-151">[Icordebugbreakpoint — interfejs](icordebugbreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="87245-152">Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.</span><span class="sxs-lookup"><span data-stu-id="87245-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="87245-153">[Icordebugbreakpointenum — interfejs](icordebugbreakpointenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-154">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugBreakpoint` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="87245-155">[Icordebugchain — interfejs](icordebugchain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-155">[ICorDebugChain Interface](icordebugchain-interface.md)\\</span></span>
 <span data-ttu-id="87245-156">Reprezentuje segment stosu wywołań fizycznych lub logicznych.</span><span class="sxs-lookup"><span data-stu-id="87245-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="87245-157">[Icordebugchainenum — interfejs](icordebugchainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-158">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugChain` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="87245-159">[ICorDebugClass Interface](icordebugclass-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-159">[ICorDebugClass Interface](icordebugclass-interface.md)\\</span></span>
 <span data-ttu-id="87245-160">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="87245-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="87245-161">Jeśli typ ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="87245-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="87245-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)\\</span></span>
 <span data-ttu-id="87245-163">Reprezentuje klasą rodzajową lub klasy z parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="87245-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="87245-164">Ten interfejs rozszerza `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="87245-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="87245-165">[Icordebugcode — interfejs](icordebugcode-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-165">[ICorDebugCode Interface](icordebugcode-interface1.md)\\</span></span>
 <span data-ttu-id="87245-166">Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="87245-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="87245-167">[Icordebugcode2 — interfejs](icordebugcode2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)\\</span></span>
 <span data-ttu-id="87245-168">Udostępnia metody, które rozszerzają możliwości `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="87245-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="87245-169">[ICorDebugCode3, interfejs](icordebugcode3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)\\</span></span>
 <span data-ttu-id="87245-170">Dostarcza metodę, która rozszerza [ICorDebugCode](icordebugcode-interface1.md) i [ICorDebugCode2](icordebugcode2-interface.md) aby podać informacje o zarządzaniu wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="87245-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="87245-171">[ICorDebugCode4, interfejs](icordebugcode4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)\\</span></span>
 <span data-ttu-id="87245-172">Dostarcza metodę, która umożliwia debugera wyliczanie zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="87245-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="87245-173">[Icordebugcodeenum — interfejs](icordebugcodeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-174">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugCode` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="87245-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-176">Dostarcza metody pobierania obiektów interfejsu w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="87245-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="87245-177">[Icordebugcontext — interfejs](icordebugcontext-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-177">[ICorDebugContext Interface](icordebugcontext-interface.md)\\</span></span>
 <span data-ttu-id="87245-178">Reprezentuje obiekt kontekstu.</span><span class="sxs-lookup"><span data-stu-id="87245-178">Represents a context object.</span></span> <span data-ttu-id="87245-179">Ten Interfejs nie został jeszcze implementowany.</span><span class="sxs-lookup"><span data-stu-id="87245-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="87245-180">[ICorDebugController Interface](icordebugcontroller-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-180">[ICorDebugController Interface](icordebugcontroller-interface.md)\\</span></span>
 <span data-ttu-id="87245-181">Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, wykonanie kodu, które mogą być kontrolowane kontekstu.</span><span class="sxs-lookup"><span data-stu-id="87245-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="87245-182">[Icordebugdatatarget — interfejs](icordebugdatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)\\</span></span>
 <span data-ttu-id="87245-183">Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="87245-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="87245-184">[ICorDebugDataTarget2, interfejs](icordebugdatatarget2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)\\</span></span>
 <span data-ttu-id="87245-185">Rozszerza logicznie [icordebugdatatarget —](icordebugdatatarget-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="87245-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="87245-186">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\\</span></span>
 <span data-ttu-id="87245-188">Rozszerza logicznie [icordebugdatatarget —](icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów.</span><span class="sxs-lookup"><span data-stu-id="87245-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="87245-189">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-190">[ICorDebugDebugEvent, interfejs](icordebugdebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)\\</span></span>
 <span data-ttu-id="87245-191">Definiuje interfejs podstawowy, z którym wszystkie `ICorDebug` pochodzić zdarzeń debugowania.</span><span class="sxs-lookup"><span data-stu-id="87245-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="87245-192">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\\</span></span>
 <span data-ttu-id="87245-194">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="87245-194">Obsolete.</span></span> <span data-ttu-id="87245-195">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="87245-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="87245-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)\\</span></span>
 <span data-ttu-id="87245-197">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="87245-197">Obsolete.</span></span> <span data-ttu-id="87245-198">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="87245-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="87245-199">[Icordebugenum — interfejs](icordebugenum-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)\\</span></span>
 <span data-ttu-id="87245-200">Służy jako abstrakcyjny interfejs podstawowy do debugowania modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="87245-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="87245-201">[Icordebugerrorinfoenum — interfejs](icordebugerrorinfoenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-202">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="87245-202">Obsolete.</span></span> <span data-ttu-id="87245-203">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="87245-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="87245-204">[Icordebugeval — interfejs](icordebugeval-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-204">[ICorDebugEval Interface](icordebugeval-interface.md)\\</span></span>
 <span data-ttu-id="87245-205">Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="87245-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="87245-206">[Icordebugeval2 — interfejs](icordebugeval2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)\\</span></span>
 <span data-ttu-id="87245-207">Rozszerza `ICorDebugEval` celu zapewnienia obsługi typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="87245-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="87245-208">[ICorDebugExceptionDebugEvent, interfejs](icordebugexceptiondebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)\\</span></span>
 <span data-ttu-id="87245-209">Rozszerza [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń dotyczących wyjątków.</span><span class="sxs-lookup"><span data-stu-id="87245-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="87245-210">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-211">[Icordebugexceptionobjectcallstackenum — interfejs](icordebugexceptionobjectcallstackenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-212">Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="87245-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="87245-213">[Icordebugexceptionobjectvalue — interfejs](icordebugexceptionobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-214">Rozszerza [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interfejsu, aby zapewnić informacje śledzenia stosu z zarządzanego obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="87245-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="87245-215">[ICorDebugFrame Interface](icordebugframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-215">[ICorDebugFrame Interface](icordebugframe-interface.md)\\</span></span>
 <span data-ttu-id="87245-216">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="87245-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="87245-217">[Icordebugframeenum — interfejs](icordebugframeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-218">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugFrame` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="87245-219">[ICorDebugFunction — interfejs](icordebugfunction-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)\\</span></span>
 <span data-ttu-id="87245-220">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="87245-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="87245-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)\\</span></span>
 <span data-ttu-id="87245-222">Rozszerza logicznie `ICorDebugFunction` zapewnia obsługę debugowania tylko mój kod krokowym.</span><span class="sxs-lookup"><span data-stu-id="87245-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="87245-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)\\</span></span>
 <span data-ttu-id="87245-224">Rozszerza logicznie [ICorDebugFunction](icordebugfunction-interface1.md) interfejsu, aby zapewnić dostęp do kodu z żądaniem ReJIT.</span><span class="sxs-lookup"><span data-stu-id="87245-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="87245-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="87245-226">Rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w obrębie funkcji.</span><span class="sxs-lookup"><span data-stu-id="87245-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="87245-227">[Icordebuggcreferenceenum — interfejs](icordebuggcreferenceenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-228">Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="87245-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="87245-229">[Icordebuggenericvalue — interfejs](icordebuggenericvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-230">Podklasa klasy `ICorDebugValue` która odnosi się do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="87245-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="87245-231">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="87245-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="87245-232">[Icordebugguidtotypeenum — interfejs](icordebugguidtotypeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-233">Dostarcza moduł wyliczający dla obiektu, który mapuje identyfikatory GUID i odpowiednie `ICorDebugType` obiektów.</span><span class="sxs-lookup"><span data-stu-id="87245-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="87245-234">[Icordebughandlevalue — interfejs](icordebughandlevalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-235">Podklasa klasy `ICorDebugReferenceValue` reprezentująca wartość odniesienia, do której debuger utworzył procedurę obsługi do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="87245-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="87245-236">[Icordebugheapenum — interfejs](icordebugheapenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-237">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="87245-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="87245-238">[Icordebugheapsegmentenum — interfejs](icordebugheapsegmentenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-239">Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="87245-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="87245-240">[Icordebugheapvalue — interfejs](icordebugheapvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-241">Podklasa klasy `ICorDebugValue` reprezentująca obiekt, który został zebrany przez moduł odśmiecania pamięci CLR.</span><span class="sxs-lookup"><span data-stu-id="87245-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="87245-242">[Icordebugheapvalue2 — interfejs](icordebugheapvalue2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)\\</span></span>
 <span data-ttu-id="87245-243">Rozszerzenie `ICorDebugHeapValue` który zapewnia obsługę dla obsługi środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="87245-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="87245-244">[Icordebugheapvalue3 — interfejs](icordebugheapvalue3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)\\</span></span>
 <span data-ttu-id="87245-245">Udostępnia właściwości blokady monitora obiektów.</span><span class="sxs-lookup"><span data-stu-id="87245-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="87245-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)\\</span></span>
 <span data-ttu-id="87245-247">Reprezentuje segment kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="87245-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="87245-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)\\</span></span>
 <span data-ttu-id="87245-249">Rozszerza logicznie [ICorDebugILCode](icordebugilcode-interface.md) interfejsu podania metod, które zwracają token do funkcji lokalnej zmiennej podpisu i mapy, program profilujący instrumentowanych języka pośredniego (IL) przesuwa się do oryginalnej metody IL przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="87245-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="87245-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)\\</span></span>
 <span data-ttu-id="87245-251">Reprezentuje ramkę stosu kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="87245-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="87245-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)\\</span></span>
 <span data-ttu-id="87245-253">Logiczne rozszerzenie `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="87245-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="87245-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)\\</span></span>
 <span data-ttu-id="87245-255">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="87245-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="87245-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)\\</span></span>
 <span data-ttu-id="87245-257">Udostępnia metody, które umożliwiają dostęp do zmiennych lokalnych i kod w ramce stosu kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="87245-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="87245-258">Parametr określa, czy narzędzie debuger ma dostęp do zmiennych i kodzie dodanym w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="87245-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="87245-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\\</span></span>
 <span data-ttu-id="87245-260">Reprezentuje informacji dotyczących symboli debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="87245-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="87245-261">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)\\</span></span>
 <span data-ttu-id="87245-263">Identyfikuje typy ramek dla debugera.</span><span class="sxs-lookup"><span data-stu-id="87245-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="87245-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)\\</span></span>
 <span data-ttu-id="87245-265">Zawiera informacje o ramkach wewnętrznych, łącznie z adresem stosu i pozycją w odniesieniu do [ICorDebugFrame](icordebugframe-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="87245-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="87245-266">[ICorDebugLoadedModule, interfejs](icordebugloadedmodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)\\</span></span>
 <span data-ttu-id="87245-267">Zawiera informacje dotyczące załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="87245-267">Provides information about a loaded module.</span></span> <span data-ttu-id="87245-268">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\\</span></span>
 <span data-ttu-id="87245-270">Dostarcza metody do przetwarzania wywołań zwrotnych debugera.</span><span class="sxs-lookup"><span data-stu-id="87245-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="87245-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\\</span></span>
 <span data-ttu-id="87245-272">Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="87245-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="87245-273">`ICorDebugManagedCallback2` jest logicznym rozszerzeniem `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="87245-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="87245-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\\</span></span>
 <span data-ttu-id="87245-275">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="87245-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="87245-276">[ICorDebugMDA Interface](icordebugmda-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-276">[ICorDebugMDA Interface](icordebugmda-interface.md)\\</span></span>
 <span data-ttu-id="87245-277">Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="87245-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="87245-278">[ICorDebugMemoryBuffer, interfejs](icordebugmemorybuffer-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)\\</span></span>
 <span data-ttu-id="87245-279">Reprezentuje buforów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="87245-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="87245-280">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-281">[ICorDebugMergedAssemblyRecord, interfejs](icordebugmergedassemblyrecord-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)\\</span></span>
 <span data-ttu-id="87245-282">Zawiera informacje o zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="87245-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="87245-283">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\\</span></span>
 <span data-ttu-id="87245-285">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="87245-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="87245-286">[Icordebugmodule — interfejs](icordebugmodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-286">[ICorDebugModule Interface](icordebugmodule-interface.md)\\</span></span>
 <span data-ttu-id="87245-287">Reprezentuje moduł CLR, który jest albo plikiem wykonywalnym lub biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="87245-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="87245-288">[Icordebugmodule2 — interfejs](icordebugmodule2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)\\</span></span>
 <span data-ttu-id="87245-289">Służy jako logiczne rozszerzenie `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="87245-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="87245-290">[Icordebugmodule3 — interfejs](icordebugmodule3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)\\</span></span>
 <span data-ttu-id="87245-291">Tworzy czytnik symbolu dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="87245-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="87245-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="87245-293">Rozszerza `ICorDebugBreakpoint` zapewnienie dostępu do konkretnych modułów.</span><span class="sxs-lookup"><span data-stu-id="87245-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="87245-294">[ICorDebugModuleDebugEvent, interfejs](icordebugmoduledebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)\\</span></span>
 <span data-ttu-id="87245-295">Rozszerza [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="87245-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="87245-296">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-297">[Icordebugmoduleenum — interfejs](icordebugmoduleenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-298">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugModule` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="87245-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\\</span></span>
 <span data-ttu-id="87245-300">Rozszerza [icordebugdatatarget —](icordebugdatatarget-interface.md) interfejsu do obsługi danych modyfikowalnych elementów docelowych.</span><span class="sxs-lookup"><span data-stu-id="87245-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="87245-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)\\</span></span>
 <span data-ttu-id="87245-302">Wyspecjalizowana implementacja `ICorDebugFrame` wykorzystywana do ramek natywnych.</span><span class="sxs-lookup"><span data-stu-id="87245-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="87245-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)\\</span></span>
 <span data-ttu-id="87245-304">Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.</span><span class="sxs-lookup"><span data-stu-id="87245-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="87245-305">[Icordebugobjectenum — interfejs](icordebugobjectenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-306">Implementuje `ICorDebugEnum` metod i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="87245-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="87245-307">[Icordebugobjectvalue — interfejs](icordebugobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-308">Podklasa klasy `ICorDebugValue` reprezentująca wartość, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="87245-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="87245-309">[Icordebugobjectvalue2 — interfejs](icordebugobjectvalue2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)\\</span></span>
 <span data-ttu-id="87245-310">Rozszerza `ICorDebugObjectValue` do obsługi dziedziczenia i zastępowania.</span><span class="sxs-lookup"><span data-stu-id="87245-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="87245-311">[Icordebugprocess — interfejs](icordebugprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)\\</span></span>
 <span data-ttu-id="87245-312">Reprezentuje proces, który wykonuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="87245-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="87245-313">[Icordebugprocess2 — interfejs](icordebugprocess2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)\\</span></span>
 <span data-ttu-id="87245-314">Logiczne rozszerzenie `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="87245-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="87245-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)\\</span></span>
 <span data-ttu-id="87245-316">Steruje niestandardowymi powiadomieniami debugera.</span><span class="sxs-lookup"><span data-stu-id="87245-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="87245-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)\\</span></span>
 <span data-ttu-id="87245-318">Zapewnia obsługę poza Kontrola wykonywania procesu.</span><span class="sxs-lookup"><span data-stu-id="87245-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="87245-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)\\</span></span>
 <span data-ttu-id="87245-320">Rozszerza [ICorDebugProcess](icordebugprocess-interface.md) obsługiwany dostęp do zarządzanej sterty, do dostarczania informacji dotyczących wyrzucania elementów bezużytecznych obiektów zarządzanych i określenia, czy debuger wczytuje obrazy z aplikacji przez interfejs użytkownika lokalnego pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="87245-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="87245-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)\\</span></span>
 <span data-ttu-id="87245-322">Rozszerza logicznie [ICorDebugProcess](icordebugprocess-interface.md) interfejsu, aby włączyć funkcje, takie jak dekodowanie zdarzenia debugowania zarządzanego, które są kodowane w zdarzeń debugowania natywnych wyjątków oraz wirtualnego modułu dzielenia.</span><span class="sxs-lookup"><span data-stu-id="87245-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="87245-323">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-324">[ICorDebugProcess7, interfejs](icordebugprocess7-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)\\</span></span>
 <span data-ttu-id="87245-325">Dostarcza metodę, która umożliwia skonfigurowanie debuger mógł obsłużyć aktualizacji metadanych w pamięci w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="87245-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="87245-326">[ICorDebugProcess8, interfejs](icordebugprocess8-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)\\</span></span>
 <span data-ttu-id="87245-327">Rozszerza logicznie [ICorDebugProcess](icordebugprocess-interface.md) interfejsu, aby włączyć lub wyłączyć niektórych rodzajów [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) wywołań zwrotnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="87245-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="87245-328">[Icordebugprocessenum — interfejs](icordebugprocessenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-329">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugProcess` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="87245-330">[Icordebugreferencevalue — interfejs](icordebugreferencevalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-331">Podklasa klasy `ICorDebugValue` obsługuje typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="87245-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="87245-332">[Icordebugregisterset — interfejs](icordebugregisterset-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)\\</span></span>
 <span data-ttu-id="87245-333">Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="87245-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="87245-334">[Icordebugregisterset2 — interfejs](icordebugregisterset2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)\\</span></span>
 <span data-ttu-id="87245-335">Rozszerza możliwości `ICorDebugRegisterSet` dla platform sprzętowych, które mają więcej niż 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="87245-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="87245-336">[Icordebugremote — interfejs](icordebugremote-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-336">[ICorDebugRemote Interface](icordebugremote-interface.md)\\</span></span>
 <span data-ttu-id="87245-337">Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="87245-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="87245-338">[Icordebugremotetarget — interfejs](icordebugremotetarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)\\</span></span>
 <span data-ttu-id="87245-339">Dostarcza metody, które umożliwiają debugowania aplikacji opartych na dodatku Silverlight w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="87245-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="87245-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)\\</span></span>
 <span data-ttu-id="87245-341">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="87245-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="87245-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)\\</span></span>
 <span data-ttu-id="87245-343">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="87245-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="87245-344">[ICorDebugStaticFieldSymbol, interfejs](icordebugstaticfieldsymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)\\</span></span>
 <span data-ttu-id="87245-345">Reprezentuje informacji dotyczących symboli debugowania dla pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="87245-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="87245-346">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-347">[ICorDebugStepper — interfejs](icordebugstepper-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)\\</span></span>
 <span data-ttu-id="87245-348">Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.</span><span class="sxs-lookup"><span data-stu-id="87245-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="87245-349">[Icordebugstepper2 — interfejs](icordebugstepper2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)\\</span></span>
 <span data-ttu-id="87245-350">Zapewnia obsługę debugowania Tylko mój kod (JMC).</span><span class="sxs-lookup"><span data-stu-id="87245-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="87245-351">[Icordebugstepperenum — interfejs](icordebugstepperenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-352">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugStepper` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="87245-353">[Icordebugstringvalue — interfejs](icordebugstringvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-354">Podklasa klasy `ICorDebugHeapValue` która odnosi się do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="87245-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="87245-355">[ICorDebugSymbolProvider, interfejs](icordebugsymbolprovider-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)\\</span></span>
 <span data-ttu-id="87245-356">Udostępnia metody, które mogą służyć do pobierania informacji dotyczących symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="87245-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="87245-357">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-358">[ICorDebugSymbolProvider2, interfejs](icordebugsymbolprovider2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)\\</span></span>
 <span data-ttu-id="87245-359">Rozszerza logicznie [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interfejsu można pobrać informacji dotyczących symboli debugowania dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="87245-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="87245-360">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-361">[Icordebugthread — interfejs](icordebugthread-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-361">[ICorDebugThread Interface](icordebugthread-interface.md)\\</span></span>
 <span data-ttu-id="87245-362">Reprezentuje wątek w procesie.</span><span class="sxs-lookup"><span data-stu-id="87245-362">Represents a thread in a process.</span></span> <span data-ttu-id="87245-363">Okres istnienia `ICorDebugThread` wystąpienie jest taki sam, jak okres istnienia wątku, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="87245-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="87245-364">[Icordebugthread2 — interfejs](icordebugthread2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)\\</span></span>
 <span data-ttu-id="87245-365">Służy jako logiczne rozszerzenie `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="87245-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="87245-366">[Icordebugthread3 — interfejs](icordebugthread3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)\\</span></span>
 <span data-ttu-id="87245-367">Zapewnia punkt wejścia do [ICorDebugStackWalk](icordebugstackwalk-interface.md) i odpowiednich interfejsów.</span><span class="sxs-lookup"><span data-stu-id="87245-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="87245-368">[Icordebugthread4 — interfejs](icordebugthread4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)\\</span></span>
 <span data-ttu-id="87245-369">Dostarcza informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="87245-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="87245-370">[Icordebugthreadenum — interfejs](icordebugthreadenum-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)\\</span></span>
 <span data-ttu-id="87245-371">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugThread` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="87245-372">[Icordebugtype — interfejs](icordebugtype-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-372">[ICorDebugType Interface](icordebugtype-interface.md)\\</span></span>
 <span data-ttu-id="87245-373">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="87245-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="87245-374">Jeśli typ ogólny, `ICorDebugType` reprezentuje typ ogólny z wystąpieniami.</span><span class="sxs-lookup"><span data-stu-id="87245-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="87245-375">[ICorDebugType2, interfejs](icordebugtype2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)\\</span></span>
 <span data-ttu-id="87245-376">Rozszerza [ICorDebugType](icordebugtype-interface.md) interfejsu, aby pobrać identyfikator typu Typ podstawowy lub złożony (typ zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="87245-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="87245-377">[Icordebugtypeenum — interfejs](icordebugtypeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-378">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugType` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="87245-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)\\</span></span>
 <span data-ttu-id="87245-380">Zapewnia powiadomienie macierzystych zdarzeń, które nie dotyczą bezpośrednio środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="87245-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="87245-381">[ICorDebugValue](icordebugvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-381">[ICorDebugValue](icordebugvalue-interface.md)\\</span></span>
 <span data-ttu-id="87245-382">Reprezentuje wartość odczytu lub zapisu w procesie debugowania.</span><span class="sxs-lookup"><span data-stu-id="87245-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="87245-383">[ICorDebugValue2](icordebugvalue2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-383">[ICorDebugValue2](icordebugvalue2-interface.md)\\</span></span>
 <span data-ttu-id="87245-384">Rozszerza `ICorDebugValue` aby zapewnić obsługę `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="87245-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="87245-385">[Icordebugvalue3 — interfejs](icordebugvalue3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)\\</span></span>
 <span data-ttu-id="87245-386">Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic, które są większe niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="87245-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="87245-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="87245-388">Rozszerza `ICorDebugBreakpoint` zapewniać dostęp do określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="87245-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="87245-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-390">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugValue` tablic.</span><span class="sxs-lookup"><span data-stu-id="87245-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="87245-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)\\</span></span>
 <span data-ttu-id="87245-392">Reprezentuje zmiennej lokalnej lub argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="87245-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="87245-393">[ICorDebugVariableHomeEnum, interfejs](icordebugvariablehomeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-394">Dostarcza moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="87245-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="87245-395">[ICorDebugVariableSymbol, interfejs](icordebugvariablesymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)\\</span></span>
 <span data-ttu-id="87245-396">Umożliwia pobranie informacji dotyczących symboli debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="87245-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="87245-397">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-398">[ICorDebugVirtualUnwinder, interfejs](icordebugvirtualunwinder-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)\\</span></span>
 <span data-ttu-id="87245-399">Dostarcza metody pomagające w wykonywania operacji odwijania stosu.</span><span class="sxs-lookup"><span data-stu-id="87245-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="87245-400">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="87245-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="87245-401">[ICorPublish — interfejs](icorpublish-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-401">[ICorPublish Interface](icorpublish-interface.md)\\</span></span>
 <span data-ttu-id="87245-402">Służy jako ogólny interfejs dla procesów publikowania.</span><span class="sxs-lookup"><span data-stu-id="87245-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="87245-403">[Icorpublishappdomain — interfejs](icorpublishappdomain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)\\</span></span>
 <span data-ttu-id="87245-404">Reprezentuje i dostarcza informacje dotyczące domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87245-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="87245-405">[Icorpublishappdomainenum — interfejs](icorpublishappdomainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-406">Udostępnia metody, które przemierzają kolekcję `ICorPublishAppDomain` obiekty, które obecnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="87245-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="87245-407">[Icorpublishenum — interfejs](icorpublishenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-408">Służy jako abstrakcyjna podstawowa do publikowania modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="87245-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="87245-409">[Icorpublishprocess — interfejs](icorpublishprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)\\</span></span>
 <span data-ttu-id="87245-410">Dostarcza metody, które mają dostęp do informacji dotyczących procesu.</span><span class="sxs-lookup"><span data-stu-id="87245-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="87245-411">[Icorpublishprocessenum — interfejs](icorpublishprocessenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)\\</span></span>
 <span data-ttu-id="87245-412">Udostępnia metody, które przemierzają kolekcję `ICorPublishProcess` obiektów.</span><span class="sxs-lookup"><span data-stu-id="87245-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="87245-413">[Interfejs ISOSDacInterface](isosdacinterface-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)\\</span></span>
 <span data-ttu-id="87245-414">Udostępnia metody pomocnicze na dostęp do danych z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="87245-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="87245-415">[Interfejs IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)\\</span></span>
 <span data-ttu-id="87245-416">Udostępnia metody do wykonywania zapytań o definicję metody.</span><span class="sxs-lookup"><span data-stu-id="87245-416">Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="87245-417">[Interfejs IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)\\</span></span>
 <span data-ttu-id="87245-418">Udostępnia metody do wykonywania zapytań o wystąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="87245-418">Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="87245-419">[Interfejs IXCLRDataModule](ixclrdatamodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)\\</span></span>
 <span data-ttu-id="87245-420">Udostępnia metody do wykonywania zapytań o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="87245-420">Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="87245-421">[Interfejs IXCLRDataProcess](ixclrdataprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)\\</span></span>
 <span data-ttu-id="87245-422">Udostępnia metody do wykonywania zapytań informacji dotyczących procesu.</span><span class="sxs-lookup"><span data-stu-id="87245-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="87245-423">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="87245-423">Related Sections</span></span>  
 <span data-ttu-id="87245-424">[Klasy coclass debugowania](debugging-coclasses.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-424">[Debugging Coclasses](debugging-coclasses.md)\\</span></span>
 <span data-ttu-id="87245-425">[Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-425">[Debugging Global Static Functions](debugging-global-static-functions.md)\\</span></span>
 <span data-ttu-id="87245-426">[Debugowanie — wyliczenia](debugging-enumerations.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-426">[Debugging Enumerations](debugging-enumerations.md)\\</span></span>
 <span data-ttu-id="87245-427">[Struktury debugowania](debugging-structures.md)\\</span><span class="sxs-lookup"><span data-stu-id="87245-427">[Debugging Structures](debugging-structures.md)\\</span></span>
