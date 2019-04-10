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
ms.openlocfilehash: d08f991204b2d74899cbd1aee82c0cc23e175dd4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298321"
---
# <a name="how-to-localize-an-application"></a>Instrukcje: Lokalizowanie aplikacji
W tym samouczku opisano sposób tworzenia zlokalizowanych aplikacji przy użyciu locbaml — narzędzie.  
  
> [!NOTE]
>  Locbaml — narzędzie nie jest aplikacją gotowe do produkcji. Jest on przedstawiony jako przykład używana część lokalizacji interfejsów API, który ilustruje, w jaki sposób można napisać narzędziem do lokalizacji.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Omówienie  
 Tej dyskusji zapewnia szczegółowe podejście do lokalizowania aplikacji. Najpierw zostanie przygotowany aplikacji, dzięki czemu można wyodrębnić tekst, który zostanie zamieniona. Po tekst jest tłumaczony, zostaną scalone przetłumaczonego tekstu do nowej kopii oryginalnej aplikacji.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W trakcie tej dyskusji, której użyjesz [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], czyli kompilatora, które jest uruchamiane z wiersza polecenia.  
  
 Ponadto pojawi się instrukcja przy użyciu pliku projektu. Aby uzyskać instrukcje dotyczące sposobu używania [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] i pliki projektu, zobacz [tworzenie i wdrażanie](../app-development/building-and-deploying-wpf-applications.md).  
  
 Wszystkie przykłady w tej dyskusji pełnić kultury en US (Angielski-Stany Zjednoczone). Dzięki temu można pracować kroki przykłady bez konieczności instalowania na inny język.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Tworzenie przykładowej aplikacji  
 W tym kroku przygotujesz się do lokalizacji aplikacji. W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przykłady HelloApp podano przykładowe, który będzie używany dla przykładów kodu w tej dyskusji. Jeśli chcesz korzystać z tej próbki, Pobierz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików ze [locbaml — narzędzie przykładowe](https://go.microsoft.com/fwlink/?LinkID=160016).  
  
1. Tworzenie aplikacji do punktu, w którym chcesz uruchomić lokalizacji.  
  
2. Wybierz język programowania w pliku projektu, aby [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generuje głównym zestawie i zestawem satelickim (plik o. resources.dll rozszerzenia) zawierać neutralny język zasobów. Plik projektu w przykładzie HelloApp jest HelloApp.csproj. W tym pliku znajdziesz języka programowania, określone w następujący sposób:  
  
     `<UICulture>en-US</UICulture>`  
  
3. UID, aby dodać swoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików. UID są używane do śledzenia zmian w plikach i zidentyfikować elementy, które musi podlegać translacji. Aby dodać UID do plików, uruchom **updateuid** w pliku projektu:  
  
     **msbuild -t:updateuid helloapp.csproj**  
  
     Aby sprawdzić, czy nie brakuje lub zduplikowane UID, uruchom **checkuid**:  
  
     **msbuild -t:checkuid helloapp.csproj**  
  
     Po uruchomieniu **updateuid**, pliki może zawierać UID. Na przykład w pliku Pane1.xaml HelloApp, powinien znajdować się następujące czynności:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Tworzenie zestawu satelickiego neutralny język zasobów  
 Po skonfigurowaniu aplikacji do generowania zestawu satelickiego neutralny język zasobów kompilacji aplikacji. Spowoduje to wygenerowanie zestawie aplikacji głównej, a także zestawu satelickiego neutralny język zasobów, wymaganego przez locbaml — dla lokalizacji. Aby skompilować aplikację:  
  
1. Skompilować HelloApp, aby utworzyć [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:  
  
     **MSBUILD helloapp.csproj**  
  
2. Nowo utworzony głównym zestawem aplikacji, HelloApp.exe, jest tworzony w następującym folderze:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. Zestawu satelickiego zasobów nowo utworzony neutralnym językiem, HelloApp.resources.dll, jest tworzony w następującym folderze:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>Tworzenie locbaml — narzędzie  
  
1. Wszystkie pliki niezbędne do utworzenia locbaml — znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przykładów. Pobierz pliki C# z [locbaml — narzędzie przykładowe](https://go.microsoft.com/fwlink/?LinkID=160016).  
  
2. Uruchom plik projektu (locbaml.csproj) do skompilowania narzędzie z wiersza polecenia:  
  
     **msbuild locbaml.csproj**  
  
3. Przejdź do katalogu Bin\Release, aby znaleźć nowo utworzony plik wykonywalny (locbaml.exe). Example:C:\LocBaml\Bin\Release\locbaml.exe.  
  
4. Dostępne są następujące opcje, które można określić po uruchomieniu locbaml —:  
  
    -   **analizowanie** lub **-p:** Analizuje Baml, zasobów, lub [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] plików, aby wygenerować plik CSV lub txt.  
  
    -   **Generowanie** lub **-g:** Generuje zlokalizowany plik binarny, używając przetłumaczonego pliku.  
  
    -   **limit** lub **-o** {*filedirectory*] **:** Nazwa pliku wyjściowego.  
  
    -   **kultura** lub **- cul** {*kultury*] **:** Ustawienia regionalne, zestawów danych wyjściowych.  
  
    -   **Tłumaczenie** lub **- trans** {*translation.csv*] **:** Przetłumaczone lub zlokalizowanego pliku.  
  
    -   **asmpath** lub **- asmpath:** {*filedirectory*] **:** Jeśli Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod zawiera kontrolki niestandardowe, należy podać **asmpath** do zestawu kontrolki niestandardowej.  
  
    -   **nologo:** Wyświetla informacje o nie logo lub praw autorskich.  
  
    -   **verbose:** Wyświetla informacje o trybie informacji pełnej.  
  
    > [!NOTE]
    >  Jeśli potrzebujesz listę opcji, gdy uruchamiasz narzędzie, należy wpisać **LocBaml.exe** i naciśnij klawisz ENTER.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Locbaml — Użyj, aby analizować plik  
 Teraz, po utworzeniu locbaml — narzędzie, jesteś gotowy na potrzeby analizowania HelloApp.resources.dll, aby wyodrębnić zawartość tekstu, który zostanie zlokalizowany.  
  
1. Skopiuj LocBaml.exe do folderu bin\debug aplikacji, w której utworzono zestawu głównej aplikacji.  
  
2. Aby przeanalizować plik zestawu satelickiego i przechowywanie danych wyjściowych w formacie pliku CSV, użyj następującego polecenia:  
  
     **LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    >  Jeśli plik wejściowy HelloApp.resources.dll, nie znajduje się w tym samym katalogu co LocBaml.exe przenieść jeden z plików, tak aby oba pliki znajdują się w tym samym katalogu.  
  
3. Po uruchomieniu locbaml — można przeanalizować pliki, dane wyjściowe składa się z siedmiu pól rozdzielonych przecinkami (.csv pliki) lub kart (txt). Poniżej przedstawiono plik CSV przeanalizowany HelloApp.resources.dll:

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   Siedem pola są:  
  
   1.  **Nazwa BAML**. Nazwa zasobu BAML w odniesieniu do zestawu satelickiego języka źródłowego.  
  
   2.  **Klucz zasobu**. Identyfikator zlokalizowanych zasobów.  
  
   3.  **Kategoria**. Typ wartości. Zobacz [lokalizacja atrybutów i komentarzy](localization-attributes-and-comments.md).  
  
   4.  **Czytelność**. Czy można odczytać wartości przez lokalizatorowi. Zobacz [lokalizacja atrybutów i komentarzy](localization-attributes-and-comments.md).  
  
   5.  **Modifiability**. Czy wartość może być modyfikowany przez lokalizatorowi. Zobacz [lokalizacja atrybutów i komentarzy](localization-attributes-and-comments.md).  
  
   6.  **Komentarze**. Dodatkowy opis wartości w celu określenia, jak wartość jest zlokalizowana. Zobacz [lokalizacja atrybutów i komentarzy](localization-attributes-and-comments.md).  
  
   7.  **Wartość**. Wartość tekstowa do translacji na żądaną kulturę.  
  
   W poniższej tabeli przedstawiono sposób mapowania tych pól do wartości rozdzielanego pliku CSV:  
  
   |Nazwa BAML|Klucz zasobu|Kategoria|Czytelność|Modifiability|Komentarze|Wartość|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Zignoruj|FAŁSZ|FAŁSZ||#Text1;#Text2|
   |HelloApp.g.en-US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|Brak|WARTOŚĆ TRUE|WARTOŚĆ TRUE||Witaj Świecie|
   |HelloApp.g.en-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|Brak|WARTOŚĆ TRUE|WARTOŚĆ TRUE||Goodbye World|
  
   Należy zauważyć, że wszystkie wartości dla **komentarze** pola nie zawierają wartości; Jeśli pola nie ma wartości, jest pusty. Także zauważyć, że elementu w pierwszym wierszu nie można odczytać ani można modyfikować oraz "Ignorowania" jako jego **kategorii** wartości, które wskazuje, że wartość jest możliwych do zlokalizowania.  
  
4. Ułatwiają odnajdowanie elementów możliwych do zlokalizowania w plikach przeanalizowany, szczególnie w dużych plików, można sortować i filtrować elementy według **kategorii**, **czytelność**, i **Modifiability**. Na przykład można odfiltrować wartości nie można go odczytać i niemodyfikowalnych.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Tłumaczenie możliwych do zlokalizowania zawartości  
 Za pomocą dowolnego narzędzia dostępne do translacji wyodrębnionej zawartości. Dobrym sposobem na to jest napisanie pliku zasobów do pliku CSV i wyświetlić je w [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], co tłumaczenia ostatnio zmiany kolumny (wartość).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Użyj locbaml —, aby wygenerować nowy. resources.dll pliku  
 Zawartość, który został zidentyfikowany przez analizowanie HelloApp.resources.dll z locbaml — został przetłumaczony i musi być scalone oryginalnej aplikacji. Użyj **Generowanie** lub **-g** opcję, aby wygenerować nowy. resources.dll pliku.  
  
1. Użyj następującej składni, aby wygenerować nowy plik HelloApp.resources.dll. Oznacz kulturę, co en US (/ cul:en — Stany Zjednoczone).  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**  
  
    > [!NOTE]
    >  Jeśli plik wejściowy Hello.csv, nie jest w tym samym katalogu co plik wykonywalny LocBaml.exe, należy przenieść jeden z plików tak, aby oba pliki znajdują się w tym samym katalogu.  
  
2. Zastąp starego pliku HelloApp.resources.dll w katalogu C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nowo utworzony plik HelloApp.resources.dll.  
  
3. "Hello World" i "Goodbye World" powinien teraz przetłumaczony na aplikację.  
  
4. Do tłumaczenia, aby określić inną kulturę, używają kultury języka, który tłumaczy do. Poniższy przykład pokazuje, jak przełożyć na French-Canadian:  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**  
  
5. Z tego samego zestawu jako zestawu głównej aplikacji Utwórz nowy folder specyficzne dla kultury do przechowywania nowego zestawu satelickiego. French-Canadian folder będzie fr-CA.  
  
6. Skopiuj wygenerowany satelicki do nowego folderu.  
  
7. Aby przetestować nowego zestawu satelickiego, musisz zmienić kulturę, w którym aplikacja jest uruchamiana. Można to zrobić na jeden z dwóch sposobów:  
  
    -   Zmień ustawienia regionalne systemu operacyjnego (**Start** &#124; **Panelu sterowania** &#124; **Opcje regionalne i językowe**).  
  
    -   W aplikacji Dodaj następujący kod do pliku App.xaml.cs:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>Wskazówki dotyczące korzystania z locbaml —  
  
-   Wszystkie zależne zestawy, które definiują niestandardowe formanty, musi być skopiowany do katalogu lokalnego locbaml — lub zainstalowane w GAC. Jest to konieczne, ponieważ lokalizacja interfejsu API musi mieć dostęp do zestawów zależnych, gdy odczytuje [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].  
  
-   Jeśli główny zestaw jest podpisany, wygenerowany Biblioteka DLL zasobu, również muszą być podpisane w celu użycia go do załadowania.  
  
-   Wersja zlokalizowanych zasobów biblioteki DLL muszą być zsynchronizowane z zestawu głównego.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Jaka jest przyszłość  
 Teraz powinien mieć podstawową wiedzę na temat sposobu użycia locbaml — narzędzie.  Powinien móc plik, który zawiera UID. Za pomocą locbaml — narzędzie, można przeanalizować pliku można wyodrębnić możliwych do zlokalizowania zawartości, a po zawartość jest tłumaczona, powinno być możliwe wygenerowanie. resources.dll zawierający scala tłumaczonej zawartości. W tym temacie nie ma możliwości szczegóły każdego zdarzenia, ale masz teraz wiedzy koniecznych do używania locbaml — do lokalizowania aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Globalizacja dla WPF](globalization-for-wpf.md)
- [Przegląd Użyj automatycznego układu](use-automatic-layout-overview.md)
