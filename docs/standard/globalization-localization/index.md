---
title: Globalizacja i lokalizacja aplikacji .NET
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31f975b45ee854c73e6d502ece69bee24a7fcc3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683135"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="2613b-102">Globalizacja i lokalizacja aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="2613b-102">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="2613b-103">Opracowywanie aplikacji gotowej dla całego świata, w tym aplikacji, która może być lokalizowana w jednym lub kilku językach, obejmuje trzy kroki: globalizacja, przegląd możliwości lokalizacji i lokalizacja.</span><span class="sxs-lookup"><span data-stu-id="2613b-103">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="2613b-104">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="2613b-104">Globalization</span></span>](globalization.md)

<span data-ttu-id="2613b-105">Ten krok obejmuje projektowanie i programowanie aplikacji neutralnej kulturowo i językowo, która obsługuje zlokalizowane interfejsy użytkownika i dane regionalne dla wszystkich użytkowników.</span><span class="sxs-lookup"><span data-stu-id="2613b-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="2613b-106">Obejmuje to podejmowanie decyzji projektowych i programistycznych, które nie są oparte na założeniach specyficznych dla kultury.</span><span class="sxs-lookup"><span data-stu-id="2613b-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="2613b-107">Aplikacja zglobalizowana nie jest zlokalizowana, ale została zaprojektowana i napisana tak, że jej lokalizacja w jednym lub kilku językach będzie stosunkowo łatwa.</span><span class="sxs-lookup"><span data-stu-id="2613b-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="2613b-108">Sprawdzenie możliwości lokalizacji</span><span class="sxs-lookup"><span data-stu-id="2613b-108">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="2613b-109">Ten krok obejmuje przegląd kodu i projektu aplikacji w celu upewnienia się, że można go łatwo zlokalizować i zidentyfikować potencjalne przeszkody dla lokalizacji, oraz potwierdzenia, że kod wykonywalny aplikacji jest oddzielony od jej zasobów.</span><span class="sxs-lookup"><span data-stu-id="2613b-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="2613b-110">Jeśli etap globalizacji był skuteczny, przegląd możliwości zlokalizowania potwierdzi wybory dotyczące projektowania i kodowania dokonane podczas globalizacji.</span><span class="sxs-lookup"><span data-stu-id="2613b-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="2613b-111">Na etapie przeglądu możliwości lokalizacji można również zidentyfikować pozostałe problemy, dzięki czemu nie trzeba będzie modyfikować kodu aplikacji na etapie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="2613b-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="2613b-112">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="2613b-112">Localization</span></span>](localization.md)

<span data-ttu-id="2613b-113">Ten krok obejmuje dostosowywanie aplikacji do określonych kultur lub regionów.</span><span class="sxs-lookup"><span data-stu-id="2613b-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="2613b-114">Jeśli etapy globalizacji i przeglądu możliwości lokalizacji zostały wykonane poprawnie, lokalizacja składa się głównie z tłumaczenia interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2613b-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="2613b-115">Wykonanie tych trzech kroków ma dwie zalety:</span><span class="sxs-lookup"><span data-stu-id="2613b-115">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="2613b-116">Uwalnia użytkownika od konieczności przeprojektować aplikację, która umożliwia obsługę jednej kultury, takie jak Stany Zjednoczone W języku angielskim, do obsługi dodatkowych kultur.</span><span class="sxs-lookup"><span data-stu-id="2613b-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="2613b-117">Skutkuje zlokalizowanymi aplikacjami, które są stabilniejsze i zawierają mniej błędów.</span><span class="sxs-lookup"><span data-stu-id="2613b-117">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="2613b-118">.NET oferuje zaawansowaną obsługę dla opracowywania aplikacji gotowej dla całego świata i zlokalizowanych.</span><span class="sxs-lookup"><span data-stu-id="2613b-118">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="2613b-119">W szczególności wiele składowych typów w .NET klasy biblioteki wspiera globalizację, zwracając wartości, które odzwierciedlają konwencje kultury bieżącego użytkownika lub określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="2613b-119">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="2613b-120">.NET obsługuje także zestawy satelickie, które ułatwiają proces lokalizowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2613b-120">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="2613b-121">Aby uzyskać więcej informacji, zobacz [dokumentacji globalizacji](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="2613b-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2613b-122">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2613b-122">In this section</span></span>

