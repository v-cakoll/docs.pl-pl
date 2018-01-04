---
title: "Przegląd Lokalizacja i globalizacja WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f2bc9021ca376b7b27f74efed6866a907b480ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-globalization-and-localization-overview"></a>Przegląd Lokalizacja i globalizacja WPF
Dostępność na produkt tylko do jednego języka, możesz ograniczenie potencjalnych klienta podstawowej ułamek naszych world MLD 6.5 populacji. Jeśli chcesz, aby aplikacje do globalnej grupy odbiorców, ekonomiczne lokalizacja produktu jest jednym z najlepszym i najbardziej ekonomiczny sposób nawiązać więcej klientów.  
  
 W tym omówieniu przedstawiono globalizacja i lokalizacja w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Globalizacja to podczas projektowania i opracowywania aplikacji, które wykonują w wielu lokalizacjach. Na przykład globalizacji obsługuje zlokalizowane interfejsy użytkownika i dane regionalne dla użytkowników w innych kultur. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia funkcje uniwersalnych projektowania, w tym układ automatyczny, zestawy satelickie i atrybuty zlokalizowanych i komentarzy.
  
 Lokalizacja jest tłumaczenie zasobów aplikacji na zlokalizowane wersje dla określonej kultury, obsługiwanych przez aplikację. Gdy localize w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], użyj interfejsów API w <xref:System.Windows.Markup.Localizer> przestrzeni nazw. Te interfejsy API zasilania [przykładowe narzędzie LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016) narzędzia wiersza polecenia. Aby uzyskać informacje o sposobie tworzenia i używania LocBaml, zobacz [lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).    
  
## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Najlepsze rozwiązania dotyczące globalizacja i lokalizacja na platformie WPF  
 Możesz wprowadzić w pełni korzystać z funkcji lokalizacja i globalizacja jest wbudowana w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykonując projektu interfejsu użytkownika i wskazówki związane z lokalizacji, które ta sekcja zawiera.  
  
### <a name="best-practices-for-wpf-ui-design"></a>Najlepsze rozwiązania dotyczące projektowania interfejsu użytkownika WPF  
 Podczas projektowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], rozważ zaimplementowanie następujące najlepsze rozwiązania:  
  
-   Pisanie programu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; Unikaj tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w kodzie. Podczas tworzenia Twojej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], je ujawnić za pośrednictwem wbudowanego lokalizacja interfejsów API.  
  
-   Unikaj układ zawartości; za pomocą stałych rozmiary i położenia bezwzględne Zamiast tego należy użyć względną lub automatycznej zmiany rozmiaru.
  
    -   Użyj <xref:System.Windows.Window.SizeToContent%2A>; i zachowanie szerokości i wysokości ustawioną `Auto`.  
  
    -   Unikaj używania <xref:System.Windows.Controls.Canvas> do określania układu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s.  
  
    -   Użyj <xref:System.Windows.Controls.Grid> i jej funkcji udostępniania rozmiar.  
  
-   Podaj dodatkowe miejsce w marginesy ponieważ zlokalizowany tekst często wymaga więcej miejsca. Dodatkowe miejsce umożliwia ich znaków.  
  
-   Włącz <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> na <xref:System.Windows.Controls.TextBlock> w celu uniknięcia wycinka.
  
-   Ustaw **XML: lang** atrybutu. Ten atrybut zawiera opis kultury określonego elementu i jego elementów podrzędnych. Wartość tej właściwości zostanie zmieniona zachowanie kilka funkcji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Na przykład zmienia zachowanie dzielenia wyrazów, sprawdzanie pisowni numer podstawienia, kształtowania złożonym i czcionki. Zobacz [globalizacji dla WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md) Aby uzyskać więcej informacji o ustawieniu [XML: lang — Obsługa w XAML](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md).  
  
-   Utwórz dostosowane czcionka złożona, aby uzyskać lepszą kontrolę czcionek, które są używane w różnych językach. Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa czcionki GlobalUserInterface.composite w katalogu Windows\Fonts.  
  
