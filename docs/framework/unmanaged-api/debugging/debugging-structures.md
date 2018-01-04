---
title: Struktury debugowania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c20bb8a9841b5ebc7a4ca9b5463fe4c541c0a82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-structures"></a><span data-ttu-id="9d146-102">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="9d146-102">Debugging Structures</span></span>
<span data-ttu-id="9d146-103">W tej sekcji opisano niezarządzane struktury, których używa interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="9d146-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d146-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9d146-104">In This Section</span></span>  
 [<span data-ttu-id="9d146-105">CLR_DEBUGGING_VERSION, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="9d146-106">Określa wersję produktu środowisko uruchomieniowe języka wspólnego (CLR) na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="9d146-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="9d146-107">CodeChunkInfo, struktura1</span><span class="sxs-lookup"><span data-stu-id="9d146-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="9d146-108">Reprezentuje pojedynczy fragmentu kodu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9d146-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="9d146-109">CorDebugBlockingObject, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="9d146-110">Definiuje obiekt, który blokuje wątku i przyczyny, dlaczego wątek jest zablokowany.</span><span class="sxs-lookup"><span data-stu-id="9d146-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="9d146-111">CorDebugEHClause, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="9d146-112">Reprezentuje wyjątek klauzuli (EH) dla danego elementu języku pośrednim (IL).</span><span class="sxs-lookup"><span data-stu-id="9d146-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="9d146-113">CorDebugExceptionObjectStackFrame, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="9d146-114">Reprezentuje stosu ramki informacji z obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9d146-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="9d146-115">CorDebugExceptionObjectStackFrame, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="9d146-116">Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] identyfikator GUID na odpowiednie [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="9d146-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="9d146-117">COR_ACTIVE_FUNCTION —</span><span class="sxs-lookup"><span data-stu-id="9d146-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="9d146-118">Zawiera informacje na temat funkcji, które są aktualnie aktywne w ramkach wątku.</span><span class="sxs-lookup"><span data-stu-id="9d146-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="9d146-119">COR_ARRAY_LAYOUT, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="9d146-120">Zawiera informacje o układzie tablicy obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9d146-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="9d146-121">COR_DEBUG_IL_TO_NATIVE_MAP —</span><span class="sxs-lookup"><span data-stu-id="9d146-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="9d146-122">Zawiera przesunięcia, które są używane do mapowania kodu natywnego kodu języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9d146-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="9d146-123">COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="9d146-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="9d146-124">Zawiera informacje przesunięcia zakresu kodu.</span><span class="sxs-lookup"><span data-stu-id="9d146-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="9d146-125">COR_FIELD, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="9d146-126">Zawiera informacje dotyczące pola w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="9d146-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="9d146-127">COR_GC_REFERENCE, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="9d146-128">Zawiera informacje dotyczące obiektu, który ma być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="9d146-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="9d146-129">COR_HEAPINFO, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="9d146-130">Ogólne informacje dotyczące odzyskiwania pamięci sterty kolekcji, także wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="9d146-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="9d146-131">COR_HEAPOBJECT, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="9d146-132">Zawiera informacje dotyczące obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="9d146-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="9d146-133">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="9d146-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="9d146-134">Określa przesunięcie względną funkcji zmiany.</span><span class="sxs-lookup"><span data-stu-id="9d146-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="9d146-135">COR_SEGMENT, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="9d146-136">Zawiera informacje na temat obszar pamięci sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="9d146-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="9d146-137">COR_TYPEID, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="9d146-138">Zawiera identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="9d146-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="9d146-139">COR_TYPE_LAYOUT, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="9d146-140">Zawiera informacje o układzie obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9d146-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="9d146-141">COR_VERSION —</span><span class="sxs-lookup"><span data-stu-id="9d146-141">COR_VERSION</span></span>  
 <span data-ttu-id="9d146-142">Przechowuje numer wersji czteroczęściową standardowe środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="9d146-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="9d146-143">StackTrace_SimpleContext, struktura</span><span class="sxs-lookup"><span data-stu-id="9d146-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="9d146-144">Udostępnia prosty kontekstu, którego można użyć zamiast pełnej `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="9d146-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9d146-145">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9d146-145">Related Sections</span></span>  
 [<span data-ttu-id="9d146-146">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="9d146-146">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="9d146-147">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9d146-147">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="9d146-148">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="9d146-148">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="9d146-149">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9d146-149">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="9d146-150">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="9d146-150">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