[<span data-ttu-id="2613b-123">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="2613b-123">Globalization</span></span>](globalization.md)

<span data-ttu-id="2613b-124">Omówienie pierwszego etapu tworzenia aplikacji gotowych do użycia na całym świecie, który obejmuje projektowanie i programowanie aplikacji neutralnej językowo i kulturowo.</span><span class="sxs-lookup"><span data-stu-id="2613b-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="2613b-125">Sprawdzenie możliwości lokalizacji</span><span class="sxs-lookup"><span data-stu-id="2613b-125">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="2613b-126">Omówienie drugiego etapu tworzenia zlokalizowanych aplikacji, który obejmuje określenie potencjalnych przeszkód w procesie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="2613b-126">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="2613b-127">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="2613b-127">Localization</span></span>](localization.md)

<span data-ttu-id="2613b-128">Omówienie końcowego etapu tworzenia zlokalizowanych aplikacji, który polega na dostosowywaniu interfejsu użytkownika aplikacji dla określonych regionów lub kultur.</span><span class="sxs-lookup"><span data-stu-id="2613b-128">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="2613b-129">Operacje na ciągach niezależnych od kultury</span><span class="sxs-lookup"><span data-stu-id="2613b-129">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="2613b-130">W tym artykule opisano sposób użycia metod .NET i klas, które są zależne od kultury domyślnie w celu uzyskania wyników niezależnych od kultury.</span><span class="sxs-lookup"><span data-stu-id="2613b-130">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="2613b-131">Najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych</span><span class="sxs-lookup"><span data-stu-id="2613b-131">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="2613b-132">Opis najlepszych rozwiązań w zakresie globalizacji, lokalizacji i projektowania gotowych do użycia na całym świecie aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2613b-132">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="2613b-133">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="2613b-133">Reference</span></span>

- <span data-ttu-id="2613b-134"><xref:System.Globalization?displayProperty=nameWithType> Namespace</span><span class="sxs-lookup"><span data-stu-id="2613b-134"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="2613b-135">Zawiera klasy, które definiują informacje związane z kulturą, w tym język, kraj/region, używane kalendarze, wzorce formatu daty, waluty i liczb oraz kolejność sortowania dla ciągów.</span><span class="sxs-lookup"><span data-stu-id="2613b-135">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="2613b-136"><xref:System.Resources> Namespace</span><span class="sxs-lookup"><span data-stu-id="2613b-136"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="2613b-137">Udostępnia klasy służące do tworzenia i używania zasobów oraz wykonywania na nich operacji.</span><span class="sxs-lookup"><span data-stu-id="2613b-137">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="2613b-138"><xref:System.Text> Namespace</span><span class="sxs-lookup"><span data-stu-id="2613b-138"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="2613b-139">Zawiera klasy reprezentujące kodowania znaków ASCII, ANSI, Unicode i inne.</span><span class="sxs-lookup"><span data-stu-id="2613b-139">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="2613b-140">Resgen.exe (generator pliku zasobów)</span><span class="sxs-lookup"><span data-stu-id="2613b-140">Resgen.exe (Resource File Generator)</span></span>](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="2613b-141">Opis sposobu używania programu Resgen.exe w celu konwertowania plików z rozszerzeniem txt i zasobów opartych na formacie języka XML (resx) na pliki binarne resources środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="2613b-141">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="2613b-142">Winres.exe (Edytor zasobów formularzy Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2613b-142">Winres.exe (Windows Forms Resource Editor)</span></span>](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="2613b-143">Opis sposobu używania programu Winres.exe w celu lokalizowania formularzy programu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2613b-143">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
