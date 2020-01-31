---
title: Struktury debugowania
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: a18094fb2621478dbdb4bbf672df436234112ed0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793759"
---
# <a name="debugging-structures"></a><span data-ttu-id="b8f04-102">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="b8f04-102">Debugging Structures</span></span>

<span data-ttu-id="b8f04-103">W tej sekcji opisano niezarządzane struktury używane przez interfejs API debugowania.</span><span class="sxs-lookup"><span data-stu-id="b8f04-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b8f04-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b8f04-104">In This Section</span></span>
 <span data-ttu-id="b8f04-105">[Struktura CLRDATA_ADDRESS_RANGE](clrdata-address-range-structure.md) Definiuje zakres adresów.</span><span class="sxs-lookup"><span data-stu-id="b8f04-105">[CLRDATA_ADDRESS_RANGE Structure](clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="b8f04-106">[Struktura CLRDATA_IL_ADDRESS_MAP](clrdata-il-address-map-structure.md) Definiuje mapowanie IL to Address</span><span class="sxs-lookup"><span data-stu-id="b8f04-106">[CLRDATA_IL_ADDRESS_MAP Structure](clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="b8f04-107">[Struktura CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) Definiuje wersję produktu środowiska uruchomieniowego języka wspólnego (CLR) do celów debugowania.</span><span class="sxs-lookup"><span data-stu-id="b8f04-107">[CLR_DEBUGGING_VERSION Structure](clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="b8f04-108">[CodeChunkInfo —, struktura](codechunkinfo-structure.md) Reprezentuje pojedynczy fragment kodu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8f04-108">[CodeChunkInfo Structure](codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="b8f04-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Zawiera informacje o funkcjach, które są obecnie aktywne w ramkach wątku.</span><span class="sxs-lookup"><span data-stu-id="b8f04-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="b8f04-110">[Struktura COR_ARRAY_LAYOUT](cor-array-layout-structure.md) Zawiera informacje o układzie obiektu tablicy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8f04-110">[COR_ARRAY_LAYOUT Structure](cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="b8f04-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Zawiera przesunięcia, które są używane do mapowania kodu języka pośredniego firmy Microsoft (MSIL) na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="b8f04-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="b8f04-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Zawiera informacje o przesunięciu dla zakresu kodu.</span><span class="sxs-lookup"><span data-stu-id="b8f04-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="b8f04-113">[Struktura COR_FIELD](cor-field-structure.md) Zawiera informacje dotyczące pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="b8f04-113">[COR_FIELD Structure](cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="b8f04-114">[Struktura COR_GC_REFERENCE](cor-gc-reference-structure.md) Zawiera informacje o obiekcie, który ma zostać pobrany do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b8f04-114">[COR_GC_REFERENCE Structure](cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="b8f04-115">[Struktura COR_HEAPINFO](cor-heapinfo-structure.md) Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy są wyliczalne</span><span class="sxs-lookup"><span data-stu-id="b8f04-115">[COR_HEAPINFO Structure](cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="b8f04-116">[Struktura COR_HEAPOBJECT](cor-heapobject-structure.md) Zawiera informacje o obiekcie na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="b8f04-116">[COR_HEAPOBJECT Structure](cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="b8f04-117">[COR_IL_MAP](cor-il-map-structure.md) Określa zmiany w względnym przesunięciu funkcji.</span><span class="sxs-lookup"><span data-stu-id="b8f04-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="b8f04-118">[Struktura COR_SEGMENT](cor-segment-structure.md) Zawiera informacje o regionie pamięci w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="b8f04-118">[COR_SEGMENT Structure](cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="b8f04-119">[Struktura COR_TYPEID](cor-typeid-structure.md) Zawiera identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="b8f04-119">[COR_TYPEID Structure](cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="b8f04-120">[Struktura COR_TYPE_LAYOUT](cor-type-layout-structure.md) Zawiera informacje na temat układu obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8f04-120">[COR_TYPE_LAYOUT Structure](cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="b8f04-121">[COR_VERSION](cor-version-structure.md) Przechowuje numer standardowej wersji 4-częściowej środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b8f04-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="b8f04-122">[CorDebugBlockingObject, struktura](cordebugblockingobject-structure.md) Definiuje obiekt, który blokuje wątek i powód, dla którego wątek jest zablokowany.</span><span class="sxs-lookup"><span data-stu-id="b8f04-122">[CorDebugBlockingObject Structure](cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="b8f04-123">[CorDebugEHClause, struktura](cordebugehclause-structure.md) Reprezentuje klauzulę obsługi wyjątków (EH) dla danego fragmentu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="b8f04-123">[CorDebugEHClause Structure](cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="b8f04-124">[CorDebugExceptionObjectStackFrame —, struktura](cordebugexceptionobjectstackframe-structure.md) Reprezentuje informacje o ramce stosu z obiektu Exception.</span><span class="sxs-lookup"><span data-stu-id="b8f04-124">[CorDebugExceptionObjectStackFrame Structure](cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="b8f04-125">[CorDebugGuidToTypeMapping —, struktura](cordebugguidtotypemapping-structure.md) Mapuje identyfikator GUID środowisko wykonawcze systemu Windows na odpowiedni obiekt [ICorDebugType](icordebugtype-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b8f04-125">[CorDebugGuidToTypeMapping Structure](cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="b8f04-126">[DacpGetModuleAddress, struktura](dacpgetmoduleaddress-structure.md) Definiuje kontener dla żądania adresu modułu.</span><span class="sxs-lookup"><span data-stu-id="b8f04-126">[DacpGetModuleAddress Structure](dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="b8f04-127">[DacpMethodDescData, struktura](dacpmethoddescdata-structure.md) Definiuje bufor transportu dla informacji o środowisku uruchomieniowym metody.</span><span class="sxs-lookup"><span data-stu-id="b8f04-127">[DacpMethodDescData Structure](dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="b8f04-128">[DacpModuleData, struktura](dacpmoduledata-structure.md) Definiuje bufor transportu dla informacji o środowisku uruchomieniowym modułu.</span><span class="sxs-lookup"><span data-stu-id="b8f04-128">[DacpModuleData Structure](dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="b8f04-129">[DacpReJitData, struktura](dacprejitdata-structure.md) Definiuje podstawowe informacje o danej metodzie Instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="b8f04-129">[DacpReJitData Structure](dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="b8f04-130">[Struktura StackTrace_SimpleContext](stacktrace-simplecontext-structure.md) Udostępnia prosty kontekst, który może być używany zamiast pełnej struktury `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="b8f04-130">[StackTrace_SimpleContext Structure](stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b8f04-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b8f04-131">Related Sections</span></span>

 [<span data-ttu-id="b8f04-132">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="b8f04-132">Debugging Coclasses</span></span>](debugging-coclasses.md)

 [<span data-ttu-id="b8f04-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b8f04-133">Debugging Interfaces</span></span>](debugging-interfaces.md)

 [<span data-ttu-id="b8f04-134">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="b8f04-134">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

 [<span data-ttu-id="b8f04-135">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b8f04-135">Debugging Enumerations</span></span>](debugging-enumerations.md)

 [<span data-ttu-id="b8f04-136">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b8f04-136">Debugging</span></span>](index.md)
