---
title: Przegląd globalizacji i lokalizacji
description: Dowiedz się więcej na temat lokalizacji i globalizacji Windows Presentation Foundation, w tym automatycznego układu, zestawów satelickich i zlokalizowanych atrybutów.
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: 9a54ce2c265b989f99383ff9cdec961c80dd655c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168292"
---
# <a name="wpf-globalization-and-localization-overview"></a>Przegląd Lokalizacja i globalizacja WPF

Po ograniczeniu dostępności produktu tylko do jednego języka należy ograniczyć potencjalną bazę klientów do ułamka populacji na świecie 7 500 000 000. Jeśli chcesz, aby Twoje aplikacje miały dostęp do globalnej grupy odbiorców, to ekonomiczne i najbardziej ekonomiczne rozwiązanie do osiągnięcia większej liczby klientów.

W tym omówieniu przedstawiono globalizację i lokalizację w programie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] . Globalizacja to projekt i programowanie aplikacji, które działają w wielu lokalizacjach. Na przykład globalizacja obsługuje zlokalizowane interfejsy użytkownika i dane regionalne dla użytkowników w różnych kulturach. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oferuje globalne funkcje projektowe, w tym automatyczne układ, zestawy satelickie oraz zlokalizowane atrybuty i komentowanie.

Lokalizacja to tłumaczenie zasobów aplikacji na zlokalizowane wersje dla określonych kultur obsługiwanych przez aplikację. Podczas lokalizowania w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] należy używać interfejsów API w <xref:System.Windows.Markup.Localizer> przestrzeni nazw. Te interfejsy API służą do włączania narzędzia wiersza polecenia [Narzędzia LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml) . Aby uzyskać informacje na temat sposobu kompilowania i używania LocBaml, zobacz [lokalizowanie aplikacji](how-to-localize-an-application.md).

## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Najlepsze rozwiązania dotyczące globalizacji i lokalizacji w WPF

Większość funkcji globalizacji i lokalizacji, która jest wbudowana w program, można uzyskać, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykonując czynności opisane w sekcji Projektowanie interfejsu użytkownika i wskazówki dotyczące lokalizacji.

### <a name="best-practices-for-wpf-ui-design"></a>Najlepsze rozwiązania dotyczące projektowania interfejsu użytkownika WPF

Podczas projektowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na podstawie należy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rozważyć wdrożenie następujących najlepszych rozwiązań:

- Napisz swój [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod, Unikaj tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kodu. Podczas tworzenia przy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] użyciu programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] należy udostępnić go za pośrednictwem wbudowanych interfejsów API lokalizacji.

- Unikaj używania pozycji bezwzględnych i stałych rozmiarów do układania zawartości; Zamiast tego należy użyć względnej lub automatycznej zmiany wielkości.

  - Użyj <xref:System.Windows.Window.SizeToContent%2A> i Zachowaj szerokość i wysokość ustawione na `Auto` .

  - Unikaj korzystania <xref:System.Windows.Controls.Canvas> z programu w celu ustalenia układu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] s.

  - Użyj <xref:System.Windows.Controls.Grid> i jej funkcji udostępniania rozmiarów.

- Podaj dodatkowe miejsce na marginesie, ponieważ zlokalizowany tekst często wymaga większej ilości miejsca. Dodatkowe miejsce pozwala na możliwe nadwieszanie znaków.

- Włącz <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> <xref:System.Windows.Controls.TextBlock> , aby uniknąć obcinania.

- Ustaw `xml:lang` atrybut. Ten atrybut opisuje kulturę określonego elementu i jego elementów podrzędnych. Wartość tej właściwości zmienia zachowanie kilku funkcji w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Na przykład zmienia zachowanie dzielenia wyrazów, sprawdzania pisowni, podstawiania numerów, złożonego kształtu skryptu i powrotu do czcionki. Zobacz [globalizacja dla WPF](globalization-for-wpf.md) , aby uzyskać więcej informacji na temat ustawiania [obsługi XML: lang w języku XAML](../../../desktop-wpf/xaml-services/xml-language-handling.md).

- Utwórz dostosowaną czcionkę kompozytową, aby uzyskać lepszą kontrolę nad czcionkami używanymi w różnych językach. Domyślnie program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa czcionki GlobalUserInterface. Composite w katalogu Windows\Fonts.