-   Podczas tworzenia aplikacji nawigacji, które mogą być zlokalizowany w kultury przedstawiający tekst w formacie od prawej do lewej, jawnie ustaw <xref:System.Windows.FlowDirection> każdej strony, aby upewnić się, nie dziedziczy strony <xref:System.Windows.FlowDirection> z <xref:System.Windows.Navigation.NavigationWindow>.  
  
-   Podczas tworzenia aplikacji autonomicznej nawigacji, które znajdują się poza przeglądarką ustawić <xref:System.Windows.Application.StartupUri%2A> dla aplikacji do początkowej <xref:System.Windows.Navigation.NavigationWindow> zamiast do strony (na przykład `<Application StartupUri="NavigationWindow.xaml">`). Ten projekt umożliwia zmianę <xref:System.Windows.FlowDirection> okna, a na pasku nawigacji. Aby uzyskać więcej informacji i przykład zobacz [przykładowe strony głównej globalizacji](http://go.microsoft.com/fwlink/?LinkID=159990).  
  
### <a name="best-practices-for-wpf-localization"></a>Najlepsze rozwiązania dotyczące lokalizacji WPF  
 Gdy localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— aplikacji, należy rozważyć zaimplementowanie następujące najlepsze rozwiązania:  
  
-   Używając komentarzy lokalizacji, aby zapewnić dodatkowy kontekst dla wiadomość dla lokalizatorów.  
  
-   Przy użyciu atrybutów lokalizacja kontrolować lokalizacja zamiast selektywne pominięcie <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości elementów. Zobacz [atrybuty lokalizacji i komentarze](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md) Aby uzyskać więcej informacji.  
  
-   Użyj **msbuild /t:updateuid** i **/t:checkuid** do dodawania i sprawdź <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości w Twojej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Użyj <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości, aby śledzić zmiany między rozwoju i lokalizacji. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>właściwości pomóc localize nowych zmian programowanie. Jeśli ręcznie dodać <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zadanie jest zwykle żmudnego i mniej dokładne.  
  
    -   Nie edytować ani zmieniać <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości po rozpoczęciu lokalizacji.  
  
    -   Nie używaj duplikat <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości (należy pamiętać o tej porady po użyciu polecenia Kopiuj i Wklej).  
  
    -   Ustaw `UltimateResourceFallback` lokalizacji w AssemblyInfo.*, aby określić odpowiedni język dla powrotu (na przykład `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).  
  
         Jeśli zdecydujesz się obejmują język źródła w zestawie głównym, pomijając `<UICulture>` tagów w pliku projektu, ustaw `UltimateResourceFallback` lokalizacji, w zestawie głównym zamiast satelity (na przykład `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).  
  
<a name="workflow_to_localize"></a>   
## <a name="localize-a-wpf-application"></a>Lokalizowanie aplikacji WPF  
 Gdy localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, dostępnych jest kilka opcji. Na przykład można powiązać zlokalizowania zasobów w aplikacji do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pliku, Lokalizowalny tekst są przechowywane w tabelach resx lub mają Twojej lokalizatora użyj [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików. W tej sekcji opisano lokalizacja przepływu pracy, który używa BAML formę XAML, który zapewnia kilka korzyści:  
  
-   Po utworzeniu można lokalizować.  
  
-   Można zaktualizować do nowszej wersji BAML formę lokalizacje XAMLwith ze starszej wersji w postaci BAML języka XAML, dzięki czemu można lokalizować w tym samym czasie, który można rozwijać.  
  
-   Możesz to sprawdzić oryginalne elementy źródłowe i semantyki w czasie kompilacji ponieważ BAML formę XAML jest skompilowanej postaci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
### <a name="localization-build-process"></a>Proces kompilacji lokalizacji  
 Podczas opracowywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, proces kompilacji do lokalizacji jest następujący:  
  
-   Deweloper tworzy i globalizes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. W projekcie plików zestawów developer `<UICulture>en-US</UICulture>` tak, aby podczas kompilowania aplikacji, jest generowany główny zestaw niezależny od języka. Ten zestaw zawiera satelity. resources.dll pliku, który zawiera wszystkie zasoby lokalizowalny. Opcjonalnie można zachować języka źródłowego w zestawie głównym ponieważ naszych lokalizacja [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] obsługuje wyodrębniania z zestawu głównego.  
  
-   Gdy plik jest kompilowany do kompilacji, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest konwertowana na formularzu BAML w języku XAML. Neutralne kulturalnie `MyDialog.exe` i kulturalnie zależnym (angielski) `MyDialog.resources.dll` pliki są wydawane anglojęzycznego odbiorcy.  
  
### <a name="localization-workflow"></a>Przepływ pracy lokalizacji  
 Proces lokalizacji rozpoczyna się po Niezlokalizowany `MyDialog.resources.dll` plik. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Elementów i właściwości w oryginalny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są wyodrębniane w formularzu BAML XAML w pary klucz wartość, przy użyciu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] w obszarze <xref:System.Windows.Markup.Localizer>. Wiadomość dla lokalizatorów Użyj pary klucz wartość do zlokalizowania aplikacji. Możesz wygenerować nowy. resource.dll z nowe wartości po zakończeniu lokalizacji.  
  
 Klucze pary klucz wartość są `x:Uid` wartości, które są wprowadzane przez dewelopera w oryginalnym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Te `x:Uid` włączyć wartości [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] do śledzenia i scalania zmian, które mają miejsce między deweloperów oraz lokalizatora podczas lokalizacji. Na przykład w przypadku zmiany dewelopera [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] po rozpoczęciu lokalizatora lokalizowanie można scalić zmiany programowanie z pracą lokalizacja już ukończone, aby minimalny tłumaczenia praca zostanie utracona.  
  
 Na poniższym rysunku przedstawiono typowe lokalizacja przepływu pracy, który jest oparta na formularzu BAML w XAML. Ten diagram przyjęto założenie, że deweloper zapisuje aplikacji w języku angielskim. Deweloper tworzy i globalizes aplikacji WPF. W projekcie plików zestawów developer `<UICulture>en-US</UICulture>` tak, aby podczas kompilacji, języka neutralnego zestawu głównego pobiera wygenerowane z satelity. resources.dll zawierający wszystkie zasoby lokalizowalny. Alternatywnie jedną Zachowaj języka źródłowego w zestawie głównym ponieważ lokalizacja WPF interfejsów API obsługuje wyodrębniania z zestawu głównego. Po procesie kompilacji XAML uzyskać skompilowany do BAML. Neutralne kulturalnie MyDialog.exe.resources.dll uzyskać dostarczane klientom wymowy angielskiej wersji językowej.  
  
 ![Przepływ pracy lokalizacji](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![Niezlokalizowany przepływu pracy](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization"></a>   
## <a name="examples-of-wpf-localization"></a>Przykłady lokalizacji WPF  
 Ta sekcja zawiera przykłady zlokalizowane aplikacje, aby ułatwić zrozumienie sposobu tworzenia i lokalizowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
#### <a name="run-dialog-box-example"></a>Uruchom przykład okno dialogowe  
 Poniższej grafice Pokaż dane wyjściowe **Uruchom** przykładowe okno dialogowe.  
  
 **Angielski:**  
  
 ![Uruchom okno dialogowe](../../../../docs/framework/wpf/advanced/media/rundialogenglish.PNG "RunDialogEnglish")  
  
 **Niemiecki:**  
  
 ![Niemiecki Uruchom okno dialogowe](../../../../docs/framework/wpf/advanced/media/rundialoggerman.PNG "RunDialogGerman")  
  
 **Projektowanie globalne Uruchom okno dialogowe**  
  
 Ten przykład generuje **Uruchom** okno dialogowe przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. To okno dialogowe jest odpowiednikiem **Uruchom** okno dialogowe, który jest dostępny z [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] Start menu.  
  
 Niektóre najważniejsze funkcje do tworzenia globalnych okna dialogowe są:  
  
 **Układ automatyczny**  
  
 *W Window1.xaml:*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 Właściwość poprzedniego okna automatycznie zmienia rozmiar okna na podstawie rozmiaru zawartości. Ta właściwość uniemożliwia okna Wycinanie poza zawartość, która zwiększa się rozmiar po lokalizacji; Usuwa również niepotrzebnych miejsce, gdy zawartość zmniejsza rozmiar po lokalizacji.  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>właściwości są wymagane, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizacja [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] działała prawidłowo.  
  
 Są one używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizacja [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] do śledzenia zmian między opracowywania i lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>właściwości umożliwia scalania nowsza wersja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z starsze lokalizacja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Możesz dodać <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości uruchamiając **msbuild /t:updateuid RunDialog.csproj** w powłoce poleceń. Jest to zalecana metoda dodawania <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości ponieważ ręczne dodanie ich jest zwykle czasochłonne i mniej dokładne. Sprawdź, czy <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> uruchamiając są poprawnie ustawione właściwości **msbuild /t:checkuid RunDialog.csproj**.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Mają strukturę przy użyciu <xref:System.Windows.Controls.Grid> kontroli, która jest formantem przydatne dla dzięki funkcji automatycznego układu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Należy pamiętać, że okno dialogowe jest podzielony na trzy wiersze i kolumny pięć. Nie jest elementem definicji wierszy i kolumn ma stały rozmiar; w związku z tym [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy, które będą umieszczane w każdej komórce można dostosować do rośnie i zmniejsza rozmiar podczas lokalizacji.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 Pierwsze dwie kolumny gdzie **Otwórz:** etykiety i <xref:System.Windows.Controls.ComboBox> są umieszczane użyj 10 procent [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] łączna szerokość.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 Należy pamiętać, że przykładu używa funkcji udostępnionych rozmiaru <xref:System.Windows.Controls.Grid>. Ostatnie trzy kolumny zostać wykorzystane przez umieszczenie się w tym samym <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>. Zgodnie z jedną oczekuje się od nazwy właściwości, dzięki temu kolumny, które chcesz udostępnić ten sam rozmiar. W takim przypadku funkcji "Przeglądaj..." pobiera zlokalizowany ciąg dłuższy "Durchsuchen...", wszystkie przyciski zwiększa się szerokość zamiast małych przycisk "OK" i nieproporcjonalnie dużych "Durchsuchen..." przycisk.  
  
 **XML: lang**  
  
 `Xml:lang="en-US"`  
  
 Powiadomienie [XML: lang — Obsługa w XAML](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) umieszczony w elemencie głównym [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Ta właściwość określa kulturę danego elementu i jego elementów podrzędnych. Ta wartość jest używana przez kilka funkcji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i należy odpowiednio zmienić podczas lokalizacji. Ta wartość zmiany, jakie słownika jest służy do dzielenia i wyrazy sprawdzania pisowni. Wpływa to również na wyświetlania cyfr i jak system rezerwowy czcionki wybiera czcionki, która do użycia. Na koniec kształt właściwość ma wpływ na, wyświetlania numerów sposób i teksty sposób napisany w ustawieniu. Wartość domyślna to "en US".  
  
 **Tworzenie zasobu Satelicki**  
  
 *W .csproj:*  
  
 `<UICulture>en-US</UICulture>`  
  
 Zwróć uwagę, dodanie `UICulture` wartość. Gdy to jest ustawiona na prawidłowy <xref:System.Globalization.CultureInfo> wartości, takich jak pl pl, wówczas skompilowanie projektu zostanie wygenerowany zestaw satelicki z wszystkimi zasobami Lokalizowalny w nim.  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG` Nie musi być lokalizowany, ponieważ są one takie same dla wszystkich języków. `Localizable`ustawiono `false` , aby pozostała w języka neutralnego główny zestaw zamiast zestawu satelickiego. Wartość domyślna wszystkich zasobów noncompilable to `Localizable` ustawioną `true`.  
  
 **Lokalizowanie Uruchom okno dialogowe**  
  
 **Analizy**  
  
 Po utworzeniu aplikacji, pierwszym krokiem podczas lokalizowania go jest analizowania zlokalizowania zasobów spoza zestawu satelickiego. Do celów tego tematu, użyj narzędzia LocBaml próbki, które można znaleźć w folderze [przykładowe narzędzie LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016). Należy pamiętać, że LocBaml tylko przykładowe narzędzie przeznaczone do ułatwiające rozpoczęcie pracy z tworzeniem narzędzia lokalizacji, która pasuje do w procesie lokalizacji. Przy użyciu LocBaml, uruchom następujące polecenie, aby przeanalizować: **LocBaml/przeanalizować RunDialog.resources.dll/out:** aby wygenerować plik "RunDialog.resources.dll.CSV".  
  
 **Lokalizowanie**  
  
 Użyj edytora ulubionych CSV, który obsługuje standard Unicode, aby edytować ten plik. Odfiltrować wszystkie wpisy z kategorią lokalizacja "None". Powinny pojawić się następujące wpisy:  
  
|Klucz zasobu|Lokalizacja kategorii|Wartość|  
|-|-|-| 
|Button_1:system.Windows.Controls.button.$Content|Przycisk|OK|  
|Button_2:system.Windows.Controls.button.$Content|Przycisk|Anuluj|  
|Button_3:system.Windows.Controls.button.$Content|Przycisk|Przeglądaj...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Tekst|Wpisz nazwę programu, folderu, dokumentu lub zasobu internetowego, a system Windows otworzy.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Tekst|Otwórz:|  
|Window_1:system.Windows.window.Title|Tytuł|Uruchom|  
  
 Lokalizowanie aplikacji na język niemiecki wymagają następujących tłumaczenia:  
  
|Klucz zasobu|Lokalizacja kategorii|Wartość|  
|-|-|-| 
|Button_1:system.Windows.Controls.button.$Content|Przycisk|OK|  
|Button_2:system.Windows.Controls.button.$Content|Przycisk|Abbrechen|  
|Button_3:system.Windows.Controls.button.$Content|Przycisk|Durchsuchen...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Tekst|WAR Geben Sie eines Namen Programms Ordners, Dokuments oder einer Internetresource.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Tekst|Öffnen:|  
|Window_1:system.Windows.window.Title|Tytuł|Uruchom|  
  
 **Generowanie**  
  
 Ostatni krok lokalizacja obejmuje tworzenie zestawu satelickiego nowo zlokalizowane. Można to zrobić za pomocą następującego polecenia LocBaml:  
  
 **LocBaml.exe / Generowanie RunDialog.resources.dll /trans:RunDialog.resources.dll.CSV/out:. /cUL:de-DE**  
  
 Na język niemiecki [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], jeśli ta resources.dll znajduje się w folderze de-DE, obok główny zestaw, ten zasób zostanie automatycznie załadowany zamiast w folderze en US. Jeśli nie masz wersji niemieckiej [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Aby to sprawdzić, należy ustawić kultura niezależnie od kultury [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] używają (tj. en US) i Zastąp oryginalny resources.dll.  
  
 **Ładowanie zasobów satelity**  
  
|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|Kod|Oryginalne angielskie BAML|BAML zlokalizowanych|  
|Kulturalnie neutralne zasoby|Inne zasoby w języku angielskim|Inne zasoby zlokalizowane na język niemiecki|  
  
 .NET framework automatycznie wybierze zestaw zasobów satelity obciążenia w zależności od aplikacji `Thread.CurrentThread.CurrentUICulture`. Wartością domyślną kulturę z Twojej [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systemu operacyjnego. Dlatego jeśli używasz niemiecki [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], de-DE\MyDialog.resources.dll ładuje, jeśli jest używany język angielski [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], ładuje en-US\MyDialog.resources.dll. Można ustawić zasobów ostatecznej rezerwowy dla aplikacji, określając NeutralResourcesLanguage w AssemblyInfo.* Twojego projektu. Na przykład jeśli określisz:  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 następnie en-US\MyDialog.resources.dll będą używane z systemu Windows w niemieckiej, jeśli de-DE\MyDialog.resources.dll lub de\MyDialog.resources.dll są niedostępne.  
  
### <a name="microsoft-saudi-arabia-homepage"></a>Strona główna programu Microsoft Arabia Saudyjska  
 Poniższej grafice Pokaż język angielski i język arabski strony głównej. Pełne przykładowej tworzącego te grafiki zobacz [przykładowe strony głównej globalizacji](http://go.microsoft.com/fwlink/?LinkID=159990).  
  
 **Angielski:**  
  
 ![Strona w języku angielskim](../../../../docs/framework/wpf/advanced/media/englishhomepage.jpg "EnglishHomepage")  
  
 **Arabski:**  
  
 ![Strona Arabic](../../../../docs/framework/wpf/advanced/media/arabichomepage.jpg "ArabicHomepage")  
  
### <a name="designing-a-global-microsoft-homepage"></a>Projektowanie globalne głównej firmy Microsoft  
 To makiety programu Microsoft Arabia Saudyjska funkcji globalizacji określonych języków RightToLeft przedstawiono witryny sieci web. Języków, takich jak hebrajski i arabski mają kolejność czytania od prawej do lewej, więc układ [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] często muszą być rozmieszczone odbywa się zupełnie inaczej niż w językach od lewej do prawej, takich jak angielski. Lokalizowanie z językiem od lewej do prawej na język od prawej do lewej lub odwrotnie może być bardzo trudne. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]został zaprojektowany aby znacznie ułatwić takie lokalizacje.  
  
 **Wartość FlowDirection**  
  
 *Homepage.XAML:*  
  
 [!code-xaml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 Powiadomienie <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość <xref:System.Windows.Controls.Page>. Zmienianie tej właściwości, aby <xref:System.Windows.FlowDirection.RightToLeft> zmieni <xref:System.Windows.FrameworkElement.FlowDirection%2A> z <xref:System.Windows.Controls.Page> i jego elementów podrzędnych, aby układ tego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest odwrócony można oczekiwać Arabic użytkownika stają się od prawej do lewej. Zachowanie dziedziczenia jedną można przesłonić, określając jawnego <xref:System.Windows.FrameworkElement.FlowDirection%2A> w dowolnym elemencie. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Właściwości jest dostępne na każdym <xref:System.Windows.FrameworkElement> lub dokumentu powiązany element a ma niejawne wartości <xref:System.Windows.FlowDirection.LeftToRight>.  
  
 Sprawdź, czy nawet pędzle gradientu tła są przerzucane prawidłowo po głównego <xref:System.Windows.FrameworkElement.FlowDirection%2A> zmiany:  
  
 **Wartość FlowDirection = "LeftToRight"**  
  
 ![Przepływ od lewej do prawej](../../../../docs/framework/wpf/advanced/media/lefttoright.PNG "LeftToRight")  
  
 **Wartość FlowDirection = "RightToLeft"**  
  
 ![Przepływ od prawej do lewej](../../../../docs/framework/wpf/advanced/media/righttoleft.PNG "RightToLeft")  
  
 **Unikaj używania stałe wymiary paneli i formantów**  
  
 Zapoznaj się za pośrednictwem Homepage.xaml, zwróć uwagę, że jako uzupełnienie stałej szerokości i wysokości określony dla całego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] u góry <xref:System.Windows.Controls.DockPanel>, istnieją inne wymiary stałym. Unikaj używania stałe wymiary zapobiegające wycinka zlokalizowanych tekst, który może być dłuższy niż tekst źródłowy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Panele i kontrolek będzie automatycznie na podstawie zawartości, które zawierają zmiany rozmiaru. Większość formantów również mieć minimalną i maksymalną wymiarów, które można ustawić, aby uzyskać większą kontrolę (tj. wartości elementu MinWidth = "20"). Z <xref:System.Windows.Controls.Grid>, można również ustawić za pomocą względną szerokości i wysokości "*" (tj. szerokość = "0,25\*") lub jego rozmiar komórki funkcja udostępniania.  
  
 **Komentarze w lokalizacji**  
  
 Istnieje wiele przypadków, w których zawartość może być niejednoznaczna i trudne do tłumaczenia. Deweloperem lub projektanta ma możliwość zapewnienia dodatkowego kontekstu i komentarze do wiadomość dla lokalizatorów za pośrednictwem lokalizacji komentarze. Na przykład poniżej Localization.Comments wyjaśnia sposób użycia znaku "&#124;".  
  
 [!code-xaml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 Ten komentarz skojarzenie z zawartością w TextBlock_1 i w przypadku narzędzia LocBaml (zobacz [lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)), może być widoczny w kolumnie 6 TextBlock_1 wiersza w pliku wyjściowego pliku CSV:  
  
|Klucz zasobu|Kategoria|Do odczytu|Można modyfikować|Komentarz|Wartość|  
|-|-|-|-|-|-|  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Tekst|WARTOŚĆ TRUE|WARTOŚĆ TRUE|Ten znak jest używany jako ozdobne reguły.|&#124;|  
  
 Komentarze mogą być umieszczane na zawartości lub właściwość elementu przy użyciu następującej składni:  
  
 [!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **Atrybuty lokalizacji**  
  
 Często dewelopera lub lokalizacja menedżera kontroli co wiadomość dla lokalizatorów można odczytywać i modyfikować. Na przykład nie można lokalizatora tłumaczenie nazwy firmy lub treść prawnych. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia Atrybuty, które umożliwiają skonfigurowanie czytelności, modifiability i Kategoria zawartości elementu lub właściwości, które narzędzie lokalizacji można użyć do blokowania, Ukryj lub sortowania elementów. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Localization.Attributes%2A>. Na potrzeby tego przykładu narzędzia LocBaml generuje tylko wartości tych atrybutów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wszystkie formanty mają przypisane wartości domyślne dla tych atrybutów, ale mogą one zastąpione. Na przykład poniższy przykład zastąpienia domyślnej lokalizacji atrybuty `TextBlock_1` i ustawia ale unmodifiable zawartość do odczytu wiadomość dla lokalizatorów.  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 Oprócz zwiększyć czytelność, a atrybuty modifiability [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wyliczenie wspólnych kategorii interfejsu użytkownika (<xref:System.Windows.LocalizationCategory>) można nadać wiadomość dla lokalizatorów więcej kontekstu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Domyślne kategorie dla formantów platformy może zostać zastąpiona w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] również:  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 Lokalizacja domyślna atrybuty, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia również może być zastąpiona przez kod, poprawnie można ustawić wartości domyślne prawa w przypadku kontrolek niestandardowych. Na przykład:  
  
 `[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]`  
  
 `public class CorporateLogo: TextBlock`  
  
 `{`  
  
 `…`  
  
 `..`  
  
 `.`  
  
 `}`  
  
 Dla wystąpienia atrybutów w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mają wyższy priorytet niż wartości ustawione w kodzie Kontrolki niestandardowe. Aby uzyskać więcej informacji dotyczących atrybutów i komentarze, zobacz [atrybuty lokalizacji i komentarze](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
 **Rezerwa czcionek i czcionek złożonych**  
  
 Jeśli określisz czcionki, która nie obsługuje danego punktu kodu zakresu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zostanie automatycznie rezerwowej na taki, który wykonuje się za pomocą globalnej Interface.compositefont użytkownika, który znajduje się w katalogu Windows\Fonts. Czcionki działają podobnie jak wszystkie inne czcionki i mogą być używane bezpośrednio przez ustawienie elementu FontFamily (tj. FontFamily = "Globalne interfejsu użytkownika"). Tworzenie własnych czcionka złożona i określając jakie czcionki do użycia dla określonych punktów kodowych znaków dwuskładnikowych zakresy i języków można określić własnych preferencji rezerwowy czcionki.  
  
 Aby uzyskać więcej informacji na temat czcionki zobacz <xref:System.Windows.Media.FontFamily>.  
  
 **Lokalizacja na stronie głównej firmy Microsoft**  
  
 Można wykonać te same czynności co w przykładzie Uruchom okno dialogowe, aby zlokalizować tę aplikację. Jest dostępne w pliku CSV zlokalizowane dla arabskiego [przykładowe strony głównej globalizacji](http://go.microsoft.com/fwlink/?LinkID=159990).
