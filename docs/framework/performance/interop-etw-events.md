---
title: "Zdarzenia ETW międzyoperacyjności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5670eb910406626096f776d3b4192e2d58d7ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="interop-etw-events"></a><span data-ttu-id="c0fd6-102">Zdarzenia ETW międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="c0fd6-102">Interop ETW Events</span></span>
<a name="top"></a><span data-ttu-id="c0fd6-103">Zdarzenia międzyoperacyjności przechwytywanie informacji na temat generowania szkieletu język pośredni (MSIL) firmy Microsoft i buforowania.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="c0fd6-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="c0fd6-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="c0fd6-105">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="c0fd6-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="c0fd6-106">Zdarzenie ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="c0fd6-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="c0fd6-107">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="c0fd6-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="c0fd6-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="c0fd6-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="c0fd6-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="c0fd6-110">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c0fd6-110">Keyword for raising the event</span></span>|<span data-ttu-id="c0fd6-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="c0fd6-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c0fd6-112">`InteropKeyword`(0x2000)</span><span class="sxs-lookup"><span data-stu-id="c0fd6-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="c0fd6-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c0fd6-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="c0fd6-114">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c0fd6-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="c0fd6-115">Event</span></span>|<span data-ttu-id="c0fd6-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c0fd6-116">Event ID</span></span>|<span data-ttu-id="c0fd6-117">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="c0fd6-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="c0fd6-118">88</span><span class="sxs-lookup"><span data-stu-id="c0fd6-118">88</span></span>|<span data-ttu-id="c0fd6-119">MSIL stub został wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="c0fd6-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c0fd6-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="c0fd6-121">Field name</span></span>|<span data-ttu-id="c0fd6-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c0fd6-122">Data type</span></span>|<span data-ttu-id="c0fd6-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c0fd6-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c0fd6-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="c0fd6-124">ModuleID</span></span>|<span data-ttu-id="c0fd6-125">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="c0fd6-125">win:UInt16</span></span>|<span data-ttu-id="c0fd6-126">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-126">The module identifier.</span></span>|  
|<span data-ttu-id="c0fd6-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="c0fd6-127">StubMethodID</span></span>|<span data-ttu-id="c0fd6-128">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c0fd6-128">win:UInt64</span></span>|<span data-ttu-id="c0fd6-129">Identyfikator metody stub.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="c0fd6-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="c0fd6-130">StubFlags</span></span>|<span data-ttu-id="c0fd6-131">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c0fd6-131">win:UInt64</span></span>|<span data-ttu-id="c0fd6-132">Flagi dla elementu zastępczego:</span><span class="sxs-lookup"><span data-stu-id="c0fd6-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="c0fd6-133">0x1 — odwrotne interop.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="c0fd6-134">0x2 — COM interop.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="c0fd6-135">0x4 - stub generowane przez NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="c0fd6-136">0x8 - delegata.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="c0fd6-137">0x10 - arrgument zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="c0fd6-138">0x20 - wywoływany niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="c0fd6-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="c0fd6-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="c0fd6-140">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-140">win:UInt32</span></span>|<span data-ttu-id="c0fd6-141">Token dla zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="c0fd6-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="c0fd6-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="c0fd6-143">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0fd6-143">win:UnicodeString</span></span>|<span data-ttu-id="c0fd6-144">Przestrzeń nazw zarządzana metoda międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="c0fd6-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="c0fd6-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="c0fd6-146">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0fd6-146">win:UnicodeString</span></span>|<span data-ttu-id="c0fd6-147">Nazwa zarządzanego metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="c0fd6-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="c0fd6-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="c0fd6-149">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0fd6-149">win:UnicodeString</span></span>|<span data-ttu-id="c0fd6-150">Podpis zarządzana metoda międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="c0fd6-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="c0fd6-151">NativeMethodSignature</span></span>|<span data-ttu-id="c0fd6-152">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0fd6-152">win:UnicodeString</span></span>|<span data-ttu-id="c0fd6-153">Podpis metody natywnej.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-153">The native method signature.</span></span>|  
|<span data-ttu-id="c0fd6-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="c0fd6-154">StubMethodSignature</span></span>|<span data-ttu-id="c0fd6-155">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0fd6-155">win:UnicodeString</span></span>|<span data-ttu-id="c0fd6-156">Podpis metody stub.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-156">The stub method signature.</span></span>|  
|<span data-ttu-id="c0fd6-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="c0fd6-157">StubMethodILCode</span></span>|<span data-ttu-id="c0fd6-158">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0fd6-158">win:UnicodeString</span></span>|<span data-ttu-id="c0fd6-159">Kod metody zastępczej MSIL.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="c0fd6-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c0fd6-160">ClrInstanceID</span></span>|<span data-ttu-id="c0fd6-161">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="c0fd6-161">win:UInt16</span></span>|<span data-ttu-id="c0fd6-162">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c0fd6-163">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="c0fd6-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="c0fd6-164">Zdarzenie ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="c0fd6-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="c0fd6-165">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c0fd6-166">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c0fd6-166">Keyword for raising the event</span></span>|<span data-ttu-id="c0fd6-167">Poziom</span><span class="sxs-lookup"><span data-stu-id="c0fd6-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c0fd6-168">`InteropKeyword`(0x2000)</span><span class="sxs-lookup"><span data-stu-id="c0fd6-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="c0fd6-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c0fd6-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="c0fd6-170">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c0fd6-171">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="c0fd6-171">Event</span></span>|<span data-ttu-id="c0fd6-172">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c0fd6-172">Event ID</span></span>|<span data-ttu-id="c0fd6-173">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="c0fd6-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="c0fd6-174">89</span><span class="sxs-lookup"><span data-stu-id="c0fd6-174">89</span></span>|<span data-ttu-id="c0fd6-175">Uzyskał dostęp do pamięci podręcznej MSIL.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="c0fd6-176">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c0fd6-177">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="c0fd6-177">Field name</span></span>|<span data-ttu-id="c0fd6-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c0fd6-178">Data type</span></span>|<span data-ttu-id="c0fd6-179">Opis</span><span class="sxs-lookup"><span data-stu-id="c0fd6-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c0fd6-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="c0fd6-180">ModuleID</span></span>|<span data-ttu-id="c0fd6-181">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="c0fd6-181">win:UInt16</span></span>|<span data-ttu-id="c0fd6-182">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-182">The module identifier.</span></span>|  
|<span data-ttu-id="c0fd6-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="c0fd6-183">StubMethodID</span></span>|<span data-ttu-id="c0fd6-184">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c0fd6-184">win:UInt64</span></span>|<span data-ttu-id="c0fd6-185">Identyfikator metody stub.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="c0fd6-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="c0fd6-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="c0fd6-187">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-187">win:UInt32</span></span>|<span data-ttu-id="c0fd6-188">Token dla zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="c0fd6-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="c0fd6-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="c0fd6-190">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0fd6-190">win:UnicodeString</span></span>|<span data-ttu-id="c0fd6-191">Przestrzeń nazw zarządzana metoda międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="c0fd6-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="c0fd6-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="c0fd6-193">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0fd6-193">win:UnicodeString</span></span>|<span data-ttu-id="c0fd6-194">Nazwa zarządzanego metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="c0fd6-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="c0fd6-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="c0fd6-196">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0fd6-196">win:UnicodeString</span></span>|<span data-ttu-id="c0fd6-197">Podpis zarządzana metoda międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="c0fd6-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c0fd6-198">ClrInstanceID</span></span>|<span data-ttu-id="c0fd6-199">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="c0fd6-199">win:UInt16</span></span>|<span data-ttu-id="c0fd6-200">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c0fd6-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c0fd6-201">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="c0fd6-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="c0fd6-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0fd6-202">See Also</span></span>  
 [<span data-ttu-id="c0fd6-203">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="c0fd6-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
