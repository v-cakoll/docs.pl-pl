---
title: "Sprawdzenie możliwości lokalizacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2aaf7c466c6662611e2b37d5c967a99d050158df
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="localizability-review"></a><span data-ttu-id="4f3f7-102">Sprawdzenie możliwości lokalizacji</span><span class="sxs-lookup"><span data-stu-id="4f3f7-102">Localizability Review</span></span>
<span data-ttu-id="4f3f7-103">Sprawdzenie możliwości lokalizacji jest etap pośredni do tworzenia aplikacji gotowe.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="4f3f7-104">Sprawdzi, czy uniwersalnych aplikacji jest gotowy do lokalizacji i identyfikuje żadnego kodu lub aspekty interfejsu użytkownika, które wymagają specjalnej obsługi.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="4f3f7-105">Ten krok pozwala, upewnij się, że proces lokalizacji nie wprowadzi wad funkcjonalności do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="4f3f7-106">Jeśli zostały rozwiązane wszystkie problemy zgłoszone przez sprawdzenie, aplikacja jest gotowa do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="4f3f7-107">W przypadku dokładne sprawdzenie, należy nie należy zmodyfikować każdy kod źródłowy podczas procesu lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="4f3f7-108">Sprawdzenie obejmuje trzy następujące testy:</span><span class="sxs-lookup"><span data-stu-id="4f3f7-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="4f3f7-109">Zalecenia dotyczące globalizacji są implementowane?</span><span class="sxs-lookup"><span data-stu-id="4f3f7-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="4f3f7-110">Funkcje zależne od kultury są obsługiwane poprawnie?</span><span class="sxs-lookup"><span data-stu-id="4f3f7-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="4f3f7-111">Zostały przetestowane jest aplikacji z danymi w różnych?</span><span class="sxs-lookup"><span data-stu-id="4f3f7-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="4f3f7-112">Wprowadzanie zaleceń globalnych</span><span class="sxs-lookup"><span data-stu-id="4f3f7-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="4f3f7-113">Jeśli zaprojektowanych i opracowanych aplikacji z lokalizacji, pamiętając, a jeśli wykonano zaleceń omówione w [globalizacji](../../../docs/standard/globalization-localization/globalization.md) artykułu, sprawdzenie przede wszystkim będzie przebieg zapewnienia jakości .</span><span class="sxs-lookup"><span data-stu-id="4f3f7-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="4f3f7-114">W przeciwnym razie na tym etapie należy przejrzeć i zalecenia dotyczące wdrożenia [globalizacji](../../../docs/standard/globalization-localization/globalization.md)i napraw błędy w kodzie źródłowym, które uniemożliwiają lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="4f3f7-115">Obsługa funkcji dot. wrażliwości na ustawienia kulturowe</span><span class="sxs-lookup"><span data-stu-id="4f3f7-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="4f3f7-116">.NET Framework nie ma wsparcia programowego na kilka obszarów, które różnią się przez kultury.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="4f3f7-117">W większości przypadków należy napisać kod niestandardowy do obsługi funkcji obszarów podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="4f3f7-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="4f3f7-118">Adresy.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-118">Addresses.</span></span>  
  
-   <span data-ttu-id="4f3f7-119">Numery telefonów.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="4f3f7-120">Rozmiarów papieru.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="4f3f7-121">Jednostki miary używane do długości, wag obszaru, woluminów i temperatury.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="4f3f7-122">Chociaż programu .NET Framework nie oferuje wbudowaną obsługę konwertowanie jednostki miary, możesz użyć <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> właściwości w celu określenia, czy danego kraju lub regionu korzysta z systemu metryki, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="4f3f7-123">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="4f3f7-123">Testing your application</span></span>  
 <span data-ttu-id="4f3f7-124">Przed lokalizowanie aplikacji, należy przetestować go przy użyciu danych międzynarodowych na międzynarodowe wersje systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="4f3f7-125">Mimo że większość funkcji interfejsu użytkownika nie jest lokalizowany na tym etapie, można wykrywać problemy, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="4f3f7-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="4f3f7-126">Dane serializowane nie deserializować prawidłowo między wersjami systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="4f3f7-127">Dane numeryczne, które nie są widoczne konwencje bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="4f3f7-128">Na przykład numery mogą być wyświetlane z separatorów grup niedokładne, separatorów dziesiętnych lub symbol waluty.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="4f3f7-129">Data i godzina dane nie są widoczne konwencje bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="4f3f7-130">Na przykład numery, które reprezentują miesiąca i dnia mogą pojawić się w niewłaściwej kolejności, separatory daty może być niepoprawna lub informacje o strefie czasowej mogą być niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="4f3f7-131">Zasoby, których nie można znaleźć, ponieważ nie znaleziono domyślną kulturę dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="4f3f7-132">Ciągi, które są wyświetlane w kolejności nietypowe dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="4f3f7-133">Ciąg porównań lub porównania równości, które zwracają nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="4f3f7-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="4f3f7-134">Jeśli już podczas opracowywania aplikacji, a następnie zalecenia dotyczące globalizacji, obsługiwane funkcje zależne od kultury poprawnie i zidentyfikować i metod rozwiązania lokalizacji, które powstały podczas testowania, możesz przejść do następnego kroku [Lokalizacja](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="4f3f7-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f3f7-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f3f7-135">See Also</span></span>  
 [<span data-ttu-id="4f3f7-136">Globalizacja i lokalizacja</span><span class="sxs-lookup"><span data-stu-id="4f3f7-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="4f3f7-137">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="4f3f7-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 [<span data-ttu-id="4f3f7-138">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="4f3f7-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="4f3f7-139">Zasoby w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="4f3f7-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
