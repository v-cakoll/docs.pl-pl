---
title: Jak lokalizować aplikację
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: f2e7e5e8879e89806cfd457a1af80f51b91871cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174215"
---
# <a name="how-to-localize-an-application"></a>Jak lokalizować aplikację
W tym samouczku wyjaśniono, jak utworzyć zlokalizowaną aplikację przy użyciu narzędzia LocBaml.  
  
> [!NOTE]
> Narzędzie LocBaml nie jest aplikacją gotową do produkcji. Jest on przedstawiony jako przykład, który używa niektórych interfejsów API lokalizacji i ilustruje, jak można napisać narzędzie lokalizacji.  
  
<a name="Introduction"></a>
## <a name="overview"></a>Omówienie  
 Ta dyskusja zawiera podejście krok po kroku do lokalizowania aplikacji. Najpierw przygotujesz aplikację, aby można było wyodrębnić tekst, który zostanie przetłumaczony. Po przetłumaczeniu tekstu zostanie scalić przetłumaczony tekst na nową kopię oryginalnej aplikacji.  
  
<a name="Requirements"></a>
## <a name="requirements"></a>Wymagania  
 W trakcie tej dyskusji użyjesz aparatu kompilacji firmy Microsoft (MSBuild), który jest kompilatorem uruchamianym z wiersza polecenia.  
  
 Ponadto zostaniesz poinstruowany, aby użyć pliku projektu. Aby uzyskać instrukcje dotyczące używania plików MSBuild i projektu, zobacz [Tworzenie i wdrażanie](../app-development/building-and-deploying-wpf-applications.md).  
  
 Wszystkie przykłady w tej dyskusji używają en-US (English-US) jako kultury. Dzięki temu można pracować przez kroki przykładów bez instalowania innego języka.  
  
