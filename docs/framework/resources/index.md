---
title: Zasoby w aplikacjach klasycznych
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- application resources
- resource files
- satellite assemblies
- localization
- packaging application resources
- localizing resources
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 023099adeeebf21b7dba631bde75332524eb0cc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resources-in-desktop-apps"></a>Zasoby w aplikacjach klasycznych
Niemal wszystkie wysokiej jakości aplikacji ma korzystać z zasobów. Zasób jest niewykonywalne dane, które logicznie jest wdrażany z aplikacją. Zasób może być wyświetlany w aplikacji jako komunikaty o błędach lub jako część interfejsu użytkownika. Zasoby mogą zawierać dane w wielu formularzy, a także ciągów, obrazy i utrwalone obiektów. (Aby napisać utrwalonych obiektów do pliku zasobów, obiekty muszą podlegać serializacji.) Przechowywanie danych w pliku zasobów umożliwia zmianę danych bez konieczności ponownego kompilowania całej aplikacji. Także umożliwia przechowywanie danych w jednej lokalizacji i eliminuje potrzebę polegać na stałe danych przechowywanych w wielu lokalizacjach.  
  
 .NET Framework zapewnia obsługę kompleksowe tworzenie i lokalizacji zasobów w aplikacjach klasycznych. Ponadto programu .NET Framework obsługuje prosty model pakowania i wdrażania tych zlokalizowanych zasobów w aplikacjach klasycznych.  
  
 Aby uzyskać informacje o zasobach w programie ASP.NET, zobacz [Omówienie zasobów strony sieci Web programu ASP.NET](http://msdn.microsoft.com/library/0936b3b2-9e6e-4abe-9c06-364efef9dbbd) w programie Internet Explorer Developer Center.  
  
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje korzystają z modelu innego zasobu z aplikacji klasycznych i zapisanie ich zasobów w pliku indeksu (PRI) pojedynczy pakiet zasobów. Aby uzyskać informacje o zasobach w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [tworzenie i pobieranie zasobów w aplikacjach w Sklepie Windows](http://go.microsoft.com/fwlink/p/?LinkId=241674) w Centrum deweloperów systemu Windows.  
  
## <a name="creating-and-localizing-resources"></a>Tworzenie i zasoby lokalizacyjne  
 W aplikacji niezlokalizowana pliki zasobów można użyć jako repozytorium dla danych aplikacji, szczególnie dla ciągów, które mogłoby zostać ustalony w wielu lokalizacjach w kodzie źródłowym. Najczęściej, utwórz zasoby jako tekstowy (txt) lub pliki XML (resx) i używać [Resgen.exe (Generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) do kompilowania ich do plików binarnych .resources. Te pliki mogą być osadzone w plik wykonywalny aplikacji przez kompilator języka. Aby uzyskać więcej informacji na temat tworzenia zasobów, zobacz [tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Możesz również dostosować zasoby aplikacji dla określonej kultury. Umożliwia to tworzenie zlokalizowane wersje (przetłumaczonego) aplikacji. Podczas opracowywania aplikacji, która używa zasobów zlokalizowanych, możesz określić kulturę, która służy jako kultury neutralnej lub rezerwowej, którego zasoby są używane, jeśli są dostępne żadne odpowiednie zasoby. Zazwyczaj zasobów kultury neutralnej są przechowywane w pliku wykonywalnym aplikacji. Pozostałe zasoby dla poszczególnych kultur zlokalizowane są przechowywane w zestawy satelickie autonomicznych. Aby uzyskać więcej informacji, zobacz [tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
## <a name="packaging-and-deploying-resources"></a>Opakowanie i wdrażanie zasobów  
 Wdrażanie aplikacji zlokalizowanych zasobów w [zestawy satelitarne](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Zestaw satelicki zawiera zasoby pojedynczego kultury; nie zawiera żadnego kodu aplikacji. W modelu wdrażania zestawu satelity Utwórz aplikację z jeden domyślny zestaw, (która jest zazwyczaj zestawie głównym) i zestawu satelickiego jednej dla każdego kultury, który obsługuje aplikacja. Ponieważ zestawów satelickich nie są częścią zestawu głównego, można łatwo Zastąp lub zaktualizować zasoby odpowiadające określoną kulturę bez zastępowania aplikacji w zestawie głównym.  
  
 Starannie sprawdzić zasobów, do których będzie tworzą zestawu zasobów domyślnego aplikacji. Ponieważ jest częścią zestawu głównego, wszystkie zmiany do niego wymaga Zastąp główny zestaw. Jeśli domyślny zasób nie zostanie określona, zostanie wygenerowany wyjątek podczas [proces rezerwowy dla zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) próbuje go znaleźć. W dobrze zaprojektowanej aplikacji przy użyciu zasoby nigdy nie powinien zgłosić wyjątek.  
  
 Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) artykułu.  
  
## <a name="retrieving-resources"></a>Pobieranie zasobów  
 W czasie wykonywania aplikacji ładuje odpowiednie zasoby zlokalizowane na podstawie dla każdego wątku, w oparciu kultury określonej przez <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości. Wartość tej właściwości jest uzyskiwana w następujący sposób:  
  
-   Bezpośrednio przypisując <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje zlokalizowanych kultura <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> właściwości.  
  
-   Jeśli kultura nie jest jawnie przypisane, przywracając domyślne wątku interfejsu użytkownika kultury z <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> właściwości.  
  
-   Jeśli wątek domyślna kultura interfejsu użytkownika nie jest jawnie przypisany, pobierając kultury dla bieżącego użytkownika na komputerze lokalnym przez wywołanie systemu Windows `GetUserDefaultUILanguage` funkcji.  
  
 Aby uzyskać więcej informacji o sposobie bieżącej kultury interfejsu użytkownika, zobacz <xref:System.Globalization.CultureInfo> i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> odwołania stron.  
  
 Następnie można pobrać zasobów dla bieżącej kultury interfejsu użytkownika lub określoną kulturę, za pomocą <xref:System.Resources.ResourceManager?displayProperty=nameWithType> klasy. Mimo że <xref:System.Resources.ResourceManager> klasy jest najczęściej używane do pobierania zasobów w aplikacjach klasycznych <xref:System.Resources?displayProperty=nameWithType> przestrzeń nazw zawiera dodatkowe typy, których można pobrać zasobów. Należą do nich następujące elementy:  
  
-   <xref:System.Resources.ResourceReader> Klasy, dzięki czemu można wyliczyć zasobów osadzone w zestawie lub przechowywane w pliku .resources binarne autonomicznej. Jest przydatne, jeśli nie znasz dokładne nazw zasobów, które są dostępne w czasie wykonywania.  
  
-   <xref:System.Resources.ResXResourceReader> Klasy, która umożliwia pobieranie zasobów z pliku XML (resx).  
  
-   <xref:System.Resources.ResourceSet> Klasy, która umożliwia pobieranie zasobów określonej kultury bez obserwowania rezerwowy reguły. Zasoby mogą być przechowywane w zestawie lub autonomiczny plik binarny .resources. Można również tworzyć <xref:System.Resources.IResourceReader> implementację, która pozwala na użycie <xref:System.Resources.ResourceSet> klasy można pobrać zasobów z z innego źródła.  
  
-   <xref:System.Resources.ResXResourceSet> Klasy, która umożliwia pobieranie wszystkich elementów w pliku XML zasobów do pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Globalization.CultureInfo>  
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>  
 [Podstawy aplikacji](../../../docs/standard/application-essentials.md)  
 [Tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)  
 [Pobieranie zasobów](../../../docs/framework/resources/retrieving-resources-in-desktop-apps.md)
