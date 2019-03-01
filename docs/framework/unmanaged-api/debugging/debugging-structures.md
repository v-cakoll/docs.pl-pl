---
title: Struktury debugowania
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50db519410b9513725c3dc10637421ba8bb37ec
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965231"
---
# <a name="debugging-structures"></a><span data-ttu-id="72aac-102">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="72aac-102">Debugging Structures</span></span>

<span data-ttu-id="72aac-103">W tej sekcji opisano niezarządzane struktury, których używa interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="72aac-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="72aac-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="72aac-104">In This Section</span></span>
 <span data-ttu-id="72aac-105">[Struktura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) definiuje zakres adresów.</span><span class="sxs-lookup"><span data-stu-id="72aac-105">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="72aac-106">[Struktura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) definiuje języka Pośredniego do mapowania adresu</span><span class="sxs-lookup"><span data-stu-id="72aac-106">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="72aac-107">[Clr_debugging_version — struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Określa wersję produktu środowisko uruchomieniowe języka wspólnego (CLR) na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="72aac-107">[CLR_DEBUGGING_VERSION Structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="72aac-108">[Codechunkinfo — struktura](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) reprezentuje jeden fragment kodu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="72aac-108">[CodeChunkInfo Structure](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="72aac-109">[Cor_active_function —](cor-active-function-structure.md) zawiera informacje na temat funkcji, które są aktualnie aktywne w ramkach w wątku.</span><span class="sxs-lookup"><span data-stu-id="72aac-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="72aac-110">[Cor_array_layout — struktury](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) informacje dotyczące układu tablicy obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="72aac-110">[COR_ARRAY_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="72aac-111">[Cor_debug_il_to_native_map —](cor-debug-il-to-native-map-structure.md) zawiera przesunięcia, które są używane do mapowania języka Microsoft intermediate language (MSIL) kod do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="72aac-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="72aac-112">[Cor_debug_step_range —](cor-debug-step-range-structure.md) zawiera informacje o przesunięciu w zakresie kodu.</span><span class="sxs-lookup"><span data-stu-id="72aac-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="72aac-113">[Cor_field — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) informacje na temat pole w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="72aac-113">[COR_FIELD Structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="72aac-114">[Cor_gc_reference — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) zawiera informacje dotyczące obiektu, który ma być zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="72aac-114">[COR_GC_REFERENCE Structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="72aac-115">[Cor_heapinfo — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym, czy jest wyliczalna.</span><span class="sxs-lookup"><span data-stu-id="72aac-115">[COR_HEAPINFO Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="72aac-116">[Cor_heapobject — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) zawiera informacje dotyczące obiektu na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="72aac-116">[COR_HEAPOBJECT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="72aac-117">[Cor_il_map —](cor-il-map-structure.md) określa zmian w przesunięcie względne funkcji.</span><span class="sxs-lookup"><span data-stu-id="72aac-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="72aac-118">[Cor_segment — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) zawiera informacje o region pamięci w stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="72aac-118">[COR_SEGMENT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="72aac-119">[Cor_typeid — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) zawiera identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="72aac-119">[COR_TYPEID Structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="72aac-120">[Cor_type_layout — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) informacje dotyczące układu obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="72aac-120">[COR_TYPE_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="72aac-121">[Cor_version —](cor-version-structure.md) przechowuje standardowe Czteroczęściowy numer środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="72aac-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="72aac-122">[Cordebugblockingobject — struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) definiuje obiekt, który blokuje wątek i przyczyny, dlaczego wątek jest blokowany.</span><span class="sxs-lookup"><span data-stu-id="72aac-122">[CorDebugBlockingObject Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="72aac-123">[Struktura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) reprezentuje klauzuli obsługi (EH) wyjątek dla danego języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="72aac-123">[CorDebugEHClause Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="72aac-124">[Cordebugexceptionobjectstackframe — struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) reprezentuje stosu ramki informacje z obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="72aac-124">[CorDebugExceptionObjectStackFrame Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="72aac-125">[Cordebugguidtotypemapping — struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] identyfikator GUID służący do odpowiadającymi mu dostawcami [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="72aac-125">[CorDebugGuidToTypeMapping Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="72aac-126">[Struktura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) definiuje kontener dla żądania adres modułu.</span><span class="sxs-lookup"><span data-stu-id="72aac-126">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="72aac-127">[Struktura DacpMethodDescData](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) definiuje bufora transportu dla metody środowiska uruchomieniowego informacje.</span><span class="sxs-lookup"><span data-stu-id="72aac-127">[DacpMethodDescData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="72aac-128">[Struktura DacpModuleData](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) definiuje bufora transportu dla informacje czasu wykonywania modułu.</span><span class="sxs-lookup"><span data-stu-id="72aac-128">[DacpModuleData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="72aac-129">[Struktura DacpReJitData](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) określa podstawowe informacje dotyczące danej metody Instrumentacji profilera.</span><span class="sxs-lookup"><span data-stu-id="72aac-129">[DacpReJitData Structure](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="72aac-130">[Stacktrace_simplecontext — struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) zapewnia proste kontekst, który można użyć zamiast pełnego `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="72aac-130">[StackTrace_SimpleContext Structure](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="72aac-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="72aac-131">Related Sections</span></span>

 [<span data-ttu-id="72aac-132">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="72aac-132">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [<span data-ttu-id="72aac-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="72aac-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [<span data-ttu-id="72aac-134">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="72aac-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [<span data-ttu-id="72aac-135">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="72aac-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [<span data-ttu-id="72aac-136">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="72aac-136">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
