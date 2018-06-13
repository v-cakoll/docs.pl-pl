---
title: Zabezpieczenia zdarzeń ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e02274b63ddf7df42d26621791de0286df9655b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395515"
---
# <a name="security-etw-events"></a><span data-ttu-id="92e35-102">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="92e35-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="92e35-103">Zdarzenia zabezpieczeń są wywoływane podczas weryfikacji silnej nazwy i weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="92e35-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="92e35-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="92e35-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="92e35-105">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92e35-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="92e35-106">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92e35-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="92e35-107">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92e35-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="92e35-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="92e35-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="92e35-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="92e35-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="92e35-110">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92e35-110">Keyword for raising the event</span></span>|<span data-ttu-id="92e35-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="92e35-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="92e35-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="92e35-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="92e35-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="92e35-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="92e35-114">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="92e35-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="92e35-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="92e35-115">Event</span></span>|<span data-ttu-id="92e35-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92e35-116">Event ID</span></span>|<span data-ttu-id="92e35-117">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="92e35-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="92e35-118">181</span><span class="sxs-lookup"><span data-stu-id="92e35-118">181</span></span>|<span data-ttu-id="92e35-119">Początek weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="92e35-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="92e35-120">182</span><span class="sxs-lookup"><span data-stu-id="92e35-120">182</span></span>|<span data-ttu-id="92e35-121">Koniec weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="92e35-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="92e35-122">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="92e35-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="92e35-123">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="92e35-123">Field name</span></span>|<span data-ttu-id="92e35-124">Typ danych</span><span class="sxs-lookup"><span data-stu-id="92e35-124">Data type</span></span>|<span data-ttu-id="92e35-125">Opis</span><span class="sxs-lookup"><span data-stu-id="92e35-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="92e35-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="92e35-126">VerificationFlags</span></span>|<span data-ttu-id="92e35-127">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="92e35-127">win:UInt32</span></span>|<span data-ttu-id="92e35-128">Weryfikacja flag.</span><span class="sxs-lookup"><span data-stu-id="92e35-128">The verification flags.</span></span>|  
|<span data-ttu-id="92e35-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="92e35-129">ErrorCode</span></span>|<span data-ttu-id="92e35-130">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="92e35-130">win:UInt32</span></span>|<span data-ttu-id="92e35-131">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="92e35-131">The HResult error code.</span></span>|  
|<span data-ttu-id="92e35-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="92e35-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="92e35-133">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="92e35-133">win:UnicodeString</span></span>|<span data-ttu-id="92e35-134">Nazwa FQDN zestawu.</span><span class="sxs-lookup"><span data-stu-id="92e35-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="92e35-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="92e35-135">ClrInstanceID</span></span>|<span data-ttu-id="92e35-136">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="92e35-136">win:UInt16</span></span>|<span data-ttu-id="92e35-137">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="92e35-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="92e35-138">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="92e35-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="92e35-139">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92e35-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="92e35-140">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="92e35-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="92e35-141">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92e35-141">Keyword for raising the event</span></span>|<span data-ttu-id="92e35-142">Poziom</span><span class="sxs-lookup"><span data-stu-id="92e35-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="92e35-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="92e35-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="92e35-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="92e35-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="92e35-145">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="92e35-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="92e35-146">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="92e35-146">Event</span></span>|<span data-ttu-id="92e35-147">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92e35-147">Event ID</span></span>|<span data-ttu-id="92e35-148">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="92e35-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="92e35-149">183</span><span class="sxs-lookup"><span data-stu-id="92e35-149">183</span></span>|<span data-ttu-id="92e35-150">Początek weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="92e35-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="92e35-151">184</span><span class="sxs-lookup"><span data-stu-id="92e35-151">184</span></span>|<span data-ttu-id="92e35-152">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="92e35-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="92e35-153">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="92e35-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="92e35-154">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="92e35-154">Field name</span></span>|<span data-ttu-id="92e35-155">Typ danych</span><span class="sxs-lookup"><span data-stu-id="92e35-155">Data type</span></span>|<span data-ttu-id="92e35-156">Opis</span><span class="sxs-lookup"><span data-stu-id="92e35-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="92e35-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="92e35-157">VerificationFlags</span></span>|<span data-ttu-id="92e35-158">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="92e35-158">win:UInt32</span></span>|<span data-ttu-id="92e35-159">Weryfikacja flag.</span><span class="sxs-lookup"><span data-stu-id="92e35-159">The verification flags.</span></span>|  
|<span data-ttu-id="92e35-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="92e35-160">ErrorCode</span></span>|<span data-ttu-id="92e35-161">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="92e35-161">win:UInt32</span></span>|<span data-ttu-id="92e35-162">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="92e35-162">The HResult error code.</span></span>|  
|<span data-ttu-id="92e35-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="92e35-163">ModulePath</span></span>|<span data-ttu-id="92e35-164">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="92e35-164">win:UnicodeString</span></span>|<span data-ttu-id="92e35-165">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="92e35-165">The module path.</span></span>|  
|<span data-ttu-id="92e35-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="92e35-166">ClrInstanceID</span></span>|<span data-ttu-id="92e35-167">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="92e35-167">win:UInt16</span></span>|<span data-ttu-id="92e35-168">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="92e35-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92e35-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92e35-169">See Also</span></span>  
 [<span data-ttu-id="92e35-170">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="92e35-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
