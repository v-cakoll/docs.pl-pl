---
title: 'Instrukcje: Lokalizowanie aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: b3ad3d0c3223d5baf937ca22fd48d46a80979aac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913673"
---
# <a name="how-to-localize-an-application"></a>Instrukcje: Lokalizowanie aplikacji
W tym samouczku wyjaśniono, jak utworzyć zlokalizowaną aplikację przy użyciu narzędzia LocBaml.  
  
> [!NOTE]
> Narzędzie LocBaml nie jest aplikacją przygotowaną do produkcji. Jest on prezentowany jako przykład, który używa niektórych interfejsów API lokalizacji i ilustruje sposób pisania narzędzia lokalizacji.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Omówienie  
 Ta dyskusja zawiera podejście krok po kroku dotyczące lokalizowania aplikacji. Najpierw przygotujesz aplikację, tak aby tekst, który zostanie przetłumaczony, mógł zostać wyodrębniony. Po przetłumaczeniu tekstu zostanie scalony przetłumaczony tekst na nową kopię oryginalnej aplikacji.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W trakcie tej dyskusji będziesz używać aparatu Microsoft Build Engine (MSBuild), który jest kompilatorem uruchamianym z wiersza polecenia.  
  
 Ponadto zostanie nadana instrukcja użycia pliku projektu. Aby uzyskać instrukcje dotyczące używania programu MSBuild i plików projektu, zobacz [Kompilowanie i wdrażanie](../app-development/building-and-deploying-wpf-applications.md).  
  
 We wszystkich przykładach w tym omówieniu użyto języka en-US (angielski-US) jako kultury. Dzięki temu można wykonać kroki przykładów bez instalowania innego języka.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Tworzenie przykładowej aplikacji  
 W tym kroku zostanie przygotowana aplikacja do lokalizacji. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] W przykładach jest dostarczany przykład HelloApp, który będzie używany w przykładach kodu w tej dyskusji. Jeśli chcesz użyć tego przykładu, Pobierz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliki z przykładu [Narzędzia LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
1. Utwórz aplikację w punkcie, w którym chcesz rozpocząć lokalizację.  
  
2. Określ język programistyczny w pliku projektu, tak aby MSBuild generował zestaw główny i zestaw satelicki (plik z rozszerzeniem. resources. dll) zawierający zasoby języka neutralnego. Plik projektu w przykładzie HelloApp jest HelloApp. csproj. W tym pliku znajdziesz następujący język programowania:  
  
     `<UICulture>en-US</UICulture>`  
  
3. Dodawanie identyfikatorów UID do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików. Identyfikatory UID są używane do śledzenia zmian w plikach i identyfikowania elementów, które muszą być przetłumaczone. Aby dodać UID do plików, uruchom **updateuid** w pliku projektu:  
  
     **MSBuild-t:updateuid helloapp. csproj**  
  
     Aby sprawdzić, czy nie ma żadnych lub zduplikowanych identyfikatorów UID, uruchom **checkuid**:  
  
     **MSBuild-t:checkuid helloapp. csproj**  
  
     Po uruchomieniu **updateuid**pliki powinny zawierać identyfikatory UID. Na przykład w pliku Pane1. XAML HelloApp należy znaleźć następujące informacje:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Tworzenie zestawu satelickiego dla zasobów języka neutralnego  
 Po skonfigurowaniu aplikacji do generowania zestawu satelickiego dla neutralnych zasobów języka należy skompilować aplikację. Spowoduje to wygenerowanie głównego zestawu aplikacji oraz zestawu satelickiego dla zasobów języka neutralnego, który jest wymagany przez LocBaml do lokalizacji. Aby skompilować aplikację:  
  
1. Kompiluj HelloApp do tworzenia biblioteki dołączanej dynamicznie (DLL):  
  
     **MSBuild helloapp. csproj**  
  
2. Nowo utworzony zestaw aplikacji głównej (HelloApp. exe) jest tworzony w następującym folderze:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. Nowo utworzony zestaw satelicki dla zasobów języka neutralnego, HelloApp. resources. dll, został utworzony w następującym folderze:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>Tworzenie narzędzia LocBaml  
  
1. Wszystkie pliki niezbędne do kompilowania LocBaml znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przykładach. Pobierz C# pliki z przykładu [Narzędzia LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016).  
  
2. W wierszu polecenia Uruchom plik projektu (LocBaml. csproj) w celu skompilowania narzędzia:  
  
     **msbuild locbaml.csproj**  
  
3. Przejdź do katalogu Bin\Release, aby znaleźć nowo utworzony plik wykonywalny (LocBaml. exe). Przykład: C: \LocBaml\Bin\Release\locbaml.exe.  
  
4. Opcje, które można określić, gdy uruchamiasz LocBaml są następujące:  
  
    - **Analizuj** lub **-p:** Analizuje pliki BAML, zasoby lub biblioteki DLL w celu wygenerowania pliku CSV lub txt.  
  
    - **Generuj** lub **-g:** Generuje zlokalizowany plik binarny przy użyciu przetłumaczonego pliku.  
  
    - **out** lub **-o** {*FileDirectory*] **:** Nazwa pliku wyjściowego.  
  
    - **kultura** lub **-CUL** {*Culture*] **:** Ustawienia regionalne zestawów wyjściowych.  
  
    - **tłumaczenie** lub **Trans** {*Translation. csv*] **:** Przetłumaczony lub zlokalizowany plik.  
  
    - **asmpath** lub **-asmpath:** {*FileDirectory*] **:** Jeśli kod zawiera niestandardowe kontrolki, należy podać asmpath do niestandardowego zestawu kontrolek. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
    - **nologo** Nie wyświetla logo ani informacji o prawach autorskich.  
  
    - **pełne** Wyświetla informacje o trybie informacji pełnej.  
  
    > [!NOTE]
    > Jeśli potrzebujesz listy opcji podczas uruchamiania narzędzia, wpisz **LocBaml. exe** i naciśnij klawisz ENTER.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Analizowanie pliku przy użyciu LocBaml  
 Po utworzeniu narzędzia LocBaml można go użyć do przeanalizowania HelloApp. resources. dll w celu wyodrębnienia zawartości tekstowej, która ma zostać zlokalizowana.  
  
1. Skopiuj plik LocBaml. exe do folderu bin\Debug aplikacji, w którym został utworzony zestaw aplikacji głównej.  
  
2. Aby przeanalizować plik zestawu satelickiego i zapisać dane wyjściowe jako plik CSV, użyj następującego polecenia:  
  
     **LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    > Jeśli plik wejściowy HelloApp. resources. dll nie znajduje się w tym samym katalogu, co LocBaml. exe Przenieś jeden z tych plików, tak aby oba pliki były w tym samym katalogu.  
  
3. Po uruchomieniu LocBaml do analizowania plików dane wyjściowe składają się z siedmiu pól rozdzielonych przecinkami (pliki CSV) lub tabulatorami (pliki. txt). Poniżej przedstawiono przeanalizowany plik CSV dla HelloApp. resources. dll:

   | |
   |-|
   |HelloApp. g. pl-US. Resources: window1. BAML, Stack1: System. Windows. Controls. StackPanel. $Content, IGNORE, FALSE, FALSE,, #Text1; #Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   Siedem pól są następujące:  
  
   1. **Nazwa BAML**. Nazwa zasobu BAML w odniesieniu do zestawu satelickiego dla języka źródłowego.  
  
   2. **Klucz zasobu**. Zlokalizowany identyfikator zasobu.  
  
   3. **Kategoria**. Typ wartości. Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).  
  
   4. **Czytelność**. Określa, czy wartość może być odczytywana przez lokalizatora. Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).  
  
   5. **Modifiability**. Czy wartość może być modyfikowana przez lokalizatora. Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).  
  
   6. **Komentarze**. Dodatkowy opis wartości, aby pomóc w ustaleniu, jak jest lokalizowana wartość. Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).  
  
   7. **Wartość**. Wartość tekstowa do przetłumaczenia na pożądaną kulturę.  
  
   W poniższej tabeli przedstawiono, w jaki sposób te pola są mapowane na wartości rozdzielane pliku CSV:  
  
   |Nazwa BAML|Klucz zasobu|Kategoria|Czytelność|Modifiability|Komentarze|Wartość|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Zignoruj|FAŁSZ|FAŁSZ||#Text1;#Text2|
   |HelloApp.g.en-US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|Brak|OZNACZA|OZNACZA||Witaj Świecie|
   |HelloApp.g.en-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|Brak|OZNACZA|OZNACZA||Na świecie|
  
   Zwróć uwagę, że wszystkie wartości pola **Komentarze** nie zawierają wartości; Jeśli pole nie ma wartości, jest puste. Zauważ również, że element w pierwszym wierszu nie jest możliwy do odczytania ani do zmodyfikowania, a jego wartość **kategorii** jest ignorowana, a wszystko wskazuje, że wartość nie jest lokalizowalna.  
  
