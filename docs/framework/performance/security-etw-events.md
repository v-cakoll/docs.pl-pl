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
ms.workload: dotnet
ms.openlocfilehash: abf6e6896267b6d1c8449b020230381923f38f1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-etw-events"></a><span data-ttu-id="751e3-102">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="751e3-102">Security ETW Events</span></span>
<a name="top"></a><span data-ttu-id="751e3-103">Zdarzenia zabezpieczeń są wywoływane podczas weryfikacji silnej nazwy i weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="751e3-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="751e3-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="751e3-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="751e3-105">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="751e3-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="751e3-106">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="751e3-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="751e3-107">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="751e3-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="751e3-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="751e3-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="751e3-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="751e3-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="751e3-110">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="751e3-110">Keyword for raising the event</span></span>|<span data-ttu-id="751e3-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="751e3-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="751e3-112">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="751e3-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="751e3-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="751e3-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="751e3-114">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="751e3-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="751e3-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="751e3-115">Event</span></span>|<span data-ttu-id="751e3-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="751e3-116">Event ID</span></span>|<span data-ttu-id="751e3-117">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="751e3-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="751e3-118">181</span><span class="sxs-lookup"><span data-stu-id="751e3-118">181</span></span>|<span data-ttu-id="751e3-119">Początek weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="751e3-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="751e3-120">182</span><span class="sxs-lookup"><span data-stu-id="751e3-120">182</span></span>|<span data-ttu-id="751e3-121">Koniec weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="751e3-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="751e3-122">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="751e3-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="751e3-123">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="751e3-123">Field name</span></span>|<span data-ttu-id="751e3-124">Typ danych</span><span class="sxs-lookup"><span data-stu-id="751e3-124">Data type</span></span>|<span data-ttu-id="751e3-125">Opis</span><span class="sxs-lookup"><span data-stu-id="751e3-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="751e3-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="751e3-126">VerificationFlags</span></span>|<span data-ttu-id="751e3-127">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="751e3-127">win:UInt32</span></span>|<span data-ttu-id="751e3-128">Weryfikacja flag.</span><span class="sxs-lookup"><span data-stu-id="751e3-128">The verification flags.</span></span>|  
|<span data-ttu-id="751e3-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="751e3-129">ErrorCode</span></span>|<span data-ttu-id="751e3-130">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="751e3-130">win:UInt32</span></span>|<span data-ttu-id="751e3-131">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="751e3-131">The HResult error code.</span></span>|  
|<span data-ttu-id="751e3-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="751e3-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="751e3-133">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="751e3-133">win:UnicodeString</span></span>|<span data-ttu-id="751e3-134">Nazwa FQDN zestawu.</span><span class="sxs-lookup"><span data-stu-id="751e3-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="751e3-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="751e3-135">ClrInstanceID</span></span>|<span data-ttu-id="751e3-136">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="751e3-136">win:UInt16</span></span>|<span data-ttu-id="751e3-137">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="751e3-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="751e3-138">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="751e3-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="751e3-139">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="751e3-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="751e3-140">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="751e3-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="751e3-141">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="751e3-141">Keyword for raising the event</span></span>|<span data-ttu-id="751e3-142">Poziom</span><span class="sxs-lookup"><span data-stu-id="751e3-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="751e3-143">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="751e3-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="751e3-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="751e3-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="751e3-145">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="751e3-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="751e3-146">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="751e3-146">Event</span></span>|<span data-ttu-id="751e3-147">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="751e3-147">Event ID</span></span>|<span data-ttu-id="751e3-148">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="751e3-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="751e3-149">183</span><span class="sxs-lookup"><span data-stu-id="751e3-149">183</span></span>|<span data-ttu-id="751e3-150">Początek weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="751e3-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="751e3-151">184</span><span class="sxs-lookup"><span data-stu-id="751e3-151">184</span></span>|<span data-ttu-id="751e3-152">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="751e3-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="751e3-153">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="751e3-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="751e3-154">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="751e3-154">Field name</span></span>|<span data-ttu-id="751e3-155">Typ danych</span><span class="sxs-lookup"><span data-stu-id="751e3-155">Data type</span></span>|<span data-ttu-id="751e3-156">Opis</span><span class="sxs-lookup"><span data-stu-id="751e3-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="751e3-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="751e3-157">VerificationFlags</span></span>|<span data-ttu-id="751e3-158">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="751e3-158">win:UInt32</span></span>|<span data-ttu-id="751e3-159">Weryfikacja flag.</span><span class="sxs-lookup"><span data-stu-id="751e3-159">The verification flags.</span></span>|  
|<span data-ttu-id="751e3-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="751e3-160">ErrorCode</span></span>|<span data-ttu-id="751e3-161">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="751e3-161">win:UInt32</span></span>|<span data-ttu-id="751e3-162">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="751e3-162">The HResult error code.</span></span>|  
|<span data-ttu-id="751e3-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="751e3-163">ModulePath</span></span>|<span data-ttu-id="751e3-164">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="751e3-164">win:UnicodeString</span></span>|<span data-ttu-id="751e3-165">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="751e3-165">The module path.</span></span>|  
|<span data-ttu-id="751e3-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="751e3-166">ClrInstanceID</span></span>|<span data-ttu-id="751e3-167">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="751e3-167">win:UInt16</span></span>|<span data-ttu-id="751e3-168">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="751e3-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="751e3-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="751e3-169">See Also</span></span>  
 [<span data-ttu-id="751e3-170">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="751e3-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
