---
title: Zdarzenia ETW międzyoperacyjności
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 787c6221b651a53dbb932a5a9d0edea123e1d97d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046435"
---
# <a name="interop-etw-events"></a><span data-ttu-id="3a9d9-102">Zdarzenia ETW międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="3a9d9-102">Interop ETW Events</span></span>
<a name="top"></a><span data-ttu-id="3a9d9-103">Zdarzenia międzyoperacyjności przechwytują informacje o generacji i buforowaniu klasy języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="3a9d9-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="3a9d9-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="3a9d9-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="3a9d9-105">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="3a9d9-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="3a9d9-106">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="3a9d9-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="3a9d9-107">Zdarzenie ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="3a9d9-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="3a9d9-108">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="3a9d9-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="3a9d9-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="3a9d9-110">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3a9d9-110">Keyword for raising the event</span></span>|<span data-ttu-id="3a9d9-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="3a9d9-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3a9d9-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="3a9d9-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="3a9d9-113">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="3a9d9-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="3a9d9-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3a9d9-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="3a9d9-115">Event</span></span>|<span data-ttu-id="3a9d9-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3a9d9-116">Event ID</span></span>|<span data-ttu-id="3a9d9-117">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="3a9d9-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="3a9d9-118">88</span><span class="sxs-lookup"><span data-stu-id="3a9d9-118">88</span></span>|<span data-ttu-id="3a9d9-119">Wygenerowało procedurę pośredniczącą MSIL.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="3a9d9-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3a9d9-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="3a9d9-121">Field name</span></span>|<span data-ttu-id="3a9d9-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="3a9d9-122">Data type</span></span>|<span data-ttu-id="3a9d9-123">Opis</span><span class="sxs-lookup"><span data-stu-id="3a9d9-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3a9d9-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="3a9d9-124">ModuleID</span></span>|<span data-ttu-id="3a9d9-125">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="3a9d9-125">win:UInt16</span></span>|<span data-ttu-id="3a9d9-126">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-126">The module identifier.</span></span>|  
|<span data-ttu-id="3a9d9-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="3a9d9-127">StubMethodID</span></span>|<span data-ttu-id="3a9d9-128">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="3a9d9-128">win:UInt64</span></span>|<span data-ttu-id="3a9d9-129">Identyfikator metody zastępczej.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="3a9d9-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="3a9d9-130">StubFlags</span></span>|<span data-ttu-id="3a9d9-131">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="3a9d9-131">win:UInt64</span></span>|<span data-ttu-id="3a9d9-132">Flagi dla elementu zastępczego:</span><span class="sxs-lookup"><span data-stu-id="3a9d9-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="3a9d9-133">0x1 — odwrotna współdziałanie.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="3a9d9-134">0x2 — międzyoperacyjność COM.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="3a9d9-135">0x4-stub wygenerowane przez program NGen. exe.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="3a9d9-136">0x8 — delegat.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="3a9d9-137">0x10 — argument zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-137">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="3a9d9-138">0x20 — niezarządzany wywoływany.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="3a9d9-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="3a9d9-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="3a9d9-140">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="3a9d9-140">win:UInt32</span></span>|<span data-ttu-id="3a9d9-141">Token dla zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="3a9d9-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="3a9d9-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="3a9d9-143">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3a9d9-143">win:UnicodeString</span></span>|<span data-ttu-id="3a9d9-144">Przestrzeń nazw zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="3a9d9-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="3a9d9-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="3a9d9-146">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3a9d9-146">win:UnicodeString</span></span>|<span data-ttu-id="3a9d9-147">Nazwa zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="3a9d9-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="3a9d9-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="3a9d9-149">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3a9d9-149">win:UnicodeString</span></span>|<span data-ttu-id="3a9d9-150">Sygnatura zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="3a9d9-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="3a9d9-151">NativeMethodSignature</span></span>|<span data-ttu-id="3a9d9-152">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3a9d9-152">win:UnicodeString</span></span>|<span data-ttu-id="3a9d9-153">Podpis metody natywnej.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-153">The native method signature.</span></span>|  
|<span data-ttu-id="3a9d9-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="3a9d9-154">StubMethodSignature</span></span>|<span data-ttu-id="3a9d9-155">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3a9d9-155">win:UnicodeString</span></span>|<span data-ttu-id="3a9d9-156">Sygnatura metody zastępczej.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-156">The stub method signature.</span></span>|  
|<span data-ttu-id="3a9d9-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="3a9d9-157">StubMethodILCode</span></span>|<span data-ttu-id="3a9d9-158">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3a9d9-158">win:UnicodeString</span></span>|<span data-ttu-id="3a9d9-159">Kod MSIL dla metody zastępczej.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="3a9d9-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3a9d9-160">ClrInstanceID</span></span>|<span data-ttu-id="3a9d9-161">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="3a9d9-161">win:UInt16</span></span>|<span data-ttu-id="3a9d9-162">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3a9d9-163">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="3a9d9-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="3a9d9-164">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="3a9d9-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="3a9d9-165">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3a9d9-166">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3a9d9-166">Keyword for raising the event</span></span>|<span data-ttu-id="3a9d9-167">Poziom</span><span class="sxs-lookup"><span data-stu-id="3a9d9-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3a9d9-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="3a9d9-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="3a9d9-169">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="3a9d9-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="3a9d9-170">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3a9d9-171">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="3a9d9-171">Event</span></span>|<span data-ttu-id="3a9d9-172">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3a9d9-172">Event ID</span></span>|<span data-ttu-id="3a9d9-173">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="3a9d9-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="3a9d9-174">89</span><span class="sxs-lookup"><span data-stu-id="3a9d9-174">89</span></span>|<span data-ttu-id="3a9d9-175">Dostęp do pamięci podręcznej MSIL został uzyskany.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="3a9d9-176">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3a9d9-177">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="3a9d9-177">Field name</span></span>|<span data-ttu-id="3a9d9-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="3a9d9-178">Data type</span></span>|<span data-ttu-id="3a9d9-179">Opis</span><span class="sxs-lookup"><span data-stu-id="3a9d9-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3a9d9-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="3a9d9-180">ModuleID</span></span>|<span data-ttu-id="3a9d9-181">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="3a9d9-181">win:UInt16</span></span>|<span data-ttu-id="3a9d9-182">Identyfikator modułu.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-182">The module identifier.</span></span>|  
|<span data-ttu-id="3a9d9-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="3a9d9-183">StubMethodID</span></span>|<span data-ttu-id="3a9d9-184">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="3a9d9-184">win:UInt64</span></span>|<span data-ttu-id="3a9d9-185">Identyfikator metody zastępczej.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="3a9d9-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="3a9d9-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="3a9d9-187">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="3a9d9-187">win:UInt32</span></span>|<span data-ttu-id="3a9d9-188">Token dla zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="3a9d9-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="3a9d9-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="3a9d9-190">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3a9d9-190">win:UnicodeString</span></span>|<span data-ttu-id="3a9d9-191">Przestrzeń nazw zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="3a9d9-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="3a9d9-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="3a9d9-193">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3a9d9-193">win:UnicodeString</span></span>|<span data-ttu-id="3a9d9-194">Nazwa zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="3a9d9-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="3a9d9-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="3a9d9-196">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3a9d9-196">win:UnicodeString</span></span>|<span data-ttu-id="3a9d9-197">Sygnatura zarządzanej metody międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="3a9d9-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3a9d9-198">ClrInstanceID</span></span>|<span data-ttu-id="3a9d9-199">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="3a9d9-199">win:UInt16</span></span>|<span data-ttu-id="3a9d9-200">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3a9d9-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3a9d9-201">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="3a9d9-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="3a9d9-202">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a9d9-202">See also</span></span>

- [<span data-ttu-id="3a9d9-203">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="3a9d9-203">CLR ETW Events</span></span>](clr-etw-events.md)
