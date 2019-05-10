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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aabf2ad437ee8a50614ca27978aa0a031f5d7e55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592230"
---
# <a name="resources-in-net-apps"></a>Zasoby w aplikacjach .NET
Niemal każda aplikacja jakości produkcyjnej ma korzystać z zasobów. Zasób to wszelkie dane niewykonywalne, które są logicznie wdrażane za pomocą aplikacji. Zasób może być wyświetlany w aplikacji jako komunikaty o błędach lub jako część interfejsu użytkownika. Zasoby mogą zawierać dane w wielu formach, takich jak ciągi, obrazy i obiekty utrwalone. (Do zapisywania obiektów utrwalonego pliku zasobów, obiekty muszą podlegać serializacji.) Przechowywanie danych w pliku zasobów umożliwia zmianę danych bez konieczności ponownego kompilowania całej aplikacji. On również pozwala na przechowywanie danych w jednej lokalizacji i eliminuje konieczność łączenia się z zakodowanych danych przechowywanych w wielu lokalizacjach.  
  
 .NET Framework i .NET Core zapewnia kompleksowe obsługi tworzenia i lokalizacji zasobów. Ponadto .NET obsługuje prosty model do pakowania i wdrażania zlokalizowanych zasobów.  
  
 Aby uzyskać informacje o zasobach w programie ASP.NET, zobacz [omówienie zasoby strony sieci Web programu ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
## <a name="creating-and-localizing-resources"></a>Tworzenia i lokalizowania zasobów  

W aplikacji — zlokalizowane pliki zasobów można użyć jako repozytorium dla danych aplikacji, szczególnie w przypadku ciągów, które mogą zostać zakodowane w wielu miejscach w kodzie źródłowym. Najczęściej, możesz tworzyć zasoby jako tekstowy (txt) lub pliki XML (resx) i używać [Resgen.exe (Generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) do kompilowania ich do binarnych plików Resources. Te pliki mogą być następnie osadzony w pliku wykonywalnym aplikacji przez kompilator języka. Aby uzyskać więcej informacji na temat tworzenia zasobów, zobacz [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  

Możesz również dostosować zasoby aplikacji dla określonych kultur. Dzięki temu można tworzyć (tłumaczenia) zlokalizowane wersje aplikacji. Opracowując aplikację, która używa zlokalizowanych zasobów należy wyznaczyć kultury, która służy jako kultury neutralnej lub rezerwowej, którego zasoby są używane, jeśli są dostępne nie odpowiednie zasoby. Zazwyczaj zasobów kultury neutralnej są przechowywane w pliku wykonywalnym aplikacji. Pozostałych zasobów poszczególnych kultur zlokalizowane są przechowywane w zestawach satelickich autonomicznych. Aby uzyskać więcej informacji, zobacz [tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
## <a name="packaging-and-deploying-resources"></a>Opakowanie i wdrażanie zasobów  
 Wdrażanie aplikacji zlokalizowanych zasobów w [zestawy satelickie](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Zestawu satelickiego zawiera zasoby, które pojedynczej kultury; nie zawiera żadnego kodu aplikacji. W modelu wdrażania zestawu satelickiego tworzenie aplikacji za pomocą zestawu jeden domyślny, (która jest zwykle zestawu głównego) i zestawu satelickiego jeden dla każdej kultury, obsługiwanego przez aplikację. Ponieważ zestawy satelickie nie są częścią zestawu głównego, można łatwo zastąpić lub aktualizacja odpowiadający określonej kultury bez zastępowania aplikacji w głównym zestawie zasobów.  
  
 Dokładnie określić, które zasoby tworzących zestaw zasobów domyślnej aplikacji. Ponieważ jest częścią zestawu głównego, wszelkie zmiany będą wymagać Zastąp zestawu głównego. Jeśli domyślny zasób nie zostanie określona, zostanie zgłoszony wyjątek podczas [proces bazowy zasobu](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) próbuje go znaleźć. W dobrze zaprojektowana aplikacja korzysta z zasobów powinno nigdy nie zgłasza wyjątku.  
  
 Aby uzyskać więcej informacji, zobacz [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) artykułu.  
  
## <a name="retrieving-resources"></a>Pobieranie zasobów  
 W czasie wykonywania aplikacja ładuje odpowiednie zlokalizowane zasoby na podstawie na wątek, w oparciu o kultury określonej parametrem <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości. Wartość tej właściwości jest tworzony w następujący sposób:  
  
- Bezpośrednie przypisanie <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje zlokalizowanej kultury do <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> właściwości.  
  
- Jeśli nie przypisano jawnie kultury, pobierając domyślnie wątku interfejsu użytkownika kultury z <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> właściwości.  
  
- Jeśli wątek domyślna kultura interfejsu użytkownika nie jest jawnie przypisana, pobierając kultury dla bieżącego użytkownika na komputerze lokalnym. Implementacje platformy .NET w systemie Windows należy to zrobić, wywołując Windows [ `GetUserDefaultUILanguage` ](/windows/desktop/api/winnls/nf-winnls-getuserdefaultuilanguage) funkcji.  
  
 Aby uzyskać więcej informacji na temat Ustawianie bieżącej kultury interfejsu użytkownika, zobacz <xref:System.Globalization.CultureInfo> i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> odwoływać się do strony.  
  
 Następnie można pobrać zasobów dla bieżącej kultury interfejsu użytkownika lub dla określonej kultury, za pomocą <xref:System.Resources.ResourceManager?displayProperty=nameWithType> klasy. Mimo że <xref:System.Resources.ResourceManager> klasy jest najczęściej używana do pobierania zasobów, <xref:System.Resources?displayProperty=nameWithType> przestrzeń nazw zawiera dodatkowe typy, których można użyć w celu pobierania zasobów. Należą do nich następujące elementy:  
  
- <xref:System.Resources.ResourceReader> Klasy, która umożliwia wyliczanie zasoby osadzone w zestawie lub przechowywane w pliku binarnego Resources autonomicznych. Może to być przydatne, gdy nie znasz dokładne nazwy zasobów, które są dostępne w czasie wykonywania.  
  
- <xref:System.Resources.ResXResourceReader> Klasy, która umożliwia pobieranie zasobów z pliku XML (resx).  
  
- <xref:System.Resources.ResourceSet> Klasy, która umożliwia pobieranie zasobów określonej kultury bez obserwowania rezerwowego reguły. Zasoby mogą być przechowywane w zestawie lub autonomiczny plik binarny Resources. Możesz również tworzyć <xref:System.Resources.IResourceReader> implementację, która pozwala na użycie <xref:System.Resources.ResourceSet> klasy do pobrania zasobów z innego źródła.  
  
- <xref:System.Resources.ResXResourceSet> Klasy, która umożliwia pobieranie wszystkich elementów w pliku XML, zasób do pamięci.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.CultureInfo>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>
- [Podstawy aplikacji](../../../docs/standard/application-essentials.md)
- [Tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Pobieranie zasobów](../../../docs/framework/resources/retrieving-resources-in-desktop-apps.md)
