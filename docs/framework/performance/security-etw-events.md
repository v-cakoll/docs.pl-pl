---
title: Zabezpieczenia zdarzeń ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a19dce496423883e5fed62375c6db8ed5efdb1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134033"
---
# <a name="security-etw-events"></a><span data-ttu-id="a61e8-102">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="a61e8-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="a61e8-103">Zdarzenia zabezpieczeń są wywoływane podczas Weryfikacja silnej nazwy i weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="a61e8-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="a61e8-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="a61e8-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="a61e8-105">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a61e8-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="a61e8-106">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a61e8-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="a61e8-107">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a61e8-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="a61e8-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="a61e8-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="a61e8-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="a61e8-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="a61e8-110">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a61e8-110">Keyword for raising the event</span></span>|<span data-ttu-id="a61e8-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="a61e8-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a61e8-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="a61e8-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="a61e8-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a61e8-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="a61e8-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="a61e8-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a61e8-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a61e8-115">Event</span></span>|<span data-ttu-id="a61e8-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a61e8-116">Event ID</span></span>|<span data-ttu-id="a61e8-117">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="a61e8-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="a61e8-118">181</span><span class="sxs-lookup"><span data-stu-id="a61e8-118">181</span></span>|<span data-ttu-id="a61e8-119">Początek Weryfikacja silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a61e8-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="a61e8-120">182</span><span class="sxs-lookup"><span data-stu-id="a61e8-120">182</span></span>|<span data-ttu-id="a61e8-121">Koniec Weryfikacja silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a61e8-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="a61e8-122">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a61e8-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a61e8-123">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="a61e8-123">Field name</span></span>|<span data-ttu-id="a61e8-124">Typ danych</span><span class="sxs-lookup"><span data-stu-id="a61e8-124">Data type</span></span>|<span data-ttu-id="a61e8-125">Opis</span><span class="sxs-lookup"><span data-stu-id="a61e8-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a61e8-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="a61e8-126">VerificationFlags</span></span>|<span data-ttu-id="a61e8-127">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="a61e8-127">win:UInt32</span></span>|<span data-ttu-id="a61e8-128">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="a61e8-128">The verification flags.</span></span>|  
|<span data-ttu-id="a61e8-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="a61e8-129">ErrorCode</span></span>|<span data-ttu-id="a61e8-130">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="a61e8-130">win:UInt32</span></span>|<span data-ttu-id="a61e8-131">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="a61e8-131">The HResult error code.</span></span>|  
|<span data-ttu-id="a61e8-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="a61e8-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="a61e8-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a61e8-133">win:UnicodeString</span></span>|<span data-ttu-id="a61e8-134">W pełni kwalifikowanej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="a61e8-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="a61e8-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a61e8-135">ClrInstanceID</span></span>|<span data-ttu-id="a61e8-136">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="a61e8-136">win:UInt16</span></span>|<span data-ttu-id="a61e8-137">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a61e8-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a61e8-138">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="a61e8-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="a61e8-139">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a61e8-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="a61e8-140">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="a61e8-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a61e8-141">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a61e8-141">Keyword for raising the event</span></span>|<span data-ttu-id="a61e8-142">Poziom</span><span class="sxs-lookup"><span data-stu-id="a61e8-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a61e8-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="a61e8-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="a61e8-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a61e8-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="a61e8-145">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="a61e8-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a61e8-146">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a61e8-146">Event</span></span>|<span data-ttu-id="a61e8-147">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a61e8-147">Event ID</span></span>|<span data-ttu-id="a61e8-148">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="a61e8-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="a61e8-149">183</span><span class="sxs-lookup"><span data-stu-id="a61e8-149">183</span></span>|<span data-ttu-id="a61e8-150">Uruchomienie weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="a61e8-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="a61e8-151">184</span><span class="sxs-lookup"><span data-stu-id="a61e8-151">184</span></span>|<span data-ttu-id="a61e8-152">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="a61e8-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="a61e8-153">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a61e8-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a61e8-154">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="a61e8-154">Field name</span></span>|<span data-ttu-id="a61e8-155">Typ danych</span><span class="sxs-lookup"><span data-stu-id="a61e8-155">Data type</span></span>|<span data-ttu-id="a61e8-156">Opis</span><span class="sxs-lookup"><span data-stu-id="a61e8-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a61e8-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="a61e8-157">VerificationFlags</span></span>|<span data-ttu-id="a61e8-158">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="a61e8-158">win:UInt32</span></span>|<span data-ttu-id="a61e8-159">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="a61e8-159">The verification flags.</span></span>|  
|<span data-ttu-id="a61e8-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="a61e8-160">ErrorCode</span></span>|<span data-ttu-id="a61e8-161">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="a61e8-161">win:UInt32</span></span>|<span data-ttu-id="a61e8-162">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="a61e8-162">The HResult error code.</span></span>|  
|<span data-ttu-id="a61e8-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="a61e8-163">ModulePath</span></span>|<span data-ttu-id="a61e8-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a61e8-164">win:UnicodeString</span></span>|<span data-ttu-id="a61e8-165">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="a61e8-165">The module path.</span></span>|  
|<span data-ttu-id="a61e8-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a61e8-166">ClrInstanceID</span></span>|<span data-ttu-id="a61e8-167">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="a61e8-167">win:UInt16</span></span>|<span data-ttu-id="a61e8-168">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a61e8-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a61e8-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a61e8-169">See also</span></span>

- [<span data-ttu-id="a61e8-170">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="a61e8-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
