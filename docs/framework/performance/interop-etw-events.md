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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083611"
---
# <a name="interop-etw-events"></a><span data-ttu-id="371ad-102">Zdarzenia ETW międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="371ad-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="371ad-103">Zdarzenia międzyoperacyjności przechwytywania informacji na temat generowania szkieletu intermediate language (MSIL) firmy Microsoft i buforowania.</span><span class="sxs-lookup"><span data-stu-id="371ad-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="371ad-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="371ad-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="371ad-105">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="371ad-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="371ad-106">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="371ad-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="371ad-107">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="371ad-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="371ad-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="371ad-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="371ad-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="371ad-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="371ad-110">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="371ad-110">Keyword for raising the event</span></span>|<span data-ttu-id="371ad-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="371ad-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="371ad-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="371ad-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="371ad-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="371ad-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="371ad-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="371ad-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="371ad-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="371ad-115">Event</span></span>|<span data-ttu-id="371ad-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="371ad-116">Event ID</span></span>|<span data-ttu-id="371ad-117">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="371ad-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="371ad-118">88</span><span class="sxs-lookup"><span data-stu-id="371ad-118">88</span></span>|<span data-ttu-id="371ad-119">Klasy zastępczej MSIL został wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="371ad-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="371ad-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="371ad-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="371ad-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="371ad-121">Field name</span></span>|<span data-ttu-id="371ad-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="371ad-122">Data type</span></span>|<span data-ttu-id="371ad-123">Opis</span><span class="sxs-lookup"><span data-stu-id="371ad-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="371ad-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="371ad-124">ModuleID</span></span>|<span data-ttu-id="371ad-125">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="371ad-125">win:UInt16</span></span>|<span data-ttu-id="371ad-126">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="371ad-126">The module identifier.</span></span>|  
|<span data-ttu-id="371ad-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="371ad-127">StubMethodID</span></span>|<span data-ttu-id="371ad-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="371ad-128">win:UInt64</span></span>|<span data-ttu-id="371ad-129">Identyfikator metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="371ad-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="371ad-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="371ad-130">StubFlags</span></span>|<span data-ttu-id="371ad-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="371ad-131">win:UInt64</span></span>|<span data-ttu-id="371ad-132">Flagi dla wycinka:</span><span class="sxs-lookup"><span data-stu-id="371ad-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="371ad-133">0x1 — interop wstecznego.</span><span class="sxs-lookup"><span data-stu-id="371ad-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="371ad-134">0x2 — Usługa międzyoperacyjna modelu COM.</span><span class="sxs-lookup"><span data-stu-id="371ad-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="371ad-135">0x4 - wycinku wygenerowanym przez NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="371ad-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="371ad-136">0x8 - delegata.</span><span class="sxs-lookup"><span data-stu-id="371ad-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="371ad-137">0x10 - arrgument zmiennej.</span><span class="sxs-lookup"><span data-stu-id="371ad-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="371ad-138">0x20 — niezarządzane / / wywoływany.</span><span class="sxs-lookup"><span data-stu-id="371ad-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="371ad-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="371ad-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="371ad-140">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="371ad-140">win:UInt32</span></span>|<span data-ttu-id="371ad-141">Token dla zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="371ad-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="371ad-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="371ad-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="371ad-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="371ad-143">win:UnicodeString</span></span>|<span data-ttu-id="371ad-144">Przestrzeń nazw zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="371ad-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="371ad-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="371ad-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="371ad-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="371ad-146">win:UnicodeString</span></span>|<span data-ttu-id="371ad-147">Nazwa zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="371ad-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="371ad-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="371ad-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="371ad-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="371ad-149">win:UnicodeString</span></span>|<span data-ttu-id="371ad-150">Podpis zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="371ad-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="371ad-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="371ad-151">NativeMethodSignature</span></span>|<span data-ttu-id="371ad-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="371ad-152">win:UnicodeString</span></span>|<span data-ttu-id="371ad-153">Podpis metody natywnej.</span><span class="sxs-lookup"><span data-stu-id="371ad-153">The native method signature.</span></span>|  
|<span data-ttu-id="371ad-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="371ad-154">StubMethodSignature</span></span>|<span data-ttu-id="371ad-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="371ad-155">win:UnicodeString</span></span>|<span data-ttu-id="371ad-156">Podpis metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="371ad-156">The stub method signature.</span></span>|  
|<span data-ttu-id="371ad-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="371ad-157">StubMethodILCode</span></span>|<span data-ttu-id="371ad-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="371ad-158">win:UnicodeString</span></span>|<span data-ttu-id="371ad-159">Kod MSIL metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="371ad-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="371ad-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="371ad-160">ClrInstanceID</span></span>|<span data-ttu-id="371ad-161">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="371ad-161">win:UInt16</span></span>|<span data-ttu-id="371ad-162">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="371ad-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="371ad-163">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="371ad-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="371ad-164">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="371ad-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="371ad-165">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="371ad-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="371ad-166">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="371ad-166">Keyword for raising the event</span></span>|<span data-ttu-id="371ad-167">Poziom</span><span class="sxs-lookup"><span data-stu-id="371ad-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="371ad-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="371ad-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="371ad-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="371ad-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="371ad-170">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="371ad-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="371ad-171">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="371ad-171">Event</span></span>|<span data-ttu-id="371ad-172">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="371ad-172">Event ID</span></span>|<span data-ttu-id="371ad-173">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="371ad-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="371ad-174">89</span><span class="sxs-lookup"><span data-stu-id="371ad-174">89</span></span>|<span data-ttu-id="371ad-175">Uzyskał dostęp do pamięci podręcznej MSIL.</span><span class="sxs-lookup"><span data-stu-id="371ad-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="371ad-176">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="371ad-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="371ad-177">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="371ad-177">Field name</span></span>|<span data-ttu-id="371ad-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="371ad-178">Data type</span></span>|<span data-ttu-id="371ad-179">Opis</span><span class="sxs-lookup"><span data-stu-id="371ad-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="371ad-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="371ad-180">ModuleID</span></span>|<span data-ttu-id="371ad-181">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="371ad-181">win:UInt16</span></span>|<span data-ttu-id="371ad-182">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="371ad-182">The module identifier.</span></span>|  
|<span data-ttu-id="371ad-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="371ad-183">StubMethodID</span></span>|<span data-ttu-id="371ad-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="371ad-184">win:UInt64</span></span>|<span data-ttu-id="371ad-185">Identyfikator metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="371ad-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="371ad-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="371ad-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="371ad-187">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="371ad-187">win:UInt32</span></span>|<span data-ttu-id="371ad-188">Token dla zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="371ad-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="371ad-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="371ad-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="371ad-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="371ad-190">win:UnicodeString</span></span>|<span data-ttu-id="371ad-191">Przestrzeń nazw zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="371ad-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="371ad-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="371ad-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="371ad-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="371ad-193">win:UnicodeString</span></span>|<span data-ttu-id="371ad-194">Nazwa zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="371ad-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="371ad-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="371ad-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="371ad-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="371ad-196">win:UnicodeString</span></span>|<span data-ttu-id="371ad-197">Podpis zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="371ad-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="371ad-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="371ad-198">ClrInstanceID</span></span>|<span data-ttu-id="371ad-199">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="371ad-199">win:UInt16</span></span>|<span data-ttu-id="371ad-200">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="371ad-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="371ad-201">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="371ad-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="371ad-202">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="371ad-202">See also</span></span>

- [<span data-ttu-id="371ad-203">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="371ad-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
