---
title: Przegląd Lokalizacja i globalizacja WPF
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: a912e0437bf986aff65fc722065e912571427189
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035786"
---
# <a name="wpf-globalization-and-localization-overview"></a>Przegląd Lokalizacja i globalizacja WPF

Po ograniczeniu dostępności produktu tylko do jednego języka należy ograniczyć potencjalną bazę klientów do ułamka populacji na świecie 6 500 000 000. Jeśli chcesz, aby Twoje aplikacje miały dostęp do globalnej grupy odbiorców, to ekonomiczne i najbardziej ekonomiczne rozwiązanie do osiągnięcia większej liczby klientów.

W tym omówieniu przedstawiono globalizację i lokalizację w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Globalizacja to projekt i programowanie aplikacji, które działają w wielu lokalizacjach. Na przykład globalizacja obsługuje zlokalizowane interfejsy użytkownika i dane regionalne dla użytkowników w różnych kulturach. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje globalne funkcje projektowe, w tym automatyczne układy, zestawy satelickie i zlokalizowane atrybuty i komentowanie.

Lokalizacja to tłumaczenie zasobów aplikacji na zlokalizowane wersje dla określonych kultur obsługiwanych przez aplikację. Podczas lokalizowania w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]należy używać interfejsów API w przestrzeni nazw <xref:System.Windows.Markup.Localizer>. Te interfejsy API służą do włączania narzędzia wiersza polecenia [Narzędzia LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016) . Aby uzyskać informacje na temat sposobu kompilowania i używania LocBaml, zobacz [lokalizowanie aplikacji](how-to-localize-an-application.md).

## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Najlepsze rozwiązania dotyczące globalizacji i lokalizacji w WPF

Większość funkcji globalizacji i lokalizacji, która jest wbudowana w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], można wykonać, wykonując czynności opisane w sekcji Projektowanie interfejsu użytkownika i wskazówki dotyczące lokalizacji.

### <a name="best-practices-for-wpf-ui-design"></a>Najlepsze rozwiązania dotyczące projektowania interfejsu użytkownika WPF

Podczas projektowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]opartych na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]należy rozważyć wdrożenie następujących najlepszych rozwiązań:

- Napisz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; Unikaj tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w kodzie. Po utworzeniu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy uwidocznić go za pośrednictwem wbudowanych interfejsów API lokalizacji.

- Unikaj używania pozycji bezwzględnych i stałych rozmiarów do układania zawartości; Zamiast tego należy użyć względnej lub automatycznej zmiany wielkości.

  - Użyj <xref:System.Windows.Window.SizeToContent%2A> i Zachowaj szerokość i wysokość ustawione na `Auto`.

  - Należy unikać używania <xref:System.Windows.Controls.Canvas> do określania układu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s.

  - Użyj <xref:System.Windows.Controls.Grid> i jej funkcji udostępniania rozmiarów.

- Podaj dodatkowe miejsce na marginesie, ponieważ zlokalizowany tekst często wymaga większej ilości miejsca. Dodatkowe miejsce pozwala na możliwe nadwieszanie znaków.

- Włącz <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> na <xref:System.Windows.Controls.TextBlock>, aby uniknąć obcinania.

- Ustaw atrybut `xml:lang`. Ten atrybut opisuje kulturę określonego elementu i jego elementów podrzędnych. Wartość tej właściwości zmienia zachowanie kilku funkcji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Na przykład zmienia zachowanie dzielenia wyrazów, sprawdzania pisowni, podstawiania numerów, złożonego kształtu skryptu i powrotu do czcionki. Zobacz [globalizacja dla WPF](globalization-for-wpf.md) , aby uzyskać więcej informacji na temat ustawiania [obsługi XML: lang w języku XAML](../../xaml-services/xml-lang-handling-in-xaml.md).

- Utwórz dostosowaną czcionkę kompozytową, aby uzyskać lepszą kontrolę nad czcionkami używanymi w różnych językach. Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa czcionki GlobalUserInterface. Composite w katalogu Windows\Fonts.

