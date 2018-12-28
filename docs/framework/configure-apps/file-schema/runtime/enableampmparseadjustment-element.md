---
title: '&lt;EnableAmPmParseAdjustment&gt; — Element'
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf56a2720ab407d05b8356280913445c15a17020
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611077"
---
# <a name="ltenableampmparseadjustmentgt-element"></a><span data-ttu-id="1105d-102">&lt;EnableAmPmParseAdjustment&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="1105d-102">&lt;EnableAmPmParseAdjustment&gt; Element</span></span>
<span data-ttu-id="1105d-103">Określa, czy data i godzina metod analizowania użyć skorygowany zbiór reguł do analizowania ciągów daty, które zawierają dzień, miesiąc, godzinę i oznaczenie AM/PM.</span><span class="sxs-lookup"><span data-stu-id="1105d-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="1105d-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1105d-104">\<configuration></span></span>  
 <span data-ttu-id="1105d-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="1105d-105">\<runtime></span></span>  
<span data-ttu-id="1105d-106">\<EnableAmPmParseAdjustment ></span><span class="sxs-lookup"><span data-stu-id="1105d-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1105d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1105d-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1105d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1105d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1105d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1105d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1105d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1105d-110">Attributes</span></span>  
  
|<span data-ttu-id="1105d-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1105d-111">Attribute</span></span>|<span data-ttu-id="1105d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1105d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1105d-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1105d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1105d-114">Określa, czy data i godzina metod analizowania użyć skorygowany zbiór reguł do analizowania ciągów daty, które zawierają tylko dnia, miesiąca, godzinę i oznaczenie AM/PM.</span><span class="sxs-lookup"><span data-stu-id="1105d-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="1105d-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="1105d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1105d-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="1105d-116">Value</span></span>|<span data-ttu-id="1105d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1105d-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1105d-118">0</span><span class="sxs-lookup"><span data-stu-id="1105d-118">0</span></span>|<span data-ttu-id="1105d-119">Data i godzina metod analizowania reguły nie są używane skorygowany do analizowania ciągów daty, które zawierają tylko dnia, miesiąca, godzinę i oznaczenie AM/PM.</span><span class="sxs-lookup"><span data-stu-id="1105d-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="1105d-120">1</span><span class="sxs-lookup"><span data-stu-id="1105d-120">1</span></span>|<span data-ttu-id="1105d-121">Data i godzina metod analizowania na użytek reguły skorygowany analizowanie ciągów daty, które zawierają tylko dnia, miesiąca, godzinę i oznaczenie AM/PM.</span><span class="sxs-lookup"><span data-stu-id="1105d-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1105d-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1105d-122">Child Elements</span></span>  
 <span data-ttu-id="1105d-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="1105d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1105d-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1105d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1105d-125">Element</span><span class="sxs-lookup"><span data-stu-id="1105d-125">Element</span></span>|<span data-ttu-id="1105d-126">Opis</span><span class="sxs-lookup"><span data-stu-id="1105d-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1105d-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1105d-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1105d-128">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1105d-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1105d-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1105d-129">Remarks</span></span>  
 <span data-ttu-id="1105d-130">`<EnableAmPmParseAdjustment>` Element kontroluje sposób przeanalizować ciąg daty, która zawiera liczbową wartość dnia i miesiąca, a następnie godzinę i oznaczenie AM/PM (na przykład "6 4/10 AM") w następujących metod:</span><span class="sxs-lookup"><span data-stu-id="1105d-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="1105d-131">Wpływają na nie inne wzorce.</span><span class="sxs-lookup"><span data-stu-id="1105d-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="1105d-132">`<EnableAmPmParseAdjustment>` Element nie ma wpływu <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, i <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1105d-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1105d-133">.NET Core i .NET Native skorygowany AM/PM reguły analizy składni są domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="1105d-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="1105d-134">Jeśli nie włączono analizy reguła korekty, pierwszą cyfrą ciąg jest interpretowany jako godzinę 12-godzinnym, a pozostała część ciągu, oprócz oznaczenia AM/PM jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="1105d-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="1105d-135">Data i godzina zwracany przez metodę analizowania składa się z bieżącą datę i godzinę dnia, o której wyodrębnione z ciągu daty.</span><span class="sxs-lookup"><span data-stu-id="1105d-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="1105d-136">Po włączeniu analizy reguła korekty analizy metody interpretacji dzień i miesiąc jako należące do bieżącego roku i interpretować czasie, co godzinę 12-godzinnym.</span><span class="sxs-lookup"><span data-stu-id="1105d-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="1105d-137">W poniższej tabeli przedstawiono różnice w <xref:System.DateTime> wartość przy <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> metoda służy do analizowania ciągu "" 4/10 6 AM"za pomocą `<EnableAmPmParseAdjustment>` elementu `enabled` właściwość ustawioną na"0"lub"1".</span><span class="sxs-lookup"><span data-stu-id="1105d-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="1105d-138">Przyjęto założenie, że dzisiaj jest 5 stycznia 2017 r. i wyświetla datę tak, jakby jest formatowana przy użyciu ciągu formatu "G" określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="1105d-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="1105d-139">Nazwa kultury</span><span class="sxs-lookup"><span data-stu-id="1105d-139">Culture name</span></span>|<span data-ttu-id="1105d-140">włączone = "0"</span><span class="sxs-lookup"><span data-stu-id="1105d-140">enabled="0"</span></span>|<span data-ttu-id="1105d-141">włączone = "1"</span><span class="sxs-lookup"><span data-stu-id="1105d-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="1105d-142">en-US</span><span class="sxs-lookup"><span data-stu-id="1105d-142">en-US</span></span>|<span data-ttu-id="1105d-143">2017-1-5 4:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="1105d-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="1105d-144">2017-10/4 6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="1105d-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="1105d-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="1105d-145">en-GB</span></span>|<span data-ttu-id="1105d-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="1105d-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="1105d-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="1105d-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1105d-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1105d-148">See Also</span></span>  
- [<span data-ttu-id="1105d-149">\<środowisko uruchomieniowe > Element</span><span class="sxs-lookup"><span data-stu-id="1105d-149">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
- [<span data-ttu-id="1105d-150">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="1105d-150">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
