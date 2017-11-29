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
ms.openlocfilehash: 55097e38161ea5c76f4e46584241344ec5a52cb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="interop-etw-events"></a><span data-ttu-id="d1203-102">Zdarzenia ETW międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="d1203-102">Interop ETW Events</span></span>
<span data-ttu-id="d1203-103"><a name="top"></a>Zdarzenia międzyoperacyjności przechwytywanie informacji na temat generowania szkieletu język pośredni (MSIL) firmy Microsoft i buforowania.</span><span class="sxs-lookup"><span data-stu-id="d1203-103"><a name="top"></a> Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="d1203-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="d1203-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="d1203-105">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="d1203-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="d1203-106">Zdarzenie ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="d1203-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="d1203-107">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="d1203-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="d1203-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="d1203-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="d1203-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="d1203-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="d1203-110">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d1203-110">Keyword for raising the event</span></span>|<span data-ttu-id="d1203-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="d1203-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d1203-112">`InteropKeyword`(0x2000)</span><span class="sxs-lookup"><span data-stu-id="d1203-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="d1203-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d1203-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="d1203-114">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d1203-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d1203-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="d1203-115">Event</span></span>|<span data-ttu-id="d1203-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d1203-116">Event ID</span></span>|<span data-ttu-id="d1203-117">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="d1203-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="d1203-118">88</span><span class="sxs-lookup"><span data-stu-id="d1203-118">88</span></span>|<span data-ttu-id="d1203-119">MSIL stub został wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="d1203-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="d1203-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d1203-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d1203-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="d1203-121">Field name</span></span>|<span data-ttu-id="d1203-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="d1203-122">Data type</span></span>|<span data-ttu-id="d1203-123">Opis</span><span class="sxs-lookup"><span data-stu-id="d1203-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d1203-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="d1203-124">ModuleID</span></span>|<span data-ttu-id="d1203-125">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="d1203-125">win:UInt16</span></span>|<span data-ttu-id="d1203-126">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="d1203-126">The module identifier.</span></span>|  
|<span data-ttu-id="d1203-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="d1203-127">StubMethodID</span></span>|<span data-ttu-id="d1203-128">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="d1203-128">win:UInt64</span></span>|<span data-ttu-id="d1203-129">Identyfikator metody stub.</span><span class="sxs-lookup"><span data-stu-id="d1203-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="d1203-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="d1203-130">StubFlags</span></span>|<span data-ttu-id="d1203-131">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="d1203-131">win:UInt64</span></span>|<span data-ttu-id="d1203-132">Flagi dla elementu zastępczego:</span><span class="sxs-lookup"><span data-stu-id="d1203-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="d1203-133">0x1 — odwrotne interop.</span><span class="sxs-lookup"><span data-stu-id="d1203-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="d1203-134">0x2 — COM interop.</span><span class="sxs-lookup"><span data-stu-id="d1203-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="d1203-135">0x4 - stub generowane przez NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="d1203-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="d1203-136">0x8 - delegata.</span><span class="sxs-lookup"><span data-stu-id="d1203-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="d1203-137">0x10 - arrgument zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d1203-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="d1203-138">0x20 - wywoływany niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="d1203-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="d1203-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="d1203-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="d1203-140">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="d1203-140">win:UInt32</span></span>|<span data-ttu-id="d1203-141">Token dla zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="d1203-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="d1203-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="d1203-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="d1203-143">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d1203-143">win:UnicodeString</span></span>|<span data-ttu-id="d1203-144">Przestrzeń nazw zarządzana metoda międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d1203-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="d1203-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="d1203-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="d1203-146">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d1203-146">win:UnicodeString</span></span>|<span data-ttu-id="d1203-147">Nazwa zarządzanego metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="d1203-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="d1203-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="d1203-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="d1203-149">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d1203-149">win:UnicodeString</span></span>|<span data-ttu-id="d1203-150">Podpis zarządzana metoda międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d1203-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="d1203-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="d1203-151">NativeMethodSignature</span></span>|<span data-ttu-id="d1203-152">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d1203-152">win:UnicodeString</span></span>|<span data-ttu-id="d1203-153">Podpis metody natywnej.</span><span class="sxs-lookup"><span data-stu-id="d1203-153">The native method signature.</span></span>|  
|<span data-ttu-id="d1203-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="d1203-154">StubMethodSignature</span></span>|<span data-ttu-id="d1203-155">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d1203-155">win:UnicodeString</span></span>|<span data-ttu-id="d1203-156">Podpis metody stub.</span><span class="sxs-lookup"><span data-stu-id="d1203-156">The stub method signature.</span></span>|  
|<span data-ttu-id="d1203-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="d1203-157">StubMethodILCode</span></span>|<span data-ttu-id="d1203-158">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d1203-158">win:UnicodeString</span></span>|<span data-ttu-id="d1203-159">Kod metody zastępczej MSIL.</span><span class="sxs-lookup"><span data-stu-id="d1203-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="d1203-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d1203-160">ClrInstanceID</span></span>|<span data-ttu-id="d1203-161">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="d1203-161">win:UInt16</span></span>|<span data-ttu-id="d1203-162">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d1203-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d1203-163">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="d1203-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="d1203-164">Zdarzenie ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="d1203-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="d1203-165">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="d1203-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d1203-166">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d1203-166">Keyword for raising the event</span></span>|<span data-ttu-id="d1203-167">Poziom</span><span class="sxs-lookup"><span data-stu-id="d1203-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d1203-168">`InteropKeyword`(0x2000)</span><span class="sxs-lookup"><span data-stu-id="d1203-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="d1203-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d1203-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="d1203-170">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d1203-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d1203-171">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="d1203-171">Event</span></span>|<span data-ttu-id="d1203-172">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d1203-172">Event ID</span></span>|<span data-ttu-id="d1203-173">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="d1203-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="d1203-174">89</span><span class="sxs-lookup"><span data-stu-id="d1203-174">89</span></span>|<span data-ttu-id="d1203-175">Uzyskał dostęp do pamięci podręcznej MSIL.</span><span class="sxs-lookup"><span data-stu-id="d1203-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="d1203-176">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d1203-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d1203-177">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="d1203-177">Field name</span></span>|<span data-ttu-id="d1203-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="d1203-178">Data type</span></span>|<span data-ttu-id="d1203-179">Opis</span><span class="sxs-lookup"><span data-stu-id="d1203-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d1203-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="d1203-180">ModuleID</span></span>|<span data-ttu-id="d1203-181">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="d1203-181">win:UInt16</span></span>|<span data-ttu-id="d1203-182">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="d1203-182">The module identifier.</span></span>|  
|<span data-ttu-id="d1203-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="d1203-183">StubMethodID</span></span>|<span data-ttu-id="d1203-184">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="d1203-184">win:UInt64</span></span>|<span data-ttu-id="d1203-185">Identyfikator metody stub.</span><span class="sxs-lookup"><span data-stu-id="d1203-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="d1203-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="d1203-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="d1203-187">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="d1203-187">win:UInt32</span></span>|<span data-ttu-id="d1203-188">Token dla zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="d1203-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="d1203-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="d1203-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="d1203-190">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d1203-190">win:UnicodeString</span></span>|<span data-ttu-id="d1203-191">Przestrzeń nazw zarządzana metoda międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d1203-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="d1203-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="d1203-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="d1203-193">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d1203-193">win:UnicodeString</span></span>|<span data-ttu-id="d1203-194">Nazwa zarządzanego metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="d1203-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="d1203-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="d1203-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="d1203-196">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d1203-196">win:UnicodeString</span></span>|<span data-ttu-id="d1203-197">Podpis zarządzana metoda międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d1203-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="d1203-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d1203-198">ClrInstanceID</span></span>|<span data-ttu-id="d1203-199">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="d1203-199">win:UInt16</span></span>|<span data-ttu-id="d1203-200">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d1203-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d1203-201">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="d1203-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="d1203-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1203-202">See Also</span></span>  
 [<span data-ttu-id="d1203-203">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="d1203-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