<a name="create_sample_app"></a>
## <a name="create-a-sample-application"></a>Tworzenie przykładowej aplikacji  
 W tym kroku przygotujesz aplikację do lokalizacji. W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przykładach podano przykład HelloApp, który będzie używany dla przykładów kodu w tej dyskusji. Jeśli chcesz użyć tego przykładu, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pobierz pliki z [przykładu narzędzia LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
1. Tworzenie aplikacji do punktu, w którym chcesz rozpocząć lokalizację.  
  
2. Określ język rozwoju w pliku projektu, tak aby MSBuild wygenerował główny zestaw i zestaw satelicki (plik z rozszerzeniem .resources.dll) zawierający zasoby języka neutralnego. Plik projektu w przykładzie HelloApp jest HelloApp.csproj. W tym pliku znajdziesz język programowania zidentyfikowany w następujący sposób:  
  
     `<UICulture>en-US</UICulture>`  
  
3. Dodaj Uids [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do plików. Uids są używane do śledzenia zmian w plikach i do identyfikowania elementów, które muszą być przetłumaczone. Aby dodać Uids do plików, uruchom **updateuid** w pliku projektu:  
  
     **msbuild -t:updateuid helloapp.csproj**  
  
     Aby sprawdzić, czy nie brakuje lub duplikuje Uids, uruchom **checkuid:**  
  
     **msbuild -t:checkuid helloapp.csproj**  
  
     Po uruchomieniu **updateuid,** pliki powinny zawierać Uids. Na przykład w pliku Pane1.xaml helloapp, należy znaleźć następujące:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Tworzenie zestawu satelitarnego zasobów języka neutralnego  
 Po skonfigurowaniu aplikacji do generowania zestawu satelitów zasobów języka neutralnego, należy utworzyć aplikację. Generuje to główny zestaw aplikacji, a także zestaw satelicki zasobów języka neutralnego, który jest wymagany przez LocBaml do lokalizacji. Aby skompilować aplikację:  
  
1. Skompiluj HelloApp, aby utworzyć bibliotekę dynamicznego łącza (DLL):  
  
     **msbuild helloapp.csproj**  
  
2. Nowo utworzony główny zestaw aplikacji, HelloApp.exe, jest tworzony w następującym folderze:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. Nowo utworzony zestaw satelicki zasobów języka neutralnego, HelloApp.resources.dll, jest tworzony w następującym folderze:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>
## <a name="build-the-locbaml-tool"></a>Tworzenie narzędzia LocBaml  
  
1. Wszystkie pliki niezbędne do zbudowania LocBaml znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przykładach. Pobierz pliki języka C# z [przykładowego narzędzia LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
2. W wierszu polecenia uruchom plik projektu (locbaml.csproj), aby utworzyć narzędzie:  
  
     **msbuild locbaml.csproj**  
  
3. Przejdź do katalogu Bin\Release, aby znaleźć nowo utworzony plik wykonywalny (locbaml.exe). Przykład:C:\LocBaml\Bin\Release\locbaml.exe.  
  
4. Opcje, które można określić po uruchomieniu LocBaml są następujące:  
  
    - **analizuj** lub **-p:** analizuje pliki Baml, zasoby lub biblioteki DLL w celu wygenerowania pliku csv lub txt.  
  
    - **generate** or **-g:** Generuje zlokalizowany plik binarny przy użyciu przetłumaczonego pliku.  
  
    - **out** lub **-o** {*filedirector*] **:** Nazwa pliku wyjściowego.  
  
    - **culture** or **-cul** {*culture*] **:** Ustawienia regionalne zestawów wyjściowych.  
  
    - **translation** or **-trans** {*translation.csv*] **:** Przetłumaczony lub zlokalizowany plik.  
  
    - **asmpath** lub **-asmpath:** {*filedirector*] **:** Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod zawiera formanty niestandardowe, należy podać **asmpath** do zestawu formantu niestandardowego.  
  
    - **nologo:** Nie wyświetla żadnych informacji o logo ani prawach autorskich.  
  
    - **pełne:** Wyświetla pełne informacje o trybie.  
  
    > [!NOTE]
    > Jeśli potrzebujesz listy opcji podczas uruchamiania narzędzia, wpisz **LocBaml.exe** i naciśnij klawisz ENTER.  
  
<a name="parse_dll"></a>
## <a name="use-locbaml-to-parse-a-file"></a>Analizowanie pliku za pomocąlocBaml  
 Po utworzeniu narzędzia LocBaml można go użyć do przeanalizowania pliku HelloApp.resources.dll w celu wyodrębnienia zawartości tekstowej, która będzie zlokalizowana.  
  
1. Skopiuj program LocBaml.exe do folderu bin\debug aplikacji aplikacji, w którym utworzono główny zestaw aplikacji.  
  
2. Aby przeanalizować plik zestawu satelickiego i zapisać dane wyjściowe jako plik csv, użyj następującego polecenia:  
  
     **LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    > Jeśli plik wejściowy HelloApp.resources.dll nie znajduje się w tym samym katalogu co LocBaml.exe przenieść jeden z plików, tak aby oba pliki znajdują się w tym samym katalogu.  
  
3. Po uruchomieniu locBaml do analizowania plików dane wyjściowe składają się z siedmiu pól rozdzielonych przecinkami (pliki csv) lub kart (pliki.txt). Poniżej przedstawiono przeanalizowany plik csv dla pliku HelloApp.resources.dll:

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   Siedem pól to:  
  
   1. **Nazwa BAML**. Nazwa zasobu BAML w odniesieniu do zestawu satelickiego języka źródłowego.  
  
   2. **Klucz zasobu**. Zlokalizowany identyfikator zasobu.  
  
   3. **Kategoria**. Typ wartości. Zobacz [Atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).  
  
   4. **Czytelność**. Czy wartość może być odczytywana przez localizer. Zobacz [Atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).  
  
   5. **Możliwość modyfikacji**. Czy wartość może być modyfikowana przez localizer. Zobacz [Atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).  
  
   6. **Komentarze**. Dodatkowy opis wartości, aby określić, jak wartość jest zlokalizowana. Zobacz [Atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).  
  
   7. **Wartość**. Wartość tekstu do przetłumaczenia na żądaną kulturę.  
  
   W poniższej tabeli pokazano, jak te pola są mapowane na rozdzielone wartości pliku csv:  
  
   |Nazwa BAML|Klucz zasobu|Kategoria|Czytelność|Modifiability|Komentarze|Wartość|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Zignoruj|FAŁSZ|FAŁSZ||#Text1;#Text2|
   |HelloApp.g.en-US.resources:window1.baml|Tekst1:System.Windows.Controls.TextBlock.$Content|Brak|Prawda|Prawda||Witaj, świecie|
   |HelloApp.g.en-US.resources:window1.baml|Tekst2:System.Windows.Controls.TextBlock.$Content|Brak|Prawda|Prawda||Żegnaj Świat|
  
   Należy zauważyć, że wszystkie wartości dla **pola Komentarze** nie zawierają żadnych wartości; jeśli pole nie ma wartości, jest puste. Należy również zauważyć, że element w pierwszym wierszu nie jest czytelny ani modyfikowalny i ma "Ignore" jako wartość **kategorii,** z których wszystkie wskazują, że wartość nie jest zlokalizowana.  
  
4. Aby ułatwić wykrywanie elementów zlokalizowanych w analizowanych plikach, szczególnie w dużych plikach, można sortować lub filtrować elementy według **kategorii,** **czytelności**i **modyfikowalności**. Na przykład można odfiltrować nieczytelne i niemodyfikowalne wartości.  
  
<a name="translate_loc_content"></a>
## <a name="translate-the-localizable-content"></a>Tłumaczenie zawartości lokalizowalnej  
 Użyj dowolnego dostępnego narzędzia do tłumaczenia wyodrębnionych treści. Dobrym sposobem jest zapisanie zasobów w pliku csv i wyświetlenie ich w programie Microsoft Excel, wprowadzenie zmian w tłumaczeniu do ostatniej kolumny (wartości).  
  
<a name="merge_translations"></a>
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Generowanie nowego pliku .resources.dll za pomocą funkcji LocBaml  
 Zawartość, która została zidentyfikowana przez analizowanie HelloApp.resources.dll z LocBaml został przetłumaczony i muszą być scalone z powrotem do oryginalnej aplikacji. Użyj opcji **generuj** lub **-g,** aby wygenerować nowy plik .resources.dll.  
  
1. Użyj następującej składni, aby wygenerować nowy plik HelloApp.resources.dll. Oznacz kulturę jako en-US (/cul:en-US).  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**  
  
    > [!NOTE]
    > Jeśli plik wejściowy Hello.csv nie znajduje się w tym samym katalogu co plik wykonywalny LocBaml.exe, przenieś jeden z plików, aby oba pliki były w tym samym katalogu.  
  
2. Zastąp stary plik HelloApp.resources.dll w katalogu C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nowo utworzonym plikiem HelloApp.resources.dll.  
  
3. "Hello World" i "Goodbye World" powinny być teraz tłumaczone w aplikacji.  
  
4. Aby przetłumaczyć na inną kulturę, użyj kultury języka, na który tłumaczysz. W poniższym przykładzie pokazano, jak przetłumaczyć na francusko-kanadyjskie:  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**  
  
5. W tym samym zestawie co główny zestaw aplikacji utwórz nowy folder specyficzny dla kultury, aby pomieścić nowy zestaw satelickiego. W przypadku języka francusko-kanadyjskiego folder będzie fr-CA.  
  
6. Skopiuj wygenerowany zestaw satelitowy do nowego folderu.  
  
7. Aby przetestować nowy zestaw satelickiego, należy zmienić kulturę, w ramach której zostanie uruchomiony aplikacji. Można to zrobić na jeden z dwóch sposobów:  
  
    - Zmienianie ustawień regionalnych systemu operacyjnego **(Start** &#124; **Panel sterowania** &#124; **opcje regionalne i językowe).**  
  
    - W aplikacji dodaj następujący kod do App.xaml.cs:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>
## <a name="some-tips-for-using-locbaml"></a>Kilka wskazówek dotyczących korzystania z LocBaml  
  
- Wszystkie zestawy zależne, które definiują formanty niestandardowe, muszą zostać skopiowane do lokalnego katalogu LocBaml lub zainstalowane w pliku GAC. Jest to konieczne, ponieważ interfejs API lokalizacji musi mieć dostęp do zestawów zależnych podczas odczytywania binarnego XAML (BAML).  
  
- Jeśli zestaw główny jest podpisany, wygenerowany rekord DLL zasobów musi być również podpisany w celu załadowania.  
  
- Wersja biblioteki DLL zlokalizowanego zasobu musi być zsynchronizowana z zestawem głównym.  
  
<a name="Whats_Next"></a>
## <a name="whats-next"></a>Co dalej  
 Teraz powinieneś mieć podstawową wiedzę na temat korzystania z narzędzia LocBaml.  Powinieneś być w stanie zrobić plik, który zawiera Uids. Za pomocą narzędzia LocBaml, należy mieć możliwość przeanalizowania pliku, aby wyodrębnić zawartość zlokalizowaną, a po przetłumaczeniu zawartości, powinien być w stanie wygenerować plik .resources.dll, który łączy przetłumaczoną zawartość. Ten temat nie zawiera wszystkich możliwych szczegółów, ale masz teraz wiedzę niezbędną do używania LocBaml do lokalizowania aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Globalizacja dla WPF](globalization-for-wpf.md)
- [Przegląd używania automatycznego układu](use-automatic-layout-overview.md)
