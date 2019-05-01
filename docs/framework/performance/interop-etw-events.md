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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949308"
---
# <a name="interop-etw-events"></a><span data-ttu-id="5f54a-102">Zdarzenia ETW międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="5f54a-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="5f54a-103">Zdarzenia międzyoperacyjności przechwytywania informacji na temat generowania szkieletu intermediate language (MSIL) firmy Microsoft i buforowania.</span><span class="sxs-lookup"><span data-stu-id="5f54a-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="5f54a-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="5f54a-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="5f54a-105">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="5f54a-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="5f54a-106">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="5f54a-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="5f54a-107">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="5f54a-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="5f54a-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="5f54a-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="5f54a-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="5f54a-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="5f54a-110">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5f54a-110">Keyword for raising the event</span></span>|<span data-ttu-id="5f54a-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="5f54a-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5f54a-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="5f54a-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="5f54a-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="5f54a-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="5f54a-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="5f54a-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5f54a-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="5f54a-115">Event</span></span>|<span data-ttu-id="5f54a-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5f54a-116">Event ID</span></span>|<span data-ttu-id="5f54a-117">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="5f54a-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="5f54a-118">88</span><span class="sxs-lookup"><span data-stu-id="5f54a-118">88</span></span>|<span data-ttu-id="5f54a-119">Klasy zastępczej MSIL został wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="5f54a-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="5f54a-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5f54a-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5f54a-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="5f54a-121">Field name</span></span>|<span data-ttu-id="5f54a-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="5f54a-122">Data type</span></span>|<span data-ttu-id="5f54a-123">Opis</span><span class="sxs-lookup"><span data-stu-id="5f54a-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5f54a-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="5f54a-124">ModuleID</span></span>|<span data-ttu-id="5f54a-125">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="5f54a-125">win:UInt16</span></span>|<span data-ttu-id="5f54a-126">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="5f54a-126">The module identifier.</span></span>|  
|<span data-ttu-id="5f54a-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="5f54a-127">StubMethodID</span></span>|<span data-ttu-id="5f54a-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f54a-128">win:UInt64</span></span>|<span data-ttu-id="5f54a-129">Identyfikator metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="5f54a-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="5f54a-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="5f54a-130">StubFlags</span></span>|<span data-ttu-id="5f54a-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f54a-131">win:UInt64</span></span>|<span data-ttu-id="5f54a-132">Flagi dla wycinka:</span><span class="sxs-lookup"><span data-stu-id="5f54a-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="5f54a-133">0x1 — interop wstecznego.</span><span class="sxs-lookup"><span data-stu-id="5f54a-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="5f54a-134">0x2 — Usługa międzyoperacyjna modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5f54a-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="5f54a-135">0x4 - wycinku wygenerowanym przez NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="5f54a-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="5f54a-136">0x8 - delegata.</span><span class="sxs-lookup"><span data-stu-id="5f54a-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="5f54a-137">0x10 - arrgument zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5f54a-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="5f54a-138">0x20 — niezarządzane / / wywoływany.</span><span class="sxs-lookup"><span data-stu-id="5f54a-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="5f54a-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="5f54a-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="5f54a-140">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="5f54a-140">win:UInt32</span></span>|<span data-ttu-id="5f54a-141">Token dla zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5f54a-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="5f54a-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="5f54a-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="5f54a-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f54a-143">win:UnicodeString</span></span>|<span data-ttu-id="5f54a-144">Przestrzeń nazw zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="5f54a-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="5f54a-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="5f54a-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="5f54a-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f54a-146">win:UnicodeString</span></span>|<span data-ttu-id="5f54a-147">Nazwa zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5f54a-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="5f54a-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="5f54a-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="5f54a-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f54a-149">win:UnicodeString</span></span>|<span data-ttu-id="5f54a-150">Podpis zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5f54a-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="5f54a-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="5f54a-151">NativeMethodSignature</span></span>|<span data-ttu-id="5f54a-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f54a-152">win:UnicodeString</span></span>|<span data-ttu-id="5f54a-153">Podpis metody natywnej.</span><span class="sxs-lookup"><span data-stu-id="5f54a-153">The native method signature.</span></span>|  
|<span data-ttu-id="5f54a-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="5f54a-154">StubMethodSignature</span></span>|<span data-ttu-id="5f54a-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f54a-155">win:UnicodeString</span></span>|<span data-ttu-id="5f54a-156">Podpis metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="5f54a-156">The stub method signature.</span></span>|  
|<span data-ttu-id="5f54a-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="5f54a-157">StubMethodILCode</span></span>|<span data-ttu-id="5f54a-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f54a-158">win:UnicodeString</span></span>|<span data-ttu-id="5f54a-159">Kod MSIL metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="5f54a-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="5f54a-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f54a-160">ClrInstanceID</span></span>|<span data-ttu-id="5f54a-161">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="5f54a-161">win:UInt16</span></span>|<span data-ttu-id="5f54a-162">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f54a-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="5f54a-163">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="5f54a-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="5f54a-164">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="5f54a-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="5f54a-165">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="5f54a-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="5f54a-166">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5f54a-166">Keyword for raising the event</span></span>|<span data-ttu-id="5f54a-167">Poziom</span><span class="sxs-lookup"><span data-stu-id="5f54a-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5f54a-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="5f54a-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="5f54a-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="5f54a-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="5f54a-170">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="5f54a-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5f54a-171">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="5f54a-171">Event</span></span>|<span data-ttu-id="5f54a-172">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5f54a-172">Event ID</span></span>|<span data-ttu-id="5f54a-173">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="5f54a-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="5f54a-174">89</span><span class="sxs-lookup"><span data-stu-id="5f54a-174">89</span></span>|<span data-ttu-id="5f54a-175">Uzyskał dostęp do pamięci podręcznej MSIL.</span><span class="sxs-lookup"><span data-stu-id="5f54a-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="5f54a-176">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5f54a-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5f54a-177">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="5f54a-177">Field name</span></span>|<span data-ttu-id="5f54a-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="5f54a-178">Data type</span></span>|<span data-ttu-id="5f54a-179">Opis</span><span class="sxs-lookup"><span data-stu-id="5f54a-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5f54a-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="5f54a-180">ModuleID</span></span>|<span data-ttu-id="5f54a-181">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="5f54a-181">win:UInt16</span></span>|<span data-ttu-id="5f54a-182">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="5f54a-182">The module identifier.</span></span>|  
|<span data-ttu-id="5f54a-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="5f54a-183">StubMethodID</span></span>|<span data-ttu-id="5f54a-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f54a-184">win:UInt64</span></span>|<span data-ttu-id="5f54a-185">Identyfikator metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="5f54a-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="5f54a-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="5f54a-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="5f54a-187">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="5f54a-187">win:UInt32</span></span>|<span data-ttu-id="5f54a-188">Token dla zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5f54a-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="5f54a-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="5f54a-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="5f54a-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f54a-190">win:UnicodeString</span></span>|<span data-ttu-id="5f54a-191">Przestrzeń nazw zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="5f54a-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="5f54a-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="5f54a-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="5f54a-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f54a-193">win:UnicodeString</span></span>|<span data-ttu-id="5f54a-194">Nazwa zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5f54a-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="5f54a-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="5f54a-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="5f54a-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f54a-196">win:UnicodeString</span></span>|<span data-ttu-id="5f54a-197">Podpis zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5f54a-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="5f54a-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f54a-198">ClrInstanceID</span></span>|<span data-ttu-id="5f54a-199">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="5f54a-199">win:UInt16</span></span>|<span data-ttu-id="5f54a-200">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f54a-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="5f54a-201">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="5f54a-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="5f54a-202">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f54a-202">See also</span></span>

- [<span data-ttu-id="5f54a-203">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="5f54a-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
