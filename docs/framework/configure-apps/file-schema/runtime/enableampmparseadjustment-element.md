---
title: <EnableAmPmParseAdjustment> Element
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: 8920e51fcaaca5cb78b80a99ea321163c9b5240f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117371"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="90528-102">\<EnableAmPmParseAdjustment> Element</span><span class="sxs-lookup"><span data-stu-id="90528-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="90528-103">Określa, czy metody analizowania dat i godzin używają dopasowanego zestawu reguł do analizowania ciągów dat zawierających dzień, miesiąc, godzinę i oznaczenie AM/PM.</span><span class="sxs-lookup"><span data-stu-id="90528-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="90528-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="90528-104">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90528-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="90528-105">Attributes and Elements</span></span>  
 <span data-ttu-id="90528-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="90528-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90528-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="90528-107">Attributes</span></span>  
  
|<span data-ttu-id="90528-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="90528-108">Attribute</span></span>|<span data-ttu-id="90528-109">Opis</span><span class="sxs-lookup"><span data-stu-id="90528-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="90528-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="90528-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="90528-111">Określa, czy metody analizowania dat i godzin używają skorygowanego zestawu reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.</span><span class="sxs-lookup"><span data-stu-id="90528-111">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="90528-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="90528-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="90528-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="90528-113">Value</span></span>|<span data-ttu-id="90528-114">Opis</span><span class="sxs-lookup"><span data-stu-id="90528-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="90528-115">0</span><span class="sxs-lookup"><span data-stu-id="90528-115">0</span></span>|<span data-ttu-id="90528-116">Metody analizowania dat i godzin nie używają skorygowanych reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.</span><span class="sxs-lookup"><span data-stu-id="90528-116">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="90528-117">1</span><span class="sxs-lookup"><span data-stu-id="90528-117">1</span></span>|<span data-ttu-id="90528-118">Metody analizowania dat i godzin używają skorygowanych reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.</span><span class="sxs-lookup"><span data-stu-id="90528-118">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90528-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="90528-119">Child Elements</span></span>  
 <span data-ttu-id="90528-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="90528-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90528-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="90528-121">Parent Elements</span></span>  
  
|<span data-ttu-id="90528-122">Element</span><span class="sxs-lookup"><span data-stu-id="90528-122">Element</span></span>|<span data-ttu-id="90528-123">Opis</span><span class="sxs-lookup"><span data-stu-id="90528-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="90528-124">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90528-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="90528-125">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="90528-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90528-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90528-126">Remarks</span></span>  
 <span data-ttu-id="90528-127">`<EnableAmPmParseAdjustment>`Element kontroluje, jak następujące metody analizują ciąg daty, który zawiera numeryczny dzień i miesiąc, po którym następuje godzina i oznaczenie AM/PM (na przykład "4/10 6 AM"):</span><span class="sxs-lookup"><span data-stu-id="90528-127">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="90528-128">Nie ma to znaczenia dla innych wzorców.</span><span class="sxs-lookup"><span data-stu-id="90528-128">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="90528-129">`<EnableAmPmParseAdjustment>`Element nie ma wpływu na <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> metody,, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="90528-129">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="90528-130">W przypadku platformy .NET Core i .NET Native dostosowane reguły analizowania AM/PM są domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="90528-130">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="90528-131">Jeśli reguła dopasowania analizy nie jest włączona, Pierwsza cyfra ciągu jest interpretowana jako godzina zegara 12-godzinnego, a pozostała część ciągu z wyjątkiem oznaczenia AM/PM jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="90528-131">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="90528-132">Data i godzina zwrócone przez metodę analizy składa się z bieżącej daty i godziny wyekstrahowanej z ciągu daty.</span><span class="sxs-lookup"><span data-stu-id="90528-132">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="90528-133">Jeśli reguła dopasowywania analizy jest włączona, metoda analizy interpretuje dzień i miesiąc jako należące do bieżącego roku i interpretuje czas jako godzinę zegara 12-godzinnego.</span><span class="sxs-lookup"><span data-stu-id="90528-133">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="90528-134">W poniższej tabeli przedstawiono różnice w wartości, <xref:System.DateTime> gdy <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> Metoda jest używana do analizowania ciągu "" 4/10 6 AM "z `<EnableAmPmParseAdjustment>` `enabled` właściwością elementu ustawioną na wartość" 0 "lub" 1 ".</span><span class="sxs-lookup"><span data-stu-id="90528-134">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="90528-135">Przyjęto założenie, że dzisiejszą datą jest 5 stycznia 2017 i wyświetla datę tak, jakby była sformatowana przy użyciu ciągu formatu "G" określonego kultury.</span><span class="sxs-lookup"><span data-stu-id="90528-135">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="90528-136">Nazwa kultury</span><span class="sxs-lookup"><span data-stu-id="90528-136">Culture name</span></span>|<span data-ttu-id="90528-137">włączone = "0"</span><span class="sxs-lookup"><span data-stu-id="90528-137">enabled="0"</span></span>|<span data-ttu-id="90528-138">włączone = "1"</span><span class="sxs-lookup"><span data-stu-id="90528-138">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="90528-139">pl-PL</span><span class="sxs-lookup"><span data-stu-id="90528-139">en-US</span></span>|<span data-ttu-id="90528-140">1/5/2017 4:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="90528-140">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="90528-141">4/10/2017 6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="90528-141">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="90528-142">en-GB</span><span class="sxs-lookup"><span data-stu-id="90528-142">en-GB</span></span>|<span data-ttu-id="90528-143">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="90528-143">5/1/2017 6:00:00</span></span>|<span data-ttu-id="90528-144">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="90528-144">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90528-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90528-145">See also</span></span>

- [<span data-ttu-id="90528-146">\<runtime>Postaci</span><span class="sxs-lookup"><span data-stu-id="90528-146">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="90528-147">\<configuration>Postaci</span><span class="sxs-lookup"><span data-stu-id="90528-147">\<configuration> Element</span></span>](../configuration-element.md)
