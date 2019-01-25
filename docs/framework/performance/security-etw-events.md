---
title: Zabezpieczenia zdarzeń ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5cd5e660778b852cfee84359bb4d7253ca8f118d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608079"
---
# <a name="security-etw-events"></a><span data-ttu-id="d85eb-102">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="d85eb-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="d85eb-103">Zdarzenia zabezpieczeń są wywoływane podczas Weryfikacja silnej nazwy i weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d85eb-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="d85eb-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="d85eb-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="d85eb-105">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d85eb-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="d85eb-106">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d85eb-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="d85eb-107">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d85eb-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="d85eb-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="d85eb-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="d85eb-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="d85eb-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="d85eb-110">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d85eb-110">Keyword for raising the event</span></span>|<span data-ttu-id="d85eb-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="d85eb-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d85eb-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="d85eb-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="d85eb-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d85eb-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="d85eb-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="d85eb-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d85eb-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="d85eb-115">Event</span></span>|<span data-ttu-id="d85eb-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d85eb-116">Event ID</span></span>|<span data-ttu-id="d85eb-117">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="d85eb-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="d85eb-118">181</span><span class="sxs-lookup"><span data-stu-id="d85eb-118">181</span></span>|<span data-ttu-id="d85eb-119">Początek Weryfikacja silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d85eb-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="d85eb-120">182</span><span class="sxs-lookup"><span data-stu-id="d85eb-120">182</span></span>|<span data-ttu-id="d85eb-121">Koniec Weryfikacja silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d85eb-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="d85eb-122">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d85eb-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d85eb-123">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="d85eb-123">Field name</span></span>|<span data-ttu-id="d85eb-124">Typ danych</span><span class="sxs-lookup"><span data-stu-id="d85eb-124">Data type</span></span>|<span data-ttu-id="d85eb-125">Opis</span><span class="sxs-lookup"><span data-stu-id="d85eb-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d85eb-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="d85eb-126">VerificationFlags</span></span>|<span data-ttu-id="d85eb-127">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="d85eb-127">win:UInt32</span></span>|<span data-ttu-id="d85eb-128">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="d85eb-128">The verification flags.</span></span>|  
|<span data-ttu-id="d85eb-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="d85eb-129">ErrorCode</span></span>|<span data-ttu-id="d85eb-130">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="d85eb-130">win:UInt32</span></span>|<span data-ttu-id="d85eb-131">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="d85eb-131">The HResult error code.</span></span>|  
|<span data-ttu-id="d85eb-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="d85eb-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="d85eb-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d85eb-133">win:UnicodeString</span></span>|<span data-ttu-id="d85eb-134">W pełni kwalifikowanej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="d85eb-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="d85eb-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d85eb-135">ClrInstanceID</span></span>|<span data-ttu-id="d85eb-136">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="d85eb-136">win:UInt16</span></span>|<span data-ttu-id="d85eb-137">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d85eb-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d85eb-138">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="d85eb-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="d85eb-139">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d85eb-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="d85eb-140">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="d85eb-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d85eb-141">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d85eb-141">Keyword for raising the event</span></span>|<span data-ttu-id="d85eb-142">Poziom</span><span class="sxs-lookup"><span data-stu-id="d85eb-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d85eb-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="d85eb-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="d85eb-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d85eb-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="d85eb-145">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="d85eb-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d85eb-146">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="d85eb-146">Event</span></span>|<span data-ttu-id="d85eb-147">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d85eb-147">Event ID</span></span>|<span data-ttu-id="d85eb-148">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="d85eb-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="d85eb-149">183</span><span class="sxs-lookup"><span data-stu-id="d85eb-149">183</span></span>|<span data-ttu-id="d85eb-150">Uruchomienie weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d85eb-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="d85eb-151">184</span><span class="sxs-lookup"><span data-stu-id="d85eb-151">184</span></span>|<span data-ttu-id="d85eb-152">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d85eb-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="d85eb-153">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d85eb-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d85eb-154">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="d85eb-154">Field name</span></span>|<span data-ttu-id="d85eb-155">Typ danych</span><span class="sxs-lookup"><span data-stu-id="d85eb-155">Data type</span></span>|<span data-ttu-id="d85eb-156">Opis</span><span class="sxs-lookup"><span data-stu-id="d85eb-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d85eb-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="d85eb-157">VerificationFlags</span></span>|<span data-ttu-id="d85eb-158">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="d85eb-158">win:UInt32</span></span>|<span data-ttu-id="d85eb-159">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="d85eb-159">The verification flags.</span></span>|  
|<span data-ttu-id="d85eb-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="d85eb-160">ErrorCode</span></span>|<span data-ttu-id="d85eb-161">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="d85eb-161">win:UInt32</span></span>|<span data-ttu-id="d85eb-162">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="d85eb-162">The HResult error code.</span></span>|  
|<span data-ttu-id="d85eb-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="d85eb-163">ModulePath</span></span>|<span data-ttu-id="d85eb-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d85eb-164">win:UnicodeString</span></span>|<span data-ttu-id="d85eb-165">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="d85eb-165">The module path.</span></span>|  
|<span data-ttu-id="d85eb-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d85eb-166">ClrInstanceID</span></span>|<span data-ttu-id="d85eb-167">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="d85eb-167">win:UInt16</span></span>|<span data-ttu-id="d85eb-168">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d85eb-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d85eb-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d85eb-169">See also</span></span>
- [<span data-ttu-id="d85eb-170">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="d85eb-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