4. Aby ułatwić odnajdywanie lokalizowalnych elementów w przeanalizowanych plikach, szczególnie w dużych plikach, można sortować lub filtrować elementy według **kategorii**, **czytelności**i **modifiability**. Na przykład można odfiltrować niemodyfikowalne i niemodyfikowane wartości.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Tłumaczenie lokalizowalnej zawartości  
 Użyj dowolnego dostępnego narzędzia, aby przetłumaczyć wyodrębnioną zawartość. Dobrym sposobem jest zapisanie zasobów do pliku CSV i wyświetlenie ich w programie w [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]celu dokonania zmiany tłumaczenia na ostatnią kolumnę (wartość).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Użyj LocBaml, aby wygenerować nowy plik resources. dll  
 Zawartość zidentyfikowana przez analizowanie HelloApp. resources. dll z LocBaml została przetłumaczona i należy ją scalić z powrotem do oryginalnej aplikacji. Użyj opcji **Generuj** lub **-g** , aby wygenerować nowy plik resources. dll.  
  
1. Użyj następującej składni, aby wygenerować nowy plik HelloApp. resources. dll. Oznacz kulturę jako en-US (/CUL: en-US).  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**  
  
    > [!NOTE]
    > Jeśli plik wejściowy, Hello. csv, nie znajduje się w tym samym katalogu co plik wykonywalny, LocBaml. exe, Przenieś jeden z tych plików, tak aby oba pliki były w tym samym katalogu.  
  
