---
title: Zabezpieczenia zdarzeń ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1dad042595608a805f978673858acaa5c01130f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974880"
---
# <a name="security-etw-events"></a><span data-ttu-id="b4fb6-102">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="b4fb6-102">Security ETW Events</span></span>

<span data-ttu-id="b4fb6-103">Zdarzenia zabezpieczeń są wywoływane podczas weryfikacji silnej nazwy i weryfikacji kodu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="b4fb6-104">Zdarzenia StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="b4fb6-104">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="b4fb6-105">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="b4fb6-106">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="b4fb6-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="b4fb6-107">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b4fb6-107">Keyword for raising the event</span></span>|<span data-ttu-id="b4fb6-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b4fb6-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b4fb6-109">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="b4fb6-109">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="b4fb6-110">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="b4fb6-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="b4fb6-111">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b4fb6-112">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="b4fb6-112">Event</span></span>|<span data-ttu-id="b4fb6-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b4fb6-113">Event ID</span></span>|<span data-ttu-id="b4fb6-114">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="b4fb6-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="b4fb6-115">181</span><span class="sxs-lookup"><span data-stu-id="b4fb6-115">181</span></span>|<span data-ttu-id="b4fb6-116">Rozpoczęcie weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-116">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="b4fb6-117">182</span><span class="sxs-lookup"><span data-stu-id="b4fb6-117">182</span></span>|<span data-ttu-id="b4fb6-118">Koniec weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-118">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="b4fb6-119">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b4fb6-120">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="b4fb6-120">Field name</span></span>|<span data-ttu-id="b4fb6-121">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b4fb6-121">Data type</span></span>|<span data-ttu-id="b4fb6-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b4fb6-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b4fb6-123">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="b4fb6-123">VerificationFlags</span></span>|<span data-ttu-id="b4fb6-124">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b4fb6-124">win:UInt32</span></span>|<span data-ttu-id="b4fb6-125">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-125">The verification flags.</span></span>|  
|<span data-ttu-id="b4fb6-126">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="b4fb6-126">ErrorCode</span></span>|<span data-ttu-id="b4fb6-127">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b4fb6-127">win:UInt32</span></span>|<span data-ttu-id="b4fb6-128">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-128">The HResult error code.</span></span>|  
|<span data-ttu-id="b4fb6-129">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="b4fb6-129">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="b4fb6-130">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b4fb6-130">win:UnicodeString</span></span>|<span data-ttu-id="b4fb6-131">W pełni kwalifikowana nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-131">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="b4fb6-132">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b4fb6-132">ClrInstanceID</span></span>|<span data-ttu-id="b4fb6-133">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b4fb6-133">win:UInt16</span></span>|<span data-ttu-id="b4fb6-134">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-134">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="b4fb6-135">Zdarzenia AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="b4fb6-135">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="b4fb6-136">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-136">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b4fb6-137">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b4fb6-137">Keyword for raising the event</span></span>|<span data-ttu-id="b4fb6-138">Poziom</span><span class="sxs-lookup"><span data-stu-id="b4fb6-138">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b4fb6-139">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="b4fb6-139">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="b4fb6-140">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="b4fb6-140">Informational(4)</span></span>|  
  
 <span data-ttu-id="b4fb6-141">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-141">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b4fb6-142">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="b4fb6-142">Event</span></span>|<span data-ttu-id="b4fb6-143">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b4fb6-143">Event ID</span></span>|<span data-ttu-id="b4fb6-144">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="b4fb6-144">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="b4fb6-145">183</span><span class="sxs-lookup"><span data-stu-id="b4fb6-145">183</span></span>|<span data-ttu-id="b4fb6-146">Rozpoczęcie weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-146">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="b4fb6-147">184</span><span class="sxs-lookup"><span data-stu-id="b4fb6-147">184</span></span>|<span data-ttu-id="b4fb6-148">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-148">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="b4fb6-149">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-149">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b4fb6-150">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="b4fb6-150">Field name</span></span>|<span data-ttu-id="b4fb6-151">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b4fb6-151">Data type</span></span>|<span data-ttu-id="b4fb6-152">Opis</span><span class="sxs-lookup"><span data-stu-id="b4fb6-152">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b4fb6-153">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="b4fb6-153">VerificationFlags</span></span>|<span data-ttu-id="b4fb6-154">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b4fb6-154">win:UInt32</span></span>|<span data-ttu-id="b4fb6-155">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-155">The verification flags.</span></span>|  
|<span data-ttu-id="b4fb6-156">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="b4fb6-156">ErrorCode</span></span>|<span data-ttu-id="b4fb6-157">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b4fb6-157">win:UInt32</span></span>|<span data-ttu-id="b4fb6-158">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-158">The HResult error code.</span></span>|  
|<span data-ttu-id="b4fb6-159">ModulePath</span><span class="sxs-lookup"><span data-stu-id="b4fb6-159">ModulePath</span></span>|<span data-ttu-id="b4fb6-160">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b4fb6-160">win:UnicodeString</span></span>|<span data-ttu-id="b4fb6-161">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-161">The module path.</span></span>|  
|<span data-ttu-id="b4fb6-162">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b4fb6-162">ClrInstanceID</span></span>|<span data-ttu-id="b4fb6-163">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b4fb6-163">win:UInt16</span></span>|<span data-ttu-id="b4fb6-164">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b4fb6-164">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4fb6-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4fb6-165">See also</span></span>

- [<span data-ttu-id="b4fb6-166">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="b4fb6-166">CLR ETW Events</span></span>](clr-etw-events.md)
