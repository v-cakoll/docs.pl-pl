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
ms.openlocfilehash: ae73ab92ebf3089eebf51f40b0c144f3dbea44da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-localize-an-application"></a>Jak lokalizować aplikację
Ten samouczek wyjaśnia sposób tworzenia zlokalizowanej aplikacji za pomocą narzędzia LocBaml.  
  
> [!NOTE]
>  Narzędzie LocBaml nie jest aplikacją gotowe do produkcji. Jest on przedstawiony jako przykład, który używa niektórych lokalizacja interfejsów API i przedstawiono, jak mogą pisać narzędzia lokalizacji.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Omówienie  
 Rozważania umożliwia podejście krok po kroku do lokalizowania aplikacji. Należy najpierw przygotować aplikacji, dzięki czemu można wyodrębnić tekst, który zostanie zamieniona. Po translacji tekst przetłumaczony tekst zostanie scalić nową kopię oryginalnej aplikacji.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W trakcie tej dyskusji użyjesz [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], która jest uruchamiana z poziomu wiersza polecenia kompilatora.  
  
 Ponadto możesz zostaniecie przy użyciu pliku projektu. Aby uzyskać instrukcje dotyczące sposobu używania [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] i pliki projektu, zobacz [tworzenie i wdrażanie](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).  
  
 Wszystkie przykłady w tej dyskusji Użyj en US (Stany Zjednoczone angielski) jako kultury. Dzięki temu można pracować kroki przykłady bez instalowania innego języka.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Tworzenie przykładowej aplikacji  
 W tym kroku przygotujesz się do lokalizacji aplikacji. W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przykłady HelloApp podano przykładowe, który będzie używany w przykładach kodu w tej dyskusji. Jeśli chcesz użyć tego przykładu, Pobierz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików ze [przykładowe narzędzie LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016).  
  
1.  Tworzenie aplikacji do punktu, w którym chcesz uruchomić lokalizacji.  
  
