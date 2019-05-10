---
title: Zabezpieczenia zdarzeń ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2ea19c88ff8b854b09ed372b35bf8c45d994585
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583655"
---
# <a name="security-etw-events"></a><span data-ttu-id="8d873-102">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="8d873-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="8d873-103">Zdarzenia zabezpieczeń są wywoływane podczas Weryfikacja silnej nazwy i weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="8d873-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="8d873-104">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="8d873-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="8d873-105">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8d873-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="8d873-106">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8d873-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="8d873-107">StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8d873-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="8d873-108">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="8d873-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="8d873-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="8d873-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="8d873-110">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8d873-110">Keyword for raising the event</span></span>|<span data-ttu-id="8d873-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="8d873-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="8d873-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="8d873-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="8d873-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="8d873-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="8d873-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="8d873-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="8d873-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="8d873-115">Event</span></span>|<span data-ttu-id="8d873-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8d873-116">Event ID</span></span>|<span data-ttu-id="8d873-117">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="8d873-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="8d873-118">181</span><span class="sxs-lookup"><span data-stu-id="8d873-118">181</span></span>|<span data-ttu-id="8d873-119">Początek Weryfikacja silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="8d873-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="8d873-120">182</span><span class="sxs-lookup"><span data-stu-id="8d873-120">182</span></span>|<span data-ttu-id="8d873-121">Koniec Weryfikacja silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="8d873-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="8d873-122">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8d873-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="8d873-123">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="8d873-123">Field name</span></span>|<span data-ttu-id="8d873-124">Typ danych</span><span class="sxs-lookup"><span data-stu-id="8d873-124">Data type</span></span>|<span data-ttu-id="8d873-125">Opis</span><span class="sxs-lookup"><span data-stu-id="8d873-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="8d873-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="8d873-126">VerificationFlags</span></span>|<span data-ttu-id="8d873-127">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="8d873-127">win:UInt32</span></span>|<span data-ttu-id="8d873-128">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="8d873-128">The verification flags.</span></span>|  
|<span data-ttu-id="8d873-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="8d873-129">ErrorCode</span></span>|<span data-ttu-id="8d873-130">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="8d873-130">win:UInt32</span></span>|<span data-ttu-id="8d873-131">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="8d873-131">The HResult error code.</span></span>|  
|<span data-ttu-id="8d873-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="8d873-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="8d873-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d873-133">win:UnicodeString</span></span>|<span data-ttu-id="8d873-134">W pełni kwalifikowanej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="8d873-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="8d873-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8d873-135">ClrInstanceID</span></span>|<span data-ttu-id="8d873-136">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="8d873-136">win:UInt16</span></span>|<span data-ttu-id="8d873-137">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="8d873-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="8d873-138">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="8d873-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="8d873-139">AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8d873-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="8d873-140">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="8d873-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="8d873-141">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8d873-141">Keyword for raising the event</span></span>|<span data-ttu-id="8d873-142">Poziom</span><span class="sxs-lookup"><span data-stu-id="8d873-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="8d873-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="8d873-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="8d873-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="8d873-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="8d873-145">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="8d873-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="8d873-146">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="8d873-146">Event</span></span>|<span data-ttu-id="8d873-147">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8d873-147">Event ID</span></span>|<span data-ttu-id="8d873-148">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="8d873-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="8d873-149">183</span><span class="sxs-lookup"><span data-stu-id="8d873-149">183</span></span>|<span data-ttu-id="8d873-150">Uruchomienie weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="8d873-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="8d873-151">184</span><span class="sxs-lookup"><span data-stu-id="8d873-151">184</span></span>|<span data-ttu-id="8d873-152">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="8d873-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="8d873-153">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8d873-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="8d873-154">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="8d873-154">Field name</span></span>|<span data-ttu-id="8d873-155">Typ danych</span><span class="sxs-lookup"><span data-stu-id="8d873-155">Data type</span></span>|<span data-ttu-id="8d873-156">Opis</span><span class="sxs-lookup"><span data-stu-id="8d873-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="8d873-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="8d873-157">VerificationFlags</span></span>|<span data-ttu-id="8d873-158">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="8d873-158">win:UInt32</span></span>|<span data-ttu-id="8d873-159">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="8d873-159">The verification flags.</span></span>|  
|<span data-ttu-id="8d873-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="8d873-160">ErrorCode</span></span>|<span data-ttu-id="8d873-161">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="8d873-161">win:UInt32</span></span>|<span data-ttu-id="8d873-162">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="8d873-162">The HResult error code.</span></span>|  
|<span data-ttu-id="8d873-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="8d873-163">ModulePath</span></span>|<span data-ttu-id="8d873-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8d873-164">win:UnicodeString</span></span>|<span data-ttu-id="8d873-165">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="8d873-165">The module path.</span></span>|  
|<span data-ttu-id="8d873-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8d873-166">ClrInstanceID</span></span>|<span data-ttu-id="8d873-167">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="8d873-167">win:UInt16</span></span>|<span data-ttu-id="8d873-168">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="8d873-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d873-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d873-169">See also</span></span>

- [<span data-ttu-id="8d873-170">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="8d873-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