- Podczas tworzenia aplikacji nawigacyjnych, które mogą być lokalizowane w kulturze, która przedstawia tekst w formacie od prawej do lewej, jawnie ustaw <xref:System.Windows.FlowDirection> każdej strony, aby upewnić się, że strona nie dziedziczy <xref:System.Windows.FlowDirection> z <xref:System.Windows.Navigation.NavigationWindow>.

- Podczas tworzenia autonomicznych aplikacji nawigacyjnych, które są hostowane poza przeglądarką, należy ustawić <xref:System.Windows.Application.StartupUri%2A> dla początkowej aplikacji na <xref:System.Windows.Navigation.NavigationWindow> zamiast na stronie (na przykład `<Application StartupUri="NavigationWindow.xaml">`). Ten projekt umożliwia zmianę <xref:System.Windows.FlowDirection> okna i paska nawigacyjnego. Aby uzyskać więcej informacji, zobacz przykład [strony głównej globalizacji](https://go.microsoft.com/fwlink/?LinkID=159990).

### <a name="best-practices-for-wpf-localization"></a>Najlepsze rozwiązania dotyczące lokalizacji WPF

Podczas lokalizowania aplikacji opartych na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]należy rozważyć wdrożenie następujących najlepszych rozwiązań:

- Użyj komentarzy dotyczących lokalizacji, aby zapewnić dodatkowy kontekst dla lokalizatorów.

- Użyj atrybutów lokalizacji, aby kontrolować lokalizację zamiast wybiórczego pomijania <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości elementów. Aby uzyskać więcej informacji [, zobacz atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md) .

- `msbuild -t:updateuid` i `-t:checkuid` umożliwiają dodawanie i sprawdzanie właściwości <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Użyj właściwości <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>, aby śledzić zmiany między programowaniem i lokalizacją. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości ułatwiają lokalizowanie nowych zmian programistycznych. W przypadku ręcznego dodawania <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]zadanie jest zwykle żmudnym i mniej dokładne.

  - Nie należy edytować ani zmieniać właściwości <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> po rozpoczęciu lokalizacji.

  - Nie używaj zduplikowanych właściwości <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> (należy pamiętać, że w przypadku korzystania z polecenia Kopiuj i wklej).

  - Ustaw lokalizację `UltimateResourceFallback` w AssemblyInfo. *, aby określić odpowiedni język dla powrotu (na przykład `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).

    Jeśli użytkownik zdecyduje się na uwzględnienie języka źródłowego w zestawie głównym przez pominięcie znacznika `<UICulture>` w pliku projektu, należy ustawić lokalizację `UltimateResourceFallback` jako główny zestaw zamiast satelity (na przykład `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).

## <a name="localize-a-wpf-application"></a>Lokalizowanie aplikacji WPF

W przypadku lokalizowania aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można korzystać z kilku opcji. Można na przykład powiązać lokalizowalne zasoby w aplikacji z plikiem [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], przechowywać Lokalizowalny tekst w tabelach resx lub używać plików [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. W tej sekcji opisano przepływ pracy dotyczący lokalizacji, który używa formy BAML języka XAML, która zapewnia kilka korzyści:

- Po skompilowaniu można zlokalizować.

- Możesz przeprowadzić aktualizację do nowszej wersji formy BAML języka XAML z lokalizacjami ze starszej wersji formy BAML języka XAML, aby można było ją zlokalizować w tym samym czasie.

- Można sprawdzić poprawność oryginalnych elementów źródłowych i semantyki w czasie kompilacji, ponieważ forma BAML języka XAML jest skompilowaną formą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

### <a name="localization-build-process"></a>Proces tworzenia lokalizacji

Podczas tworzenia aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] proces tworzenia lokalizacji jest następujący:

- Deweloper tworzy i globalizacj aplikację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. W pliku projektu, deweloper ustawia `<UICulture>en-US</UICulture>` tak, aby podczas kompilowania aplikacji Wygenerowano zestaw główny, który jest niezależny od języka. Ten zestaw ma plik satelickie. resources. dll, który zawiera wszystkie lokalizowalne zasoby. Opcjonalnie można zachować język źródłowy w zestawie głównym, ponieważ nasze interfejsy API lokalizacji obsługują wyodrębnianie z głównego zestawu.

