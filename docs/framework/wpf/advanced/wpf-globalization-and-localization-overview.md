---
title: Przegląd Lokalizacja i globalizacja WPF
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: fcf5b8f872e2f97497ff5387adb755da1832bf8c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47424470"
---
# <a name="wpf-globalization-and-localization-overview"></a>Przegląd Lokalizacja i globalizacja WPF
Dostępność produktów do tylko jednego języka, możesz ograniczenie z potencjalnym klientem podstawowy ułamek populacji MLD 6.5 naszym świecie. Jeśli chcesz, aby aplikacje, aby dotrzeć do odbiorców globalnych, ekonomiczne lokalizacji produktu jest najlepszym i najbardziej ekonomiczny sposób dotrzeć do większej liczby klientów.  
  
 W tym omówieniu przedstawiono globalizacja i lokalizacja w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Globalizacja to projektowania i tworzenia aplikacji, które wykonują w wielu lokalizacjach. Na przykład globalizacji obsługuje dane regionalne i zlokalizowane interfejsy użytkownika dla użytkowników w różnych kulturach. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia funkcje zglobalizowanej projektu, łącznie z automatycznego układu, zestawy satelickie i zlokalizowane atrybutów i komentowania.
  
 Lokalizacja jest tłumaczenie zasobów aplikacji na zlokalizowane wersje dla określonych kultur, obsługiwanych przez aplikację. Gdy lokalizowane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], za pomocą interfejsów API w <xref:System.Windows.Markup.Localizer> przestrzeni nazw. Te interfejsy API usługi power [locbaml — narzędzie przykładowe](https://go.microsoft.com/fwlink/?LinkID=160016) narzędzie wiersza polecenia. Aby uzyskać informacje o sposobie tworzenia i używania locbaml —, zobacz [lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).    
  
## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Najlepsze rozwiązania dotyczące globalizacji i lokalizacji na platformie WPF  
 Użytkownik może w pełni wykorzystać funkcje lokalizacja i globalizacja, która jest wbudowana w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykonując projektowania interfejsu użytkownika i wskazówki związane z lokalizacji, udostępnianych w tej sekcji.  
  
### <a name="best-practices-for-wpf-ui-design"></a>Najlepsze rozwiązania dotyczące projektowania interfejsu użytkownika aplikacji WPF  
 Podczas projektowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], rozważ zaimplementowanie tych najlepszych rozwiązań:  
  
-   Zapisać swoje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; należy unikać tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w kodzie. Podczas tworzenia usługi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy udostępnić za pośrednictwem wbudowanego lokalizacji interfejsów API.  
  
