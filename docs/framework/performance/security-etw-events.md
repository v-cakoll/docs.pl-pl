---
title: "Zabezpieczenia zdarzeń ETW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a7e28eeabecfe0f1043328618f6e1be143f198a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-etw-events"></a><span data-ttu-id="e6298-102">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="e6298-102">Security ETW Events</span></span>
<span data-ttu-id="e6298-103"><a name="top"></a>Zdarzenia zabezpieczeń są wywoływane podczas weryfikacji silnej nazwy i weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="e6298-103"><a name="top"></a> Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="e6298-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="e6298-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="e6298-105">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e6298-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="e6298-106">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e6298-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="e6298-107">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e6298-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="e6298-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="e6298-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="e6298-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="e6298-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="e6298-110">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e6298-110">Keyword for raising the event</span></span>|<span data-ttu-id="e6298-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="e6298-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e6298-112">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="e6298-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="e6298-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e6298-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="e6298-114">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e6298-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e6298-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="e6298-115">Event</span></span>|<span data-ttu-id="e6298-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e6298-116">Event ID</span></span>|<span data-ttu-id="e6298-117">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="e6298-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="e6298-118">181</span><span class="sxs-lookup"><span data-stu-id="e6298-118">181</span></span>|<span data-ttu-id="e6298-119">Początek weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e6298-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="e6298-120">182</span><span class="sxs-lookup"><span data-stu-id="e6298-120">182</span></span>|<span data-ttu-id="e6298-121">Koniec weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e6298-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="e6298-122">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e6298-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e6298-123">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="e6298-123">Field name</span></span>|<span data-ttu-id="e6298-124">Typ danych</span><span class="sxs-lookup"><span data-stu-id="e6298-124">Data type</span></span>|<span data-ttu-id="e6298-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e6298-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e6298-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="e6298-126">VerificationFlags</span></span>|<span data-ttu-id="e6298-127">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="e6298-127">win:UInt32</span></span>|<span data-ttu-id="e6298-128">Weryfikacja flag.</span><span class="sxs-lookup"><span data-stu-id="e6298-128">The verification flags.</span></span>|  
|<span data-ttu-id="e6298-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="e6298-129">ErrorCode</span></span>|<span data-ttu-id="e6298-130">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="e6298-130">win:UInt32</span></span>|<span data-ttu-id="e6298-131">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="e6298-131">The HResult error code.</span></span>|  
|<span data-ttu-id="e6298-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="e6298-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="e6298-133">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6298-133">win:UnicodeString</span></span>|<span data-ttu-id="e6298-134">Nazwa FQDN zestawu.</span><span class="sxs-lookup"><span data-stu-id="e6298-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="e6298-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e6298-135">ClrInstanceID</span></span>|<span data-ttu-id="e6298-136">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="e6298-136">win:UInt16</span></span>|<span data-ttu-id="e6298-137">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e6298-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e6298-138">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="e6298-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="e6298-139">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e6298-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="e6298-140">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="e6298-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e6298-141">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e6298-141">Keyword for raising the event</span></span>|<span data-ttu-id="e6298-142">Poziom</span><span class="sxs-lookup"><span data-stu-id="e6298-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e6298-143">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="e6298-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="e6298-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e6298-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="e6298-145">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e6298-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e6298-146">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="e6298-146">Event</span></span>|<span data-ttu-id="e6298-147">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e6298-147">Event ID</span></span>|<span data-ttu-id="e6298-148">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="e6298-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="e6298-149">183</span><span class="sxs-lookup"><span data-stu-id="e6298-149">183</span></span>|<span data-ttu-id="e6298-150">Początek weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="e6298-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="e6298-151">184</span><span class="sxs-lookup"><span data-stu-id="e6298-151">184</span></span>|<span data-ttu-id="e6298-152">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="e6298-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="e6298-153">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e6298-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e6298-154">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="e6298-154">Field name</span></span>|<span data-ttu-id="e6298-155">Typ danych</span><span class="sxs-lookup"><span data-stu-id="e6298-155">Data type</span></span>|<span data-ttu-id="e6298-156">Opis</span><span class="sxs-lookup"><span data-stu-id="e6298-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e6298-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="e6298-157">VerificationFlags</span></span>|<span data-ttu-id="e6298-158">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="e6298-158">win:UInt32</span></span>|<span data-ttu-id="e6298-159">Weryfikacja flag.</span><span class="sxs-lookup"><span data-stu-id="e6298-159">The verification flags.</span></span>|  
|<span data-ttu-id="e6298-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="e6298-160">ErrorCode</span></span>|<span data-ttu-id="e6298-161">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="e6298-161">win:UInt32</span></span>|<span data-ttu-id="e6298-162">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="e6298-162">The HResult error code.</span></span>|  
|<span data-ttu-id="e6298-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="e6298-163">ModulePath</span></span>|<span data-ttu-id="e6298-164">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6298-164">win:UnicodeString</span></span>|<span data-ttu-id="e6298-165">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="e6298-165">The module path.</span></span>|  
|<span data-ttu-id="e6298-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e6298-166">ClrInstanceID</span></span>|<span data-ttu-id="e6298-167">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="e6298-167">win:UInt16</span></span>|<span data-ttu-id="e6298-168">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e6298-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6298-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6298-169">See Also</span></span>  
 [<span data-ttu-id="e6298-170">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="e6298-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
