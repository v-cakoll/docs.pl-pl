---
title: Debugowanie — Interfejsy
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: c4b9cdc2bc90096ab7c3b041bd8aa2742b48c35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179164"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="41614-102">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="41614-102">Debugging Interfaces</span></span>
<span data-ttu-id="41614-103">W tej sekcji opisano niezarządzane interfejsy obsługujące debugowanie programu wykonywanego w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="41614-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41614-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="41614-104">In This Section</span></span>  
 <span data-ttu-id="41614-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="41614-106">Zapewnia metodę pozwalającą wyliczyć obszary pamięci, które są określone przez obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="41614-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="41614-107">[Interfejs ICLRDataEnemoryMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="41614-108">Zawiera metodę wywołania `EnumMemoryRegions` zwrotnego do raportu do debugera, wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="41614-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="41614-109">[Interfejs ICLRDataTarget](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="41614-110">Zapewnia metody interakcji z obiektem docelowym procesu CLR.</span><span class="sxs-lookup"><span data-stu-id="41614-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="41614-111">[Interfejs ICLRDataTarget2](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="41614-112">Podklasa, `ICLRDataTarget` która jest używana przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="41614-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="41614-113">[Interfejs ICLRDataTarget3](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="41614-114">Podklasa [ICLRDataTarget2,](iclrdatatarget2-interface.md) która zapewnia dostęp do informacji o wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="41614-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="41614-115">[Interfejs ICLRDebugging](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-115">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="41614-116">Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.</span><span class="sxs-lookup"><span data-stu-id="41614-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="41614-117">[Interfejs ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="41614-118">Zawiera [Metodę ProvideLibrary,](iclrdebugginglibraryprovider-providelibrary-method.md) która pobiera interfejs wywołania zwrotnego dostawcy biblioteki, który umożliwia zlokalizowanie i załadowanie bibliotek debugowania specyficzne dla środowiska wykonawczego języka wspólnego języka.</span><span class="sxs-lookup"><span data-stu-id="41614-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="41614-119">[Interfejs ICLRMetadataLocator](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="41614-120">Interfejs używany przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="41614-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="41614-121">[Interfejs ICorDebug](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-121">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="41614-122">Dostarcza metody, które umożliwiają programistom debugowanie aplikacji w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="41614-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="41614-123">[Interfejs ICorDebugAppDomain](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="41614-124">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41614-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="41614-125">[Interfejs ICorDebugAppDomain2](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="41614-126">Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami ByRef.</span><span class="sxs-lookup"><span data-stu-id="41614-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="41614-127">Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="41614-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="41614-128">[Interfejs ICorDebugAppDomain3](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="41614-129">Udostępnia metody do pracy z typami środowiska wykonawczego systemu Windows w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41614-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="41614-130">Ten interfejs jest `ICorDebugAppDomain` rozszerzeniem `ICorDebugAppDomain2` i interfejsów.</span><span class="sxs-lookup"><span data-stu-id="41614-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="41614-131">[Interfejs ICorDebugAppDomain4](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="41614-132">Logicznie rozszerza interfejs [ICorDebugAppDomain,](icordebugappdomain-interface.md) aby uzyskać obiekt zarządzany z otoki wywoływanej przez COM.</span><span class="sxs-lookup"><span data-stu-id="41614-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="41614-133">[Interfejs ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="41614-134">Zawiera metodę, która zwraca `ICorDebugAppDomain` określoną liczbę wartości, począwszy od następnej lokalizacji w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="41614-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="41614-135">[Interfejs ICorDebugArrayValue](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="41614-136">Podklasa, `ICorDebugHeapValue` która reprezentuje tablicę jednowymiarową lub wielowymiarową.</span><span class="sxs-lookup"><span data-stu-id="41614-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="41614-137">[Interfejs ICorDebugAssembly](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="41614-138">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="41614-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="41614-139">[Interfejs ICorDebugAssembly2](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="41614-140">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="41614-140">Represents an assembly.</span></span> <span data-ttu-id="41614-141">Ten interfejs jest rozszerzeniem `ICorDebugAssembly` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="41614-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="41614-142">[Interfejs ICorDebugAssembly3](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="41614-143">Logicznie rozszerza interfejs [ICorDebugAssembly,](icordebugassembly-interface.md) aby zapewnić obsługę zestawów kontenerów i ich zestawów zawartych.</span><span class="sxs-lookup"><span data-stu-id="41614-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="41614-144">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-145">[Interfejs ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="41614-146">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugAssembly` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="41614-147">[Interfejs ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="41614-148">Zawiera wyliczenie listy [CorDebugBlockingObject](cordebugblockingobject-structure.md) struktur.</span><span class="sxs-lookup"><span data-stu-id="41614-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="41614-149">[Interfejs ICorDebugBoxValue](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="41614-150">Podklasa, `ICorDebugHeapValue` która reprezentuje obiekt klasy wartości w pudełku.</span><span class="sxs-lookup"><span data-stu-id="41614-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="41614-151">[Interfejs ICorDebugBreakpoint](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="41614-152">Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.</span><span class="sxs-lookup"><span data-stu-id="41614-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="41614-153">[Interfejs ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="41614-154">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugBreakpoint` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="41614-155">[Interfejs ICorDebugChain](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="41614-156">Reprezentuje segment stosu wywołań fizycznych lub logicznych.</span><span class="sxs-lookup"><span data-stu-id="41614-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="41614-157">[Interfejs ICorDebugChainEnum](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="41614-158">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugChain` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="41614-159">[Interfejs ICorDebugClass](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="41614-160">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="41614-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="41614-161">Jeśli typ jest `ICorDebugClass` ogólny, reprezentuje nieustannego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="41614-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="41614-162">[Interfejs ICorDebugClass2](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="41614-163">Reprezentuje klasę rodzajową lub klasę z <xref:System.Type>parametrem metody typu .</span><span class="sxs-lookup"><span data-stu-id="41614-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="41614-164">Ten interfejs `ICorDebugClass`rozszerza .</span><span class="sxs-lookup"><span data-stu-id="41614-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="41614-165">[Interfejs ICorDebugCode](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="41614-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="41614-166">Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="41614-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="41614-167">[Interfejs ICorDebugCode2](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="41614-168">Zawiera metody, które rozszerzają możliwości . `ICorDebugCode`</span><span class="sxs-lookup"><span data-stu-id="41614-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="41614-169">[Interfejs ICorDebugCode3](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="41614-170">Zawiera metodę, która rozszerza [ICorDebugCode](icordebugcode-interface1.md) i [ICorDebugCode2,](icordebugcode2-interface.md) aby zapewnić informacje o wartości zarządzanej zwracanej.</span><span class="sxs-lookup"><span data-stu-id="41614-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="41614-171">[Interfejs ICorDebugCode4](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="41614-172">Udostępnia metodę, która umożliwia debugerowi wyliczyć zmienne lokalne i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="41614-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="41614-173">[Interfejs ICorDebugCodeEnum](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="41614-174">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugCode` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="41614-175">[Interfejs ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="41614-176">Dostarcza metody pobierania obiektów interfejsu w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="41614-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="41614-177">[Interfejs ICorDebugContext](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-177">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="41614-178">Reprezentuje obiekt kontekstu.</span><span class="sxs-lookup"><span data-stu-id="41614-178">Represents a context object.</span></span> <span data-ttu-id="41614-179">Ten Interfejs nie został jeszcze implementowany.</span><span class="sxs-lookup"><span data-stu-id="41614-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="41614-180">[Interfejs ICorDebugController](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-180">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="41614-181">Reprezentuje zakres, a <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, w którym można kontrolować kontekst wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="41614-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="41614-182">[Interfejs ICorDebugDataTarget](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="41614-183">Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="41614-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="41614-184">[Interfejs ICorDebugDataTarget2](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="41614-185">Logicznie rozszerza interfejs [ICorDebugDataTarget.](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="41614-186">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-187">[Interfejs ICorDebugDataTarget3](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="41614-188">Logicznie rozszerza interfejs [ICorDebugDataTarget,](icordebugdatatarget-interface.md) aby zapewnić informacje o załadowanych modułach.</span><span class="sxs-lookup"><span data-stu-id="41614-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="41614-189">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-190">[Interfejs ICorDebugDebugEvent](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="41614-191">Definiuje interfejs podstawowy, z `ICorDebug` którego pochodzą wszystkie zdarzenia debugowania.</span><span class="sxs-lookup"><span data-stu-id="41614-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="41614-192">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-193">[Interfejs ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="41614-194">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="41614-194">Obsolete.</span></span> <span data-ttu-id="41614-195">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="41614-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="41614-196">[Interfejs ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="41614-197">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="41614-197">Obsolete.</span></span> <span data-ttu-id="41614-198">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="41614-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="41614-199">[Interfejs ICorDebugEnum](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="41614-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="41614-200">Służy jako abstrakcyjny interfejs podstawowy do debugowania modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="41614-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="41614-201">[Interfejs ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="41614-202">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="41614-202">Obsolete.</span></span> <span data-ttu-id="41614-203">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="41614-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="41614-204">[Interfejs ICorDebugEval](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="41614-205">Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="41614-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="41614-206">[Interfejs ICorDebugEval2](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="41614-207">`ICorDebugEval` Rozszerza, aby zapewnić obsługę typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="41614-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="41614-208">[Interfejs ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="41614-209">Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) do obsługi zdarzeń wyjątków.</span><span class="sxs-lookup"><span data-stu-id="41614-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="41614-210">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-211">[Interfejs ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="41614-212">Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="41614-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="41614-213">[Interfejs ICorDebugExceptionObjectValue](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="41614-214">Rozszerza interfejs [ICorDebugObjectValue,](icordebugobjectvalue-interface.md) aby zapewnić informacje śledzenia stosu z zarządzanego obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="41614-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="41614-215">[Interfejs ICorDebugFrame](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="41614-216">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="41614-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="41614-217">[Interfejs ICorDebugFrameEnum](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="41614-218">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugFrame` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="41614-219">[Interfejs ICorDebugFunction](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="41614-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="41614-220">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="41614-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="41614-221">[Interfejs ICorDebugFunction2](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="41614-222">Logicznie `ICorDebugFunction` rozszerza, aby zapewnić obsługę debugowania krok po kroku tylko mój kod.</span><span class="sxs-lookup"><span data-stu-id="41614-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="41614-223">[Interfejs ICorDebugFunction3](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="41614-224">Logicznie rozszerza interfejs [ICorDebugFunction,](icordebugfunction-interface1.md) aby zapewnić dostęp do kodu z żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="41614-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="41614-225">[Interfejs ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="41614-226">Rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w ramach funkcji.</span><span class="sxs-lookup"><span data-stu-id="41614-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="41614-227">[Interfejs ICorDebugCReferenceEnum](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="41614-228">Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="41614-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="41614-229">[Interfejs ICorDebugGenericValue](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="41614-230">Podklasa, `ICorDebugValue` która ma zastosowanie do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="41614-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="41614-231">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="41614-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="41614-232">[Interfejs ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="41614-233">Zawiera wyliczenie obiektu, który mapuje identyfikatory `ICorDebugType` GUID i odpowiadające im obiekty.</span><span class="sxs-lookup"><span data-stu-id="41614-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="41614-234">[Interfejs ICorDebugHandleValue](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="41614-235">Podklasa, `ICorDebugReferenceValue` która reprezentuje wartość odwołania, do której debuger utworzył dojście do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="41614-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="41614-236">[Interfejs ICorDebugHeapEnum](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="41614-237">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="41614-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="41614-238">[Interfejs ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="41614-239">Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="41614-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="41614-240">[Interfejs ICorDebugHeapValue](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="41614-241">Podklasa, `ICorDebugValue` która reprezentuje obiekt, który został zebrany przez moduł zbierający elementy bezużyteczne CLR.</span><span class="sxs-lookup"><span data-stu-id="41614-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="41614-242">[Interfejs ICorDebugHeapValue2](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="41614-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="41614-243">`ICorDebugHeapValue` Rozszerzenie, które zapewnia obsługę dojść w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="41614-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="41614-244">[Interfejs ICorDebugHeapValue3](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="41614-245">Udostępnia właściwości blokady monitora obiektów.</span><span class="sxs-lookup"><span data-stu-id="41614-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="41614-246">[Interfejs ICorDebugILCode](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="41614-247">Reprezentuje segment kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="41614-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="41614-248">[Interfejs ICorDebugILCode2](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="41614-249">Logicznie rozszerza interfejs [ICorDebugILCode,](icordebugilcode-interface.md) aby zapewnić metody, które zwracają token dla sygnatury zmiennej lokalnej funkcji i które mapują przesunięcia języka pośredniego (IL) oprzyrządowania profilera do przesunięć oryginalnej metody IL.</span><span class="sxs-lookup"><span data-stu-id="41614-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="41614-250">[Interfejs ICorDebugILFrame](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="41614-251">Reprezentuje ramkę stosu kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="41614-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="41614-252">[Interfejs ICorDebugILFrame2](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="41614-253">Logiczne rozszerzenie `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="41614-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="41614-254">[Interfejs ICorDebugILFrame3](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="41614-255">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="41614-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="41614-256">[Interfejs ICorDebugILFrame4](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="41614-257">Zawiera metody, które umożliwiają dostęp do zmiennych lokalnych i kodu w ramce stosu kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="41614-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="41614-258">Parametr określa, czy debuger ma dostęp do zmiennych i kodu dodanego w instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="41614-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="41614-259">[Interfejs ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="41614-260">Reprezentuje informacje o symbolu debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="41614-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="41614-261">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-262">[Interfejs ICorDebugInternalFrame](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="41614-263">Identyfikuje typy ramek dla debugera.</span><span class="sxs-lookup"><span data-stu-id="41614-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="41614-264">[Interfejs ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="41614-265">Zawiera informacje o ramkach wewnętrznych, w tym adres stosu i położenie w odniesieniu do obiektów [ICorDebugFrame.](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="41614-266">[Interfejs ICorDebugLoadedModule](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="41614-267">Zawiera informacje o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="41614-267">Provides information about a loaded module.</span></span> <span data-ttu-id="41614-268">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-269">[Interfejs ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="41614-270">Dostarcza metody do przetwarzania wywołań zwrotnych debugera.</span><span class="sxs-lookup"><span data-stu-id="41614-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="41614-271">[Interfejs ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="41614-272">Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="41614-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="41614-273">`ICorDebugManagedCallback2`jest logicznym `ICorDebugManagedCallback`rozszerzeniem .</span><span class="sxs-lookup"><span data-stu-id="41614-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="41614-274">[Interfejs ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="41614-275">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="41614-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="41614-276">[Interfejs ICorDebugMDA](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="41614-277">Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="41614-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="41614-278">[Interfejs ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="41614-279">Reprezentuje bufor w pamięci.</span><span class="sxs-lookup"><span data-stu-id="41614-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="41614-280">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-281">[Interfejs ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="41614-282">Zawiera informacje o scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="41614-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="41614-283">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-284">[Interfejs ICorDebugMetaDataLocator](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="41614-285">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="41614-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="41614-286">[Interfejs ICorDebugModule](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="41614-287">Reprezentuje moduł CLR, który jest albo plikiem wykonywalnym lub biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="41614-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="41614-288">[Interfejs ICorDebugModule2](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="41614-289">Służy jako logiczne `ICorDebugModule`rozszerzenie do .</span><span class="sxs-lookup"><span data-stu-id="41614-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="41614-290">[Interfejs ICorDebugModule3](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="41614-291">Tworzy czytnik symbolu dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="41614-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="41614-292">[Interfejs ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="41614-293">`ICorDebugBreakpoint` Rozszerza, aby zapewnić dostęp do określonych modułów.</span><span class="sxs-lookup"><span data-stu-id="41614-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="41614-294">[Interfejs ICorDebugModuleDebugEvent](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="41614-295">Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) do obsługi zdarzeń na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="41614-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="41614-296">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-297">[Interfejs ICorDebugModuleEnum](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="41614-298">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugModule` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="41614-299">[Interfejs ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="41614-300">Rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) do obsługi docelowych danych modyfikowalnych.</span><span class="sxs-lookup"><span data-stu-id="41614-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="41614-301">[Interfejs ICorDebugNativeFrame](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="41614-302">Specjalistyczna implementacja `ICorDebugFrame` używana dla ram natywnych.</span><span class="sxs-lookup"><span data-stu-id="41614-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="41614-303">[Interfejs ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="41614-304">Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.</span><span class="sxs-lookup"><span data-stu-id="41614-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="41614-305">[Interfejs ICorDebugObjectEnum](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="41614-306">Implementuje `ICorDebugEnum` metody i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="41614-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="41614-307">[Interfejs ICorDebugObectValue](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="41614-308">Podklasa, `ICorDebugValue` która reprezentuje wartość, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="41614-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="41614-309">[Interfejs ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="41614-310">Rozszerza `ICorDebugObjectValue` do obsługi dziedziczenia i zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="41614-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="41614-311">[Interfejs ICorDebugProcess](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="41614-312">Reprezentuje proces, który wykonuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="41614-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="41614-313">[Interfejs ICorDebugProcess2](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="41614-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="41614-314">Logiczne rozszerzenie `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="41614-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="41614-315">[Interfejs ICorDebugProcess3](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="41614-316">Steruje niestandardowymi powiadomieniami debugera.</span><span class="sxs-lookup"><span data-stu-id="41614-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="41614-317">[Interfejs ICorDebugProcess4](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="41614-318">Zapewnia obsługę poza kontrolą wykonywania procesu.</span><span class="sxs-lookup"><span data-stu-id="41614-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="41614-319">[Interfejs ICorDebugProcess5](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="41614-320">Rozszerza interfejs [ICorDebugProcess](icordebugprocess-interface.md) do obsługi dostępu do zarządzanego stosu, aby zapewnić informacje o wyrzucaniu elementów bezużytecznych obiektów zarządzanych i określić, czy debuger ładuje obrazy z lokalnej pamięci podręcznej obrazu macierzystego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41614-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="41614-321">[Interfejs ICorDebugProcess6](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="41614-322">Logicznie rozszerza interfejs [ICorDebugProcess,](icordebugprocess-interface.md) aby włączyć funkcje, takie jak dekodowanie zarządzanych zdarzeń debugowania, które są zakodowane w natywnych zdarzeń debugowania wyjątków i dzielenia modułu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="41614-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="41614-323">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-324">[Interfejs ICorDebugProcess7](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="41614-325">Udostępnia metodę, która konfiguruje debugera do obsługi aktualizacji metadanych w pamięci w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="41614-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="41614-326">[Interfejs ICorDebugProcess8](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="41614-327">Logicznie rozszerza interfejs [ICorDebugProcess,](icordebugprocess-interface.md) aby włączyć lub wyłączyć niektóre typy wywołań zwrotnych wyjątków [ICorDebugManagedCallback2.](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="41614-328">[Interfejs ICorDebugProcessEnum](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="41614-329">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugProcess` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="41614-330">[Interfejs ICorDebugReferenceValue](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="41614-331">Podklasa, `ICorDebugValue` która obsługuje typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="41614-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="41614-332">[Interfejs ICorDebugRegisterSet](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="41614-333">Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="41614-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="41614-334">[Interfejs ICorDebugRegisterSet2](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="41614-335">Rozszerza możliwości `ICorDebugRegisterSet` dla platform sprzętowych, które mają więcej niż 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="41614-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="41614-336">[Interfejs ICorDebugRemote](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-336">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="41614-337">Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="41614-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="41614-338">[Interfejs ICorDebugRemoteTarget](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="41614-339">Dostarcza metody, które umożliwiają debugowania aplikacji opartych na dodatku Silverlight w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="41614-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="41614-340">[Interfejs ICorDebugRuntimeUnwindableFrame](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="41614-341">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="41614-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="41614-342">[Interfejs ICorDebugStackWalk](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="41614-343">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="41614-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="41614-344">[Interfejs ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="41614-345">Reprezentuje informacje o symbolu debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="41614-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="41614-346">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-347">[Interfejs ICorDebugStepper](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="41614-348">Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.</span><span class="sxs-lookup"><span data-stu-id="41614-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="41614-349">[Interfejs ICorDebugStepper2](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="41614-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="41614-350">Zapewnia obsługę debugowania Tylko mój kod (JMC).</span><span class="sxs-lookup"><span data-stu-id="41614-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="41614-351">[Interfejs ICorDebugStepperEnum](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="41614-352">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugStepper` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="41614-353">[Interfejs ICorDebugStringValue](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="41614-354">Podklasa, `ICorDebugHeapValue` która ma zastosowanie do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="41614-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="41614-355">[Interfejs ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="41614-356">Zawiera metody, które mogą służyć do pobierania informacji o symbolu debugowania.</span><span class="sxs-lookup"><span data-stu-id="41614-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="41614-357">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-358">[Interfejs ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="41614-359">Logicznie rozszerza interfejs [ICorDebugSymbolProvider,](icordebugsymbolprovider-interface.md) aby pobrać dodatkowe informacje o symbolu debugowania.</span><span class="sxs-lookup"><span data-stu-id="41614-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="41614-360">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-361">[Interfejs ICorDebugThread](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="41614-362">Reprezentuje wątek w procesie.</span><span class="sxs-lookup"><span data-stu-id="41614-362">Represents a thread in a process.</span></span> <span data-ttu-id="41614-363">Okres istnienia `ICorDebugThread` wystąpienia jest taki sam jak okres istnienia wątku, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="41614-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="41614-364">[Interfejs ICorDebugThread2](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="41614-365">Służy jako logiczne `ICorDebugThread`rozszerzenie do .</span><span class="sxs-lookup"><span data-stu-id="41614-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="41614-366">[Interfejs ICorDebugThread3](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="41614-367">Zawiera punkt wejścia do [ICorDebugStackWalk](icordebugstackwalk-interface.md) i odpowiednich interfejsów.</span><span class="sxs-lookup"><span data-stu-id="41614-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="41614-368">[Interfejs ICorDebugThread4](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="41614-369">Dostarcza informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="41614-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="41614-370">[Interfejs ICorDebugThreadEnum](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="41614-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="41614-371">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugThread` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="41614-372">[Interfejs ICorDebugType](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-372">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="41614-373">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="41614-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="41614-374">Jeśli typ jest `ICorDebugType` ogólny, reprezentuje smowany typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="41614-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="41614-375">[Interfejs ICorDebugType2](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="41614-376">Rozszerza interfejs [ICorDebugType,](icordebugtype-interface.md) aby pobrać identyfikator typu typu podstawowego lub typu złożonego (zdefiniowanego przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="41614-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="41614-377">[Interfejs ICorDebugTypeEnum](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="41614-378">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugType` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="41614-379">[Interfejs ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="41614-380">Zapewnia powiadomienie macierzystych zdarzeń, które nie dotyczą bezpośrednio środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="41614-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="41614-381">[Icordebugvalue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="41614-382">Reprezentuje wartość odczytu lub zapisu w procesie debugowania.</span><span class="sxs-lookup"><span data-stu-id="41614-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="41614-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="41614-384">`ICorDebugValue` Rozszerza, aby zapewnić `ICorDebugType`wsparcie dla .</span><span class="sxs-lookup"><span data-stu-id="41614-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="41614-385">[Interfejs ICorDebugValue3](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="41614-386">Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic, które są większe niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="41614-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="41614-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="41614-388">`ICorDebugBreakpoint` Rozszerza, aby zapewnić dostęp do określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="41614-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="41614-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="41614-390">Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugValue` tablice.</span><span class="sxs-lookup"><span data-stu-id="41614-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="41614-391">[Interfejs ICorDebugVariableHome](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="41614-392">Reprezentuje zmienną lokalną lub argument funkcji.</span><span class="sxs-lookup"><span data-stu-id="41614-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="41614-393">[Interfejs ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="41614-394">Zawiera wyliczenia do zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="41614-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="41614-395">[Interfejs ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="41614-396">Pobiera informacje o symbolu debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="41614-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="41614-397">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-398">[Interfejs ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="41614-399">Zawiera metody, które pomogą w odwijaniu stosu.</span><span class="sxs-lookup"><span data-stu-id="41614-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="41614-400">**Dostępne tylko w programie .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="41614-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="41614-401">[Interfejs ICorPublish](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-401">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="41614-402">Służy jako ogólny interfejs dla procesów publikowania.</span><span class="sxs-lookup"><span data-stu-id="41614-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="41614-403">[Interfejs ICorPublishAppDomain](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="41614-404">Reprezentuje i dostarcza informacje dotyczące domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41614-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="41614-405">[Interfejs ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="41614-406">Zawiera metody, które przechodzą `ICorPublishAppDomain` przez kolekcję obiektów, które obecnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="41614-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="41614-407">[Interfejs ICorPublishEnum](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="41614-408">Służy jako abstrakcyjna podstawowa do publikowania modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="41614-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="41614-409">[Interfejs ICorPublishProcess](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="41614-410">Dostarcza metody, które mają dostęp do informacji dotyczących procesu.</span><span class="sxs-lookup"><span data-stu-id="41614-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="41614-411">[Interfejs ICorPublishProcessEnum](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="41614-412">Zawiera metody, które przechodzą `ICorPublishProcess` przez kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="41614-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="41614-413">[Interfejs ISOSDacInterface](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="41614-414">Udostępnia metody pomocnicze dostępu `SOS`do danych z programu .</span><span class="sxs-lookup"><span data-stu-id="41614-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="41614-415">[Interfejs ixclrdataMethodDefinition](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="41614-416">Zawiera metody wykonywania zapytań o definicję metody.</span><span class="sxs-lookup"><span data-stu-id="41614-416">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="41614-417">[Interfejs IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="41614-418">Zawiera metody wykonywania zapytań o wystąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="41614-418">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="41614-419">[Interfejs IXCLRDataModule](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="41614-420">Zawiera metody wykonywania zapytań o załadowany moduł.</span><span class="sxs-lookup"><span data-stu-id="41614-420">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="41614-421">[Interfejs IXCLRDataProcess](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="41614-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="41614-422">Zawiera metody wykonywania zapytań o proces.</span><span class="sxs-lookup"><span data-stu-id="41614-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="41614-423">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="41614-423">Related Sections</span></span>  
 <span data-ttu-id="41614-424">[Coclasses debugowania](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="41614-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="41614-425">[Debugowanie globalnych funkcji statycznych](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="41614-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="41614-426">[Wyliczenia debugowania](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="41614-426">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="41614-427">[Struktury debugowania](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="41614-427">[Debugging Structures](debugging-structures.md)</span></span>\
