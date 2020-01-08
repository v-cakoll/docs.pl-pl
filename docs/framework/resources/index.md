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
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346738"
---
# <a name="resources-in-net-apps"></a>Zasoby w aplikacjach .NET

Prawie każda aplikacja do jakości produkcyjnej musi korzystać z zasobów. Zasób to wszystkie niewykonywalne dane, które są logicznie wdrażane za pomocą aplikacji. Zasób może być wyświetlany w aplikacji jako komunikaty o błędach lub jako część interfejsu użytkownika. Zasoby mogą zawierać dane w wielu formularzach, w tym ciągi, obrazy i utrwalone obiekty. (Aby zapisać utrwalone obiekty w pliku zasobów, obiekty muszą być serializowane). Przechowywanie danych w pliku zasobów pozwala na zmianę danych bez konieczności ponownego kompilowania całej aplikacji. Umożliwia także przechowywanie danych w jednej lokalizacji i eliminuje konieczność polegania na zakodowanych danych przechowywanych w wielu lokalizacjach.

.NET Framework i .NET Core zapewniają kompleksową obsługę tworzenia i lokalizowania zasobów. Ponadto platforma .NET obsługuje prosty model do pakowania i wdrażania zlokalizowanych zasobów.

Aby uzyskać informacje o zasobach w programie ASP.NET, zobacz [ASP.NET — Omówienie zasobów strony sieci Web](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).

## <a name="create-and-localize-resources"></a>Tworzenie i lokalizowanie zasobów

W aplikacji niezlokalizowanej można używać plików zasobów jako repozytorium dla danych aplikacji, szczególnie w przypadku ciągów, które w przeciwnym razie mogą być zakodowane w wielu lokalizacjach w kodzie źródłowym. Najczęściej można utworzyć zasoby jako pliki tekstowe (. txt) lub XML (. resx), a następnie użyć [Resgen. exe (Generator plików zasobów)](../tools/resgen-exe-resource-file-generator.md) do skompilowania ich do plików binarnych. resources. Te pliki mogą być następnie osadzone w pliku wykonywalnym aplikacji przez kompilator języka. Aby uzyskać więcej informacji na temat tworzenia zasobów, zobacz [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md).

Możesz również lokalizować zasoby aplikacji dla określonych kultur. Dzięki temu można tworzyć zlokalizowane (tłumaczone) wersje aplikacji. Podczas tworzenia aplikacji korzystającej z zlokalizowanych zasobów należy określić kulturę, która służy jako kultura neutralna lub rezerwowa, której zasoby są używane, jeśli nie są dostępne odpowiednie zasoby. Zazwyczaj zasoby kultury neutralnej są przechowywane w pliku wykonywalnym aplikacji. Pozostałe zasoby dla poszczególnych zlokalizowanych kultur są przechowywane w autonomicznych zestawach satelickich. Aby uzyskać więcej informacji, zobacz [Tworzenie zestawów satelickich](creating-satellite-assemblies-for-desktop-apps.md).

## <a name="package-and-deploy-resources"></a>Pakowanie i wdrażanie zasobów

Wdrażasz zlokalizowane zasoby aplikacji w [zestawach satelickich](packaging-and-deploying-resources-in-desktop-apps.md). Zestaw satelicki zawiera zasoby pojedynczej kultury; nie zawiera kodu aplikacji. W modelu wdrażania satelitarnego można utworzyć aplikację z jednym zestawem domyślnym (który jest zazwyczaj głównym zestawem) i jednym zestawem satelickim dla każdej kultury obsługiwanej przez aplikację. Ponieważ zestawy satelickie nie są częścią głównego zestawu, można łatwo zamienić lub zaktualizować zasoby odpowiadające określonej kulturze bez zastępowania głównego zestawu aplikacji.

Dokładnie Ustal, które zasoby składają się na domyślny zestaw zasobów aplikacji. Ponieważ jest częścią głównego zestawu, wszelkie zmiany w nim wymagają zastąpienia zestawu głównego. Jeśli nie podasz domyślnego zasobu, zostanie zgłoszony wyjątek, gdy [proces rezerwowy zasobu](packaging-and-deploying-resources-in-desktop-apps.md) spróbuje go znaleźć. W dobrze zaprojektowanej aplikacji używanie zasobów nigdy nie zgłasza wyjątku.

Aby uzyskać więcej informacji, zobacz artykuł [pakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md) .

## <a name="retrieve-resources"></a>Pobieranie zasobów

W czasie wykonywania aplikacja ładuje odpowiednie zlokalizowane zasoby dla poszczególnych wątków na podstawie kultury określonej przez właściwość <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>. Ta wartość właściwości jest pochodna w następujący sposób:

- Przez bezpośrednie przypisanie obiektu <xref:System.Globalization.CultureInfo>, który reprezentuje zlokalizowaną kulturę do właściwości <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType>.

- Jeśli kultura nie jest jawnie przypisana, pobierając domyślną kulturę interfejsu użytkownika wątku z właściwości <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType>.

- Jeśli domyślna kultura interfejsu użytkownika wątku nie jest jawnie przypisana, pobierając kulturę dla bieżącego użytkownika na komputerze lokalnym. Implementacje platformy .NET działające w systemie Windows to przez wywołanie funkcji [`GetUserDefaultUILanguage`](/windows/desktop/api/winnls/nf-winnls-getuserdefaultuilanguage) systemu Windows.

Aby uzyskać więcej informacji na temat sposobu ustawiania bieżącej kultury interfejsu użytkownika, zobacz strony referencyjne <xref:System.Globalization.CultureInfo> i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>.

Następnie można pobrać zasoby dla bieżącej kultury interfejsu użytkownika lub dla określonej kultury przy użyciu klasy <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Chociaż Klasa <xref:System.Resources.ResourceManager> jest najczęściej używana do pobierania zasobów, <xref:System.Resources?displayProperty=nameWithType> przestrzeni nazw zawiera dodatkowe typy, których można użyć do pobierania zasobów. Należą do nich następujące elementy:

- Klasa <xref:System.Resources.ResourceReader>, która umożliwia Wyliczenie zasobów osadzonych w zestawie lub przechowywanych w autonomicznym pliku Binary. resources. Jest to przydatne, gdy nie znasz dokładnych nazw zasobów, które są dostępne w czasie wykonywania.

- Klasa <xref:System.Resources.ResXResourceReader>, która umożliwia pobieranie zasobów z pliku XML (. resx).

- Klasa <xref:System.Resources.ResourceSet>, która umożliwia pobieranie zasobów określonej kultury bez przestrzegania reguł powrotu. Zasoby mogą być przechowywane w zestawie lub autonomiczny plik binarny. resources. Możesz również opracować implementację <xref:System.Resources.IResourceReader>, która umożliwia korzystanie z klasy <xref:System.Resources.ResourceSet> do pobierania zasobów z innego źródła.

- Klasa <xref:System.Resources.ResXResourceSet>, która umożliwia pobranie wszystkich elementów w pliku zasobów XML do pamięci.

## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.CultureInfo>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>
- [Podstawy aplikacji](../../standard/application-essentials.md)
- [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md)
- [Opakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md)
- [Tworzenie zestawów satelickich](creating-satellite-assemblies-for-desktop-apps.md)
- [Pobieranie zasobów](retrieving-resources-in-desktop-apps.md)