- Podczas tworzenia aplikacji nawigacyjnych, które mogą być zlokalizowane w kulturze, która przedstawia tekst w formacie od prawej do lewej, należy jawnie ustawić dla <xref:System.Windows.FlowDirection> każdej strony, aby upewnić się, że strona nie dziedziczy po <xref:System.Windows.FlowDirection> <xref:System.Windows.Navigation.NavigationWindow> .

- Podczas tworzenia autonomicznych aplikacji nawigacyjnych, które są hostowane poza przeglądarką, ustaw <xref:System.Windows.Application.StartupUri%2A> dla początkowej aplikacji wartość <xref:System.Windows.Navigation.NavigationWindow> zamiast na stronę (na przykład `<Application StartupUri="NavigationWindow.xaml">` ). Ten projekt umożliwia zmianę <xref:System.Windows.FlowDirection> okna i paska nawigacyjnego. Aby uzyskać więcej informacji, zobacz przykład [strony głównej globalizacji](https://github.com/microsoft/WPF-Samples/tree/master/Globalization%20and%20Localization/GlobalizationHomepage).

### <a name="best-practices-for-wpf-localization"></a>Najlepsze rozwiązania dotyczące lokalizacji WPF

Podczas lokalizowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji opartych na programie należy rozważyć wdrożenie następujących najlepszych rozwiązań:

- Użyj komentarzy dotyczących lokalizacji, aby zapewnić dodatkowy kontekst dla lokalizatorów.

- Użyj atrybutów lokalizacji, aby kontrolować lokalizację zamiast wybiórczych pomijania <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości elementów. Aby uzyskać więcej informacji [, zobacz atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md) .

- Używaj `msbuild -t:updateuid` i, `-t:checkuid` Aby dodawać i sprawdzać <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Użyj <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości, aby śledzić zmiany między programowaniem i lokalizacją. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>Właściwości ułatwiają lokalizowanie nowych zmian programistycznych. W przypadku ręcznego dodawania <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , zadanie jest zwykle żmudnym i mniej dokładne.

  - Nie należy edytować ani zmieniać <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości po rozpoczęciu lokalizacji.

  - Nie używaj zduplikowanych <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości (należy pamiętać, że w przypadku korzystania z polecenia Kopiuj i wklej).

  - Ustaw `UltimateResourceFallback` lokalizację w AssemblyInfo. \* Aby określić odpowiedni język dla rezerwy (na przykład `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]` ).

    Jeśli zdecydujesz się na uwzględnienie języka źródłowego w zestawie głównym przez pominięcie `<UICulture>` znacznika w pliku projektu, ustaw `UltimateResourceFallback` lokalizację jako główny zestaw zamiast satelity (na przykład `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]` ).

## <a name="localize-a-wpf-application"></a>Lokalizowanie aplikacji WPF

W przypadku lokalizowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji istnieje kilka opcji. Na przykład można powiązać lokalizowalne zasoby w aplikacji z plikiem XML, przechowywać Lokalizowalny tekst w tabelach resx lub używać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików. W tej sekcji opisano przepływ pracy dotyczący lokalizacji, który używa formy BAML języka XAML, która zapewnia kilka korzyści:

- Po skompilowaniu można zlokalizować.

- Możesz przeprowadzić aktualizację do nowszej wersji formy BAML języka XAML z lokalizacjami ze starszej wersji formy BAML języka XAML, aby można było ją zlokalizować w tym samym czasie.

- Można sprawdzić poprawność oryginalnych elementów źródłowych i semantyki w czasie kompilacji, ponieważ forma BAML języka XAML jest skompilowaną formą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

### <a name="localization-build-process"></a>Proces tworzenia lokalizacji

Podczas tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji proces kompilacji dla lokalizacji jest następujący:

- Deweloper tworzy i globalizacj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikację. W pliku projektu zestaw deweloperów `<UICulture>en-US</UICulture>` tak, aby podczas kompilowania aplikacji został wygenerowany zestaw główny, który jest niezależny od języka. Ten zestaw zawiera plik .resources.dll satelitarnych, który zawiera wszystkie lokalizowalne zasoby. Opcjonalnie można zachować język źródłowy w zestawie głównym, ponieważ nasze interfejsy API lokalizacji obsługują wyodrębnianie z głównego zestawu.

- Gdy plik jest kompilowany do kompilacji, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest konwertowany na postać BAML języka XAML. Kulturowo neutralne `MyDialog.exe` i zależne od kultury pliki (angielskie) `MyDialog.resources.dll` są udostępniane dla klienta w języku angielskim.

### <a name="localization-workflow"></a>Przepływ pracy lokalizacji

Proces lokalizacji rozpocznie się po skompilowaniu niezlokalizowanego `MyDialog.resources.dll` pliku. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Elementy i właściwości w pierwotnej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] postaci są wyodrębniane z formy BAML języka XAML do par klucz-wartość przy użyciu interfejsów API w ramach programu <xref:System.Windows.Markup.Localizer> . Lokalizatory używają par klucz-wartość do lokalizowania aplikacji. Nowe .resource.dll można generować z nowych wartości po zakończeniu lokalizacji.