- Gdy plik jest kompilowany do kompilacji, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest konwertowany na postać BAML języka XAML. `MyDialog.exe` neutralnie kulturowe i zależne od kultury (angielskie) pliki `MyDialog.resources.dll` są udostępniane dla klienta w języku angielskim.

### <a name="localization-workflow"></a>Przepływ pracy lokalizacji

Proces lokalizacji rozpocznie się po skompilowaniu niezlokalizowanego pliku `MyDialog.resources.dll`. Elementy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i właściwości w oryginalnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są wyodrębniane z formy BAML języka XAML do par klucz-wartość przy użyciu interfejsów API w obszarze <xref:System.Windows.Markup.Localizer>. Lokalizatory używają par klucz-wartość do lokalizowania aplikacji. Po zakończeniu lokalizowania można wygenerować nowy plik Resource. dll z nowych wartości.

Klucze par klucz-wartość są `x:Uid` wartości, które są umieszczane przez dewelopera w pierwotnym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Te `x:Uid` wartości umożliwiają interfejsowi API śledzenie i scalanie zmian, które występują między deweloperem i lokalizatorem podczas lokalizacji. Na przykład, jeśli deweloper zmieni [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] po rozpoczęciu lokalizowania, można scalić zmiany programistyczne z już ukończoną lokalizacją, aby zapewnić utratę minimalnej pracy tłumaczenia.

Na poniższej ilustracji przedstawiono typowy przepływ pracy lokalizacji oparty na formularzu BAML języka XAML. Na tym diagramie założono, że deweloper zapisuje aplikację w języku angielskim. Deweloper tworzy i globalizacj aplikację WPF. W pliku projektu, deweloper ustawia `<UICulture>en-US</UICulture>` tak, aby podczas kompilowania zestaw główny niezależny od języka zostanie wygenerowany z satelitą. resources. dll zawierającym wszystkie lokalizowalne zasoby. Alternatywnie, jeden może zachować język źródłowy w zestawie głównym, ponieważ interfejsy API lokalizacji WPF obsługują wyodrębnianie z głównego zestawu. Po zakończeniu procesu kompilacji kod XAML zostanie skompilowany jako BAML. Plik. exe. resources. dll o kulturze neutralnej jest dostarczany do angielskiej wersji językowej.

![Diagram przedstawiający przepływ pracy lokalizacji.](./media/wpf-globalization-and-localization-overview/localization-workflow.png)

![Diagram przedstawiający nielokalny przepływ pracy.](./media/wpf-globalization-and-localization-overview/unlocalized-workflow.png)

## <a name="examples-of-wpf-localization"></a>Przykłady lokalizacji WPF

Ta sekcja zawiera przykłady zlokalizowanych aplikacji, które ułatwiają zrozumienie sposobu kompilowania i lokalizowania aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

#### <a name="run-dialog-box-example"></a>Uruchom okno dialogowe przykład

Poniższa Grafika przedstawia dane wyjściowe okna dialogowego **uruchamiania** .

**Angielski:**

![Zrzut ekranu przedstawiający okno dialogowe Uruchamianie w języku angielskim.](./media/wpf-globalization-and-localization-overview/run-dialog-box-english.png)

**Niemiecki:**

![Zrzut ekranu przedstawiający okno dialogowe uruchamiania w języku niemieckim.](./media/wpf-globalization-and-localization-overview/run-dialog-box-german.png)

**Projektowanie okna dialogowego uruchamiania globalnego**

Ten przykład generuje okno dialogowe **uruchamiania** przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. To okno dialogowe jest równoważne z oknem dialogowym **uruchamiania** , które jest dostępne w menu Start systemu Microsoft Windows.

Niektóre najważniejsze elementy okna dialogowego tworzenia globalnego są następujące:

**Układ automatyczny**

*W window1. XAML:*

`<Window SizeToContent="WidthAndHeight">`

