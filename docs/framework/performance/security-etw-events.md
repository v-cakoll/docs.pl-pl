---
title: Zabezpieczenia zdarzeń ETW
description: Informacje o zdarzeniach ETW zabezpieczeń, które są wywoływane podczas weryfikacji silnej nazwy i weryfikacji kodu Authenticode w programie .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 2fd2d450223cd16a7791b8f6c67afe6bcb954eb3
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474218"
---
# <a name="security-etw-events"></a><span data-ttu-id="693e5-103">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="693e5-103">Security ETW Events</span></span>

<span data-ttu-id="693e5-104">Zdarzenia zabezpieczeń są wywoływane podczas weryfikacji silnej nazwy i weryfikacji kodu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="693e5-104">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="693e5-105">Zdarzenia StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="693e5-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="693e5-106">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="693e5-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="693e5-107">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="693e5-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="693e5-108">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="693e5-108">Keyword for raising the event</span></span>|<span data-ttu-id="693e5-109">Poziom</span><span class="sxs-lookup"><span data-stu-id="693e5-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="693e5-110">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="693e5-110">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="693e5-111">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="693e5-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="693e5-112">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="693e5-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="693e5-113">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="693e5-113">Event</span></span>|<span data-ttu-id="693e5-114">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="693e5-114">Event ID</span></span>|<span data-ttu-id="693e5-115">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="693e5-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="693e5-116">181</span><span class="sxs-lookup"><span data-stu-id="693e5-116">181</span></span>|<span data-ttu-id="693e5-117">Rozpoczęcie weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="693e5-117">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="693e5-118">182</span><span class="sxs-lookup"><span data-stu-id="693e5-118">182</span></span>|<span data-ttu-id="693e5-119">Koniec weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="693e5-119">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="693e5-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="693e5-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="693e5-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="693e5-121">Field name</span></span>|<span data-ttu-id="693e5-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="693e5-122">Data type</span></span>|<span data-ttu-id="693e5-123">Opis</span><span class="sxs-lookup"><span data-stu-id="693e5-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="693e5-124">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="693e5-124">VerificationFlags</span></span>|<span data-ttu-id="693e5-125">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="693e5-125">win:UInt32</span></span>|<span data-ttu-id="693e5-126">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="693e5-126">The verification flags.</span></span>|  
|<span data-ttu-id="693e5-127">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="693e5-127">ErrorCode</span></span>|<span data-ttu-id="693e5-128">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="693e5-128">win:UInt32</span></span>|<span data-ttu-id="693e5-129">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="693e5-129">The HResult error code.</span></span>|  
|<span data-ttu-id="693e5-130">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="693e5-130">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="693e5-131">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="693e5-131">win:UnicodeString</span></span>|<span data-ttu-id="693e5-132">W pełni kwalifikowana nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="693e5-132">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="693e5-133">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="693e5-133">ClrInstanceID</span></span>|<span data-ttu-id="693e5-134">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="693e5-134">win:UInt16</span></span>|<span data-ttu-id="693e5-135">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="693e5-135">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="693e5-136">Zdarzenia AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="693e5-136">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="693e5-137">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="693e5-137">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="693e5-138">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="693e5-138">Keyword for raising the event</span></span>|<span data-ttu-id="693e5-139">Poziom</span><span class="sxs-lookup"><span data-stu-id="693e5-139">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="693e5-140">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="693e5-140">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="693e5-141">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="693e5-141">Informational(4)</span></span>|  
  
 <span data-ttu-id="693e5-142">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="693e5-142">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="693e5-143">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="693e5-143">Event</span></span>|<span data-ttu-id="693e5-144">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="693e5-144">Event ID</span></span>|<span data-ttu-id="693e5-145">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="693e5-145">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="693e5-146">183</span><span class="sxs-lookup"><span data-stu-id="693e5-146">183</span></span>|<span data-ttu-id="693e5-147">Rozpoczęcie weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="693e5-147">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="693e5-148">184</span><span class="sxs-lookup"><span data-stu-id="693e5-148">184</span></span>|<span data-ttu-id="693e5-149">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="693e5-149">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="693e5-150">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="693e5-150">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="693e5-151">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="693e5-151">Field name</span></span>|<span data-ttu-id="693e5-152">Typ danych</span><span class="sxs-lookup"><span data-stu-id="693e5-152">Data type</span></span>|<span data-ttu-id="693e5-153">Opis</span><span class="sxs-lookup"><span data-stu-id="693e5-153">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="693e5-154">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="693e5-154">VerificationFlags</span></span>|<span data-ttu-id="693e5-155">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="693e5-155">win:UInt32</span></span>|<span data-ttu-id="693e5-156">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="693e5-156">The verification flags.</span></span>|  
|<span data-ttu-id="693e5-157">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="693e5-157">ErrorCode</span></span>|<span data-ttu-id="693e5-158">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="693e5-158">win:UInt32</span></span>|<span data-ttu-id="693e5-159">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="693e5-159">The HResult error code.</span></span>|  
|<span data-ttu-id="693e5-160">ModulePath</span><span class="sxs-lookup"><span data-stu-id="693e5-160">ModulePath</span></span>|<span data-ttu-id="693e5-161">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="693e5-161">win:UnicodeString</span></span>|<span data-ttu-id="693e5-162">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="693e5-162">The module path.</span></span>|  
|<span data-ttu-id="693e5-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="693e5-163">ClrInstanceID</span></span>|<span data-ttu-id="693e5-164">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="693e5-164">win:UInt16</span></span>|<span data-ttu-id="693e5-165">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="693e5-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="693e5-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="693e5-166">See also</span></span>

- [<span data-ttu-id="693e5-167">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="693e5-167">CLR ETW Events</span></span>](clr-etw-events.md)