2. Zastąp stary plik HelloApp. resources. dll w katalogu C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nowo utworzonym plikiem HelloApp. resources. dll.  
  
3. "Hello world" i "Pożegnanie świata" powinny teraz zostać przetłumaczone w aplikacji.  
  
4. Aby przetłumaczyć na inną kulturę, należy użyć kultury języka, do którego jest przeprowadzana translacja. Poniższy przykład pokazuje, jak przetłumaczyć na francuski — kanadyjski:  
  
     **LocBaml. exe/Generate HelloApp. resources. dll/Trans: Hellofr-CA. csv/out: c:\/CUL: fr-CA**  
  
5. W tym samym zestawie, w którym znajduje się główny zestaw aplikacji, Utwórz nowy folder specyficzny dla kultury, który ma być nowym zestawem satelickim. W języku francuskim — kanadyjskim folderem będzie fr-CA.  
  
6. Skopiuj wygenerowany zestaw satelicki do nowego folderu.  
  
7. Aby przetestować nowy zestaw satelicki, należy zmienić kulturę, w której zostanie uruchomiona aplikacja. Można to zrobić na jeden z dwóch sposobów:  
  
    - Zmień ustawienia regionalne systemu operacyjnego (**Uruchom** &#124; **panel** &#124; sterowania **Opcje regionalne i językowe**).  
  
    - W aplikacji Dodaj następujący kod do App.xaml.cs:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>Niektóre wskazówki dotyczące używania LocBaml  
  
- Wszystkie zestawy zależne, które definiują niestandardowe kontrolki, muszą zostać skopiowane do katalogu lokalnego LocBaml lub zainstalowane w pamięci podręcznej GAC. Jest to konieczne, ponieważ interfejs API lokalizacji musi mieć dostęp do zestawów zależnych, gdy odczytuje plik binarny XAML (BAML).  
  
- Jeśli główny zestaw jest podpisany, wygenerowana Biblioteka DLL zasobów musi być również podpisana, aby można było ją załadować.  
  
- Wersja zlokalizowanej biblioteki DLL zasobów musi być synchronizowana z zestawem głównym.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Co dalej  
 Teraz należy uzyskać podstawową wiedzę na temat sposobu korzystania z narzędzia LocBaml.  Powinno być możliwe tworzenie pliku, który zawiera identyfikatory UID. Za pomocą narzędzia LocBaml, powinno być możliwe przeanalizowanie pliku w celu wyodrębnienia zawartości lokalizowalnej i po przetłumaczeniu zawartości, powinno być możliwe wygenerowanie pliku. resources. dll, który scala przetłumaczoną zawartość. Ten temat nie zawiera wszystkich szczegółów, ale teraz masz wiedzę niezbędną do lokalizowania aplikacji za pomocą LocBaml.  
  
## <a name="see-also"></a>Zobacz także

- [Globalizacja dla WPF](globalization-for-wpf.md)
- [Przegląd używania automatycznego układu](use-automatic-layout-overview.md)