2.  Wybierz język programowania w pliku projektu, aby [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generuje główny zestaw i zestawu satelickiego (plik o. rozszerzenie resources.dll) zawiera zasoby niezależnym od języka. Plik projektu w przykładowym HelloApp jest HelloApp.csproj. W tym pliku znajdziesz języka programowania, określone w następujący sposób:  
  
     `<UICulture>en-US</UICulture>`  
  
3.  Dodaj UID do Twojej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików. UID są używane do śledzenia zmian w plikach i zidentyfikować elementy, które muszą zostać przetłumaczone. Aby dodać UID do plików, uruchom **updateuid** w pliku projektu:  
  
     **MSBUILD /t:updateuid helloapp.csproj**  
  
     Aby sprawdzić, czy nie brakuje lub zduplikowane identyfikatory UID, uruchom **checkuid**:  
  
     **MSBUILD /t:checkuid helloapp.csproj**  
  
     Po uruchomieniu **updateuid**, pliki powinny zawierać UID. Na przykład w pliku Pane1.xaml HelloApp, powinien znajdować się następujące czynności:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Tworzenie zestawu satelickiego neutralny język zasobów  
 Po skonfigurowaniu aplikacji do wygenerowania neutralny język zasobów satelicki kompilowania aplikacji. Spowoduje to wygenerowanie zestawu aplikacji głównej, a także niezależnym od języka zestawu satelickiego zasoby wymagane przez LocBaml lokalizacji. Aby skompilować aplikację:  
  
1.  Kompiluj HelloApp, aby utworzyć [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:  
  
     **MSBUILD helloapp.csproj**  
  
2.  Zestaw nowo utworzonej aplikacji głównej HelloApp.exe, jest tworzony w następującym folderze:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3.  Zestawu satelickiego zasobów nowo utworzony niezależnym od języka, HelloApp.resources.dll, jest tworzony w następującym folderze:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>Narzędzie LocBaml kompilacji  
  
1.  Wszystkie pliki niezbędne do utworzenia LocBaml znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] próbek. Pobierz pliki C# z [przykładowe narzędzie LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016).  
  
2.  W wierszu polecenia Uruchom pliku projektu (locbaml.csproj) w celu utworzenia narzędzie:  
  
     **MSBUILD locbaml.csproj**  
  
3.  Przejdź do katalogu Bin\Release odszukaj nowo utworzony plik wykonywalny (locbaml.exe). Example:C:\LocBaml\Bin\Release\locbaml.exe.  
  
4.  Dostępne są następujące opcje, które można określić podczas uruchamiania LocBaml:  
  
    -   **przeanalizować** lub **-p:** analizuje Baml zasoby, lub [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] pliki, aby wygenerować plik CSV lub txt.  
  
    -   **Generowanie** lub **-g:** generuje zlokalizowanego pliku binarnego przy użyciu przetłumaczonego pliku.  
  
    -   **limit** lub **-o** {*filedirectory*] **:** nazwę pliku wyjściowego.  
  
    -   **kultura** lub **- cul** {*kultury*] **:** ustawień regionalnych zestawów danych wyjściowych.  
  
    -   **Tłumaczenie** lub **— transakcja** {*translation.csv*] **:** tłumaczone lub zlokalizowanego pliku.  
  
    -   **asmpath** lub **- asmpath:** {*filedirectory*] **:** Jeśli Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod zawiera kontrolki niestandardowe, należy podać  **asmpath** do zestawu kontrolki niestandardowej.  
  
    -   **nologo:** Wyświetla żadne logo lub prawa autorskie informacje.  
  
    -   **verbose:** Wyświetla informacje o trybie informacji pełnej.  
  
    > [!NOTE]
    >  Aby uzyskać listę opcji po uruchomieniu narzędzia, wpisz **LocBaml.exe** i naciśnij klawisz ENTER.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Użyj LocBaml można przeanalizować pliku  
 Teraz, po utworzeniu narzędzia LocBaml, można przystąpić do jej użyć do analizowania HelloApp.resources.dll w celu wyodrębnienia zawartości tekstowej, który zostanie zlokalizowany.  
  
1.  Skopiuj LocBaml.exe do folderu bin\debug aplikacji, w której został utworzony zestaw aplikacji głównej.  
  
2.  Aby przeanalizować plik zestawu satelity i przechowywanie danych wyjściowych w formacie pliku CSV, użyj następującego polecenia:  
  
     **/Parse LocBaml.exe HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    >  Jeśli plik wejściowy HelloApp.resources.dll, nie znajduje się w tym samym katalogu co LocBaml.exe przenieść jeden z plików, tak aby oba pliki znajdują się w tym samym katalogu.  
  
3.  Po uruchomieniu LocBaml do analizy pliki, dane wyjściowe składa się z siedmiu pola oddzielane przecinkami (.csv pliki) lub kart (txt). Poniżej przedstawiono plik CSV przeanalizowany HelloApp.resources.dll:

   | |
   |-|
   |HelloApp.g.en US.resources:window1.baml, Stack1:System.Windows.Controls.StackPanel. $Content, zignorować, FALSE, FALSE, # Tekst1; tekst2 #;|
   |HelloApp.g.en US.resources:window1.baml, Text1:System.Windows.Controls.TextBlock. $Content, None, wartość TRUE, TRUE,, Witaj świecie|
   |HelloApp.g.en US.resources:window1.baml, Text2:System.Windows.Controls.TextBlock. $Content, None, wartość TRUE, TRUE,, World praktyczny brak jakichkolwiek|

   Siedem pola to:  
  
   1.  **Nazwa BAML**. Nazwa zasobu BAML względem zestawu satelickiego języka źródłowego.  
  
   2.  **Klucz zasobu**. Identyfikator zlokalizowanego zasobu.  
  
   3.  **Kategoria**. Typ wartości. Zobacz [atrybuty lokalizacji i komentarze](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   4.  **Czytelność**. Określa, czy można odczytać wartości przez lokalizatora. Zobacz [atrybuty lokalizacji i komentarze](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   5.  **Modifiability**. Określa, czy wartość może być modyfikowany przez lokalizatora. Zobacz [atrybuty lokalizacji i komentarze](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   6.  **Komentarze**. Dodatkowy opis wartości w celu określenia sposobu zlokalizowaną wartość. Zobacz [atrybuty lokalizacji i komentarze](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   7.  **Wartość**. Wartości tekstowe można przetłumaczyć na żądaną kulturę.  
  
   W poniższej tabeli przedstawiono sposób mapowania te pola z wartościami rozdzielanego pliku CSV:  
  
   |Nazwa BAML|Klucz zasobu|Kategoria|Czytelności|Modifiability|Komentarze|Wartość|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en US.resources:window1.baml|Stack1:system.Windows.Controls.StackPanel.$Content|Ignoruj|FAŁSZ|FAŁSZ||# Tekst1; tekst2 #|
   |HelloApp.g.en US.resources:window1.baml|Text1:system.Windows.Controls.TextBlock.$Content|Brak|WARTOŚĆ TRUE|WARTOŚĆ TRUE||Witaj Świecie|
   |HelloApp.g.en US.resources:window1.baml|Text2:system.Windows.Controls.TextBlock.$Content|Brak|WARTOŚĆ TRUE|WARTOŚĆ TRUE||Praktyczny brak jakichkolwiek świata|
  
   Zwróć uwagę, że wszystkie wartości dla **komentarze** pola nie zawierają wartości; Jeśli pole nie zawiera wartości, jest pusta. Również zauważyć, że nie można odczytać ani modyfikować elementu w pierwszym wierszu, a ma "Ignoruj" jako jego **kategorii** wartości, które wskazuje, czy wartość nie jest lokalizowalny.  
  
4.  Ułatwia odnajdywanie Lokalizowalny elementów w plikach przeanalizowane, szczególnie w przypadku dużych plików, można sortować i filtrować elementy według **kategorii**, **czytelność**, i **Modifiability**. Na przykład można odfiltrować wartości nie można go odczytać i unmodifiable.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Tłumaczenie zlokalizowania zawartości  
 Narzędzie wszystkie dostępne do tłumaczenia wyodrębnionej zawartości. Dobrym sposobem, w tym celu jest napisanie zasobów do pliku CSV pliku i wyświetlić je w [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], tłumaczenia wprowadzania zmian do ostatniego kolumny (wartość).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Użyj LocBaml, aby wygenerować nowy. plik resources.dll  
 Zawartość, która została zidentyfikowana analizując HelloApp.resources.dll z LocBaml został przetłumaczony i musi być scalone oryginalnej aplikacji. Użyj **Generowanie** lub **-g** opcję, aby wygenerować nowy. resources.dll pliku.  
  
1.  Użyj następującej składni, aby wygenerować nowy plik HelloApp.resources.dll. Oznacz kultury jako en US (/ cul:en-US).  
  
     **LocBaml.exe / generuje HelloApp.resources.dll /trans:Hello.csv /out:c: \ /cul:en — stany USA**  
  
    > [!NOTE]
    >  Jeśli plik wejściowy Hello.csv, nie jest w tym samym katalogu co plik wykonywalny, LocBaml.exe, przenieść jeden z plików, tak aby oba pliki znajdują się w tym samym katalogu.  
  
2.  Zamień stary plik HelloApp.resources.dll w katalogu C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nowo utworzony plik HelloApp.resources.dll.  
  
3.  "Hello World" i "Goodbye World" powinna teraz translacji w aplikacji.  
  
4.  Aby przełożyć na inną kulturę, użyj kultury są tłumaczenia na język. Poniższy przykład przedstawia sposób przełożyć na French-Canadian:  
  
     **LocBaml.exe / generuje HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c: \ /cul:fr — urzędu certyfikacji**  
  
5.  W skład zestawu jako zestawu głównego aplikacji Utwórz nowy folder specyficzne dla kultury do przechowywania nowego zestawu satelickiego. French-Canadian folder będzie fr-CA.  
  
6.  Skopiuj ten plik zestawu generowanej satelitarnej do nowego folderu.  
  
7.  Aby przetestować nowego zestawu satelickiego, musisz zmienić kultury uruchamiania aplikacji. Można to zrobić na jeden z dwóch sposobów:  
  
    -   Zmień ustawienia regionalne systemu operacyjnego (**Start** &#124; **Panelu sterowania** &#124; **Opcje regionalne i językowe**).  
  
    -   W aplikacji Dodaj następujący kod do pliku App.xaml.cs:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>Wskazówki dotyczące korzystania z LocBaml  
  
-   Wszystkie zależne zestawy definiujące niestandardowych formantów muszą być kopiowane do katalogu lokalnego LocBaml lub zainstalowane w pamięci GAC. Jest to konieczne, ponieważ lokalizacja interfejsu API musi mieć dostęp do zestawów zależnych, gdy odczytuje [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].  
  
-   Jeśli główny zestaw został podpisany, biblioteka DLL zasobów wygenerowany również muszą być podpisane w celu załadowania.  
  
-   Wersja zlokalizowanych zasobów biblioteki DLL muszą być zsynchronizowane z zestawu głównego.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Co to jest dalej  
 Teraz powinien mieć podstawową wiedzę na temat używania narzędzia LocBaml.  Należy wprowadzać plik zawierający UID. Za pomocą narzędzia LocBaml, można przeanalizować pliku można wyodrębnić zlokalizowania zawartości, a po translacji zawartości powinno być możliwe do wygenerowania. plik resources.dll scala przetłumaczonego zawartości. Ten temat nie zawiera wszystkich możliwych szczegółach, ale teraz ma wiedzy koniecznych do używania LocBaml do lokalizowania aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Globalizacja dla WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Przegląd używania automatycznego układu](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