Klucze par klucz-wartość są `x:Uid` wartościami, które są umieszczane przez dewelopera w oryginalnym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Te `x:Uid` wartości umożliwiają interfejsowi API śledzenie i scalanie zmian, które są wykonywane między deweloperem i lokalizatorem podczas lokalizacji. Na przykład, jeśli deweloper zmieni się [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] po rozpoczęciu lokalizowania, można scalić zmiany programistyczne z już ukończoną lokalizacją, aby zapewnić utratę minimalnej pracy tłumaczenia.

Na poniższej ilustracji przedstawiono typowy przepływ pracy lokalizacji oparty na formularzu BAML języka XAML. Na tym diagramie założono, że deweloper zapisuje aplikację w języku angielskim. Deweloper tworzy i globalizacj aplikację WPF. W pliku projektu zestawy deweloperów, `<UICulture>en-US</UICulture>` tak aby podczas kompilacji, zestaw główny, który jest niezależny od języka, są generowane przy użyciu satelity .resources.dll zawierającego wszystkie lokalizowalne zasoby. Alternatywnie, jeden może zachować język źródłowy w zestawie głównym, ponieważ interfejsy API lokalizacji WPF obsługują wyodrębnianie z głównego zestawu. Po zakończeniu procesu kompilacji kod XAML zostanie skompilowany jako BAML. Niezależne od kultury MyDialog.exe.resources.dll są wysyłane do angielskiej wersji językowej.

![Diagram przedstawiający przepływ pracy lokalizacji.](./media/wpf-globalization-and-localization-overview/localization-workflow.png)

![Diagram przedstawiający nielokalny przepływ pracy.](./media/wpf-globalization-and-localization-overview/unlocalized-workflow.png)

## <a name="examples-of-wpf-localization"></a>Przykłady lokalizacji WPF

Ta sekcja zawiera przykłady zlokalizowanych aplikacji, które ułatwiają zrozumienie sposobu kompilowania i lokalizowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.

### <a name="run-dialog-box-example"></a>Uruchom okno dialogowe przykład

Poniższa Grafika przedstawia dane wyjściowe okna dialogowego **uruchamiania** .

**Angielski:**

![Zrzut ekranu przedstawiający okno dialogowe Uruchamianie w języku angielskim.](./media/wpf-globalization-and-localization-overview/run-dialog-box-english.png)

**Niemiecki:**

![Zrzut ekranu przedstawiający okno dialogowe uruchamiania w języku niemieckim.](./media/wpf-globalization-and-localization-overview/run-dialog-box-german.png)

**Projektowanie okna dialogowego uruchamiania globalnego**

Ten przykład generuje okno dialogowe **uruchamiania** przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . To okno dialogowe jest równoważne z oknem dialogowym **uruchamiania** , które jest dostępne w menu Start systemu Microsoft Windows.

Niektóre najważniejsze elementy okna dialogowego tworzenia globalnego są następujące:

**Układ automatyczny**

*W window1. XAML:*

`<Window SizeToContent="WidthAndHeight">`

Poprzednia Właściwość okna automatycznie zmienia rozmiar okna zgodnie z rozmiarem zawartości. Ta właściwość Zapobiega wycięciu zawartości okna, która zwiększa rozmiar po lokalizacji; powoduje również usunięcie niepotrzebnych spacji w przypadku zmniejszenia rozmiaru zawartości po lokalizacji.

`<Grid x:Uid="Grid_1">`

<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>Aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsy API lokalizacji działały prawidłowo, są konieczne właściwości.

