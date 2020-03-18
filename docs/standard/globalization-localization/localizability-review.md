---
title: Sprawdzenie możliwości lokalizacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
ms.openlocfilehash: b286bdd2c5d7b03a0a2b5f94478e252da6cd0ae2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120860"
---
# <a name="localizability-review"></a><span data-ttu-id="1437f-102">Sprawdzenie możliwości lokalizacji</span><span class="sxs-lookup"><span data-stu-id="1437f-102">Localizability review</span></span>

<span data-ttu-id="1437f-103">Przegląd lokalizacji jest pośrednim krokiem w rozwoju aplikacji gotowej na świat.</span><span class="sxs-lookup"><span data-stu-id="1437f-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="1437f-104">Sprawdza, czy zglobalizowana aplikacja jest gotowa do lokalizacji i identyfikuje dowolny kod lub wszelkie aspekty interfejsu użytkownika, które wymagają specjalnej obsługi.</span><span class="sxs-lookup"><span data-stu-id="1437f-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="1437f-105">Ten krok pomaga również upewnić się, że proces lokalizacji nie wprowadzi żadnych wad funkcjonalnych do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1437f-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="1437f-106">Po usunięciu wszystkich problemów zgłoszonych przez przegląd localizability, aplikacja jest gotowa do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="1437f-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="1437f-107">Jeśli przegląd możliwości lokalizowania jest dokładny, nie należy modyfikować żadnego kodu źródłowego podczas procesu lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="1437f-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>

<span data-ttu-id="1437f-108">Przegląd lokalizacji składa się z następujących trzech kontroli:</span><span class="sxs-lookup"><span data-stu-id="1437f-108">The localizability review consists of the following three checks:</span></span>

- [<span data-ttu-id="1437f-109">Czy zalecenia dotyczące globalizacji są wdrażane?</span><span class="sxs-lookup"><span data-stu-id="1437f-109">Are the globalization recommendations implemented?</span></span>](#global)

- [<span data-ttu-id="1437f-110">Czy funkcje zależne od kultury są obsługiwane poprawnie?</span><span class="sxs-lookup"><span data-stu-id="1437f-110">Are culture-sensitive features handled correctly?</span></span>](#culture)

- [<span data-ttu-id="1437f-111">Czy przetestowałeś swoją aplikację na międzynarodowych danych?</span><span class="sxs-lookup"><span data-stu-id="1437f-111">Have you tested your application with international data?</span></span>](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a><span data-ttu-id="1437f-112">Wdrażanie zaleceń dotyczących globalizacji</span><span class="sxs-lookup"><span data-stu-id="1437f-112">Implement globalization recommendations</span></span>

<span data-ttu-id="1437f-113">Jeśli zaprojektowałeś i opracowałeś aplikację z myślą o lokalizacji, a jeśli zastosowałeś się do zaleceń omówionych w artykule [Globalizacja,](../../../docs/standard/globalization-localization/globalization.md) przegląd lokalizacji będzie w dużej mierze przepustką zapewniającą jakość.</span><span class="sxs-lookup"><span data-stu-id="1437f-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="1437f-114">W przeciwnym razie na tym etapie należy przejrzeć i zaimplementować zalecenia dotyczące [globalizacji](../../../docs/standard/globalization-localization/globalization.md) i naprawić błędy w kodzie źródłowym, które uniemożliwiają lokalizację.</span><span class="sxs-lookup"><span data-stu-id="1437f-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md) and fix the errors in source code that prevent localization.</span></span>

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a><span data-ttu-id="1437f-115">Obsługa funkcji wrażliwych na kulturę</span><span class="sxs-lookup"><span data-stu-id="1437f-115">Handle culture-sensitive features</span></span>

<span data-ttu-id="1437f-116">.NET nie zapewnia obsługę programową w wielu obszarach, które różnią się znacznie w zależności od kultury.</span><span class="sxs-lookup"><span data-stu-id="1437f-116">.NET does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="1437f-117">W większości przypadków musisz napisać kod niestandardowy, aby obsłużyć obszary funkcji, takie jak:</span><span class="sxs-lookup"><span data-stu-id="1437f-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>

- <span data-ttu-id="1437f-118">Adresy</span><span class="sxs-lookup"><span data-stu-id="1437f-118">Addresses</span></span>

- <span data-ttu-id="1437f-119">Numery telefonów</span><span class="sxs-lookup"><span data-stu-id="1437f-119">Telephone numbers</span></span>

- <span data-ttu-id="1437f-120">Rozmiary papieru</span><span class="sxs-lookup"><span data-stu-id="1437f-120">Paper sizes</span></span>

- <span data-ttu-id="1437f-121">Jednostki miary stosowane do długości, wag, powierzchni, objętości i temperatur</span><span class="sxs-lookup"><span data-stu-id="1437f-121">Units of measure used for lengths, weights, area, volume, and temperatures</span></span>

   <span data-ttu-id="1437f-122">Mimo że .NET nie oferuje wbudowanej obsługi konwersji między jednostkami <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> miary, można użyć właściwości, aby określić, czy dany kraj lub region używa systemu metryk, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1437f-122">Although .NET does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a><span data-ttu-id="1437f-123">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="1437f-123">Test your application</span></span>

<span data-ttu-id="1437f-124">Przed zlokalizowaniem aplikacji należy przetestować ją przy użyciu danych międzynarodowych w międzynarodowych wersjach systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="1437f-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="1437f-125">Chociaż większość interfejsu użytkownika nie zostanie zlokalizowana w tym momencie, będzie można wykryć problemy, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="1437f-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>

- <span data-ttu-id="1437f-126">Serializowane dane, które nie deserialize poprawnie w wersjach systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="1437f-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>

- <span data-ttu-id="1437f-127">Dane liczbowe, które nie odzwierciedlają konwencji bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="1437f-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="1437f-128">Na przykład liczby mogą być wyświetlane z niedokładnymi separatorami grup, separatorami dziesiętnymi lub symbolami walut.</span><span class="sxs-lookup"><span data-stu-id="1437f-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>

- <span data-ttu-id="1437f-129">Dane daty i godziny, które nie odzwierciedlają konwencji bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="1437f-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="1437f-130">Na przykład liczby reprezentujące miesiąc i dzień mogą pojawić się w niewłaściwej kolejności, separatory dat mogą być niepoprawne lub informacje o strefie czasowej mogą być nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="1437f-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>

- <span data-ttu-id="1437f-131">Zasoby, których nie można odnaleźć, ponieważ nie zidentyfikowano kultury domyślnej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1437f-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>

- <span data-ttu-id="1437f-132">Ciągi, które są wyświetlane w nietypowej kolejności dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="1437f-132">Strings that are displayed in an unusual order for the specific culture.</span></span>

- <span data-ttu-id="1437f-133">Porównania ciągów lub porównania równości, które zwracają nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="1437f-133">String comparisons or comparisons for equality that return unexpected results.</span></span>

<span data-ttu-id="1437f-134">Jeśli podczas opracowywania aplikacji zapoznasz się z zaleceniami dotyczącymi globalizacji, poprawnie obsługiwałeś funkcje zależne od kultury oraz identyfikowano i rozwiązywano problemy z lokalizacją, które pojawiły się podczas testowania, można przejść do następnego [kroku, Lokalizacja](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="1437f-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1437f-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1437f-135">See also</span></span>

- [<span data-ttu-id="1437f-136">Globalizacja i lokalizacja</span><span class="sxs-lookup"><span data-stu-id="1437f-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="1437f-137">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="1437f-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)
- [<span data-ttu-id="1437f-138">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="1437f-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="1437f-139">Zasoby w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="1437f-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
