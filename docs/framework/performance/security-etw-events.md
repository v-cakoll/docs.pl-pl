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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949204"
---
# <a name="security-etw-events"></a><span data-ttu-id="532c6-102">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="532c6-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="532c6-103">Zdarzenia zabezpieczeń są wywoływane podczas Weryfikacja silnej nazwy i weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="532c6-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="532c6-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="532c6-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="532c6-105">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="532c6-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="532c6-106">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="532c6-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="532c6-107">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="532c6-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="532c6-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="532c6-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="532c6-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="532c6-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="532c6-110">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="532c6-110">Keyword for raising the event</span></span>|<span data-ttu-id="532c6-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="532c6-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="532c6-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="532c6-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="532c6-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="532c6-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="532c6-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="532c6-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="532c6-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="532c6-115">Event</span></span>|<span data-ttu-id="532c6-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="532c6-116">Event ID</span></span>|<span data-ttu-id="532c6-117">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="532c6-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="532c6-118">181</span><span class="sxs-lookup"><span data-stu-id="532c6-118">181</span></span>|<span data-ttu-id="532c6-119">Początek Weryfikacja silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="532c6-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="532c6-120">182</span><span class="sxs-lookup"><span data-stu-id="532c6-120">182</span></span>|<span data-ttu-id="532c6-121">Koniec Weryfikacja silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="532c6-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="532c6-122">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="532c6-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="532c6-123">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="532c6-123">Field name</span></span>|<span data-ttu-id="532c6-124">Typ danych</span><span class="sxs-lookup"><span data-stu-id="532c6-124">Data type</span></span>|<span data-ttu-id="532c6-125">Opis</span><span class="sxs-lookup"><span data-stu-id="532c6-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="532c6-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="532c6-126">VerificationFlags</span></span>|<span data-ttu-id="532c6-127">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="532c6-127">win:UInt32</span></span>|<span data-ttu-id="532c6-128">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="532c6-128">The verification flags.</span></span>|  
|<span data-ttu-id="532c6-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="532c6-129">ErrorCode</span></span>|<span data-ttu-id="532c6-130">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="532c6-130">win:UInt32</span></span>|<span data-ttu-id="532c6-131">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="532c6-131">The HResult error code.</span></span>|  
|<span data-ttu-id="532c6-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="532c6-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="532c6-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="532c6-133">win:UnicodeString</span></span>|<span data-ttu-id="532c6-134">W pełni kwalifikowanej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="532c6-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="532c6-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="532c6-135">ClrInstanceID</span></span>|<span data-ttu-id="532c6-136">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="532c6-136">win:UInt16</span></span>|<span data-ttu-id="532c6-137">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="532c6-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="532c6-138">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="532c6-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="532c6-139">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="532c6-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="532c6-140">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="532c6-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="532c6-141">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="532c6-141">Keyword for raising the event</span></span>|<span data-ttu-id="532c6-142">Poziom</span><span class="sxs-lookup"><span data-stu-id="532c6-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="532c6-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="532c6-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="532c6-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="532c6-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="532c6-145">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="532c6-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="532c6-146">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="532c6-146">Event</span></span>|<span data-ttu-id="532c6-147">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="532c6-147">Event ID</span></span>|<span data-ttu-id="532c6-148">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="532c6-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="532c6-149">183</span><span class="sxs-lookup"><span data-stu-id="532c6-149">183</span></span>|<span data-ttu-id="532c6-150">Uruchomienie weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="532c6-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="532c6-151">184</span><span class="sxs-lookup"><span data-stu-id="532c6-151">184</span></span>|<span data-ttu-id="532c6-152">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="532c6-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="532c6-153">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="532c6-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="532c6-154">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="532c6-154">Field name</span></span>|<span data-ttu-id="532c6-155">Typ danych</span><span class="sxs-lookup"><span data-stu-id="532c6-155">Data type</span></span>|<span data-ttu-id="532c6-156">Opis</span><span class="sxs-lookup"><span data-stu-id="532c6-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="532c6-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="532c6-157">VerificationFlags</span></span>|<span data-ttu-id="532c6-158">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="532c6-158">win:UInt32</span></span>|<span data-ttu-id="532c6-159">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="532c6-159">The verification flags.</span></span>|  
|<span data-ttu-id="532c6-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="532c6-160">ErrorCode</span></span>|<span data-ttu-id="532c6-161">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="532c6-161">win:UInt32</span></span>|<span data-ttu-id="532c6-162">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="532c6-162">The HResult error code.</span></span>|  
|<span data-ttu-id="532c6-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="532c6-163">ModulePath</span></span>|<span data-ttu-id="532c6-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="532c6-164">win:UnicodeString</span></span>|<span data-ttu-id="532c6-165">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="532c6-165">The module path.</span></span>|  
|<span data-ttu-id="532c6-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="532c6-166">ClrInstanceID</span></span>|<span data-ttu-id="532c6-167">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="532c6-167">win:UInt16</span></span>|<span data-ttu-id="532c6-168">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="532c6-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="532c6-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="532c6-169">See also</span></span>

- [<span data-ttu-id="532c6-170">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="532c6-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
