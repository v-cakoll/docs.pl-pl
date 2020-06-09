---
title: Globalizacja i lokalizowanie aplikacji platformy .NET
description: Dowiedz się, jak tworzyć aplikacje gotowe do użycia na całym świecie. Zapoznaj się z globalizacją, przeglądem lokalizacji i lokalizacją platformy .NET.
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
ms.openlocfilehash: a3894b7bf9b8aa013b346c169d21c6db270fe987
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600792"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="cfe5e-104">Globalizacja i lokalizowanie aplikacji platformy .NET</span><span class="sxs-lookup"><span data-stu-id="cfe5e-104">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="cfe5e-105">Tworzenie aplikacji gotowej do używania na świecie, w tym aplikacji, która może być lokalizowana do jednego lub kilku języków, obejmuje trzy kroki: globalizacja, przegląd możliwości zlokalizowania i lokalizacja.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-105">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="cfe5e-106">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="cfe5e-106">Globalization</span></span>](globalization.md)

<span data-ttu-id="cfe5e-107">Ten krok obejmuje projektowanie i programowanie aplikacji neutralnej kulturowo i językowo, która obsługuje zlokalizowane interfejsy użytkownika i dane regionalne dla wszystkich użytkowników.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-107">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="cfe5e-108">Obejmuje to podejmowanie decyzji projektowych i programistycznych, które nie są oparte na założeniach specyficznych dla kultury.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-108">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="cfe5e-109">Aplikacja zglobalizowana nie jest zlokalizowana, ale została zaprojektowana i napisana tak, że jej lokalizacja w jednym lub kilku językach będzie stosunkowo łatwa.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-109">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="cfe5e-110">Sprawdzenie możliwości lokalizacji</span><span class="sxs-lookup"><span data-stu-id="cfe5e-110">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="cfe5e-111">Ten krok obejmuje przegląd kodu i projektu aplikacji w celu upewnienia się, że można go łatwo zlokalizować i zidentyfikować potencjalne przeszkody dla lokalizacji, oraz potwierdzenia, że kod wykonywalny aplikacji jest oddzielony od jej zasobów.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-111">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="cfe5e-112">Jeśli etap globalizacji był skuteczny, przegląd możliwości zlokalizowania potwierdzi wybory dotyczące projektowania i kodowania dokonane podczas globalizacji.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-112">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="cfe5e-113">Na etapie przeglądu możliwości lokalizacji można również zidentyfikować pozostałe problemy, dzięki czemu nie trzeba będzie modyfikować kodu aplikacji na etapie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-113">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="cfe5e-114">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="cfe5e-114">Localization</span></span>](localization.md)

<span data-ttu-id="cfe5e-115">Ten krok obejmuje dostosowywanie aplikacji do określonych kultur lub regionów.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-115">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="cfe5e-116">Jeśli etapy globalizacji i przeglądu możliwości lokalizacji zostały wykonane poprawnie, lokalizacja składa się głównie z tłumaczenia interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-116">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="cfe5e-117">Wykonanie tych trzech kroków ma dwie zalety:</span><span class="sxs-lookup"><span data-stu-id="cfe5e-117">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="cfe5e-118">Uwalnia użytkownika od konieczności przeprojektowywania aplikacji, której konstrukcja przewiduje obsługę jednej kultury, takiej jak Angielski-Stany Zjednoczone, w celu obsługi dodatkowych kultur.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-118">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="cfe5e-119">Skutkuje zlokalizowanymi aplikacjami, które są stabilniejsze i zawierają mniej błędów.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-119">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="cfe5e-120">Platforma .NET zapewnia szeroką pomoc techniczną dla rozwoju aplikacji gotowych do użycia na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-120">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="cfe5e-121">W szczególności wiele elementów członkowskich typu w bibliotece klas .NET ułatwia globalizację przez zwrócenie wartości, które odzwierciedlają konwencje kultury bieżącego użytkownika lub określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-121">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="cfe5e-122">Ponadto platforma .NET obsługuje zestawy satelickie, które ułatwiają proces lokalizowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-122">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="cfe5e-123">Aby uzyskać dodatkowe informacje, zobacz [dokumentację globalizacji](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="cfe5e-123">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cfe5e-124">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cfe5e-124">In this section</span></span>