-   Należy unikać położenia bezwzględne i stałych rozmiarach układ zawartości; Zamiast tego należy użyć względną lub automatycznego ustalania rozmiaru.
  
    -   Użyj <xref:System.Windows.Window.SizeToContent%2A> i zachowanie szerokości i wysokości równa `Auto`.  
  
    -   Unikaj używania <xref:System.Windows.Controls.Canvas> układ [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s.  
  
    -   Użyj <xref:System.Windows.Controls.Grid> i udostępnianie jej rozmiaru.  
  
-   Udostępnić dodatkowe miejsce w marginesy, dlatego zlokalizowanego tekstu często wymaga więcej miejsca. Dodatkowe miejsce umożliwia ich znaków.  
  
-   Włącz <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> na <xref:System.Windows.Controls.TextBlock> w celu uniknięcia wycinka.
  
-   Ustaw `xml:lang` atrybutu. Ten atrybut zawiera opis kultury określonego elementu i jego elementy podrzędne. Wartość tej właściwości powoduje zmianę zachowania kilka funkcji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Na przykład zmienia zachowanie dzielenie wyrazów, sprawdzanie pisowni, liczba podstawienia, złożonym kształtowania i czcionka fallback. Zobacz [globalizacja dla WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md) Aby uzyskać więcej informacji o ustawieniu [XML: lang — Obsługa w XAML](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md).  
  
-   Utwórz dostosowane czcionkę złożonego uzyskać lepszą kontrolę nad czcionek, które są używane w różnych językach. Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa czcionki GlobalUserInterface.composite w Twoim katalogu Windows\Fonts.  
  
-   Podczas tworzenia aplikacji nawigacji, które mogą być zlokalizowane w kulturze, wyświetlany jest tekst w formacie od prawej do lewej, jawnie ustawić <xref:System.Windows.FlowDirection> każdej strony, aby upewnić się, stronę odziedziczy <xref:System.Windows.FlowDirection> z <xref:System.Windows.Navigation.NavigationWindow>.  
  
-   Podczas tworzenia aplikacji autonomicznej nawigacji, które znajdują się poza przeglądarki ustawić <xref:System.Windows.Application.StartupUri%2A> dla aplikacji początkowej <xref:System.Windows.Navigation.NavigationWindow> zamiast do strony (na przykład `<Application StartupUri="NavigationWindow.xaml">`). Ten projekt umożliwia zmianę <xref:System.Windows.FlowDirection> okna, a na pasku nawigacyjnym. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [globalizacji strona główna przykładowej](https://go.microsoft.com/fwlink/?LinkID=159990).  
  
### <a name="best-practices-for-wpf-localization"></a>Najlepsze rozwiązania dotyczące lokalizacji WPF  
 Podczas lokalizowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji, należy wziąć pod uwagę implementowania tych najlepszych rozwiązań:  
  
-   Użyj lokalizacji komentarze, aby dostarczyć dodatkowego kontekstu lokalizatorzy.  
  
-   Używanie atrybutów lokalizacji do kontrolowania lokalizacji zamiast selektywnie pominięcie <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości elementów. Zobacz [lokalizacja atrybutów i komentarzy](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md) Aby uzyskać więcej informacji.  
  
-   Użyj `msbuild -t:updateuid` i `-t:checkuid` Dodaj i sprawdź <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości w swojej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Użyj <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości do śledzenia zmian między środowiskami deweloperskim i lokalizacji. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości ułatwiają lokalizowanie nowe zmiany deweloperskie. Jeśli ręcznie dodasz <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zadanie jest zazwyczaj żmudnym i mniej dokładne.  
  
    -   Nie edytować ani zmieniać <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości po rozpoczęciu lokalizacji.  
  
    -   Nie używaj zduplikowane <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości (Pamiętaj tej porady, korzystając z polecenia kopiowania i wklejania).  
  
    -   Ustaw `UltimateResourceFallback` lokalizacji w AssemblyInfo.*, aby określić odpowiedni język, w przypadku uwierzytelniania rezerwowego (na przykład `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).  
  
         Jeśli zdecydujesz się umieścić swój język źródłowy w głównym zestawie, pomijając `<UICulture>` tagów w pliku projektu, należy ustawić `UltimateResourceFallback` lokalizacji zestawu głównego zamiast satelity (na przykład `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).  
  
<a name="workflow_to_localize" />   
## <a name="localize-a-wpf-application"></a>Lokalizowanie aplikacji WPF  
 Podczas lokalizowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, dostępnych jest kilka opcji. Na przykład, można powiązać lokalizowalne zasoby w aplikacji, aby [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pliku, tekst Lokalizowalny są przechowywane w tabelach resx lub mają swoje lokalizatorowi użyj [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików. W tej sekcji opisano lokalizacji przepływu pracy, który używa formularz BAML XAML, która zapewnia kilka korzyści:  
  
-   Można lokalizować Po skompilowaniu.  
  
-   Możesz zaktualizować do nowszej wersji formularz BAML lokalizacje XAMLwith ze starszej wersji formularz BAML XAML, dzięki czemu można lokalizować w tym samym czasie, który tworzysz.  
  
-   Można sprawdzić poprawność oryginalnego elementy źródłowe i semantyka w czasie kompilacji ponieważ formularz BAML XAML jest skompilowanej formy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
### <a name="localization-build-process"></a>Proces kompilacji w lokalizacji  
 Podczas opracowywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, proces kompilacji do lokalizacji jest następujący:  
  
-   Deweloper tworzy i globalizes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. W pliku projektu do zestawów dla deweloperów `<UICulture>en-US</UICulture>` tak, aby podczas kompilowania aplikacji, jest generowany głównym zestawie niezależny od języka. Ten zestaw zawiera Satelita. resources.dll pliku, który zawiera wszystkie lokalizowalne zasoby. Opcjonalnie możesz zachować języka źródłowego w głównym zestawie ponieważ naszych lokalizacji [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] obsługuje wyodrębniania z zestawu głównego.  
  
-   Gdy plik jest skompilowany w kompilacji, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest konwertowana na formularz BAML XAML. Neutralne kulturalnie `MyDialog.exe` i kulturalnie zależne (angielski) `MyDialog.resources.dll` pliki są wydawane dla anglojęzycznego klienta.  
  
### <a name="localization-workflow"></a>Przepływ pracy lokalizacji  
 Proces lokalizacji rozpoczyna się po Niezlokalizowany `MyDialog.resources.dll` utworzony plik. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Elementów i właściwości w swojej pierwotnej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są wyodrębniane z formularz BAML XAML do pary klucz wartość, przy użyciu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] w obszarze <xref:System.Windows.Markup.Localizer>. Lokalizatorzy używają pary klucz wartość, aby zlokalizować aplikację. Możesz wygenerować nowy. resource.dll z nowymi wartościami miar po zakończeniu lokalizacji.  
  
 Klucze pary klucz wartość są `x:Uid` wartości, które są wprowadzane przez dewelopera w oryginalnym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Te `x:Uid` Włącz wartości [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] do śledzenia i scalania zmian, które odbywa się między warstwą Deweloper a lokalizatorowi podczas lokalizacji. Na przykład, jeśli deweloper zmienia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] po rozpoczęciu lokalizatorowi lokalizowanie można scalić zmiany programowania za pomocą proces lokalizacji już zakończonej tak, aby minimalny tłumaczenia praca zostanie utracona.  
  
 Na poniższym rysunku przedstawiono typowej lokalizacji przepływu pracy, który jest oparty na formularz BAML XAML. Ten diagram przyjęto założenie, że deweloper zapisuje aplikację w języku angielskim. Deweloper tworzy i globalizes aplikacji WPF. W pliku projektu do zestawów dla deweloperów `<UICulture>en-US</UICulture>` tak, aby podczas kompilacji, Język neutralny zestawu głównego pobiera wygenerowany z satelity. resources.dll zawierający wszystkie lokalizowalne zasoby. Alternatywnie można jeden zachowanie języka źródłowego w głównym zestawie, ponieważ lokalizacji WPF interfejsy API obsługują wyodrębniania z głównego zestawu. Po zakończeniu procesu kompilacji XAML Pobierz skompilowany do BAML. Neutralne kulturalnie MyDialog.exe.resources.dll uzyskać dostarczane klientom wypowiedzi angielskiego.  
  
 ![Przepływ pracy lokalizacji](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![Niezlokalizowany przepływu pracy](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization" />   
## <a name="examples-of-wpf-localization"></a>Przykłady lokalizacji WPF  
 Ta sekcja zawiera przykłady zlokalizowanych aplikacji, aby pomóc Ci zrozumieć, jak tworzyć i lokalizować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
#### <a name="run-dialog-box-example"></a>Uruchom przykład okno dialogowe  
 Następujące graficznych Pokaż dane wyjściowe **Uruchom** przykładowe okno dialogowe.  
  
 **Angielski:**  
  
 ![Okno dialogowe uruchamiania](../../../../docs/framework/wpf/advanced/media/rundialogenglish.PNG "RunDialogEnglish")  
  
 **Niemiecki:**  
  
 ![Niemiecki Uruchom okno dialogowe](../../../../docs/framework/wpf/advanced/media/rundialoggerman.PNG "RunDialogGerman")  
  
 **Projektowanie globalnego Uruchom okno dialogowe**  
  
 Ten przykład generuje **Uruchom** okno dialogowe, za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. To okno dialogowe jest odpowiednikiem **Uruchom** okno dialogowe, które jest dostępne z [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] Start menu.  
  
 Niektóre z najważniejszych składania globalnego okna dialogowe są następujące:  
  
 **Układ automatyczny**  
  
 *W Window1.xaml:*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 Właściwość poprzednie okno automatycznie zmienia rozmiar okna według rozmiaru zawartości. Tej właściwości zapobiega odcięcie zawartość, która zwiększa się rozmiar po lokalizacji; okna Usuwa również niepotrzebne miejsce, gdy zawartość zmniejszy rozmiar po lokalizacji.  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości są wymagane, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizacji [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] działała prawidłowo.  
  
 Są one używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizacji [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] do śledzenia zmian między środowiskami deweloperskim i lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości umożliwia scalanie nowszą wersję [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przy użyciu starszych lokalizacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Możesz dodać <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości, uruchamiając `msbuild -t:updateuid RunDialog.csproj` w powłoce poleceń. Jest to zalecana metoda dodawania <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości ponieważ ręcznie dodawane jest zazwyczaj czasochłonne i mniej dokładne. Sprawdź, czy <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> właściwości są poprawnie ustawione, uruchamiając `msbuild -t:checkuid RunDialog.csproj`.
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Mają strukturę za pomocą <xref:System.Windows.Controls.Grid> formant, który jest formantem przydatne dla zalet automatycznego układu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Należy pamiętać, że okno dialogowe jest podzielony na trzy wiersze i kolumny pięć. Nie jest jedną z definicji wierszy i kolumn ma stały rozmiar; Dzięki temu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy, które są umieszczone w każdej komórce dostosowują się do wzrostu i zmniejsza rozmiar podczas lokalizacji.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 Pierwsze dwie kolumny gdzie **Otwórz:** etykiety i <xref:System.Windows.Controls.ComboBox> są umieszczane użyj 10 procent [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] łączna szerokość.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 Należy zauważyć, że przykład używa funkcji udostępnionych rozmiaru <xref:System.Windows.Controls.Grid>. Ostatnie trzy kolumny zalet tego użytkownika, umieszczając się w tej samej <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>. Zgodnie z jedną powinna mieć nazwę właściwości, dzięki temu kolumn udostępnić ten sam rozmiar. Dlatego jeśli "Przeglądaj..." zlokalizowania dłuższy ciąg "Durchsuchen...", wszystkie przyciski powiększać szerokość zamiast małego przycisku "OK", a nieproporcjonalnie duży przycisk "Durchsuchen...".  
  
 **Xml:lang**
  
 `Xml:lang="en-US"`  
  
 Zwróć uwagę [XML: lang — Obsługa w XAML](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) umieszczone na element główny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Ta właściwość opisuje kultura danego elementu i jego elementy podrzędne. Ta wartość jest używana przez kilka funkcji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i należy odpowiednio zmienić podczas lokalizacji. Ta wartość zmienia się, jakie słownika jest używany do dzielenia i słów sprawdzania pisowni. Wpływa również na wyświetlanie cyfry oraz sposobu wybierania czcionki, która do użycia przez system rezerwowy czcionki. Na koniec kształt ma wpływ na właściwość, wyświetlane są numery sposób i zapisywane w złożonych skryptach teksty sposób. Wartość domyślna to "en US".  
  
 **Tworzenie satelickim zestawem zasobów**  
  
 *W pliku csproj:*  

 Edytuj `.csproj` pliku i Dodaj następujący tag do bezwarunkowe `<PropertyGroup>`:
 
 `<UICulture>en-US</UICulture>`  
  
 Zwróć uwagę, dodanie `UICulture` wartość. Gdy jest ono ustawione na prawidłową <xref:System.Globalization.CultureInfo> wartości, takich jak en US, kompilowania projektu spowoduje wygenerowanie w zestawie satelickim o wszystkie lokalizowalne zasoby w niej.  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG` Nie musi być lokalizowany, ponieważ są one takie same dla wszystkich języków. `Localizable` ustawiono `false` tak, aby pozostała w Język neutralny głównym zestawie zamiast zestawu satelickiego. Jest wartością domyślną dla wszystkich zasobów noncompilable `Localizable` równa `true`.  
  
 **Lokalizowanie Uruchom okno dialogowe**  
  
 **Parse**  
  
 Po skompilowaniu aplikacji, pierwszym krokiem podczas jego lokalizacja jest analizowania lokalizowalne zasoby z zestawu satelickiego. Na potrzeby tego tematu, użyj przykładowych locbaml — narzędzie, w której znajduje się w temacie [locbaml — narzędzie przykładowe](https://go.microsoft.com/fwlink/?LinkID=160016). Należy pamiętać, że locbaml — jest tylko przykładowe narzędzie przeznaczone do ułatwiających rozpoczęcie pracy z tworzeniem narzędziem do lokalizacji, która pasuje w procesie lokalizacji. Za pomocą locbaml —, uruchom następujące polecenie, aby przeanalizować: **locbaml — / przeanalizować RunDialog.resources.dll/out:** można wygenerować pliku "RunDialog.resources.dll.CSV".  
  
 **Lokalizowanie**  
  
 Użyj ulubionego edytora CSV, który obsługuje standard Unicode, aby edytować ten plik. Odfiltruj wszystkich wpisów z lokalizacji kategorii "None". Powinny pojawić się następujące wpisy:  
  
|Klucz zasobu|Kategoria lokalizacji|Wartość|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Przycisk|OK|  
|Button_2:System.Windows.Controls.Button.$Content|Przycisk|Anuluj|  
|Button_3:System.Windows.Controls.Button.$Content|Przycisk|Przeglądaj...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Tekst|Wpisz nazwę programu, folderu, dokumentu lub zasobu internetowego, a Windows otworzy.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Tekst|Otwórz:|  
|Window_1:System.Windows.Window.Title|Tytuł|Uruchom|  
  
 Lokalizacja aplikacji na język niemiecki wymagałoby tłumaczenia następujące:  
  
|Klucz zasobu|Kategoria lokalizacji|Wartość|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Przycisk|OK|  
|Button_2:System.Windows.Controls.Button.$Content|Przycisk|Abbrechen|  
|Button_3:System.Windows.Controls.Button.$Content|Przycisk|Durchsuchen...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Tekst|Den Geben Sie eines Namen Programms Ordners, einer Dokuments oder Internetresource.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Tekst|Öffnen:|  
|Window_1:System.Windows.Window.Title|Tytuł|Uruchom|  
  
 **Generowanie**  
  
 Ostatni krok lokalizacji obejmuje tworzenie zestawu satelickiego nowo zlokalizowane. Można to zrobić za pomocą następującego polecenia locbaml —:  
  
 **LocBaml.exe /generate RunDialog.resources.dll /trans:RunDialog.resources.dll.CSV /out: . /cul:de-DE**  
  
 Na niemiecki [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], jeśli ta resources.dll znajduje się w folderze de-DE, obok zestawu głównego, ten zasób zostanie automatycznie załadowany zamiast w folderze en US. Jeśli nie masz wersji niemieckiej [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] testować tę aplikację, ustawienie kultury do niezależnie od kultury [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] używasz (na przykład `en-US`) i Zastąp oryginalny Biblioteka DLL zasobów.  
  
 **Ładowanie zasobów satelitarnej**  
  
|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|Kod|Oryginalne angielskie BAML|Zlokalizowane BAML|  
|Kulturalnie neutralne zasoby|Inne zasoby w języku angielskim|Inne zasoby zlokalizowane na język niemiecki|  
  
 .NET framework automatycznie wybiera zestawu zasobów satelitarnej obciążenia aplikacji w oparciu o `Thread.CurrentThread.CurrentUICulture`. Domyślnie jest to kultura swoje [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systemu operacyjnego. Jeśli używasz niemiecki [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], de-DE\MyDialog.resources.dll ładuje, jeśli używasz języka angielskiego [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], ładuje en-US\MyDialog.resources.dll. Ultimate bazoey zasoby aplikacji można ustawić przez określenie NeutralResourcesLanguage w AssemblyInfo.* projektu. Na przykład jeśli określisz:  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 następnie en-US\MyDialog.resources.dll będą używane z Windows niemiecki, jeśli de-DE\MyDialog.resources.dll lub de\MyDialog.resources.dll są niedostępne.  
  
### <a name="microsoft-saudi-arabia-homepage"></a>Microsoft Saudi Arabia Homepage  
 Następujące grafiki Pokaż język angielski i arabski strony głównej. Aby uzyskać pełny przykład, który generuje te grafiki zobacz [globalizacji strona główna przykładowej](https://go.microsoft.com/fwlink/?LinkID=159990).  
  
 **Angielski:**  
  
 ![Strona w języku angielskim](../../../../docs/framework/wpf/advanced/media/englishhomepage.jpg "EnglishHomepage")  
  
 **Arabski:**  
  
 ![Arabski strony](../../../../docs/framework/wpf/advanced/media/arabichomepage.jpg "ArabicHomepage")  
  
### <a name="designing-a-global-microsoft-homepage"></a>Projektowanie globalnego strony głównej firmy Microsoft  
 To makiety programu Microsoft Arabia Saudyjska witryny sieci web ilustruje funkcji globalizacyjnych przewidziane RightToLeft języków. Języków, takich jak języków hebrajskiego i arabskiego ma kolejność czytania od prawej do lewej, więc układ [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] często muszą być rozmieszczone odbywa się zupełnie inaczej niż w przypadku w językach od lewej do prawej, takich jak angielski. Lokalizowanie języka od lewej do prawej na język od prawej do lewej lub odwrotnie może być bardzo trudne. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] została zaprojektowana w celu znacznie ułatwić takie lokalizacje.  
  
 **FlowDirection**  
  
 *Homepage.XAML:*  
  
 [!code-xaml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 Zwróć uwagę <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość <xref:System.Windows.Controls.Page>. Zmiana tej właściwości, aby <xref:System.Windows.FlowDirection.RightToLeft> zmieni <xref:System.Windows.FrameworkElement.FlowDirection%2A> z <xref:System.Windows.Controls.Page> i jego elementy podrzędne tak, aby w układzie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest odwrócony stanie od prawej do lewej, jak arabski użytkownika mogą spodziewać się. Jeden zachowanie można przesłonić dziedziczenie, określając jawnego <xref:System.Windows.FrameworkElement.FlowDirection%2A> dowolnego elementu. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Właściwości jest dostępne na każdym <xref:System.Windows.FrameworkElement> lub dokumentów powiązanych elementów, a ma niejawne wartości <xref:System.Windows.FlowDirection.LeftToRight>.  
  
 Sprawdź, czy nawet pędzle gradientów tła są przerzucane prawidłowo po głównego <xref:System.Windows.FrameworkElement.FlowDirection%2A> zmiany:  
  
 **FlowDirection="LeftToRight"**  
  
 ![Przepływ od lewej do prawej](../../../../docs/framework/wpf/advanced/media/lefttoright.PNG "LeftToRight")  
  
 **FlowDirection="RightToLeft"**  
  
 ![Przepływ od prawej do lewej](../../../../docs/framework/wpf/advanced/media/righttoleft.PNG "RightToLeft")  
  
 **Należy unikać stałe wymiary paneli i kontrolek**  
  
 Zapoznaj się za pośrednictwem Homepage.xaml należy zauważyć, że oprócz stałą szerokość i wysokość, określony dla całego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] u góry <xref:System.Windows.Controls.DockPanel>, istnieją nie stały wymiarów. Należy unikać używania stałe wymiary, aby zapobiec przycinania zlokalizowanego tekstu, który może być dłuższy niż tekst źródłowy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] paneli i zostanie automatycznie na podstawie zawartości, które zawierają zmiany rozmiaru kontrolek. Większość formantów również ma minimalne i maksymalne wymiary, które można ustawić, aby uzyskać większą kontrolę (na przykład wartości elementu MinWidth = "20"). Za pomocą <xref:System.Windows.Controls.Grid>, można również ustawić za pomocą względne szerokości i wysokości "\*" (na przykład `Width="0.25*"`) lub jego rozmiar komórki, funkcja udostępniania.  
  
 **Lokalizacja komentarzy**  
  
 Istnieje wiele przypadków, w których zawartość może być niejednoznaczna i trudne do translacji. Dla deweloperów lub projektant ma możliwość zapewnienia dodatkowego kontekstu i komentarze do lokalizatorzy za pośrednictwem lokalizacji komentarzy. Na przykład poniżej Localization.Comments wyjaśnia sposób użycia znaku "&#124;".  
  
 [!code-xaml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 Ten komentarz staje się skojarzone z zawartością TextBlock_1 firmy i w przypadku locbaml — narzędzie, (zobacz [Lokalizuj aplikację](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)), może być widoczny w kolumnie 6 TextBlock_1 wiersza w pliku CSV w danych wyjściowych:  
  
|Klucz zasobu|Kategoria|Do odczytu|Można modyfikować|Komentarz|Wartość|  
|-|-|-|-|-|-|  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Tekst|WARTOŚĆ TRUE|WARTOŚĆ TRUE|Ten znak jest używany jako dekoracyjnych reguły.|&#124;|  
  
 Komentarze mogą być umieszczane na zawartość i właściwości dowolnego elementu przy użyciu następującej składni:  
  
 [!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **Lokalizacja atrybutów**  
  
 Często deweloperów lub Menedżer lokalizacji wymaga kontrolę nad czym lokalizatorzy może odczytywać i modyfikować. Na przykład nie można lokalizatorowi do przetłumaczenia nazwy firmy lub prawnych treść. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera atrybuty, które umożliwiają skonfigurowanie czytelności, modifiability i kategorii zawartość element lub właściwość, która jest narzędziem do lokalizacji służy do blokowania, ukrywanie i sortowanie elementów. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Localization.Attributes%2A>. Na potrzeby tego przykładu locbaml — narzędzie generuje tylko wartościami tych atrybutów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wszystkie kontrolki mają przypisane wartości domyślne tych atrybutów, ale mogą one zastąpione. Na przykład, poniższy przykład zastępuje atrybuty lokalizacji domyślne `TextBlock_1` i ustawia zawartość, aby można było odczytać ale niemodyfikowalnych lokalizatorzy.  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 Oprócz czytelność i atrybuty modifiability [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wyliczenie typowe kategorie interfejsu użytkownika (<xref:System.Windows.LocalizationCategory>) można nadać lokalizatorzy dodatkowy kontekst. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Domyślne kategorie dla kontrolek platformy mogą zostać zastąpione w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] także:  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 Lokalizacja domyślna atrybuty, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia również może być zastąpiona przez kod, dzięki czemu można poprawnie ustawione wartości domyślne odpowiednie dla kontrolek niestandardowych. Na przykład:  

```csharp 
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)] 
public class CorporateLogo : TextBlock
{
    // ...
}
``` 
 
 Na atrybuty wystąpienia w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mają wyższy priorytet niż wartości ustawione w kodzie na kontrolek niestandardowych. Aby uzyskać więcej informacji na temat atrybutów i komentarzy, zobacz [lokalizacja atrybutów i komentarzy](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
 **Rezerwa czcionek i czcionek złożone**  
  
 Jeśli określisz czcionkę, która nie obsługuje w zakresie danego punktu kodu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zostanie automatycznie powrotu do jednego, który wykonuje się za pomocą globalnego Interface.compositefont użytkownika, który znajduje się w katalogu Windows\Fonts. Czcionki działają podobnie jak wszystkie inne czcionki i może służyć jawnie ustawiając element `FontFamily` (na przykład `FontFamily="Global User Interface"`). Tworzenie złożonych czcionki i określając jakie czcionki do użycia dla określonego punktu kodu zakresów i języków, można określić własnych preferencji rezerwowego czcionek.  
  
 Aby uzyskać więcej informacji na temat czcionki zobacz <xref:System.Windows.Media.FontFamily>.  
  
 **Lokalizacja strony głównej firmy Microsoft**  
  
 Aby wykonać te same czynności co w przykładzie Uruchom okno dialogowe, aby zlokalizować tę aplikację. Plik CSV zlokalizowane dla języka arabskiego jest dostępny w [globalizacji strona główna przykładowej](https://go.microsoft.com/fwlink/?LinkID=159990).
