---
title: Zdarzenia ETW międzyoperacyjności
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09b2848619256a255cc27f0268d46e5e6db8cbe4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083611"
---
# <a name="interop-etw-events"></a><span data-ttu-id="a32f2-102">Zdarzenia ETW międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="a32f2-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="a32f2-103">Zdarzenia międzyoperacyjności przechwytywania informacji na temat generowania szkieletu intermediate language (MSIL) firmy Microsoft i buforowania.</span><span class="sxs-lookup"><span data-stu-id="a32f2-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="a32f2-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="a32f2-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="a32f2-105">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="a32f2-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="a32f2-106">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="a32f2-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="a32f2-107">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="a32f2-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="a32f2-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="a32f2-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="a32f2-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="a32f2-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="a32f2-110">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a32f2-110">Keyword for raising the event</span></span>|<span data-ttu-id="a32f2-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="a32f2-111">Level</span></span>|  
|-----------------------------------|-----------|  
|`InteropKeyword` <span data-ttu-id="a32f2-112">(0x2000)</span><span class="sxs-lookup"><span data-stu-id="a32f2-112">(0x2000)</span></span>|<span data-ttu-id="a32f2-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a32f2-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="a32f2-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="a32f2-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a32f2-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a32f2-115">Event</span></span>|<span data-ttu-id="a32f2-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a32f2-116">Event ID</span></span>|<span data-ttu-id="a32f2-117">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="a32f2-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="a32f2-118">88</span><span class="sxs-lookup"><span data-stu-id="a32f2-118">88</span></span>|<span data-ttu-id="a32f2-119">Klasy zastępczej MSIL został wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="a32f2-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="a32f2-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a32f2-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a32f2-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="a32f2-121">Field name</span></span>|<span data-ttu-id="a32f2-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="a32f2-122">Data type</span></span>|<span data-ttu-id="a32f2-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a32f2-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a32f2-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="a32f2-124">ModuleID</span></span>|<span data-ttu-id="a32f2-125">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="a32f2-125">win:UInt16</span></span>|<span data-ttu-id="a32f2-126">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="a32f2-126">The module identifier.</span></span>|  
|<span data-ttu-id="a32f2-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="a32f2-127">StubMethodID</span></span>|<span data-ttu-id="a32f2-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a32f2-128">win:UInt64</span></span>|<span data-ttu-id="a32f2-129">Identyfikator metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="a32f2-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="a32f2-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="a32f2-130">StubFlags</span></span>|<span data-ttu-id="a32f2-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a32f2-131">win:UInt64</span></span>|<span data-ttu-id="a32f2-132">Flagi dla wycinka:</span><span class="sxs-lookup"><span data-stu-id="a32f2-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="a32f2-133">0x1 — interop wstecznego.</span><span class="sxs-lookup"><span data-stu-id="a32f2-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="a32f2-134">0x2 — Usługa międzyoperacyjna modelu COM.</span><span class="sxs-lookup"><span data-stu-id="a32f2-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="a32f2-135">0x4 - wycinku wygenerowanym przez NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="a32f2-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="a32f2-136">0x8 - delegata.</span><span class="sxs-lookup"><span data-stu-id="a32f2-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="a32f2-137">0x10 - arrgument zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a32f2-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="a32f2-138">0x20 — niezarządzane / / wywoływany.</span><span class="sxs-lookup"><span data-stu-id="a32f2-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="a32f2-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="a32f2-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="a32f2-140">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="a32f2-140">win:UInt32</span></span>|<span data-ttu-id="a32f2-141">Token dla zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a32f2-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="a32f2-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="a32f2-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="a32f2-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a32f2-143">win:UnicodeString</span></span>|<span data-ttu-id="a32f2-144">Przestrzeń nazw zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="a32f2-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="a32f2-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="a32f2-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="a32f2-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a32f2-146">win:UnicodeString</span></span>|<span data-ttu-id="a32f2-147">Nazwa zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a32f2-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="a32f2-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a32f2-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="a32f2-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a32f2-149">win:UnicodeString</span></span>|<span data-ttu-id="a32f2-150">Podpis zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a32f2-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="a32f2-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a32f2-151">NativeMethodSignature</span></span>|<span data-ttu-id="a32f2-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a32f2-152">win:UnicodeString</span></span>|<span data-ttu-id="a32f2-153">Podpis metody natywnej.</span><span class="sxs-lookup"><span data-stu-id="a32f2-153">The native method signature.</span></span>|  
|<span data-ttu-id="a32f2-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a32f2-154">StubMethodSignature</span></span>|<span data-ttu-id="a32f2-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a32f2-155">win:UnicodeString</span></span>|<span data-ttu-id="a32f2-156">Podpis metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="a32f2-156">The stub method signature.</span></span>|  
|<span data-ttu-id="a32f2-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="a32f2-157">StubMethodILCode</span></span>|<span data-ttu-id="a32f2-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a32f2-158">win:UnicodeString</span></span>|<span data-ttu-id="a32f2-159">Kod MSIL metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="a32f2-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="a32f2-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a32f2-160">ClrInstanceID</span></span>|<span data-ttu-id="a32f2-161">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="a32f2-161">win:UInt16</span></span>|<span data-ttu-id="a32f2-162">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a32f2-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a32f2-163">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="a32f2-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="a32f2-164">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="a32f2-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="a32f2-165">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="a32f2-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a32f2-166">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a32f2-166">Keyword for raising the event</span></span>|<span data-ttu-id="a32f2-167">Poziom</span><span class="sxs-lookup"><span data-stu-id="a32f2-167">Level</span></span>|  
|-----------------------------------|-----------|  
|`InteropKeyword` <span data-ttu-id="a32f2-168">(0x2000)</span><span class="sxs-lookup"><span data-stu-id="a32f2-168">(0x2000)</span></span>|<span data-ttu-id="a32f2-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a32f2-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="a32f2-170">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="a32f2-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a32f2-171">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a32f2-171">Event</span></span>|<span data-ttu-id="a32f2-172">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a32f2-172">Event ID</span></span>|<span data-ttu-id="a32f2-173">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="a32f2-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="a32f2-174">89</span><span class="sxs-lookup"><span data-stu-id="a32f2-174">89</span></span>|<span data-ttu-id="a32f2-175">Uzyskał dostęp do pamięci podręcznej MSIL.</span><span class="sxs-lookup"><span data-stu-id="a32f2-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="a32f2-176">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a32f2-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a32f2-177">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="a32f2-177">Field name</span></span>|<span data-ttu-id="a32f2-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="a32f2-178">Data type</span></span>|<span data-ttu-id="a32f2-179">Opis</span><span class="sxs-lookup"><span data-stu-id="a32f2-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a32f2-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="a32f2-180">ModuleID</span></span>|<span data-ttu-id="a32f2-181">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="a32f2-181">win:UInt16</span></span>|<span data-ttu-id="a32f2-182">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="a32f2-182">The module identifier.</span></span>|  
|<span data-ttu-id="a32f2-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="a32f2-183">StubMethodID</span></span>|<span data-ttu-id="a32f2-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a32f2-184">win:UInt64</span></span>|<span data-ttu-id="a32f2-185">Identyfikator metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="a32f2-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="a32f2-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="a32f2-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="a32f2-187">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="a32f2-187">win:UInt32</span></span>|<span data-ttu-id="a32f2-188">Token dla zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a32f2-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="a32f2-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="a32f2-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="a32f2-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a32f2-190">win:UnicodeString</span></span>|<span data-ttu-id="a32f2-191">Przestrzeń nazw zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="a32f2-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="a32f2-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="a32f2-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="a32f2-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a32f2-193">win:UnicodeString</span></span>|<span data-ttu-id="a32f2-194">Nazwa zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a32f2-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="a32f2-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a32f2-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="a32f2-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a32f2-196">win:UnicodeString</span></span>|<span data-ttu-id="a32f2-197">Podpis zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a32f2-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="a32f2-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a32f2-198">ClrInstanceID</span></span>|<span data-ttu-id="a32f2-199">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="a32f2-199">win:UInt16</span></span>|<span data-ttu-id="a32f2-200">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a32f2-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a32f2-201">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="a32f2-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="a32f2-202">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a32f2-202">See also</span></span>

- [<span data-ttu-id="a32f2-203">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="a32f2-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
