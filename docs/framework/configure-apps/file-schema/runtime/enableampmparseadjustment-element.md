---
title: <EnableAmPmParseAdjustment>, element
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46cf37ee800c05eb7fe12e8491ad3b2130c3a04d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920821"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="e20ee-102">\<EnableAmPmParseAdjustment, element ></span><span class="sxs-lookup"><span data-stu-id="e20ee-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="e20ee-103">Określa, czy metody analizowania dat i godzin używają dopasowanego zestawu reguł do analizowania ciągów dat zawierających dzień, miesiąc, godzinę i oznaczenie AM/PM.</span><span class="sxs-lookup"><span data-stu-id="e20ee-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="e20ee-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e20ee-104">\<configuration></span></span>  
 <span data-ttu-id="e20ee-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="e20ee-105">\<runtime></span></span>  
<span data-ttu-id="e20ee-106">\<EnableAmPmParseAdjustment ></span><span class="sxs-lookup"><span data-stu-id="e20ee-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e20ee-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e20ee-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e20ee-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e20ee-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e20ee-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e20ee-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e20ee-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e20ee-110">Attributes</span></span>  
  
|<span data-ttu-id="e20ee-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e20ee-111">Attribute</span></span>|<span data-ttu-id="e20ee-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e20ee-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e20ee-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="e20ee-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e20ee-114">Określa, czy metody analizowania dat i godzin używają skorygowanego zestawu reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.</span><span class="sxs-lookup"><span data-stu-id="e20ee-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="e20ee-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="e20ee-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e20ee-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="e20ee-116">Value</span></span>|<span data-ttu-id="e20ee-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e20ee-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e20ee-118">0</span><span class="sxs-lookup"><span data-stu-id="e20ee-118">0</span></span>|<span data-ttu-id="e20ee-119">Metody analizowania dat i godzin nie używają skorygowanych reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.</span><span class="sxs-lookup"><span data-stu-id="e20ee-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="e20ee-120">1</span><span class="sxs-lookup"><span data-stu-id="e20ee-120">1</span></span>|<span data-ttu-id="e20ee-121">Metody analizowania dat i godzin używają skorygowanych reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.</span><span class="sxs-lookup"><span data-stu-id="e20ee-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e20ee-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e20ee-122">Child Elements</span></span>  
 <span data-ttu-id="e20ee-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="e20ee-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e20ee-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e20ee-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e20ee-125">Element</span><span class="sxs-lookup"><span data-stu-id="e20ee-125">Element</span></span>|<span data-ttu-id="e20ee-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e20ee-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e20ee-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e20ee-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e20ee-128">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e20ee-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e20ee-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e20ee-129">Remarks</span></span>  
 <span data-ttu-id="e20ee-130">`<EnableAmPmParseAdjustment>` Element kontroluje, jak następujące metody analizują ciąg daty, który zawiera numeryczny dzień i miesiąc, po którym następuje godzina i oznaczenie AM/PM (na przykład "4/10 6 AM"):</span><span class="sxs-lookup"><span data-stu-id="e20ee-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="e20ee-131">Nie ma to znaczenia dla innych wzorców.</span><span class="sxs-lookup"><span data-stu-id="e20ee-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="e20ee-132"><xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> Element nie ma wpływu <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>na metody,, i. `<EnableAmPmParseAdjustment>`</span><span class="sxs-lookup"><span data-stu-id="e20ee-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e20ee-133">W przypadku platformy .NET Core i .NET Native dostosowane reguły analizowania AM/PM są domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="e20ee-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="e20ee-134">Jeśli reguła dopasowania analizy nie jest włączona, Pierwsza cyfra ciągu jest interpretowana jako godzina zegara 12-godzinnego, a pozostała część ciągu z wyjątkiem oznaczenia AM/PM jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="e20ee-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="e20ee-135">Data i godzina zwrócone przez metodę analizy składa się z bieżącej daty i godziny wyekstrahowanej z ciągu daty.</span><span class="sxs-lookup"><span data-stu-id="e20ee-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="e20ee-136">Jeśli reguła dopasowywania analizy jest włączona, metoda analizy interpretuje dzień i miesiąc jako należące do bieżącego roku i interpretuje czas jako godzinę zegara 12-godzinnego.</span><span class="sxs-lookup"><span data-stu-id="e20ee-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="e20ee-137">W poniższej tabeli <xref:System.DateTime> przedstawiono różnice w wartości, <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> gdy metoda jest używana do analizowania ciągu "" `<EnableAmPmParseAdjustment>` 4/10 6 am `enabled` "z właściwością elementu ustawioną na wartość" 0 "lub" 1 ".</span><span class="sxs-lookup"><span data-stu-id="e20ee-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="e20ee-138">Przyjęto założenie, że dzisiejszą datą jest 5 stycznia 2017 i wyświetla datę tak, jakby była sformatowana przy użyciu ciągu formatu "G" określonego kultury.</span><span class="sxs-lookup"><span data-stu-id="e20ee-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="e20ee-139">Nazwa kultury</span><span class="sxs-lookup"><span data-stu-id="e20ee-139">Culture name</span></span>|<span data-ttu-id="e20ee-140">enabled="0"</span><span class="sxs-lookup"><span data-stu-id="e20ee-140">enabled="0"</span></span>|<span data-ttu-id="e20ee-141">enabled="1"</span><span class="sxs-lookup"><span data-stu-id="e20ee-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="e20ee-142">en-US</span><span class="sxs-lookup"><span data-stu-id="e20ee-142">en-US</span></span>|<span data-ttu-id="e20ee-143">1/5/2017 4:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="e20ee-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="e20ee-144">4/10/2017 6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="e20ee-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="e20ee-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="e20ee-145">en-GB</span></span>|<span data-ttu-id="e20ee-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="e20ee-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="e20ee-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="e20ee-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e20ee-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e20ee-148">See also</span></span>

- [<span data-ttu-id="e20ee-149">\<Element > środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e20ee-149">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="e20ee-150">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e20ee-150">\<configuration> Element</span></span>](../configuration-element.md)