Są one używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsy API lokalizacyjne do śledzenia zmian między programowaniem i lokalizacją [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>właściwości umożliwiają scalanie nowszej wersji programu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ze starszą lokalizacją [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Dodaj <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> Właściwość przez uruchomienie `msbuild -t:updateuid RunDialog.csproj` w powłoce poleceń. Jest to zalecana metoda dodawania właściwości, <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> ponieważ Ręczne dodawanie są zwykle czasochłonne i mniej dokładne. Aby sprawdzić, czy <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości zostały prawidłowo ustawione, należy uruchomić `msbuild -t:checkuid RunDialog.csproj` .

[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Jest to struktura przy użyciu <xref:System.Windows.Controls.Grid> kontrolki, która jest przydatną kontrolą do korzystania z automatycznego układu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Należy pamiętać, że okno dialogowe jest podzielone na trzy wiersze i pięć kolumn. Nie jeden z definicji wiersza i kolumny ma stały rozmiar; w związku z tym [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy, które są pozycjonowane w każdej komórce, można dostosowywać do zwiększania i zmniejszania rozmiaru podczas lokalizacji.

[!code-xaml[GlobalizationRunDialog#GridColumnDef](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]

Pierwsze dwie kolumny, w których w kolumnie **Open:** i <xref:System.Windows.Controls.ComboBox> są umieszczone 10% [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] całkowitej szerokości.

[!code-xaml[GlobalizationRunDialog#GridColumnDef2](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]

Należy zauważyć, że w przykładzie zastosowano funkcję współużytkowanego określania wielkości <xref:System.Windows.Controls.Grid> . Ostatnie trzy kolumny wykorzystują tę możliwość, umieszczając je w tym samym <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> . Jeden z nich będzie oczekiwał od nazwy właściwości, dzięki czemu kolumny mogą współużytkować ten sam rozmiar. Tak więc, gdy "Przeglądaj..." jest zlokalizowany na dłuższym ciągu "Durchsuchen...", a wszystkie przyciski rozwijają się w szerokości zamiast mieć niewielki przycisk "OK" i nieproporcjonalnie duży "Durchsuchen..." przycisk.

**XML: lang**

`xml:lang="en-US"`

Zwróć uwagę, że [Obsługa języka XML: lang w języku XAML](../../../desktop-wpf/xaml-services/xml-language-handling.md) umieszczonym w elemencie głównym elementu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Ta właściwość opisuje kulturę danego elementu i jego elementów podrzędnych. Ta wartość jest używana przez kilka funkcji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i powinna być odpowiednio zmieniana podczas lokalizacji. Ta wartość zmienia używany słownik języka do dzielenia wyrazów i sprawdzania pisowni. Ma także wpływ na wyświetlanie cyfr i sposób, w jaki system rezerwowy czcionki wybiera czcionkę do użycia. Na koniec Właściwość wpływa na sposób wyświetlania liczb i sposób, w jaki teksty złożone w złożonych skryptach są w kształcie. Wartość domyślna to "pl-US".

**Kompilowanie zestawu zasobów satelitarnych**

*W. csproj:*

Edytuj `.csproj` plik i Dodaj następujący tag do bezwarunkowego `<PropertyGroup>` :

`<UICulture>en-US</UICulture>`

Zwróć uwagę na dodanie `UICulture` wartości. Gdy ta wartość jest równa prawidłowej <xref:System.Globalization.CultureInfo> wartości, takiej jak en-us, kompilowanie projektu spowoduje wygenerowanie zestawu satelickiego ze wszystkimi lokalizowalnymi zasobami.

`<Resource Include="RunIcon.JPG">`

`<Localizable>False</Localizable>`

`</Resource>`

Nie `RunIcon.JPG` musi być lokalizowana, ponieważ powinna być taka sama we wszystkich kulturach. `Localizable`jest ustawiona na `false` tak, aby pozostała w zestawie głównym niezależnym od języka, a nie w zestawie satelickim. Wartość domyślna wszystkich zasobów noncompilable jest `Localizable` ustawiona na `true` .

**Lokalizowanie okna dialogowego uruchamiania**

**Analizuj**

Po skompilowaniu aplikacji pierwszy krok lokalizowania zasobów jest analizowany z zestawu satelickiego. Na potrzeby tego tematu Użyj przykładowego narzędzia LocBaml, które można znaleźć w [przykładowym narzędziu LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml). Należy pamiętać, że LocBaml to tylko przykładowe narzędzie, które ułatwia rozpoczęcie pracy nad tworzeniem narzędzia lokalizacyjnego, które mieści się w procesie lokalizacji. Korzystając z LocBaml, uruchom następujące polecenie, aby przeanalizować: **LocBaml/parse RunDialog.resources.dll/out:** aby wygenerować plik "RunDialog.resources.dll.CSV".

**Zlokalizować**

Użyj ulubionego edytora CSV, który obsługuje kodowanie Unicode, aby edytować ten plik. Odfiltruj wszystkie wpisy z kategorią lokalizacji "Brak". Powinny pojawić się następujące wpisy:

|Klucz zasobu|Kategoria lokalizacji|Wartość|
|-|-|-|
|Button_1: System. Windows. Controls. Button. $Content|Przycisk|OK|
|Button_2: System. Windows. Controls. Button. $Content|Przycisk|Anuluj|
|Button_3: System. Windows. Controls. Button. $Content|Przycisk|Przeglądaj...|
|ComboBox_1: System. Windows. Controls. ComboBox. $Content|ComboBox||
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Tekst|Wpisz nazwę programu, folderu, dokumentu lub zasobu internetowego, a system Windows go otworzy.|
|TextBlock_2: System. Windows. Controls. TextBlock. $Content|Tekst|Otwórz:|
|Window_1: System. Windows. Window. title|Tytuł|Uruchom|

Lokalizowanie aplikacji do wersji niemieckiej wymaga następujących tłumaczeń:

|Klucz zasobu|Kategoria lokalizacji|Wartość|
|-|-|-|
|Button_1: System. Windows. Controls. Button. $Content|Przycisk|OK|
|Button_2: System. Windows. Controls. Button. $Content|Przycisk|Abbrechen|
|Button_3: System. Windows. Controls. Button. $Content|Przycisk|Durchsuchen...|
|ComboBox_1: System. Windows. Controls. ComboBox. $Content|ComboBox||
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Tekst|Geben sie Den Namen, eines, Ordners, Dokuments Oder einer Internetresource.|
|TextBlock_2: System. Windows. Controls. TextBlock. $Content|Tekst|Öffnen:|
|Window_1: System. Windows. Window. title|Tytuł|Uruchom|

**Generowanie**

Ostatni krok lokalizacji obejmuje utworzenie nowo zlokalizowanego zestawu satelickiego. Można to zrobić za pomocą następującego polecenia LocBaml:

**LocBaml.exe/Generate RunDialog.resources.dll/trans:RunDialog.resources.dll.CSV/out:. /CUL: de-DE**

W przypadku okien niemieckich, jeśli ten resources.dll zostanie umieszczony w folderze de-DE obok zestawu głównego, ten zasób zostanie automatycznie załadowany zamiast tego w folderze en-US. Jeśli nie masz niemieckiej wersji systemu Windows do przetestowania, ustaw kulturę na dowolną kulturę systemu Windows, z której korzystasz (na przykład `en-US` ), i Zastąp pierwotną bibliotekę DLL zasobów.

**Ładowanie zasobów satelitarnych**

|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|
|------------------|------------------------------------|------------------------------------|
|Kod|Oryginalna BAML|Zlokalizowana BAML|
|Zasoby neutralne dla kultury|Inne zasoby w języku angielskim|Inne zasoby zlokalizowane do wersji niemieckiej|

Platforma .NET automatycznie wybiera, który zestaw zasobów satelitarnych ma zostać załadowany na podstawie aplikacji <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> . Ta wartość domyślna jest kulturą systemu operacyjnego Windows. W przypadku korzystania z systemu Windows w języku niemieckim *de-DE\MyDialog.resources.dll* ładowania pliku. W przypadku korzystania z systemu Windows w języku angielskim *en-US\MyDialog.resources.dll* ładowania pliku. Możesz ustawić ostateczny rezerwowy zasób dla aplikacji, określając `NeutralResourcesLanguage` atrybut w pliku *AssemblyInfo* projektu. Na przykład, jeśli określisz:

`[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`

następnie plik *en-US\MyDialog.resources.dll* jest używany z niemieckimi oknami, jeśli nie są dostępne żadne z następujących plików: *de-DE\MyDialog.resources.dll* lub *de\MyDialog.resources.dll*.

### <a name="microsoft-saudi-arabia-homepage"></a>Strona główna Microsoft Arabia Saudyjska

Na poniższej grafice przedstawiono angielskie i arabskiej stronę główną. Aby zapoznać się z kompletnym przykładem, który tworzy te grafiki, zobacz sekcję dotyczącą [globalizacji strony głównej](https://github.com/microsoft/WPF-Samples/tree/master/Globalization%20and%20Localization/GlobalizationHomepage).

**Angielski:**

![Zrzut ekranu przedstawiający stronę główną w języku angielskim.](./media/wpf-globalization-and-localization-overview/english-home-page-sample.jpg)

**Arabski:**

![Zrzut ekranu przedstawiający arabskiej strony głównej.](./media/wpf-globalization-and-localization-overview/arabic-home-page-sample.jpg)

### <a name="designing-a-global-microsoft-home-page"></a>Projektowanie globalnej strony głównej firmy Microsoft

Ten makieta witryny sieci Web Microsoft Arabia Saudyjska ilustruje funkcje globalizacji dostępne dla języków RightToLeft. Języki takie jak hebrajski i arabski mają kolejność odczytywania od prawej do lewej, więc układ [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musi być często określany w inny sposób niż w językach od lewej do prawej, np. w języku angielskim. Lokalizowanie z języka od lewej do prawej do języka od prawej do lewej lub odwrotnie może być bardzo trudne. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]została zaprojektowana, aby znacznie ułatwić tworzenie takich lokalizacji.

**FlowDirection**

*Strona główna. XAML:*

[!code-xaml[GlobalizationHomepage#Homepage](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]

Zwróć uwagę <xref:System.Windows.FrameworkElement.FlowDirection%2A> na Właściwość <xref:System.Windows.Controls.Page> . Zmiana tej właściwości na wartość <xref:System.Windows.FlowDirection.RightToLeft> spowoduje zmianę elementu <xref:System.Windows.FrameworkElement.FlowDirection%2A> <xref:System.Windows.Controls.Page> i jego elementów podrzędnych w taki sposób, aby układ tego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] obiektu został przerzucony tak, aby stał się od prawej do lewej w przypadku, gdy oczekiwany jest użytkownik arabski. Jeden może przesłonić zachowanie dziedziczenia, określając jawnie <xref:System.Windows.FrameworkElement.FlowDirection%2A> dla dowolnego elementu. <xref:System.Windows.FrameworkElement.FlowDirection%2A>Właściwość jest dostępna dla dowolnego <xref:System.Windows.FrameworkElement> elementu lub dokumentu powiązanego i ma niejawną wartość <xref:System.Windows.FlowDirection.LeftToRight> .

Zwróć uwagę, że nawet pędzle gradientu w tle są przerzucane prawidłowo po zmianie elementu głównego <xref:System.Windows.FrameworkElement.FlowDirection%2A> :

**FlowDirection = "LeftToRight"**

![Zrzut ekranu przedstawiający przepływ gradientu od lewej do prawej.](./media/wpf-globalization-and-localization-overview/gradient-flow-left-right.png)

**FlowDirection = "RightToLeft"**

![Zrzut ekranu przedstawiający przepływ gradientu od prawej do lewej.](./media/wpf-globalization-and-localization-overview/gradient-flow-right-left.png)

**Unikaj używania stałych wymiarów dla paneli i kontrolek**

Zapoznaj się z dokumentem Strona główna. XAML, zwróć uwagę na to, że od ustalonej szerokości i wysokości określonej dla całego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] na górze <xref:System.Windows.Controls.DockPanel> nie ma żadnych stałych wymiarów. Unikaj używania stałych wymiarów, aby zapobiec przycinaniu zlokalizowanego tekstu, który może być dłuższy niż tekst źródłowy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Panele i kontrolki będą automatycznie zmieniać rozmiar na podstawie zawartości, która zawiera. Większość formantów ma także minimalne i maksymalne wymiary, które można ustawić w celu uzyskania większej kontroli (na przykład MinWidth = "20"). W programie <xref:System.Windows.Controls.Grid> można również ustawić szerokości względne i wysokość przy użyciu " \* " (na przykład `Width="0.25*"` ) lub użyć funkcji udostępniania rozmiaru komórki.

**Komentarze dotyczące lokalizacji**

Istnieje wiele przypadków, w których zawartość może być niejednoznaczna i trudny do przetłumaczenia. Deweloper lub Projektant ma możliwość udostępnienia dodatkowego kontekstu i komentarzy do lokalizatorów przy użyciu komentarzy do lokalizacji. Na przykład lokalizacja. komentarze poniżej wyjaśnia użycie znaku "&#124;".

[!code-xaml[GlobalizationHomepage#LocalizationComment](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]

Ten komentarz jest kojarzony z zawartością TextBlock_1 i w przypadku narzędzia LocBaml (zobacz temat [lokalizowanie aplikacji](how-to-localize-an-application.md)). można go zobaczyć w szóstej kolumnie TextBlock_1 wiersza w pliku Output. CSV:

|Klucz zasobu|Kategoria|Odczytu|Można modyfikować|Komentarz|Wartość|
|-|-|-|-|-|-|
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Tekst|Prawda|Prawda|Ten znak jest używany jako reguła dekoracyjna.|&#124;|

Komentarze mogą być umieszczane na zawartości lub właściwości dowolnego elementu przy użyciu następującej składni:

[!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]

**Atrybuty lokalizacji**

Często menedżerowie deweloperów lub lokalizacji wymagają kontroli, jakie lokalizatory mogą odczytywać i modyfikować. Na przykład możesz nie chcieć, aby lokalizator przetłumaczy nazwę firmy lub wyraz prawny. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera atrybuty, które umożliwiają ustawienie czytelności, modifiability i kategorii zawartości lub właściwości elementu, którego narzędzie lokalizacyjne może używać do blokowania, ukrywania i sortowania elementów. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Localization.Attributes%2A>. Na potrzeby tego przykładu narzędzie LocBaml jedynie wyprowadza wartości tych atrybutów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kontrolki All mają wartości domyślne dla tych atrybutów, ale można je zastąpić. Na przykład poniższy przykład zastępuje domyślne atrybuty lokalizacji dla `TextBlock_1` i ustawia zawartość do odczytu, ale nie można jej modyfikować dla lokalizatorów.

[!code-xaml[LocalizationComAtt#LocalizationAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]

Oprócz atrybutów czytelności i modifiability, program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia Wyliczenie wspólnych kategorii interfejsu użytkownika ( <xref:System.Windows.LocalizationCategory> ), które mogą być używane do nadawania więcej kontekstu dla lokalizatorów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Domyślne kategorie dla kontrolek platformy można [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] również zastąpić:

[!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]

Domyślne atrybuty lokalizacji, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia, można również zastąpić za pomocą kodu, więc można prawidłowo ustawić odpowiednie wartości domyślne dla kontrolek niestandardowych. Na przykład:

```csharp
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]
public class CorporateLogo : TextBlock
{
    // ...
}
```

Atrybuty na wystąpienie ustawione w programie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mają pierwszeństwo przed wartościami ustawionymi w kodzie w kontrolkach niestandardowych. Aby uzyskać więcej informacji o atrybutach i komentarzach, zobacz temat [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).

**Czcionki bazowe i kompozytowe czcionek**

Jeśli określisz czcionkę, która nie obsługuje danego zakresu kodu, program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] automatycznie powróci do jednego z nich, korzystając z globalnego interfejsu użytkownika. compositefont, który znajduje się w katalogu Windows\Fonts. Czcionki złożone działają podobnie jak jakakolwiek inna czcionka i mogą być używane jawnie przez ustawienie elementu `FontFamily` (na przykład `FontFamily="Global User Interface"` ). Możesz określić własne preferencje powrotu do czcionki, tworząc własną czcionkę złożoną i określając czcionkę używaną dla konkretnych kodu zakresów i języków.

Aby uzyskać więcej informacji na temat czcionek złożonych, zobacz <xref:System.Windows.Media.FontFamily> .

**Lokalizowanie strony głównej firmy Microsoft**

Aby zlokalizować tę aplikację, można wykonać te same czynności co w oknie dialogowym uruchamiania. Zlokalizowany plik CSV dla języka arabskiego jest dostępny dla Ciebie w [przykładowej stronie głównej globalizacji](https://github.com/microsoft/WPF-Samples/tree/master/Globalization%20and%20Localization/GlobalizationHomepage).