[<span data-ttu-id="cfe5e-125">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="cfe5e-125">Globalization</span></span>](globalization.md)

<span data-ttu-id="cfe5e-126">Omówienie pierwszego etapu tworzenia aplikacji gotowych do użycia na całym świecie, który obejmuje projektowanie i programowanie aplikacji neutralnej językowo i kulturowo.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-126">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="cfe5e-127">Globalizacja i ICU platformy .NET</span><span class="sxs-lookup"><span data-stu-id="cfe5e-127">.NET globalization and ICU</span></span>](globalization-icu.md)

<span data-ttu-id="cfe5e-128">Opisuje, w jaki sposób globalizacja platformy .NET używa [składników międzynarodowych dla standardu Unicode (ICU)](http://site.icu-project.org/home).</span><span class="sxs-lookup"><span data-stu-id="cfe5e-128">Describes how .NET globalization uses [International Components for Unicode (ICU)](http://site.icu-project.org/home).</span></span>

[<span data-ttu-id="cfe5e-129">Sprawdzenie możliwości lokalizacji</span><span class="sxs-lookup"><span data-stu-id="cfe5e-129">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="cfe5e-130">Omówienie drugiego etapu tworzenia zlokalizowanych aplikacji, który obejmuje określenie potencjalnych przeszkód w procesie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-130">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="cfe5e-131">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="cfe5e-131">Localization</span></span>](localization.md)

<span data-ttu-id="cfe5e-132">Omówienie końcowego etapu tworzenia zlokalizowanych aplikacji, który polega na dostosowywaniu interfejsu użytkownika aplikacji dla określonych regionów lub kultur.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-132">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="cfe5e-133">Niezależne od kultury operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="cfe5e-133">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="cfe5e-134">Opisuje sposób użycia metod i klas .NET, które domyślnie są zależne od kultury w celu uzyskania wyników niewrażliwych na kulturę.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-134">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="cfe5e-135">Najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych do użytku na całym świecie</span><span class="sxs-lookup"><span data-stu-id="cfe5e-135">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="cfe5e-136">Opis najlepszych rozwiązań w zakresie globalizacji, lokalizacji i projektowania gotowych do użycia na całym świecie aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-136">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="cfe5e-137">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="cfe5e-137">Reference</span></span>

- <span data-ttu-id="cfe5e-138"><xref:System.Globalization?displayProperty=nameWithType>obszaru</span><span class="sxs-lookup"><span data-stu-id="cfe5e-138"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="cfe5e-139">Zawiera klasy, które definiują informacje związane z kulturą, w tym język, kraj/region, używane kalendarze, wzorce formatu daty, waluty i liczb oraz kolejność sortowania dla ciągów.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-139">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="cfe5e-140"><xref:System.Resources>obszaru</span><span class="sxs-lookup"><span data-stu-id="cfe5e-140"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="cfe5e-141">Udostępnia klasy służące do tworzenia i używania zasobów oraz wykonywania na nich operacji.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-141">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="cfe5e-142"><xref:System.Text>obszaru</span><span class="sxs-lookup"><span data-stu-id="cfe5e-142"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="cfe5e-143">Zawiera klasy reprezentujące kodowania znaków ASCII, ANSI, Unicode i inne.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-143">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="cfe5e-144">Resgen. exe (Generator plików zasobów)</span><span class="sxs-lookup"><span data-stu-id="cfe5e-144">Resgen.exe (Resource File Generator)</span></span>](../../framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="cfe5e-145">Opis sposobu używania programu Resgen.exe w celu konwertowania plików z rozszerzeniem txt i zasobów opartych na formacie języka XML (resx) na pliki binarne resources środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-145">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="cfe5e-146">Winres. exe (Edytor zasobów Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="cfe5e-146">Winres.exe (Windows Forms Resource Editor)</span></span>](../../framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="cfe5e-147">Opis sposobu używania programu Winres.exe w celu lokalizowania formularzy programu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cfe5e-147">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
