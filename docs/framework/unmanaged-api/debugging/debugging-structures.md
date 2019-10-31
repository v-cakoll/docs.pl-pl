---
title: Struktury debugowania
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: 05a321d5025f03d6a0378b462178bf06c0291f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123033"
---
# <a name="debugging-structures"></a><span data-ttu-id="c8138-102">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="c8138-102">Debugging Structures</span></span>

<span data-ttu-id="c8138-103">W tej sekcji opisano niezarządzane struktury używane przez interfejs API debugowania.</span><span class="sxs-lookup"><span data-stu-id="c8138-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c8138-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c8138-104">In This Section</span></span>
 <span data-ttu-id="c8138-105">[CLRDATA_ADDRESS_RANGE, struktura](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Definiuje zakres adresów.</span><span class="sxs-lookup"><span data-stu-id="c8138-105">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="c8138-106">[CLRDATA_IL_ADDRESS_MAP, struktura](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Definiuje mapowanie IL to Address</span><span class="sxs-lookup"><span data-stu-id="c8138-106">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="c8138-107">[CLR_DEBUGGING_VERSION, struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Definiuje wersję produktu środowiska uruchomieniowego języka wspólnego (CLR) do celów debugowania.</span><span class="sxs-lookup"><span data-stu-id="c8138-107">[CLR_DEBUGGING_VERSION Structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="c8138-108">[CodeChunkInfo —, struktura](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Reprezentuje pojedynczy fragment kodu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c8138-108">[CodeChunkInfo Structure](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="c8138-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Zawiera informacje o funkcjach, które są obecnie aktywne w ramkach wątku.</span><span class="sxs-lookup"><span data-stu-id="c8138-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="c8138-110">[COR_ARRAY_LAYOUT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Zawiera informacje o układzie obiektu tablicy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c8138-110">[COR_ARRAY_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="c8138-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Zawiera przesunięcia, które są używane do mapowania kodu języka pośredniego firmy Microsoft (MSIL) na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="c8138-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="c8138-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Zawiera informacje o przesunięciu dla zakresu kodu.</span><span class="sxs-lookup"><span data-stu-id="c8138-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="c8138-113">[COR_FIELD, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Zawiera informacje dotyczące pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="c8138-113">[COR_FIELD Structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="c8138-114">[COR_GC_REFERENCE, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Zawiera informacje o obiekcie, który ma zostać pobrany do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c8138-114">[COR_GC_REFERENCE Structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="c8138-115">[COR_HEAPINFO, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy są wyliczalne</span><span class="sxs-lookup"><span data-stu-id="c8138-115">[COR_HEAPINFO Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="c8138-116">[COR_HEAPOBJECT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Zawiera informacje o obiekcie na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="c8138-116">[COR_HEAPOBJECT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="c8138-117">[COR_IL_MAP](cor-il-map-structure.md) Określa zmiany w względnym przesunięciu funkcji.</span><span class="sxs-lookup"><span data-stu-id="c8138-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="c8138-118">[COR_SEGMENT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Zawiera informacje o regionie pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="c8138-118">[COR_SEGMENT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="c8138-119">[COR_TYPEID, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Zawiera identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="c8138-119">[COR_TYPEID Structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="c8138-120">[COR_TYPE_LAYOUT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Zawiera informacje na temat układu obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c8138-120">[COR_TYPE_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="c8138-121">[COR_VERSION](cor-version-structure.md) Przechowuje numer standardowej wersji 4-częściowej środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="c8138-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="c8138-122">[CorDebugBlockingObject, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Definiuje obiekt, który blokuje wątek i powód, dla którego wątek jest zablokowany.</span><span class="sxs-lookup"><span data-stu-id="c8138-122">[CorDebugBlockingObject Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="c8138-123">[CorDebugEHClause, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Reprezentuje klauzulę obsługi wyjątków (EH) dla danego fragmentu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="c8138-123">[CorDebugEHClause Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="c8138-124">[CorDebugExceptionObjectStackFrame —, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Reprezentuje informacje o ramce stosu z obiektu Exception.</span><span class="sxs-lookup"><span data-stu-id="c8138-124">[CorDebugExceptionObjectStackFrame Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="c8138-125">[CorDebugGuidToTypeMapping —, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Mapuje identyfikator GUID środowisko wykonawcze systemu Windows na odpowiedni obiekt [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c8138-125">[CorDebugGuidToTypeMapping Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="c8138-126">[DacpGetModuleAddress, struktura](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Definiuje kontener dla żądania adresu modułu.</span><span class="sxs-lookup"><span data-stu-id="c8138-126">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="c8138-127">[DacpMethodDescData, struktura](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Definiuje bufor transportu dla informacji o środowisku uruchomieniowym metody.</span><span class="sxs-lookup"><span data-stu-id="c8138-127">[DacpMethodDescData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="c8138-128">[DacpModuleData, struktura](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Definiuje bufor transportu dla informacji o środowisku uruchomieniowym modułu.</span><span class="sxs-lookup"><span data-stu-id="c8138-128">[DacpModuleData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="c8138-129">[DacpReJitData, struktura](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Definiuje podstawowe informacje o danej metodzie Instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="c8138-129">[DacpReJitData Structure](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="c8138-130">[StackTrace_SimpleContext, struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Udostępnia prosty kontekst, który może być używany zamiast pełnej struktury `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="c8138-130">[StackTrace_SimpleContext Structure](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c8138-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c8138-131">Related Sections</span></span>

 [<span data-ttu-id="c8138-132">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="c8138-132">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [<span data-ttu-id="c8138-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c8138-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [<span data-ttu-id="c8138-134">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="c8138-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [<span data-ttu-id="c8138-135">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c8138-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [<span data-ttu-id="c8138-136">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c8138-136">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
