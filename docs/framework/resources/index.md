---
title: Zasoby w aplikacjach .NET
ms.date: 07/25/2018
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- deploying applications [.NET Core], resources
- application resources
- resource files
- satellite assemblies
- localization
- packaging application resources
- localizing resources
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
ms.openlocfilehash: f7db871c6643973ab18a5bb6bbfac7ab85a11a76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75346738"
---
# <a name="resources-in-net-apps"></a>Zasoby w aplikacjach .NET

Prawie każda aplikacja o jakości produkcyjnej musi korzystać z zasobów. Zasób to wszystkie niewykonalne dane, które są logicznie wdrażane za pomocą aplikacji. Zasób może być wyświetlany w aplikacji jako komunikaty o błędach lub jako część interfejsu użytkownika. Zasoby mogą zawierać dane w wielu formach, w tym ciągi, obrazy i utrwalone obiekty. (Aby zapisać utrwalone obiekty w pliku zasobów, obiekty muszą być serializable.) Przechowywanie danych w pliku zasobów umożliwia zmianę danych bez ponownej kompilacji całej aplikacji. Umożliwia również przechowywanie danych w jednej lokalizacji i eliminuje konieczność polegania na danych zakodowanych na twardo, które są przechowywane w wielu lokalizacjach.

.NET Framework i .NET Core zapewniają kompleksową obsługę tworzenia i lokalizacji zasobów. Ponadto .NET obsługuje prosty model do pakowania i wdrażania zlokalizowanych zasobów.

Aby uzyskać informacje o zasobach w ASP.NET, zobacz [ASP.NET Omówienie zasobów strony sieci Web](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).

## <a name="create-and-localize-resources"></a>Tworzenie i lokalizowanie zasobów

W aplikacji nieodlokalizowanej można używać plików zasobów jako repozytorium danych aplikacji, szczególnie w przypadku ciągów, które w przeciwnym razie mogą być zakodowane na stałe w wielu lokalizacjach w kodzie źródłowym. Najczęściej zasoby są tworzono jako pliki tekstowe (txt) lub XML (.resx) i używane [jest polecenie Resgen.exe (Resource File Generator)](../tools/resgen-exe-resource-file-generator.md) do kompilowania ich w binarne pliki .resources. Pliki te mogą być następnie osadzone w pliku wykonywalnym aplikacji przez kompilator języka. Aby uzyskać więcej informacji na temat tworzenia zasobów, zobacz [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md).

Możesz również zlokalizować zasoby aplikacji dla określonych kultur. Dzięki temu można tworzyć zlokalizowane (przetłumaczone) wersje aplikacji. Podczas tworzenia aplikacji, która używa zlokalizowanych zasobów, należy wyznaczyć kultury, która służy jako kultury neutralne lub rezerwowe, których zasoby są używane, jeśli nie są dostępne odpowiednie zasoby. Zazwyczaj zasoby kultury neutralnej są przechowywane w pliku wykonywalnym aplikacji. Pozostałe zasoby dla poszczególnych zlokalizowanych kultur są przechowywane w autonomicznych zestawach satelitalnych. Aby uzyskać więcej informacji, zobacz [Tworzenie zestawów satelickich](creating-satellite-assemblies-for-desktop-apps.md).

## <a name="package-and-deploy-resources"></a>Pakowanie i wdrażanie zasobów

Wdrażasz zlokalizowane zasoby aplikacji w [zestawach satelickich](packaging-and-deploying-resources-in-desktop-apps.md). Zestaw satelickiego zawiera zasoby jednej kultury; nie zawiera żadnego kodu aplikacji. W modelu wdrażania zestawu satelickiego można utworzyć aplikację z jednym zestawem domyślnym (który jest zazwyczaj głównym zestawem) i jednym zestawem satelickiego dla każdej kultury, która obsługuje aplikację. Ponieważ zestawy satelitowane nie są częścią głównego zestawu, można łatwo zastąpić lub zaktualizować zasoby odpowiadające określonej kulturze bez zastępowania głównego zestawu aplikacji.

Dokładnie określ, które zasoby będą stanowić domyślny zestaw zasobów aplikacji. Ponieważ jest to część głównego złożenia, wszelkie zmiany w nim będą wymagały zastąpienia głównego złożenia. Jeśli nie podasz domyślnego zasobu, wyjątek zostanie zgłoszony, gdy [proces rezerwowy zasobu](packaging-and-deploying-resources-in-desktop-apps.md) próbuje go znaleźć. W dobrze zaprojektowanej aplikacji przy użyciu zasobów nigdy nie należy zgłaszać wyjątek.

Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md) artykułu.

## <a name="retrieve-resources"></a>Pobieranie zasobów

W czasie wykonywania aplikacja ładuje odpowiednie zlokalizowane zasoby na podstawie wątku, na <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> podstawie kultury określonej przez właściwość. Ta wartość właściwości jest obliczany w następujący sposób:

- Poprzez bezpośrednie przypisanie <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje zlokalizowane kultury do <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> właściwości.

- Jeśli kultura nie jest jawnie przypisana, pobierając domyślną <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> kulturę interfejsu użytkownika wątku z właściwości.

- Jeśli domyślna kultura interfejsu użytkownika wątku nie jest jawnie przypisana, pobierając kulturę dla bieżącego użytkownika na komputerze lokalnym. Implementacje platformy .NET uruchomione w [`GetUserDefaultUILanguage`](/windows/desktop/api/winnls/nf-winnls-getuserdefaultuilanguage) systemie Windows robią to, wywołując funkcję systemu Windows.

Aby uzyskać więcej informacji na temat sposobu ustawiania bieżącej kultury interfejsu użytkownika, zobacz strony <xref:System.Globalization.CultureInfo> i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> odwołania.

Następnie można pobrać zasoby dla bieżącej kultury interfejsu użytkownika lub <xref:System.Resources.ResourceManager?displayProperty=nameWithType> dla określonej kultury przy użyciu klasy. Chociaż <xref:System.Resources.ResourceManager> klasa jest najczęściej używana do pobierania <xref:System.Resources?displayProperty=nameWithType> zasobów, obszar nazw zawiera dodatkowe typy, których można użyć do pobierania zasobów. Należą do nich:

- Klasa, <xref:System.Resources.ResourceReader> która umożliwia wyliczania zasobów osadzonych w zestawie lub przechowywanych w autonomicznym pliku binarnym .resources. Jest to przydatne, gdy nie znasz dokładnych nazw zasobów, które są dostępne w czasie wykonywania.

- Klasa, <xref:System.Resources.ResXResourceReader> która umożliwia pobieranie zasobów z pliku XML (.resx).

- Klasa, <xref:System.Resources.ResourceSet> która umożliwia pobieranie zasobów określonej kultury bez przestrzegania reguł rezerwowych. Zasoby mogą być przechowywane w zestawie lub autonomicznym pliku binarnym .resources. Można również opracować <xref:System.Resources.IResourceReader> implementację, która <xref:System.Resources.ResourceSet> umożliwia użycie klasy do pobierania zasobów z innego źródła.

- Klasa, <xref:System.Resources.ResXResourceSet> która umożliwia pobieranie wszystkich elementów w pliku zasobów XML do pamięci.

## <a name="see-also"></a>Zobacz też

- <xref:System.Globalization.CultureInfo>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>
- [Podstawy aplikacji](../../standard/application-essentials.md)
- [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md)
- [Opakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md)
- [Tworzenie zestawów satelickich](creating-satellite-assemblies-for-desktop-apps.md)
- [Pobieranie zasobów](retrieving-resources-in-desktop-apps.md)
