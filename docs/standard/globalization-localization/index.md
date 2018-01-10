---
title: Globalizacja i lokalizacja aplikacji .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- international applications [.NET Framework]
- globalization [.NET Framework], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET Framework], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 63f0e001280773c55f18f0604ca93986acbb9674
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="globalizing-and-localizing-net-framework-applications"></a><span data-ttu-id="27bce-102">Globalizacja i lokalizacja aplikacji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="27bce-102">Globalizing and Localizing .NET Framework Applications</span></span>
<span data-ttu-id="27bce-103">Tworzenie [aplikacji gotowe](http://msdn.microsoft.com/goglobal/bb978433.aspx), w tym aplikacji, która może być lokalizowany do co najmniej jednego języka, obejmuje trzy kroki: sprawdzenie, lokalizacja i globalizacja.</span><span class="sxs-lookup"><span data-stu-id="27bce-103">Developing a [world-ready application](http://msdn.microsoft.com/goglobal/bb978433.aspx), including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>  
  
 [<span data-ttu-id="27bce-104">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="27bce-104">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 <span data-ttu-id="27bce-105">Ten krok obejmuje projektowanie i programowanie aplikacji neutralnej kulturowo i językowo, która obsługuje zlokalizowane interfejsy użytkownika i dane regionalne dla wszystkich użytkowników.</span><span class="sxs-lookup"><span data-stu-id="27bce-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="27bce-106">Obejmuje to podejmowanie decyzji projektowych i programistycznych, które nie są oparte na założeniach specyficznych dla kultury.</span><span class="sxs-lookup"><span data-stu-id="27bce-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="27bce-107">Aplikacja zglobalizowana nie jest zlokalizowana, ale została zaprojektowana i napisana tak, że jej lokalizacja w jednym lub kilku językach będzie stosunkowo łatwa.</span><span class="sxs-lookup"><span data-stu-id="27bce-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>  
  
 [<span data-ttu-id="27bce-108">Sprawdzenie możliwości lokalizacji</span><span class="sxs-lookup"><span data-stu-id="27bce-108">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 <span data-ttu-id="27bce-109">Ten krok obejmuje przegląd kodu i projektu aplikacji w celu upewnienia się, że można go łatwo zlokalizować i zidentyfikować potencjalne przeszkody dla lokalizacji, oraz potwierdzenia, że kod wykonywalny aplikacji jest oddzielony od jej zasobów.</span><span class="sxs-lookup"><span data-stu-id="27bce-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="27bce-110">Jeśli etap globalizacji był skuteczny, przegląd możliwości zlokalizowania potwierdzi wybory dotyczące projektowania i kodowania dokonane podczas globalizacji.</span><span class="sxs-lookup"><span data-stu-id="27bce-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="27bce-111">Na etapie przeglądu możliwości lokalizacji można również zidentyfikować pozostałe problemy, dzięki czemu nie trzeba będzie modyfikować kodu aplikacji na etapie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="27bce-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>  
  
 [<span data-ttu-id="27bce-112">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="27bce-112">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="27bce-113">Ten krok obejmuje dostosowywanie aplikacji do określonych kultur lub regionów.</span><span class="sxs-lookup"><span data-stu-id="27bce-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="27bce-114">Jeśli etapy globalizacji i przeglądu możliwości lokalizacji zostały wykonane poprawnie, lokalizacja składa się głównie z tłumaczenia interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="27bce-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>  
  
 <span data-ttu-id="27bce-115">Wykonanie tych trzech kroków ma dwie zalety:</span><span class="sxs-lookup"><span data-stu-id="27bce-115">Following these three steps provides two advantages:</span></span>  
  
-   <span data-ttu-id="27bce-116">Go zwalnia z konieczności zakresie wyposażenia aplikacji, która jest przeznaczona do obsługi pojedynczego kultury, takie jak stany USA Angielski, do obsługi dodatkowych kultur.</span><span class="sxs-lookup"><span data-stu-id="27bce-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>  
  
-   <span data-ttu-id="27bce-117">Skutkuje zlokalizowanymi aplikacjami, które są stabilniejsze i zawierają mniej błędów.</span><span class="sxs-lookup"><span data-stu-id="27bce-117">It results in localized applications that are more stable and have fewer bugs.</span></span>  
  
 <span data-ttu-id="27bce-118">Program .NET Framework oferuje zaawansowaną obsługę dla rozwoju aplikacji gotowych do użycia na całym świecie i aplikacji zlokalizowanych.</span><span class="sxs-lookup"><span data-stu-id="27bce-118">The .NET Framework provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="27bce-119">W szczególności wiele składowych typów w bibliotece klas programu .NET Framework wspiera globalizację, zwracając wartości, które odzwierciedlają konwencje kultury bieżącego użytkownika lub określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="27bce-119">In particular, many type members in the .NET Framework class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="27bce-120">Program .NET Framework obsługuje także zestawy satelickie, które ułatwiają proces lokalizowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27bce-120">Also, the .NET Framework supports satellite assemblies, which facilitate the process of localizing an application.</span></span>  
  
 <span data-ttu-id="27bce-121">Aby uzyskać dodatkowe informacje, zobacz [dokumentacji globalizacji](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="27bce-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27bce-122">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="27bce-122">In This Section</span></span>  
 [<span data-ttu-id="27bce-123">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="27bce-123">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 <span data-ttu-id="27bce-124">Omówienie pierwszego etapu tworzenia aplikacji gotowych do użycia na całym świecie, który obejmuje projektowanie i programowanie aplikacji neutralnej językowo i kulturowo.</span><span class="sxs-lookup"><span data-stu-id="27bce-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>  
  
 [<span data-ttu-id="27bce-125">Sprawdzenie możliwości lokalizacji</span><span class="sxs-lookup"><span data-stu-id="27bce-125">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 <span data-ttu-id="27bce-126">Omówienie drugiego etapu tworzenia zlokalizowanych aplikacji, który obejmuje określenie potencjalnych przeszkód w procesie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="27bce-126">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>  
  
 [<span data-ttu-id="27bce-127">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="27bce-127">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="27bce-128">Omówienie końcowego etapu tworzenia zlokalizowanych aplikacji, który polega na dostosowywaniu interfejsu użytkownika aplikacji dla określonych regionów lub kultur.</span><span class="sxs-lookup"><span data-stu-id="27bce-128">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>  
  
 [<span data-ttu-id="27bce-129">Niezależne od kultury operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="27bce-129">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="27bce-130">Opis sposobu użycia metod i klas programu .NET Framework, które domyślnie są zależne od kultury w celu uzyskania wyników niezależnych od kultury.</span><span class="sxs-lookup"><span data-stu-id="27bce-130">Describes how to use .NET Framework methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>  
  
 [<span data-ttu-id="27bce-131">Najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych do wydania</span><span class="sxs-lookup"><span data-stu-id="27bce-131">Best Practices for Developing World-Ready Applications</span></span>](../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)  
 <span data-ttu-id="27bce-132">Opis najlepszych rozwiązań w zakresie globalizacji, lokalizacji i projektowania gotowych do użycia na całym świecie aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="27bce-132">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="27bce-133">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="27bce-133">Reference</span></span>  
 <span data-ttu-id="27bce-134"><xref:System.Globalization?displayProperty=nameWithType>przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="27bce-134"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>  
 <span data-ttu-id="27bce-135">Zawiera klasy, które definiują informacje związane z kulturą, w tym język, kraj/region, używane kalendarze, wzorce formatu daty, waluty i liczb oraz kolejność sortowania dla ciągów.</span><span class="sxs-lookup"><span data-stu-id="27bce-135">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>  
  
 <span data-ttu-id="27bce-136"><xref:System.Resources>przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="27bce-136"><xref:System.Resources> namespace</span></span>  
 <span data-ttu-id="27bce-137">Udostępnia klasy służące do tworzenia i używania zasobów oraz wykonywania na nich operacji.</span><span class="sxs-lookup"><span data-stu-id="27bce-137">Provides classes for creating, manipulating, and using resources.</span></span>  
  
 <span data-ttu-id="27bce-138"><xref:System.Text>przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="27bce-138"><xref:System.Text> namespace</span></span>  
 <span data-ttu-id="27bce-139">Zawiera klasy reprezentujące kodowania znaków ASCII, ANSI, Unicode i inne.</span><span class="sxs-lookup"><span data-stu-id="27bce-139">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>  
  
 [<span data-ttu-id="27bce-140">Resgen.exe (generator pliku zasobów)</span><span class="sxs-lookup"><span data-stu-id="27bce-140">Resgen.exe (Resource File Generator)</span></span>](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 <span data-ttu-id="27bce-141">Opis sposobu używania programu Resgen.exe w celu konwertowania plików z rozszerzeniem txt i zasobów opartych na formacie języka XML (resx) na pliki binarne resources środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="27bce-141">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>  
  
 [<span data-ttu-id="27bce-142">Winres.exe (Edytor zasobów formularzy Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="27bce-142">Winres.exe (Windows Forms Resource Editor)</span></span>](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 <span data-ttu-id="27bce-143">Opis sposobu używania programu Winres.exe w celu lokalizowania formularzy programu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="27bce-143">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
