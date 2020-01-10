---
title: Zabezpieczenia zdarzeń ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: c443bda8cdc2c6b32760e9dcba8b81a29d81660b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715939"
---
# <a name="security-etw-events"></a><span data-ttu-id="fdd22-102">Zabezpieczenia zdarzeń ETW</span><span class="sxs-lookup"><span data-stu-id="fdd22-102">Security ETW Events</span></span>

<span data-ttu-id="fdd22-103">Zdarzenia zabezpieczeń są wywoływane podczas weryfikacji silnej nazwy i weryfikacji kodu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="fdd22-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="fdd22-104">Zdarzenia StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="fdd22-104">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="fdd22-105">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="fdd22-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="fdd22-106">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="fdd22-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="fdd22-107">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fdd22-107">Keyword for raising the event</span></span>|<span data-ttu-id="fdd22-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="fdd22-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fdd22-109">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="fdd22-109">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="fdd22-110">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="fdd22-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="fdd22-111">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="fdd22-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fdd22-112">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="fdd22-112">Event</span></span>|<span data-ttu-id="fdd22-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fdd22-113">Event ID</span></span>|<span data-ttu-id="fdd22-114">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="fdd22-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="fdd22-115">181</span><span class="sxs-lookup"><span data-stu-id="fdd22-115">181</span></span>|<span data-ttu-id="fdd22-116">Rozpoczęcie weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fdd22-116">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="fdd22-117">182</span><span class="sxs-lookup"><span data-stu-id="fdd22-117">182</span></span>|<span data-ttu-id="fdd22-118">Koniec weryfikacji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fdd22-118">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="fdd22-119">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fdd22-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fdd22-120">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="fdd22-120">Field name</span></span>|<span data-ttu-id="fdd22-121">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fdd22-121">Data type</span></span>|<span data-ttu-id="fdd22-122">Opis</span><span class="sxs-lookup"><span data-stu-id="fdd22-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fdd22-123">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="fdd22-123">VerificationFlags</span></span>|<span data-ttu-id="fdd22-124">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fdd22-124">win:UInt32</span></span>|<span data-ttu-id="fdd22-125">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="fdd22-125">The verification flags.</span></span>|  
|<span data-ttu-id="fdd22-126">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="fdd22-126">ErrorCode</span></span>|<span data-ttu-id="fdd22-127">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fdd22-127">win:UInt32</span></span>|<span data-ttu-id="fdd22-128">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="fdd22-128">The HResult error code.</span></span>|  
|<span data-ttu-id="fdd22-129">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="fdd22-129">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="fdd22-130">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="fdd22-130">win:UnicodeString</span></span>|<span data-ttu-id="fdd22-131">W pełni kwalifikowana nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="fdd22-131">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="fdd22-132">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fdd22-132">ClrInstanceID</span></span>|<span data-ttu-id="fdd22-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fdd22-133">win:UInt16</span></span>|<span data-ttu-id="fdd22-134">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fdd22-134">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="fdd22-135">Zdarzenia AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="fdd22-135">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="fdd22-136">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="fdd22-136">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fdd22-137">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fdd22-137">Keyword for raising the event</span></span>|<span data-ttu-id="fdd22-138">Poziom</span><span class="sxs-lookup"><span data-stu-id="fdd22-138">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fdd22-139">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="fdd22-139">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="fdd22-140">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="fdd22-140">Informational(4)</span></span>|  
  
 <span data-ttu-id="fdd22-141">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="fdd22-141">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fdd22-142">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="fdd22-142">Event</span></span>|<span data-ttu-id="fdd22-143">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fdd22-143">Event ID</span></span>|<span data-ttu-id="fdd22-144">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="fdd22-144">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="fdd22-145">183</span><span class="sxs-lookup"><span data-stu-id="fdd22-145">183</span></span>|<span data-ttu-id="fdd22-146">Rozpoczęcie weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="fdd22-146">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="fdd22-147">184</span><span class="sxs-lookup"><span data-stu-id="fdd22-147">184</span></span>|<span data-ttu-id="fdd22-148">Koniec weryfikacji Authenticode.</span><span class="sxs-lookup"><span data-stu-id="fdd22-148">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="fdd22-149">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fdd22-149">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fdd22-150">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="fdd22-150">Field name</span></span>|<span data-ttu-id="fdd22-151">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fdd22-151">Data type</span></span>|<span data-ttu-id="fdd22-152">Opis</span><span class="sxs-lookup"><span data-stu-id="fdd22-152">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fdd22-153">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="fdd22-153">VerificationFlags</span></span>|<span data-ttu-id="fdd22-154">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fdd22-154">win:UInt32</span></span>|<span data-ttu-id="fdd22-155">Flagi weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="fdd22-155">The verification flags.</span></span>|  
|<span data-ttu-id="fdd22-156">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="fdd22-156">ErrorCode</span></span>|<span data-ttu-id="fdd22-157">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fdd22-157">win:UInt32</span></span>|<span data-ttu-id="fdd22-158">Kod błędu HResult.</span><span class="sxs-lookup"><span data-stu-id="fdd22-158">The HResult error code.</span></span>|  
|<span data-ttu-id="fdd22-159">ModulePath</span><span class="sxs-lookup"><span data-stu-id="fdd22-159">ModulePath</span></span>|<span data-ttu-id="fdd22-160">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="fdd22-160">win:UnicodeString</span></span>|<span data-ttu-id="fdd22-161">Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="fdd22-161">The module path.</span></span>|  
|<span data-ttu-id="fdd22-162">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fdd22-162">ClrInstanceID</span></span>|<span data-ttu-id="fdd22-163">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fdd22-163">win:UInt16</span></span>|<span data-ttu-id="fdd22-164">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fdd22-164">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdd22-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdd22-165">See also</span></span>

- [<span data-ttu-id="fdd22-166">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="fdd22-166">CLR ETW Events</span></span>](clr-etw-events.md)