Poprzednia Właściwość okna automatycznie zmienia rozmiar okna zgodnie z rozmiarem zawartości. Ta właściwość Zapobiega wycięciu zawartości okna, która zwiększa rozmiar po lokalizacji; powoduje również usunięcie niepotrzebnych spacji w przypadku zmniejszenia rozmiaru zawartości po lokalizacji.

`<Grid x:Uid="Grid_1">`

Aby interfejsy API lokalizacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] działały prawidłowo, <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości są zbędne.

Są one używane przez interfejsy API lokalizacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], aby śledzić zmiany między programowaniem i lokalizowaniem [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości umożliwiają scalanie nowszej wersji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z użyciem starszej lokalizacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Należy dodać właściwość <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>, uruchamiając `msbuild -t:updateuid RunDialog.csproj` w powłoce poleceń. Jest to zalecana metoda dodawania <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości, ponieważ Ręczne dodawanie są zwykle czasochłonne i mniej dokładne. Aby sprawdzić, czy właściwości <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> są prawidłowo ustawione, należy uruchomić `msbuild -t:checkuid RunDialog.csproj`.

[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest strukturalna przy użyciu kontrolki <xref:System.Windows.Controls.Grid>, która jest przydatną kontrolą do korzystania z automatycznego układu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Należy pamiętać, że okno dialogowe jest podzielone na trzy wiersze i pięć kolumn. Nie jeden z definicji wiersza i kolumny ma stały rozmiar; w związku z tym, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy, które są pozycjonowane w każdej komórce, można dostosowywać do zwiększania i zmniejszania rozmiaru podczas lokalizacji.

[!code-xaml[GlobalizationRunDialog#GridColumnDef](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]

Pierwsze dwie kolumny, w których w polu **Open:** label i <xref:System.Windows.Controls.ComboBox> są umieszczone 10% całkowitej szerokości [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].

[!code-xaml[GlobalizationRunDialog#GridColumnDef2](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]

Należy zauważyć, że w przykładzie zastosowano funkcję współużytkowanego określania wielkości <xref:System.Windows.Controls.Grid>. Ostatnie trzy kolumny wykorzystują to przez umieszczenie ich w tym samym <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>. Jeden z nich będzie oczekiwał od nazwy właściwości, dzięki czemu kolumny mogą współużytkować ten sam rozmiar. Tak więc, gdy "Przeglądaj..." jest zlokalizowany na dłuższym ciągu "Durchsuchen...", a wszystkie przyciski rozwijają się w szerokości zamiast mieć niewielki przycisk "OK" i nieproporcjonalnie duży "Durchsuchen..." przycisk.

**XML: lang**

`xml:lang="en-US"`

Zwróć uwagę, że [Obsługa języka XML: lang w języku XAML](../../xaml-services/xml-lang-handling-in-xaml.md) umieszczonym w elemencie głównym [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Ta właściwość opisuje kulturę danego elementu i jego elementów podrzędnych. Ta wartość jest używana przez kilka funkcji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i powinna być odpowiednio zmieniana podczas lokalizacji. Ta wartość zmienia używany słownik języka do dzielenia wyrazów i sprawdzania pisowni. Ma także wpływ na wyświetlanie cyfr i sposób, w jaki system rezerwowy czcionki wybiera czcionkę do użycia. Na koniec Właściwość wpływa na sposób wyświetlania liczb i sposób, w jaki teksty złożone w złożonych skryptach są w kształcie. Wartość domyślna to "pl-US".

**Kompilowanie zestawu zasobów satelitarnych**

*W. csproj:*

Edytuj plik `.csproj` i Dodaj następujący tag do niewarunkowego `<PropertyGroup>`:

`<UICulture>en-US</UICulture>`

Zwróć uwagę na dodanie wartości `UICulture`. Gdy jest ustawiona na prawidłową wartość <xref:System.Globalization.CultureInfo>, na przykład en-US, kompilowanie projektu spowoduje wygenerowanie zestawu satelickiego ze wszystkimi lokalizowalnymi zasobami.

`<Resource Include="RunIcon.JPG">`

`<Localizable>False</Localizable>`

`</Resource>`

`RunIcon.JPG` nie musi być lokalizowana, ponieważ powinna być taka sama dla wszystkich kultur. `Localizable` jest ustawiona na `false` tak, aby pozostawała w zestawie głównym neutralnym od języka, a nie w zestawie satelity. Wartość domyślna wszystkich zasobów noncompilable `Localizable` jest ustawiona na `true`.

**Lokalizowanie okna dialogowego uruchamiania**

**Parse**

Po skompilowaniu aplikacji pierwszy krok lokalizowania zasobów jest analizowany z zestawu satelickiego. Na potrzeby tego tematu Użyj przykładowego narzędzia LocBaml, które można znaleźć w [przykładowym narzędziu LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016). Należy pamiętać, że LocBaml to tylko przykładowe narzędzie, które ułatwia rozpoczęcie pracy nad tworzeniem narzędzia lokalizacyjnego, które mieści się w procesie lokalizacji. Korzystając z LocBaml, uruchom następujące polecenie, aby przeanalizować: **LocBaml/Parse RunDialog. resources. dll/out:** aby wygenerować plik "RunDialog. resources. dll. csv".

**Zlokalizować**

Użyj ulubionego edytora CSV, który obsługuje kodowanie Unicode, aby edytować ten plik. Odfiltruj wszystkie wpisy z kategorią lokalizacji "Brak". Powinny pojawić się następujące wpisy:

|Klucz zasobu|Kategoria lokalizacji|Wartość|
|-|-|-|
|Button_1: System. Windows. Controls. Button. $Content|Przycisk|OK|
|Button_2: System. Windows. Controls. Button. $Content|Przycisk|Anuluj|
|Button_3: System. Windows. Controls. Button. $Content|Przycisk|Przeglądaj...|
|ComboBox_1: System. Windows. Controls. ComboBox. $Content|ComboBox||
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Tekst|Wpisz nazwę programu, folderu, dokumentu lub zasobu internetowego, a system Windows otworzy go.|
|TextBlock_2: System. Windows. Controls. TextBlock. $Content|Tekst|Otwórz|
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

**Utworzenie**

Ostatni krok lokalizacji obejmuje utworzenie nowo zlokalizowanego zestawu satelickiego. Można to zrobić za pomocą następującego polecenia LocBaml:

**LocBaml. exe/Generate RunDialog. resources. dll/Trans: RunDialog. resources. dll. CSV/out:. /CUL: de-DE**

W przypadku okien niemieckich, jeśli ten plik resources. dll zostanie umieszczony w folderze de-DE obok zestawu głównego, ten zasób zostanie automatycznie załadowany zamiast tego w folderze en-US. Jeśli nie masz niemieckiej wersji systemu Windows do przetestowania, ustaw kulturę na dowolną kulturę systemu Windows, z której korzystasz (na przykład `en-US`), i Zastąp pierwotną bibliotekę DLL zasobów.

**Ładowanie zasobów satelitarnych**

|Plik. exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|
|------------------|------------------------------------|------------------------------------|
|Kod|Oryginalna BAML|Zlokalizowana BAML|
|Zasoby neutralne dla kultury|Inne zasoby w języku angielskim|Inne zasoby zlokalizowane do wersji niemieckiej|

Program .NET Framework automatycznie wybiera, który zestaw zasobów satelitarnych ma zostać załadowany na podstawie `Thread.CurrentThread.CurrentUICulture`aplikacji. Ta wartość domyślna jest kulturą systemu operacyjnego Windows. W przypadku korzystania z systemu Windows w języku niemieckim de-DE\MyDialog.resources.dll ładuje się w przypadku korzystania z systemu Windows, a en-US\MyDialog.resources.dll ładuje. Możesz ustawić ostateczny rezerwowy zasób dla aplikacji, określając NeutralResourcesLanguage w AssemblyInfo projektu. Na przykład jeśli określisz:

`[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`

następnie en-US\MyDialog.resources.dll będzie używany z niemieckimi oknami, jeśli de-DE\MyDialog.resources.dll lub de\MyDialog.resources.dll są niedostępne.

### <a name="microsoft-saudi-arabia-homepage"></a>Strona główna Microsoft Arabia Saudyjska

Na poniższej grafice przedstawiono angielskie i arabskiej stronę główną. Aby zapoznać się z kompletnym przykładem, który tworzy te grafiki, zobacz sekcję dotyczącą [globalizacji strony głównej](https://go.microsoft.com/fwlink/?LinkID=159990).

**Angielski:**

![Zrzut ekranu przedstawiający stronę główną w języku angielskim.](./media/wpf-globalization-and-localization-overview/english-home-page-sample.jpg)

**Arabski:**

![Zrzut ekranu przedstawiający arabskiej strony głównej.](./media/wpf-globalization-and-localization-overview/arabic-home-page-sample.jpg)

### <a name="designing-a-global-microsoft-home-page"></a>Projektowanie globalnej strony głównej firmy Microsoft

Ten makieta witryny sieci Web Microsoft Arabia Saudyjska ilustruje funkcje globalizacji dostępne dla języków RightToLeft. Języki takie jak hebrajski i arabski mają kolejność odczytywania od prawej do lewej, więc układ [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musi być często ustalany w inny sposób niż w językach od lewej do prawej, takich jak angielski. Lokalizowanie z języka od lewej do prawej do języka od prawej do lewej lub odwrotnie może być bardzo trudne. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] został zaprojektowany, aby znacznie ułatwić tworzenie takich lokalizacji.

**FlowDirection**

*Strona główna. XAML:*

[!code-xaml[GlobalizationHomepage#Homepage](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]

Zwróć uwagę na Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A> w <xref:System.Windows.Controls.Page>. Zmiana tej właściwości na <xref:System.Windows.FlowDirection.RightToLeft> spowoduje zmianę <xref:System.Windows.FrameworkElement.FlowDirection%2A> <xref:System.Windows.Controls.Page> i jego elementów podrzędnych, dzięki czemu układ tego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zostanie przerzucony w celu przełączenia do prawej strony, ponieważ oczekuje się, że jest to użytkownik arabski. Jeden może zastąpić zachowanie dziedziczenia, określając jawną <xref:System.Windows.FrameworkElement.FlowDirection%2A> na dowolnym elemencie. Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A> jest dostępna dla dowolnego elementu <xref:System.Windows.FrameworkElement> lub powiązanego z dokumentem i ma niejawną wartość <xref:System.Windows.FlowDirection.LeftToRight>.

Zwróć uwagę, że nawet pędzle gradientu tła są przerzucane prawidłowo po zmianie <xref:System.Windows.FrameworkElement.FlowDirection%2A> głównej:

**FlowDirection = "LeftToRight"**

![Zrzut ekranu przedstawiający przepływ gradientu od lewej do prawej.](./media/wpf-globalization-and-localization-overview/gradient-flow-left-right.png)

**FlowDirection = "RightToLeft"**

![Zrzut ekranu przedstawiający przepływ gradientu od prawej do lewej.](./media/wpf-globalization-and-localization-overview/gradient-flow-right-left.png)

**Unikaj używania stałych wymiarów dla paneli i kontrolek**

Zapoznaj się z dokumentem Strona główna. XAML, Zauważ, że od stałej szerokości i wysokości określonej dla całego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w górnym <xref:System.Windows.Controls.DockPanel>, nie ma żadnych innych stałych wymiarów. Unikaj używania stałych wymiarów, aby zapobiec przycinaniu zlokalizowanego tekstu, który może być dłuższy niż tekst źródłowy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] panele i kontrolki będą automatycznie zmieniać rozmiar na podstawie zawartości, która zawiera. Większość formantów ma także minimalne i maksymalne wymiary, które można ustawić w celu uzyskania większej kontroli (na przykład MinWidth = "20"). Za pomocą <xref:System.Windows.Controls.Grid>można również ustawić szerokości względne i wysokość przy użyciu "\*" (na przykład `Width="0.25*"`) lub użyć funkcji udostępniania rozmiaru komórki.

**Komentarze dotyczące lokalizacji**

Istnieje wiele przypadków, w których zawartość może być niejednoznaczna i trudny do przetłumaczenia. Deweloper lub Projektant ma możliwość udostępnienia dodatkowego kontekstu i komentarzy do lokalizatorów przy użyciu komentarzy do lokalizacji. Na przykład lokalizacja. komentarze poniżej objaśnia użycie znaku "&#124;".

[!code-xaml[GlobalizationHomepage#LocalizationComment](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]

Ten komentarz jest kojarzony z zawartością TextBlock_1's i w przypadku narzędzia LocBaml (zobacz temat [lokalizowanie aplikacji](how-to-localize-an-application.md)), można go zobaczyć w szóstej kolumnie wiersza TextBlock_1 w pliku Output. CSV:

|Klucz zasobu|Kategoria|odczytu|Można modyfikować|Komentarz|Wartość|
|-|-|-|-|-|-|
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Tekst|OZNACZA|OZNACZA|Ten znak jest używany jako reguła dekoracyjna.|&#124;|

Komentarze mogą być umieszczane na zawartości lub właściwości dowolnego elementu przy użyciu następującej składni:

[!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]

**Atrybuty lokalizacji**

Często menedżerowie deweloperów lub lokalizacji wymagają kontroli, jakie lokalizatory mogą odczytywać i modyfikować. Na przykład możesz nie chcieć, aby lokalizator przetłumaczy nazwę firmy lub wyraz prawny. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera atrybuty, które umożliwiają ustawienie czytelności, modifiability i kategorii zawartości lub właściwości elementu, którego narzędzie lokalizacyjne może używać do blokowania, ukrywania i sortowania elementów. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Localization.Attributes%2A>. Na potrzeby tego przykładu narzędzie LocBaml jedynie wyprowadza wartości tych atrybutów. kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wszystkie mają wartości domyślne dla tych atrybutów, ale można je zastąpić. Na przykład poniższy przykład zastępuje domyślne atrybuty lokalizacji `TextBlock_1` i ustawia zawartość do odczytu, ale nie można jej modyfikować dla lokalizatorów.

[!code-xaml[LocalizationComAtt#LocalizationAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]

Oprócz atrybutów czytelności i modifiability, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera Wyliczenie wspólnych kategorii interfejsu użytkownika (<xref:System.Windows.LocalizationCategory>), które mogą być używane do nadawania lokalizatorów więcej kontekstu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] domyślne kategorie dla kontrolek platformy można również zastąpić w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:

[!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]

Domyślne atrybuty lokalizacji udostępniane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mogą być również przesłonięte przez kod, więc można prawidłowo ustawić odpowiednie wartości domyślne dla kontrolek niestandardowych. Na przykład:

```csharp
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]
public class CorporateLogo : TextBlock
{
    // ...
}
```

Atrybuty na wystąpienie ustawione w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] będą mieć pierwszeństwo przed wartościami ustawionymi w kodzie w kontrolkach niestandardowych. Aby uzyskać więcej informacji o atrybutach i komentarzach, zobacz temat [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).

**Czcionki bazowe i kompozytowe czcionek**

Jeśli określisz czcionkę, która nie obsługuje danego zakresu kodu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] automatycznie przejdzie do tej, która korzysta z globalnego interfejsu użytkownika. compositefont, który znajduje się w katalogu Windows\Fonts. Czcionki złożone działają podobnie jak jakakolwiek inna czcionka i mogą być używane jawnie przez ustawienie `FontFamily` elementu (na przykład `FontFamily="Global User Interface"`). Możesz określić własne preferencje powrotu do czcionki, tworząc własną czcionkę złożoną i określając czcionkę używaną dla konkretnych kodu zakresów i języków.

Aby uzyskać więcej informacji na temat czcionek kompozytowych, zobacz <xref:System.Windows.Media.FontFamily>.

**Lokalizowanie strony głównej firmy Microsoft**

Aby zlokalizować tę aplikację, można wykonać te same czynności co w oknie dialogowym uruchamiania. Zlokalizowany plik CSV dla języka arabskiego jest dostępny dla Ciebie w [przykładowej stronie głównej globalizacji](https://go.microsoft.com/fwlink/?LinkID=159990).
