---
title: Zabezpieczenia zdarzeń ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d09b5b76c39f33848d44beb43d9b09c5e6ed13b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046174"
---
# <a name="security-etw-events"></a><span data-ttu-id="5f02f-102">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="5f02f-102">Security ETW Events</span></span>
<a name="top"></a><span data-ttu-id="5f02f-103">Zdarzenia zabezpieczeń są wywoływane podczas weryfikacji silnej nazwy i weryfikacji kodu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="5f02f-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="5f02f-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="5f02f-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="5f02f-105">Zdarzenia StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="5f02f-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="5f02f-106">Zdarzenia AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="5f02f-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="5f02f-107">Zdarzenia StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="5f02f-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="5f02f-108">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="5f02f-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="5f02f-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="5f02f-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="5f02f-110">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5f02f-110">Keyword for raising the event</span></span>|<span data-ttu-id="5f02f-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="5f02f-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5f02f-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="5f02f-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="5f02f-113">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="5f02f-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="5f02f-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="5f02f-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5f02f-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="5f02f-115">Event</span></span>|<span data-ttu-id="5f02f-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5f02f-116">Event ID</span></span>|<span data-ttu-id="5f02f-117">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="5f02f-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="5f02f-118">181</span><span class="sxs-lookup"><span data-stu-id="5f02f-118">181</span></span>|<span data-ttu-id="5f02f-119">Rozpoczęcie weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5f02f-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="5f02f-120">182</span><span class="sxs-lookup"><span data-stu-id="5f02f-120">182</span></span>|<span data-ttu-id="5f02f-121">Koniec weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5f02f-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="5f02f-122">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5f02f-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5f02f-123">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="5f02f-123">Field name</span></span>|<span data-ttu-id="5f02f-124">Typ danych</span><span class="sxs-lookup"><span data-stu-id="5f02f-124">Data type</span></span>|<span data-ttu-id="5f02f-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5f02f-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5f02f-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="5f02f-126">VerificationFlags</span></span>|<span data-ttu-id="5f02f-127">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="5f02f-127">win:UInt32</span></span>|<span data-ttu-id="5f02f-128">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="5f02f-128">The verification flags.</span></span>|  
|<span data-ttu-id="5f02f-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="5f02f-129">ErrorCode</span></span>|<span data-ttu-id="5f02f-130">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="5f02f-130">win:UInt32</span></span>|<span data-ttu-id="5f02f-131">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="5f02f-131">The HResult error code.</span></span>|  
|<span data-ttu-id="5f02f-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="5f02f-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="5f02f-133">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f02f-133">win:UnicodeString</span></span>|<span data-ttu-id="5f02f-134">W pełni kwalifikowana nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="5f02f-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="5f02f-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f02f-135">ClrInstanceID</span></span>|<span data-ttu-id="5f02f-136">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="5f02f-136">win:UInt16</span></span>|<span data-ttu-id="5f02f-137">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f02f-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="5f02f-138">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="5f02f-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="5f02f-139">Zdarzenia AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="5f02f-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="5f02f-140">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="5f02f-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="5f02f-141">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5f02f-141">Keyword for raising the event</span></span>|<span data-ttu-id="5f02f-142">Poziom</span><span class="sxs-lookup"><span data-stu-id="5f02f-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5f02f-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="5f02f-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="5f02f-144">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="5f02f-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="5f02f-145">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="5f02f-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5f02f-146">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="5f02f-146">Event</span></span>|<span data-ttu-id="5f02f-147">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5f02f-147">Event ID</span></span>|<span data-ttu-id="5f02f-148">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="5f02f-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="5f02f-149">183</span><span class="sxs-lookup"><span data-stu-id="5f02f-149">183</span></span>|<span data-ttu-id="5f02f-150">Rozpoczęcie weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="5f02f-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="5f02f-151">184</span><span class="sxs-lookup"><span data-stu-id="5f02f-151">184</span></span>|<span data-ttu-id="5f02f-152">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="5f02f-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="5f02f-153">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5f02f-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5f02f-154">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="5f02f-154">Field name</span></span>|<span data-ttu-id="5f02f-155">Typ danych</span><span class="sxs-lookup"><span data-stu-id="5f02f-155">Data type</span></span>|<span data-ttu-id="5f02f-156">Opis</span><span class="sxs-lookup"><span data-stu-id="5f02f-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5f02f-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="5f02f-157">VerificationFlags</span></span>|<span data-ttu-id="5f02f-158">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="5f02f-158">win:UInt32</span></span>|<span data-ttu-id="5f02f-159">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="5f02f-159">The verification flags.</span></span>|  
|<span data-ttu-id="5f02f-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="5f02f-160">ErrorCode</span></span>|<span data-ttu-id="5f02f-161">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="5f02f-161">win:UInt32</span></span>|<span data-ttu-id="5f02f-162">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="5f02f-162">The HResult error code.</span></span>|  
|<span data-ttu-id="5f02f-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="5f02f-163">ModulePath</span></span>|<span data-ttu-id="5f02f-164">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f02f-164">win:UnicodeString</span></span>|<span data-ttu-id="5f02f-165">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="5f02f-165">The module path.</span></span>|  
|<span data-ttu-id="5f02f-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f02f-166">ClrInstanceID</span></span>|<span data-ttu-id="5f02f-167">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="5f02f-167">win:UInt16</span></span>|<span data-ttu-id="5f02f-168">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f02f-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f02f-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f02f-169">See also</span></span>

- [<span data-ttu-id="5f02f-170">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="5f02f-170">CLR ETW Events</span></span>](clr-etw-events.md)
