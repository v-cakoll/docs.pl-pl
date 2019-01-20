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
ms.openlocfilehash: 23aa619d666f2e0b9eb67ab4cf8d4f92761865d3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415328"
---
# <a name="debugging-structures"></a><span data-ttu-id="d5669-102">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="d5669-102">Debugging Structures</span></span>
<span data-ttu-id="d5669-103">W tej sekcji opisano niezarządzane struktury, których używa interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="d5669-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5669-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d5669-104">In This Section</span></span>  
 [<span data-ttu-id="d5669-105">CLR_DEBUGGING_VERSION, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="d5669-106">Określa wersję produktu środowisko uruchomieniowe języka wspólnego (CLR) na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="d5669-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="d5669-107">CodeChunkInfo, struktura1</span><span class="sxs-lookup"><span data-stu-id="d5669-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="d5669-108">Reprezentuje jeden fragment kodu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d5669-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="d5669-109">CorDebugBlockingObject, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="d5669-110">Definiuje obiekt, który blokuje wątek i przyczyny, dlaczego wątek jest blokowany.</span><span class="sxs-lookup"><span data-stu-id="d5669-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="d5669-111">CorDebugEHClause, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="d5669-112">Reprezentuje wyjątek obsługi klauzuli (EH) dla danego języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="d5669-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="d5669-113">CorDebugExceptionObjectStackFrame, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="d5669-114">Reprezentuje stosu ramki informacje z obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d5669-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="d5669-115">CorDebugExceptionObjectStackFrame, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="d5669-116">Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] identyfikator GUID służący do odpowiadającymi mu dostawcami [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="d5669-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="d5669-117">COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="d5669-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="d5669-118">Zawiera informacje na temat funkcji, które są aktualnie aktywne w ramkach w wątku.</span><span class="sxs-lookup"><span data-stu-id="d5669-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="d5669-119">COR_ARRAY_LAYOUT, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="d5669-120">Informacje dotyczące układu obiektu tablicowego w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d5669-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="d5669-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="d5669-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="d5669-122">Zawiera przesunięcia, które są używane do mapowania kod intermediate language (MSIL) firmy Microsoft do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="d5669-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="d5669-123">COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="d5669-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="d5669-124">Zawiera informacje przesunięcia w zakresie kodu.</span><span class="sxs-lookup"><span data-stu-id="d5669-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="d5669-125">COR_FIELD, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="d5669-126">Zawiera informacje dotyczące pól w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="d5669-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="d5669-127">COR_GC_REFERENCE, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="d5669-128">Zawiera informacje dotyczące obiektu, który ma być zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d5669-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="d5669-129">COR_HEAPINFO, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="d5669-130">Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym, czy jest wyliczalna.</span><span class="sxs-lookup"><span data-stu-id="d5669-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="d5669-131">COR_HEAPOBJECT, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="d5669-132">Zawiera informacje dotyczące obiektu na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d5669-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="d5669-133">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="d5669-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="d5669-134">Określa przesunięcie względne funkcji zmiany.</span><span class="sxs-lookup"><span data-stu-id="d5669-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="d5669-135">COR_SEGMENT, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="d5669-136">Zawiera informacje o region pamięci w stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d5669-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="d5669-137">COR_TYPEID, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="d5669-138">Zawiera identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="d5669-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="d5669-139">COR_TYPE_LAYOUT, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="d5669-140">Informacje dotyczące układu obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d5669-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="d5669-141">COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="d5669-141">COR_VERSION</span></span>  
 <span data-ttu-id="d5669-142">Przechowuje standardowe Czteroczęściowy numer środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="d5669-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="d5669-143">StackTrace_SimpleContext, struktura</span><span class="sxs-lookup"><span data-stu-id="d5669-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="d5669-144">Udostępnia prosty kontekst, który można użyć zamiast pełnego `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="d5669-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

 <span data-ttu-id="d5669-145">[Struktura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) definiuje zakres adresów.</span><span class="sxs-lookup"><span data-stu-id="d5669-145">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>
 
 <span data-ttu-id="d5669-146">[Struktura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) definiuje języka Pośredniego do mapowania adresu</span><span class="sxs-lookup"><span data-stu-id="d5669-146">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>
 
 <span data-ttu-id="d5669-147">[Struktura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) definiuje kontener dla żądania adres modułu.</span><span class="sxs-lookup"><span data-stu-id="d5669-147">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

  
## <a name="related-sections"></a><span data-ttu-id="d5669-148">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d5669-148">Related Sections</span></span>  
 [<span data-ttu-id="d5669-149">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="d5669-149">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="d5669-150">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d5669-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="d5669-151">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="d5669-151">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="d5669-152">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d5669-152">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="d5669-153">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d5669-153">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
