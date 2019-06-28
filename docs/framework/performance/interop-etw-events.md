---
title: Zdarzenia ETW międzyoperacyjności
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c52c9bf37e67e4d26867d2b3754945e86e2bf609
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422423"
---
# <a name="interop-etw-events"></a><span data-ttu-id="10d25-102">Zdarzenia ETW międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="10d25-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="10d25-103">Zdarzenia międzyoperacyjności przechwytywania informacji na temat generowania szkieletu intermediate language (MSIL) firmy Microsoft i buforowania.</span><span class="sxs-lookup"><span data-stu-id="10d25-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="10d25-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="10d25-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="10d25-105">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="10d25-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="10d25-106">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="10d25-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="10d25-107">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="10d25-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="10d25-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="10d25-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="10d25-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="10d25-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="10d25-110">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="10d25-110">Keyword for raising the event</span></span>|<span data-ttu-id="10d25-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="10d25-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="10d25-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="10d25-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="10d25-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="10d25-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="10d25-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="10d25-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="10d25-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="10d25-115">Event</span></span>|<span data-ttu-id="10d25-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="10d25-116">Event ID</span></span>|<span data-ttu-id="10d25-117">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="10d25-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="10d25-118">88</span><span class="sxs-lookup"><span data-stu-id="10d25-118">88</span></span>|<span data-ttu-id="10d25-119">Klasy zastępczej MSIL został wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="10d25-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="10d25-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="10d25-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="10d25-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="10d25-121">Field name</span></span>|<span data-ttu-id="10d25-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="10d25-122">Data type</span></span>|<span data-ttu-id="10d25-123">Opis</span><span class="sxs-lookup"><span data-stu-id="10d25-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="10d25-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="10d25-124">ModuleID</span></span>|<span data-ttu-id="10d25-125">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="10d25-125">win:UInt16</span></span>|<span data-ttu-id="10d25-126">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="10d25-126">The module identifier.</span></span>|  
|<span data-ttu-id="10d25-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="10d25-127">StubMethodID</span></span>|<span data-ttu-id="10d25-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="10d25-128">win:UInt64</span></span>|<span data-ttu-id="10d25-129">Identyfikator metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="10d25-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="10d25-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="10d25-130">StubFlags</span></span>|<span data-ttu-id="10d25-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="10d25-131">win:UInt64</span></span>|<span data-ttu-id="10d25-132">Flagi dla wycinka:</span><span class="sxs-lookup"><span data-stu-id="10d25-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="10d25-133">0x1 — interop wstecznego.</span><span class="sxs-lookup"><span data-stu-id="10d25-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="10d25-134">0x2 — Usługa międzyoperacyjna modelu COM.</span><span class="sxs-lookup"><span data-stu-id="10d25-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="10d25-135">0x4 - wycinku wygenerowanym przez NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="10d25-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="10d25-136">0x8 - delegata.</span><span class="sxs-lookup"><span data-stu-id="10d25-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="10d25-137">0x10 - zmiennych argumentów.</span><span class="sxs-lookup"><span data-stu-id="10d25-137">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="10d25-138">0x20 — niezarządzane / / wywoływany.</span><span class="sxs-lookup"><span data-stu-id="10d25-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="10d25-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="10d25-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="10d25-140">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="10d25-140">win:UInt32</span></span>|<span data-ttu-id="10d25-141">Token dla zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="10d25-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="10d25-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="10d25-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="10d25-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10d25-143">win:UnicodeString</span></span>|<span data-ttu-id="10d25-144">Przestrzeń nazw zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="10d25-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="10d25-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="10d25-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="10d25-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10d25-146">win:UnicodeString</span></span>|<span data-ttu-id="10d25-147">Nazwa zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="10d25-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="10d25-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="10d25-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="10d25-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10d25-149">win:UnicodeString</span></span>|<span data-ttu-id="10d25-150">Podpis zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="10d25-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="10d25-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="10d25-151">NativeMethodSignature</span></span>|<span data-ttu-id="10d25-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10d25-152">win:UnicodeString</span></span>|<span data-ttu-id="10d25-153">Podpis metody natywnej.</span><span class="sxs-lookup"><span data-stu-id="10d25-153">The native method signature.</span></span>|  
|<span data-ttu-id="10d25-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="10d25-154">StubMethodSignature</span></span>|<span data-ttu-id="10d25-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10d25-155">win:UnicodeString</span></span>|<span data-ttu-id="10d25-156">Podpis metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="10d25-156">The stub method signature.</span></span>|  
|<span data-ttu-id="10d25-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="10d25-157">StubMethodILCode</span></span>|<span data-ttu-id="10d25-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10d25-158">win:UnicodeString</span></span>|<span data-ttu-id="10d25-159">Kod MSIL metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="10d25-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="10d25-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="10d25-160">ClrInstanceID</span></span>|<span data-ttu-id="10d25-161">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="10d25-161">win:UInt16</span></span>|<span data-ttu-id="10d25-162">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="10d25-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="10d25-163">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="10d25-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="10d25-164">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="10d25-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="10d25-165">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="10d25-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="10d25-166">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="10d25-166">Keyword for raising the event</span></span>|<span data-ttu-id="10d25-167">Poziom</span><span class="sxs-lookup"><span data-stu-id="10d25-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="10d25-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="10d25-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="10d25-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="10d25-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="10d25-170">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="10d25-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="10d25-171">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="10d25-171">Event</span></span>|<span data-ttu-id="10d25-172">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="10d25-172">Event ID</span></span>|<span data-ttu-id="10d25-173">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="10d25-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="10d25-174">89</span><span class="sxs-lookup"><span data-stu-id="10d25-174">89</span></span>|<span data-ttu-id="10d25-175">Uzyskał dostęp do pamięci podręcznej MSIL.</span><span class="sxs-lookup"><span data-stu-id="10d25-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="10d25-176">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="10d25-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="10d25-177">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="10d25-177">Field name</span></span>|<span data-ttu-id="10d25-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="10d25-178">Data type</span></span>|<span data-ttu-id="10d25-179">Opis</span><span class="sxs-lookup"><span data-stu-id="10d25-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="10d25-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="10d25-180">ModuleID</span></span>|<span data-ttu-id="10d25-181">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="10d25-181">win:UInt16</span></span>|<span data-ttu-id="10d25-182">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="10d25-182">The module identifier.</span></span>|  
|<span data-ttu-id="10d25-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="10d25-183">StubMethodID</span></span>|<span data-ttu-id="10d25-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="10d25-184">win:UInt64</span></span>|<span data-ttu-id="10d25-185">Identyfikator metody klasy zastępczej.</span><span class="sxs-lookup"><span data-stu-id="10d25-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="10d25-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="10d25-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="10d25-187">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="10d25-187">win:UInt32</span></span>|<span data-ttu-id="10d25-188">Token dla zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="10d25-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="10d25-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="10d25-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="10d25-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10d25-190">win:UnicodeString</span></span>|<span data-ttu-id="10d25-191">Przestrzeń nazw zarządzanych metoda międzyoperacyjna.</span><span class="sxs-lookup"><span data-stu-id="10d25-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="10d25-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="10d25-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="10d25-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10d25-193">win:UnicodeString</span></span>|<span data-ttu-id="10d25-194">Nazwa zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="10d25-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="10d25-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="10d25-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="10d25-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10d25-196">win:UnicodeString</span></span>|<span data-ttu-id="10d25-197">Podpis zarządzaną metodą międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="10d25-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="10d25-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="10d25-198">ClrInstanceID</span></span>|<span data-ttu-id="10d25-199">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="10d25-199">win:UInt16</span></span>|<span data-ttu-id="10d25-200">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="10d25-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="10d25-201">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="10d25-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="10d25-202">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10d25-202">See also</span></span>

- [<span data-ttu-id="10d25-203">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="10d25-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
