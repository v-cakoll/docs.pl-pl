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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b19bc78f44781923df6873ccc9720f4605731976
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46477864"
---
# <a name="localizability-review"></a><span data-ttu-id="2df28-102">Sprawdzenie możliwości lokalizacji</span><span class="sxs-lookup"><span data-stu-id="2df28-102">Localizability Review</span></span>
<span data-ttu-id="2df28-103">Przegląd możliwości zlokalizowania jest etap pośredni, w trakcie opracowywania aplikacji gotowej dla całego świata.</span><span class="sxs-lookup"><span data-stu-id="2df28-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="2df28-104">Sprawdza, czy uniwersalnych aplikacji jest gotowy do lokalizacji i identyfikuje każdy kod lub jakiekolwiek aspekty interfejsu użytkownika, które wymagają specjalnej obsługi.</span><span class="sxs-lookup"><span data-stu-id="2df28-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="2df28-105">Ten krok umożliwia również upewnić się, że proces lokalizacji nie wprowadza żadnych defektów funkcjonalnych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2df28-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="2df28-106">Gdy rozwiązano wszystkie problemy zgłoszone przez sprawdzenie, aplikacja jest gotowa do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="2df28-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="2df28-107">W przypadku dokładne sprawdzenie, nie trzeba zmodyfikować każdy kod źródłowy w procesie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="2df28-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="2df28-108">Przegląd możliwości lokalizacji składa się z trzech następujące testy:</span><span class="sxs-lookup"><span data-stu-id="2df28-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="2df28-109">Zaleceń globalnych są implementowane?</span><span class="sxs-lookup"><span data-stu-id="2df28-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="2df28-110">Wrażliwość na ustawienia kulturowe funkcje są obsługiwane poprawnie?</span><span class="sxs-lookup"><span data-stu-id="2df28-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="2df28-111">Zostały przetestowane aplikacji z danymi międzynarodowymi?</span><span class="sxs-lookup"><span data-stu-id="2df28-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="2df28-112">Wprowadzanie zaleceń globalnych</span><span class="sxs-lookup"><span data-stu-id="2df28-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="2df28-113">Jeśli zostały zaprojektowane i opracowane aplikacji przy użyciu lokalizacji należy pamiętać, a jeśli wykonano zaleceń omówione w [globalizacji](../../../docs/standard/globalization-localization/globalization.md) artykułu, przegląd możliwości lokalizacji w dużej mierze jest zapewnienie jakości — dostęp próbny .</span><span class="sxs-lookup"><span data-stu-id="2df28-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="2df28-114">W przeciwnym razie na tym etapie należy przejrzeć i zaimplementować zalecenia dotyczące [globalizacji](../../../docs/standard/globalization-localization/globalization.md)i naprawiać błędy w kodzie źródłowym, które uniemożliwiają lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="2df28-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="2df28-115">Obsługa funkcji dot. wrażliwości na ustawienia kulturowe</span><span class="sxs-lookup"><span data-stu-id="2df28-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="2df28-116">.NET Framework nie zapewnia wsparcia programowego kilka obszarów, które różnią się od kultury.</span><span class="sxs-lookup"><span data-stu-id="2df28-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="2df28-117">W większości przypadków trzeba napisać kod niestandardowy w celu obsługi obszary funkcji, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="2df28-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="2df28-118">Adresy.</span><span class="sxs-lookup"><span data-stu-id="2df28-118">Addresses.</span></span>  
  
-   <span data-ttu-id="2df28-119">Numery telefonów.</span><span class="sxs-lookup"><span data-stu-id="2df28-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="2df28-120">Rozmiary papieru.</span><span class="sxs-lookup"><span data-stu-id="2df28-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="2df28-121">Jednostki miary, używane do długości, wagi, obszaru, woluminów i temperatury.</span><span class="sxs-lookup"><span data-stu-id="2df28-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="2df28-122">Chociaż programu .NET Framework oferuje wbudowaną obsługę konwertowanie między jednostkami miary, możesz użyć <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> właściwości w celu określenia, czy danego kraju lub regionu korzysta z systemu metryki, tak jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2df28-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="2df28-123">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="2df28-123">Testing your application</span></span>  
 <span data-ttu-id="2df28-124">Zanim możesz zlokalizować aplikację, należy go przetestować, korzystając z danych w różnych językach w międzynarodowych wersjach systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2df28-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="2df28-125">Chociaż nie jest lokalizowany w tym momencie większość interfejsu użytkownika, będzie można wykrywać problemy, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="2df28-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="2df28-126">Serializowane dane nie poprawnie zdeserializować różnych wersjach systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2df28-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="2df28-127">Dane numeryczne, które nie odzwierciedlają konwencje bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="2df28-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="2df28-128">Na przykład liczby mogą być wyświetlane z separatory grup niedokładne, separatory dziesiętne i symbole walut.</span><span class="sxs-lookup"><span data-stu-id="2df28-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="2df28-129">Dane daty i godziny, który nie będzie odzwierciedlał Konwencji bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="2df28-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="2df28-130">Na przykład numery, które reprezentują miesiąc i dzień, może pojawić się w nieprawidłowej kolejności, separatorów daty może być niepoprawna lub informacje o strefie czasowej mogą być niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="2df28-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="2df28-131">Zasoby, których nie można znaleźć, ponieważ nie znaleziono domyślną kulturę używaną dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2df28-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="2df28-132">Ciągi, które są wyświetlane w kolejności nietypowe dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="2df28-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="2df28-133">Ciąg porównania lub porównania dla równości, które zwracają nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="2df28-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="2df28-134">Jeśli już przestrzegać zaleceń globalnych, podczas tworzenia aplikacji, obsługiwane funkcje wrażliwość na ustawienia kulturowe prawidłowo i zidentyfikować i rozwiązane problemy związane z lokalizacją, które powstały podczas testowania, możesz przejść do następnego kroku [Lokalizacji](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="2df28-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df28-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2df28-135">See also</span></span>

- [<span data-ttu-id="2df28-136">Globalizacja i lokalizacja</span><span class="sxs-lookup"><span data-stu-id="2df28-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
- [<span data-ttu-id="2df28-137">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="2df28-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
- [<span data-ttu-id="2df28-138">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="2df28-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
- [<span data-ttu-id="2df28-139">Zasoby w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="2df28-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
