---
title: "Debugowanie — Interfejsy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e625818238a1fd18ef3885d2699e0f532efa40e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-interfaces"></a><span data-ttu-id="461c4-102">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="461c4-102">Debugging Interfaces</span></span>
<span data-ttu-id="461c4-103">W tej sekcji opisano niezarządzane interfejsy obsługujące debugowanie programu wykonywanego w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="461c4-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="461c4-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="461c4-104">In This Section</span></span>  
 [<span data-ttu-id="461c4-105">ICLRDataEnumMemoryRegions, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-105">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 <span data-ttu-id="461c4-106">Zapewnia metodę pozwalającą wyliczyć obszary pamięci, które są określone przez obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="461c4-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 [<span data-ttu-id="461c4-107">ICLRDataEnumMemoryRegionsCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-107">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 <span data-ttu-id="461c4-108">Zapewnia metodę wywołania zwrotnego `EnumMemoryRegions` zgłoszenia do debugera, wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="461c4-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 [<span data-ttu-id="461c4-109">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-109">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 <span data-ttu-id="461c4-110">Zapewnia metody interakcji z obiektem docelowym procesu CLR.</span><span class="sxs-lookup"><span data-stu-id="461c4-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 [<span data-ttu-id="461c4-111">ICLRDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-111">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 <span data-ttu-id="461c4-112">Podklasa `ICLRDataTarget` używany przez warstwę usługi dostępu do danych do manipulowania regiony pamięci wirtualnej w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="461c4-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 [<span data-ttu-id="461c4-113">ICLRDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-113">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 <span data-ttu-id="461c4-114">Podklasa [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , który zapewnia dostęp do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="461c4-114">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 [<span data-ttu-id="461c4-115">ICLRDebugging, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-115">ICLRDebugging Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 <span data-ttu-id="461c4-116">Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.</span><span class="sxs-lookup"><span data-stu-id="461c4-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 [<span data-ttu-id="461c4-117">ICLRDebuggingLibraryProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-117">ICLRDebuggingLibraryProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 <span data-ttu-id="461c4-118">Obejmuje [ProvideLibrary — metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metodę, która pobiera dostawcę biblioteki interfejsu wywołania zwrotnego, który umożliwia języka wspólnego bibliotek debugowania określonej wersji środowiska uruchomieniowego należy odnaleźć i załadować na żądanie.</span><span class="sxs-lookup"><span data-stu-id="461c4-118">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 [<span data-ttu-id="461c4-119">ICLRMetadataLocator, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-119">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 <span data-ttu-id="461c4-120">Interfejs używany przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="461c4-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 [<span data-ttu-id="461c4-121">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 <span data-ttu-id="461c4-122">Dostarcza metody, które umożliwiają programistom debugowanie aplikacji w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="461c4-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="461c4-123">ICorDebugAppDomain, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-123">ICorDebugAppDomain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 <span data-ttu-id="461c4-124">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="461c4-124">Provides methods for debugging application domains.</span></span>  
  
 [<span data-ttu-id="461c4-125">ICorDebugAppDomain2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-125">ICorDebugAppDomain2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 <span data-ttu-id="461c4-126">Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami ByRef.</span><span class="sxs-lookup"><span data-stu-id="461c4-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="461c4-127">Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="461c4-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 [<span data-ttu-id="461c4-128">ICorDebugAppDomain3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-128">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 <span data-ttu-id="461c4-129">Udostępnia metody do pracy z [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="461c4-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="461c4-130">Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` i `ICorDebugAppDomain2` interfejsów.</span><span class="sxs-lookup"><span data-stu-id="461c4-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 [<span data-ttu-id="461c4-131">ICorDebugAppDomain4, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-131">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 <span data-ttu-id="461c4-132">Rozszerza logicznie [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interfejs do pobierania obiektu zarządzanych z wywoływana otoka COM.</span><span class="sxs-lookup"><span data-stu-id="461c4-132">Logically extends the [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 [<span data-ttu-id="461c4-133">ICorDebugAppDomainEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-133">ICorDebugAppDomainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 <span data-ttu-id="461c4-134">Udostępnia metodę, która zwraca określoną liczbę `ICorDebugAppDomain` wartości, zaczynając od następnej lokalizacji w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="461c4-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 [<span data-ttu-id="461c4-135">ICorDebugArrayValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-135">ICorDebugArrayValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 <span data-ttu-id="461c4-136">Podklasa `ICorDebugHeapValue` reprezentujący tablicy jednowymiarowej lub wielowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="461c4-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 [<span data-ttu-id="461c4-137">ICorDebugAssembly, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-137">ICorDebugAssembly Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 <span data-ttu-id="461c4-138">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="461c4-138">Represents an assembly.</span></span>  
  
 [<span data-ttu-id="461c4-139">ICorDebugAssembly2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-139">ICorDebugAssembly2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 <span data-ttu-id="461c4-140">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="461c4-140">Represents an assembly.</span></span> <span data-ttu-id="461c4-141">Ten interfejs jest rozszerzeniem `ICorDebugAssembly` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="461c4-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 [<span data-ttu-id="461c4-142">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-142">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 <span data-ttu-id="461c4-143">Rozszerza logicznie [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interfejsu, aby zapewnić obsługę dla zestawów kontenera i ich zawartych w niej zestawów.</span><span class="sxs-lookup"><span data-stu-id="461c4-143">Logically extends the [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="461c4-144">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-144">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-145">ICorDebugAssemblyEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-145">ICorDebugAssemblyEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 <span data-ttu-id="461c4-146">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugAssembly` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-147">ICorDebugBlockingObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-147">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 <span data-ttu-id="461c4-148">Udostępnia moduł wyliczający listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="461c4-148">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
 [<span data-ttu-id="461c4-149">ICorDebugBoxValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-149">ICorDebugBoxValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 <span data-ttu-id="461c4-150">Podklasa `ICorDebugHeapValue` reprezentujący obiekt klasy wartości spakowanej.</span><span class="sxs-lookup"><span data-stu-id="461c4-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 [<span data-ttu-id="461c4-151">ICorDebugBreakpoint, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-151">ICorDebugBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 <span data-ttu-id="461c4-152">Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.</span><span class="sxs-lookup"><span data-stu-id="461c4-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 [<span data-ttu-id="461c4-153">ICorDebugBreakpointEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-153">ICorDebugBreakpointEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 <span data-ttu-id="461c4-154">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugBreakpoint` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-155">ICorDebugChain, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-155">ICorDebugChain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 <span data-ttu-id="461c4-156">Reprezentuje segment stosu wywołań fizycznych lub logicznych.</span><span class="sxs-lookup"><span data-stu-id="461c4-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 [<span data-ttu-id="461c4-157">ICorDebugChainEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-157">ICorDebugChainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 <span data-ttu-id="461c4-158">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugChain` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-159">ICorDebugClass, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-159">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 <span data-ttu-id="461c4-160">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="461c4-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="461c4-161">Jeśli typ jest rodzajowy, `ICorDebugClass` reprezentuje bez wystąpień typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="461c4-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 [<span data-ttu-id="461c4-162">ICorDebugClass2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-162">ICorDebugClass2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 <span data-ttu-id="461c4-163">Reprezentuje klasy ogólnej lub klasie z parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="461c4-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="461c4-164">Ten interfejs stanowi rozszerzenie `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="461c4-164">This interface extends `ICorDebugClass`.</span></span>  
  
 [<span data-ttu-id="461c4-165">ICorDebugCode, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-165">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 <span data-ttu-id="461c4-166">Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="461c4-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 [<span data-ttu-id="461c4-167">ICorDebugCode2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-167">ICorDebugCode2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 <span data-ttu-id="461c4-168">Udostępnia metody, które rozszerzają możliwości `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="461c4-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 [<span data-ttu-id="461c4-169">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-169">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 <span data-ttu-id="461c4-170">Udostępnia metodę, która rozszerza [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) i [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) aby podać informacje o zarządzanych wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="461c4-170">Provides a method that extends [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) and [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 [<span data-ttu-id="461c4-171">ICorDebugCode4, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-171">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 <span data-ttu-id="461c4-172">Udostępnia metodę umożliwiającą debugera wyliczyć zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="461c4-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="461c4-173">ICorDebugCodeEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-173">ICorDebugCodeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 <span data-ttu-id="461c4-174">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugCode` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-175">ICorDebugComObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-175">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 <span data-ttu-id="461c4-176">Dostarcza metody pobierania obiektów interfejsu w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="461c4-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 [<span data-ttu-id="461c4-177">ICorDebugContext, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-177">ICorDebugContext Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 <span data-ttu-id="461c4-178">Reprezentuje obiekt kontekstu.</span><span class="sxs-lookup"><span data-stu-id="461c4-178">Represents a context object.</span></span> <span data-ttu-id="461c4-179">Ten Interfejs nie został jeszcze implementowany.</span><span class="sxs-lookup"><span data-stu-id="461c4-179">This interface has not been implemented yet.</span></span>  
  
 [<span data-ttu-id="461c4-180">ICorDebugController, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-180">ICorDebugController Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 <span data-ttu-id="461c4-181">Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, których wykonanie kodu mogą być kontrolowane kontekstu.</span><span class="sxs-lookup"><span data-stu-id="461c4-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 [<span data-ttu-id="461c4-182">ICorDebugDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-182">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 <span data-ttu-id="461c4-183">Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="461c4-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 [<span data-ttu-id="461c4-184">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-184">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 <span data-ttu-id="461c4-185">Rozszerza logicznie [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="461c4-185">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="461c4-186">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-186">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-187">ICorDebugDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-187">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 <span data-ttu-id="461c4-188">Rozszerza logicznie [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów.</span><span class="sxs-lookup"><span data-stu-id="461c4-188">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="461c4-189">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-189">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-190">ICorDebugDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-190">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 <span data-ttu-id="461c4-191">Definiuje interfejs podstawowy, z którym wszystkie `ICorDebug` pochodzi zdarzeń debugowania.</span><span class="sxs-lookup"><span data-stu-id="461c4-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="461c4-192">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-192">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-193">ICorDebugEditAndContinueErrorInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-193">ICorDebugEditAndContinueErrorInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 <span data-ttu-id="461c4-194">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="461c4-194">Obsolete.</span></span> <span data-ttu-id="461c4-195">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="461c4-195">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="461c4-196">ICorDebugEditAndContinueSnapshot, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-196">ICorDebugEditAndContinueSnapshot Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 <span data-ttu-id="461c4-197">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="461c4-197">Obsolete.</span></span> <span data-ttu-id="461c4-198">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="461c4-198">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="461c4-199">ICorDebugEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-199">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 <span data-ttu-id="461c4-200">Służy jako abstrakcyjny interfejs podstawowy do debugowania modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="461c4-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 [<span data-ttu-id="461c4-201">ICorDebugErrorInfoEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-201">ICorDebugErrorInfoEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 <span data-ttu-id="461c4-202">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="461c4-202">Obsolete.</span></span> <span data-ttu-id="461c4-203">Nie używaj tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="461c4-203">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="461c4-204">ICorDebugEval, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-204">ICorDebugEval Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 <span data-ttu-id="461c4-205">Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="461c4-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 [<span data-ttu-id="461c4-206">ICorDebugEval2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-206">ICorDebugEval2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 <span data-ttu-id="461c4-207">Rozszerza `ICorDebugEval` zapewnienie wsparcia dla typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="461c4-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 [<span data-ttu-id="461c4-208">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-208">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 <span data-ttu-id="461c4-209">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejs do obsługi zdarzeń wyjątków.</span><span class="sxs-lookup"><span data-stu-id="461c4-209">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="461c4-210">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-210">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-211">ICorDebugExceptionObjectCallStackEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-211">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 <span data-ttu-id="461c4-212">Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="461c4-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 [<span data-ttu-id="461c4-213">ICorDebugExceptionObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-213">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 <span data-ttu-id="461c4-214">Rozszerza [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interfejsu, aby podać informacje śledzenia stosu z obiektem zarządzanym wyjątku.</span><span class="sxs-lookup"><span data-stu-id="461c4-214">Extends the [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 [<span data-ttu-id="461c4-215">ICorDebugFrame, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-215">ICorDebugFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 <span data-ttu-id="461c4-216">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="461c4-216">Represents a frame on the current stack.</span></span>  
  
 [<span data-ttu-id="461c4-217">ICorDebugFrameEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-217">ICorDebugFrameEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 <span data-ttu-id="461c4-218">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugFrame` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-219">ICorDebugFunction, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-219">ICorDebugFunction Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 <span data-ttu-id="461c4-220">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="461c4-220">Represents a managed function or method.</span></span>  
  
 [<span data-ttu-id="461c4-221">ICorDebugFunction2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-221">ICorDebugFunction2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 <span data-ttu-id="461c4-222">Rozszerza logicznie `ICorDebugFunction` zapewnia obsługę tylko mój kod krokowym debugowania.</span><span class="sxs-lookup"><span data-stu-id="461c4-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 [<span data-ttu-id="461c4-223">ICorDebugFunction3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-223">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 <span data-ttu-id="461c4-224">Rozszerza logicznie [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interfejsu w celu zapewnienia dostępu do kodu z żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="461c4-224">Logically extends the [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 [<span data-ttu-id="461c4-225">ICorDebugFunctionBreakpoint, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-225">ICorDebugFunctionBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 <span data-ttu-id="461c4-226">Rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="461c4-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 [<span data-ttu-id="461c4-227">ICorDebugGCReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-227">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 <span data-ttu-id="461c4-228">Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="461c4-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 [<span data-ttu-id="461c4-229">ICorDebugGenericValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-229">ICorDebugGenericValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 <span data-ttu-id="461c4-230">Podklasa `ICorDebugValue` dotyczy wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="461c4-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="461c4-231">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="461c4-231">This interface provides Get and Set methods for the value.</span></span>  
  
 [<span data-ttu-id="461c4-232">ICorDebugGuidToTypeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-232">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 <span data-ttu-id="461c4-233">Udostępnia moduł wyliczający dla obiekt, który mapuje identyfikatorów GUID i odpowiednie `ICorDebugType` obiektów.</span><span class="sxs-lookup"><span data-stu-id="461c4-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 [<span data-ttu-id="461c4-234">ICorDebugHandleValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-234">ICorDebugHandleValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 <span data-ttu-id="461c4-235">Podklasa `ICorDebugReferenceValue` reprezentujący wartość odwołania, do których debuger został utworzony obsługę wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="461c4-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 [<span data-ttu-id="461c4-236">ICorDebugHeapEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-236">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 <span data-ttu-id="461c4-237">Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.</span><span class="sxs-lookup"><span data-stu-id="461c4-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 [<span data-ttu-id="461c4-238">ICorDebugHeapSegmentEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-238">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 <span data-ttu-id="461c4-239">Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="461c4-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 [<span data-ttu-id="461c4-240">ICorDebugHeapValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-240">ICorDebugHeapValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 <span data-ttu-id="461c4-241">Podklasa `ICorDebugValue` reprezentujący obiekt, które zostały zebrane przez moduł garbage collector środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="461c4-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 [<span data-ttu-id="461c4-242">ICorDebugHeapValue2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-242">ICorDebugHeapValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 <span data-ttu-id="461c4-243">Rozszerzenie `ICorDebugHeapValue` który zapewnia obsługę środowiska uruchomieniowego uchwytów.</span><span class="sxs-lookup"><span data-stu-id="461c4-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 [<span data-ttu-id="461c4-244">ICorDebugHeapValue3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-244">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 <span data-ttu-id="461c4-245">Udostępnia właściwości blokady monitora obiektów.</span><span class="sxs-lookup"><span data-stu-id="461c4-245">Exposes the monitor lock properties of objects.</span></span>  
  
 [<span data-ttu-id="461c4-246">ICorDebugILCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-246">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 <span data-ttu-id="461c4-247">Reprezentuje segment kodu w języku pośrednim (IL).</span><span class="sxs-lookup"><span data-stu-id="461c4-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 [<span data-ttu-id="461c4-248">ICorDebugILCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-248">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 <span data-ttu-id="461c4-249">Rozszerza logicznie [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interfejsu podania metod tokenem podpisu lokalnego zmiennej funkcji, które zwracają, oraz że mapowanie profilera instrumentowanych język pośredni (IL) przesuwa się do oryginalnej metody IL przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="461c4-249">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 [<span data-ttu-id="461c4-250">ICorDebugILFrame, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-250">ICorDebugILFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 <span data-ttu-id="461c4-251">Reprezentuje ramkę stosu kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="461c4-251">Represents a stack frame of MSIL code.</span></span>  
  
 [<span data-ttu-id="461c4-252">ICorDebugILFrame2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-252">ICorDebugILFrame2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 <span data-ttu-id="461c4-253">Rozszerzenie logicznej `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="461c4-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 [<span data-ttu-id="461c4-254">ICorDebugILFrame3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-254">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 <span data-ttu-id="461c4-255">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="461c4-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 [<span data-ttu-id="461c4-256">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-256">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 <span data-ttu-id="461c4-257">Udostępnia metody, które umożliwiają dostęp do zmiennych lokalnych i kod w ramce stosu kodu w języku pośrednim (IL).</span><span class="sxs-lookup"><span data-stu-id="461c4-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="461c4-258">Parametr określa, czy debuger ma dostęp do zmiennych i kodzie dodanym w ReJIT Instrumentacji profilera.</span><span class="sxs-lookup"><span data-stu-id="461c4-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="461c4-259">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-259">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 <span data-ttu-id="461c4-260">Reprezentuje informacje symbolu debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="461c4-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="461c4-261">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-261">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-262">ICorDebugInternalFrame, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-262">ICorDebugInternalFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 <span data-ttu-id="461c4-263">Identyfikuje typy ramek dla debugera.</span><span class="sxs-lookup"><span data-stu-id="461c4-263">Identifies frame types for the debugger.</span></span>  
  
 [<span data-ttu-id="461c4-264">ICorDebugInternalFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-264">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 <span data-ttu-id="461c4-265">Informacje na temat wewnętrznej ramki, w tym adresu stosu i pozycji w odniesieniu do [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="461c4-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objects.</span></span>  
  
 [<span data-ttu-id="461c4-266">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-266">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 <span data-ttu-id="461c4-267">Udostępnia informacje na temat załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="461c4-267">Provides information about a loaded module.</span></span> <span data-ttu-id="461c4-268">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-268">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-269">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-269">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 <span data-ttu-id="461c4-270">Dostarcza metody do przetwarzania wywołań zwrotnych debugera.</span><span class="sxs-lookup"><span data-stu-id="461c4-270">Provides methods to process debugger callbacks.</span></span>  
  
 [<span data-ttu-id="461c4-271">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-271">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 <span data-ttu-id="461c4-272">Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="461c4-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="461c4-273">`ICorDebugManagedCallback2`jest logiczną rozszerzenie `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="461c4-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 [<span data-ttu-id="461c4-274">ICorDebugManagedCallback3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-274">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 <span data-ttu-id="461c4-275">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="461c4-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 [<span data-ttu-id="461c4-276">ICorDebugMDA, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-276">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 <span data-ttu-id="461c4-277">Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="461c4-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 [<span data-ttu-id="461c4-278">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-278">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 <span data-ttu-id="461c4-279">Reprezentuje buforów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="461c4-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="461c4-280">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-280">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-281">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-281">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 <span data-ttu-id="461c4-282">Zawiera informacje o zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="461c4-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="461c4-283">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-283">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-284">ICorDebugMetaDataLocator, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-284">ICorDebugMetaDataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 <span data-ttu-id="461c4-285">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="461c4-285">Provides metadata information to the debugger.</span></span>  
  
 [<span data-ttu-id="461c4-286">ICorDebugModule, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-286">ICorDebugModule Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 <span data-ttu-id="461c4-287">Reprezentuje moduł CLR, który jest albo plikiem wykonywalnym lub biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="461c4-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 [<span data-ttu-id="461c4-288">ICorDebugModule2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-288">ICorDebugModule2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 <span data-ttu-id="461c4-289">Służy jako logiczne rozszerzenia `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="461c4-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 [<span data-ttu-id="461c4-290">ICorDebugModule3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-290">ICorDebugModule3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 <span data-ttu-id="461c4-291">Tworzy czytnik symbolu dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="461c4-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 [<span data-ttu-id="461c4-292">ICorDebugModuleBreakpoint, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-292">ICorDebugModuleBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 <span data-ttu-id="461c4-293">Rozszerza `ICorDebugBreakpoint` umożliwia dostęp do określonych modułów.</span><span class="sxs-lookup"><span data-stu-id="461c4-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 [<span data-ttu-id="461c4-294">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-294">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 <span data-ttu-id="461c4-295">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejs do obsługi zdarzenia na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="461c4-295">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="461c4-296">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-296">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-297">ICorDebugModuleEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-297">ICorDebugModuleEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 <span data-ttu-id="461c4-298">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugModule` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-299">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-299">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 <span data-ttu-id="461c4-300">Rozszerza [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejs do obsługi danych modyfikowalne elementy docelowe.</span><span class="sxs-lookup"><span data-stu-id="461c4-300">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 [<span data-ttu-id="461c4-301">ICorDebugNativeFrame, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-301">ICorDebugNativeFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 <span data-ttu-id="461c4-302">Specjalne implementacja `ICorDebugFrame` używany dla ramek natywnych.</span><span class="sxs-lookup"><span data-stu-id="461c4-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 [<span data-ttu-id="461c4-303">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-303">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 <span data-ttu-id="461c4-304">Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.</span><span class="sxs-lookup"><span data-stu-id="461c4-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 [<span data-ttu-id="461c4-305">ICorDebugObjectEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-305">ICorDebugObjectEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 <span data-ttu-id="461c4-306">Implementuje `ICorDebugEnum` metod i wylicza tablice obiektów przez względną wirtualnych adresów (RVAs).</span><span class="sxs-lookup"><span data-stu-id="461c4-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 [<span data-ttu-id="461c4-307">ICorDebugObjectValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-307">ICorDebugObjectValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 <span data-ttu-id="461c4-308">Podklasa `ICorDebugValue` reprezentujący wartość, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="461c4-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 [<span data-ttu-id="461c4-309">ICorDebugObjectValue2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-309">ICorDebugObjectValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 <span data-ttu-id="461c4-310">Rozszerza `ICorDebugObjectValue` do obsługi dziedziczenia i zastąpień.</span><span class="sxs-lookup"><span data-stu-id="461c4-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 [<span data-ttu-id="461c4-311">ICorDebugProcess, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-311">ICorDebugProcess Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 <span data-ttu-id="461c4-312">Reprezentuje proces, który wykonuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="461c4-312">Represents a process that is executing managed code.</span></span>  
  
 [<span data-ttu-id="461c4-313">ICorDebugProcess2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-313">ICorDebugProcess2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 <span data-ttu-id="461c4-314">Rozszerzenie logicznej `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="461c4-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 [<span data-ttu-id="461c4-315">ICorDebugProcess3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-315">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 <span data-ttu-id="461c4-316">Steruje niestandardowymi powiadomieniami debugera.</span><span class="sxs-lookup"><span data-stu-id="461c4-316">Controls custom debugger notifications.</span></span>  
  
 [<span data-ttu-id="461c4-317">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-317">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 <span data-ttu-id="461c4-318">Rozszerza [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interfejs do obsługi dostępu do sterty zarządzanej, aby podać informacje o wyrzucanie elementów bezużytecznych zarządzanych obiektów i ustalenie, czy debuger ładuje obrazów z aplikacji do lokalnego pamięć podręczna obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="461c4-318">Extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 [<span data-ttu-id="461c4-319">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-319">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 <span data-ttu-id="461c4-320">Rozszerza logicznie [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interfejsu, aby włączyć funkcje, takie jak dekodowania zdarzenia debugowania zarządzanego, które są zakodowane w zdarzenia debugowania natywnego wyjątków i dzielenia wirtualnych modułu.</span><span class="sxs-lookup"><span data-stu-id="461c4-320">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="461c4-321">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-321">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-322">ICorDebugProcess7, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-322">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 <span data-ttu-id="461c4-323">Udostępnia metodę, która konfiguruje debugera do obsługi aktualizacji metadanych w pamięci w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="461c4-323">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 [<span data-ttu-id="461c4-324">ICorDebugProcess8, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-324">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 <span data-ttu-id="461c4-325">Rozszerza logicznie [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interfejsu, aby włączyć lub wyłączyć niektórych typów [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) wyjątek wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="461c4-325">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 [<span data-ttu-id="461c4-326">ICorDebugProcessEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-326">ICorDebugProcessEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 <span data-ttu-id="461c4-327">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugProcess` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-327">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-328">ICorDebugReferenceValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-328">ICorDebugReferenceValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 <span data-ttu-id="461c4-329">Podklasa `ICorDebugValue` obsługuje typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="461c4-329">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 [<span data-ttu-id="461c4-330">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-330">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 <span data-ttu-id="461c4-331">Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="461c4-331">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 [<span data-ttu-id="461c4-332">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-332">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 <span data-ttu-id="461c4-333">Rozszerza możliwości `ICorDebugRegisterSet` dla platform sprzętowych, które mają ponad 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="461c4-333">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 [<span data-ttu-id="461c4-334">ICorDebugRemote, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-334">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 <span data-ttu-id="461c4-335">Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="461c4-335">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 [<span data-ttu-id="461c4-336">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-336">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 <span data-ttu-id="461c4-337">Dostarcza metody, które umożliwiają debugowania aplikacji opartych na dodatku Silverlight w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="461c4-337">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="461c4-338">ICorDebugRuntimeUnwindableFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-338">ICorDebugRuntimeUnwindableFrame Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 <span data-ttu-id="461c4-339">Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.</span><span class="sxs-lookup"><span data-stu-id="461c4-339">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 [<span data-ttu-id="461c4-340">ICorDebugStackWalk, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-340">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 <span data-ttu-id="461c4-341">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="461c4-341">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 [<span data-ttu-id="461c4-342">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-342">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 <span data-ttu-id="461c4-343">Reprezentuje informacje symbolu debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="461c4-343">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="461c4-344">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-344">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-345">ICorDebugStepper, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-345">ICorDebugStepper Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 <span data-ttu-id="461c4-346">Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.</span><span class="sxs-lookup"><span data-stu-id="461c4-346">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 [<span data-ttu-id="461c4-347">ICorDebugStepper2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-347">ICorDebugStepper2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 <span data-ttu-id="461c4-348">Zapewnia obsługę debugowania Tylko mój kod (JMC).</span><span class="sxs-lookup"><span data-stu-id="461c4-348">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 [<span data-ttu-id="461c4-349">ICorDebugStepperEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-349">ICorDebugStepperEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 <span data-ttu-id="461c4-350">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugStepper` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-350">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-351">ICorDebugStringValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-351">ICorDebugStringValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 <span data-ttu-id="461c4-352">Podklasa `ICorDebugHeapValue` dotyczący wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="461c4-352">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 [<span data-ttu-id="461c4-353">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-353">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 <span data-ttu-id="461c4-354">Udostępnia metody, które mogą służyć do pobierania informacji o symbolach debugowania.</span><span class="sxs-lookup"><span data-stu-id="461c4-354">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="461c4-355">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-355">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-356">ICorDebugSymbolProvider2, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-356">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 <span data-ttu-id="461c4-357">Rozszerza logicznie [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interfejsu można pobrać informacji o symbolach dodatkowe debugowania.</span><span class="sxs-lookup"><span data-stu-id="461c4-357">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="461c4-358">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-358">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-359">ICorDebugThread, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-359">ICorDebugThread Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 <span data-ttu-id="461c4-360">Reprezentuje wątek w procesie.</span><span class="sxs-lookup"><span data-stu-id="461c4-360">Represents a thread in a process.</span></span> <span data-ttu-id="461c4-361">Okres istnienia `ICorDebugThread` wystąpienie jest taki sam jak okres istnienia reprezentuje wątku.</span><span class="sxs-lookup"><span data-stu-id="461c4-361">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 [<span data-ttu-id="461c4-362">ICorDebugThread2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-362">ICorDebugThread2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 <span data-ttu-id="461c4-363">Służy jako logiczne rozszerzenia `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="461c4-363">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 [<span data-ttu-id="461c4-364">ICorDebugThread3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-364">ICorDebugThread3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 <span data-ttu-id="461c4-365">Zapewnia punkt wejścia do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) i odpowiednie interfejsy.</span><span class="sxs-lookup"><span data-stu-id="461c4-365">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 [<span data-ttu-id="461c4-366">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-366">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 <span data-ttu-id="461c4-367">Dostarcza informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="461c4-367">Provides thread blocking information.</span></span>  
  
 [<span data-ttu-id="461c4-368">ICorDebugThreadEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-368">ICorDebugThreadEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 <span data-ttu-id="461c4-369">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugThread` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-369">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-370">ICorDebugType, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-370">ICorDebugType Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 <span data-ttu-id="461c4-371">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="461c4-371">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="461c4-372">Jeśli typ jest rodzajowy, `ICorDebugType` reprezentuje wystąpień typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="461c4-372">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 [<span data-ttu-id="461c4-373">ICorDebugType2, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-373">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 <span data-ttu-id="461c4-374">Rozszerza [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interfejsu można pobrać identyfikatora typu podstawowego typu lub typu złożonego (zdefiniowane przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="461c4-374">Extends the [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 [<span data-ttu-id="461c4-375">ICorDebugTypeEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="461c4-375">ICorDebugTypeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 <span data-ttu-id="461c4-376">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugType` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-376">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-377">ICorDebugUnmanagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-377">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 <span data-ttu-id="461c4-378">Zapewnia powiadomienie macierzystych zdarzeń, które nie dotyczą bezpośrednio środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="461c4-378">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="461c4-379">"ICorDebugValue"</span><span class="sxs-lookup"><span data-stu-id="461c4-379">"ICorDebugValue"</span></span>  
 <span data-ttu-id="461c4-380">Reprezentuje wartość odczytu lub zapisu w procesie debugowania.</span><span class="sxs-lookup"><span data-stu-id="461c4-380">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="461c4-381">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="461c4-381">"ICorDebugValue2"</span></span>  
 <span data-ttu-id="461c4-382">Rozszerza `ICorDebugValue` aby zapewnić obsługę `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="461c4-382">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 [<span data-ttu-id="461c4-383">ICorDebugValue3, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-383">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 <span data-ttu-id="461c4-384">Rozszerza interfejsów "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę dla tablic, które są większe niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="461c4-384">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="461c4-385">"ICorDebugValueBreakpoint"</span><span class="sxs-lookup"><span data-stu-id="461c4-385">"ICorDebugValueBreakpoint"</span></span>  
 <span data-ttu-id="461c4-386">Rozszerza `ICorDebugBreakpoint` do zapewniania dostępu do określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="461c4-386">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="461c4-387">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="461c4-387">"ICorDebugValueEnum"</span></span>  
 <span data-ttu-id="461c4-388">Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugValue` tablic.</span><span class="sxs-lookup"><span data-stu-id="461c4-388">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 [<span data-ttu-id="461c4-389">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-389">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 <span data-ttu-id="461c4-390">Reprezentuje lokalnej zmiennej lub argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="461c4-390">Represents a local variable or argument of a function.</span></span>  
  
 [<span data-ttu-id="461c4-391">ICorDebugVariableHomeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-391">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 <span data-ttu-id="461c4-392">Udostępnia moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="461c4-392">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="461c4-393">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-393">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 <span data-ttu-id="461c4-394">Pobiera informacje o symbolu debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="461c4-394">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="461c4-395">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-395">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-396">ICorDebugVirtualUnwinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-396">ICorDebugVirtualUnwinder Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 <span data-ttu-id="461c4-397">Udostępnia metody, aby pomóc w odwijanie stosu.</span><span class="sxs-lookup"><span data-stu-id="461c4-397">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="461c4-398">**Dostępne na tylko platforma .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="461c4-398">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="461c4-399">ICorPublish, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-399">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 <span data-ttu-id="461c4-400">Służy jako ogólny interfejs dla procesów publikowania.</span><span class="sxs-lookup"><span data-stu-id="461c4-400">Serves as the general interface for the publishing processes.</span></span>  
  
 [<span data-ttu-id="461c4-401">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-401">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 <span data-ttu-id="461c4-402">Reprezentuje i dostarcza informacje dotyczące domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="461c4-402">Represents and provides information about an application domain.</span></span>  
  
 [<span data-ttu-id="461c4-403">ICorPublishAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-403">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 <span data-ttu-id="461c4-404">Udostępnia metody przechodzących przez kolekcję `ICorPublishAppDomain` obiekty znajdujące się obecnie w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="461c4-404">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 [<span data-ttu-id="461c4-405">ICorPublishEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-405">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 <span data-ttu-id="461c4-406">Służy jako abstrakcyjna podstawowa do publikowania modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="461c4-406">Serves as the abstract base for publishing enumerators.</span></span>  
  
 [<span data-ttu-id="461c4-407">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-407">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 <span data-ttu-id="461c4-408">Dostarcza metody, które mają dostęp do informacji dotyczących procesu.</span><span class="sxs-lookup"><span data-stu-id="461c4-408">Provides methods that access information about a process.</span></span>  
  
 [<span data-ttu-id="461c4-409">ICorPublishProcessEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="461c4-409">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 <span data-ttu-id="461c4-410">Udostępnia metody przechodzących przez kolekcję `ICorPublishProcess` obiektów.</span><span class="sxs-lookup"><span data-stu-id="461c4-410">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="461c4-411">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="461c4-411">Related Sections</span></span>  
 [<span data-ttu-id="461c4-412">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="461c4-412">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="461c4-413">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="461c4-413">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="461c4-414">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="461c4-414">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="461c4-415">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="461c4-415">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
