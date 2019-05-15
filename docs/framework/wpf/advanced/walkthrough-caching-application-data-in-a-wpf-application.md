---
title: 'Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: d8f37431279cc22b8e9c131f860b5de82f35af2e
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591208"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF
Pamięć podręczna umożliwia przechowywanie danych w pamięci, aby uzyskać szybki dostęp. Gdy dane są używane ponownie, aplikacje można uzyskać danych z pamięci podręcznej, zamiast pobierania z oryginalnego źródła. Może to poprawić wydajność i skalowalność. Ponadto buforowania sprawia, że dane dostępne, gdy źródłem danych jest tymczasowo niedostępna.

 .NET Framework zawiera klasy, które umożliwiają używanie buforowania w aplikacjach .NET Framework. W ramach tych zajęć, znajdują się w <xref:System.Runtime.Caching> przestrzeni nazw.

> [!NOTE]
>  <xref:System.Runtime.Caching> Przestrzeń nazw jest nowa w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. Ta przestrzeń nazw sprawia, że pamięć podręczna jest dostępna dla wszystkich aplikacji .NET Framework. W poprzednich wersjach programu .NET Framework, pamięć podręczna była dostępna tylko w <xref:System.Web> przestrzeni nazw i dlatego wymagane zależności klas programu ASP.NET.

 W tym instruktażu pokazano, jak korzystać z funkcji buforowania, która jest dostępna w programie .NET Framework jako część [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. W instruktażu pamięci podręcznej zawartość pliku tekstowego.

 Zadania przedstawione w niniejszym przewodniku to m.in.:

- Tworzenie projektu aplikacji WPF.

- Dodawanie odwołania do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].

- Inicjowanie pamięci podręcznej.

- Dodawanie wpisu pamięci podręcznej, który zawiera zawartość pliku tekstowego.

- Zapewnianie zasady eksmisji dla wpisu pamięci podręcznej.

- Monitorowanie ścieżkę do pliku pamięci podręcznej i powiadamiania wystąpienie pamięci podręcznej o zmiany monitorowania elementów.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, potrzebne są:

- Microsoft Visual Studio 2010.

- Plik tekstowy, który zawiera niewielkiej ilości tekstu. (W oknie komunikatu zostanie wyświetlona zawartość pliku tekstowego). Kod zilustrowane w instruktażu przyjęto założenie, że pracujesz z następującego pliku:

     `c:\cache\cacheText.txt`

     Można jednak użyć dowolnego pliku tekstowego i wprowadzać niewielkie zmiany w kodzie, w tym przewodniku.

## <a name="creating-a-wpf-application-project"></a>Tworzenie projektu aplikacji WPF
 Rozpoczniesz od utworzenia projektu aplikacji WPF.

#### <a name="to-create-a-wpf-application"></a>Aby utworzyć aplikację WPF

1. Uruchom program Visual Studio.

2. W **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **nowy projekt**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

3. W obszarze **zainstalowane szablony**, wybierz język programowania, którego chcesz użyć (**języka Visual Basic** lub **Visual C#**).

4. W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji WPF**.

    > [!NOTE]
    >  Jeśli nie widzisz **aplikacji WPF** szablonu, upewnij się, że są przeznaczone dla wersji programu .NET Framework, która obsługuje WPF. W **nowy projekt** okno dialogowe, wybierz opcję [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] z listy.

5. W **nazwa** tekstu wprowadź nazwę dla projektu. Na przykład można wprowadzić **WPFCaching**.

6. Wybierz **Utwórz katalog rozwiązania** pole wyboru.

7. Kliknij przycisk **OK**.

     Zostanie otwarty projektant WPF w **projektowania** służy do wyświetlania i wyświetla pliku MainWindow.xaml. Program Visual Studio tworzy **mój projekt** folder, plik Application.xaml i pliku MainWindow.xaml.

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>Zgodne z .NET Framework i dodanie odwołania do pamięci podręcznej zestawów
 Domyślnie docelowych aplikacji programu WPF [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]. Aby użyć <xref:System.Runtime.Caching> przestrzeni nazw w aplikacji WPF, aplikacja musi być przeznaczony dla [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (nie [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) i może zawierać odwołanie do przestrzeni nazw.

 W związku z tym, następnym krokiem jest zmienić docelową .NET Framework i Dodaj odwołanie do <xref:System.Runtime.Caching> przestrzeni nazw.

> [!NOTE]
>  Procedury dotyczące zmieniania obiektu docelowego .NET Framework różni się w projekcie języka Visual Basic, jak i w projektach Visual C#.

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Aby zmienić docelową aplikację .NET Framework w języku Visual Basic

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.

     Zostanie wyświetlone okno właściwości dla aplikacji.

2. Kliknij przycisk **skompilować** kartę.

3. W dolnej części okna kliknij **zaawansowane opcje kompilacji...** .

     **Zaawansowane ustawienia kompilatora** zostanie wyświetlone okno dialogowe.

4. W **platformy docelowej (wszystkie konfiguracje)** listy wybierz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Nie należy wybierać [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)

5. Kliknij przycisk **OK**.

     **Zmiana platformy docelowej** zostanie wyświetlone okno dialogowe.

6. W **zmiana platformy docelowej** okno dialogowe, kliknij przycisk **tak**.

     Projekt jest zamknięty, a następnie ponownego otworzenia.

7. Dodaj odwołanie do pamięci podręcznej zestawów, wykonując następujące czynności:

    1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**.

    2. Wybierz **.NET** zaznacz `System.Runtime.Caching`, a następnie kliknij przycisk **OK**.

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Aby zmienić docelową aplikację .NET Framework w projektach Visual C#

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.

     Zostanie wyświetlone okno właściwości dla aplikacji.

2. Kliknij przycisk **aplikacji** kartę.

3. W **platformę docelową** listy wybierz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Nie należy wybierać **.NET Framework 4 Client Profile**.)

4. Dodaj odwołanie do pamięci podręcznej zestawów, wykonując następujące czynności:

    1. Kliknij prawym przyciskiem myszy **odwołania** folder, a następnie kliknij przycisk **Dodaj odwołanie**.

    2. Wybierz **.NET** zaznacz `System.Runtime.Caching`, a następnie kliknij przycisk **OK**.

## <a name="adding-a-button-to-the-wpf-window"></a>Dodawanie przycisku do okna WPF
 Następnie będzie dodać formant przycisku i utworzyć program obsługi zdarzeń dla przycisku `Click` zdarzeń. Później dodasz kod, po kliknięciu przycisku, zawartość pliku tekstowego są buforowane i wyświetlane.

#### <a name="to-add-a-button-control"></a>Aby dodać kontrolkę przycisku

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie plik MainWindow.xaml, aby go otworzyć.

2. Z **przybornika**w obszarze **wspólnych formantów WPF**, przeciągnij `Button` kontrolę `MainWindow` okna.

3. W **właściwości** oknie `Content` właściwość `Button` kontrolę **Pobieranie pamięci podręcznej**.

## <a name="initializing-the-cache-and-caching-an-entry"></a>Inicjowanie pamięci podręcznej i buforowania wpis
 Następnie dodasz kod do wykonywania następujących zadań:

- Tworzenie wystąpienia klasy pamięci podręcznej — oznacza to, można będzie utworzyć <xref:System.Runtime.Caching.MemoryCache> obiektu.

- Korzysta z pamięci podręcznej <xref:System.Runtime.Caching.HostFileChangeMonitor> obiektów do monitorowania zmian w pliku tekstowym.

- Odczyt pliku tekstowego i jego zawartość w pamięci podręcznej jako wpis pamięci podręcznej.

- Wyświetl zawartość pliku tekstowego pamięci podręcznej.

#### <a name="to-create-the-cache-object"></a>Można utworzyć obiektu pamięci podręcznej

1. Kliknij dwukrotnie przycisk, który właśnie został dodany w celu utworzenia programu obsługi zdarzeń w pliku MainWindow.xaml.cs lub MainWindow.Xaml.vb.

2. W górnej części pliku (przed deklaracją klasy), Dodaj następujący kod `Imports` (Visual Basic) lub `using` instrukcje (C#):

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. W procedurze obsługi zdarzeń Dodaj następujący kod, aby utworzyć wystąpienie obiektu pamięci podręcznej:

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <xref:System.Runtime.Caching.ObjectCache> Klasy jest klasą wbudowanych, która udostępnia pamięć podręczną obiektów w pamięci.

4. Dodaj następujący kod, aby odczytać zawartość wpisu pamięci podręcznej, o nazwie `filecontents`:

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. Dodaj następujący kod, aby sprawdzić, czy wpis pamięci podręcznej o nazwie `filecontents` istnieje:

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     Jeśli nie istnieje wpis określony w pamięci podręcznej, należy odczytać plik tekstowy i dodać go jako wpis pamięci podręcznej w pamięci podręcznej.

6. W `if/then` zablokować, Dodaj następujący kod, aby utworzyć nowy <xref:System.Runtime.Caching.CacheItemPolicy> obiektu, który określa, że wpis pamięci podręcznej wygaśnie po 10 sekundach.

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     Jeśli nie podano żadnych informacji eksmisji lub data jej wygaśnięcia, wartość domyślna to <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, co oznacza, że wpisy w pamięci podręcznej nigdy nie wygasa oparte tylko na bezwzględnego czasu. Zamiast tego wpisy w pamięci podręcznej wygasa tylko wtedy, gdy wykorzystanie pamięci. Najlepszym rozwiązaniem należy zawsze jawnie określić bezwzględną lub wygaśniecie.

7. Wewnątrz `if/then` blokowania i po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby utworzyć kolekcję dla ścieżki do plików, które chcesz monitorować i Dodaj ścieżkę do pliku tekstowego do kolekcji:

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    >  Jeśli nie jest plik tekstowy, którego chcesz użyć `c:\cache\cacheText.txt`, określ ścieżkę do pliku tekstowego chcesz użyć.

8. Po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby dodać nowy <xref:System.Runtime.Caching.HostFileChangeMonitor> do kolekcji zmiany monitoruje wpisu pamięci podręcznej:

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <xref:System.Runtime.Caching.HostFileChangeMonitor> Obiekt monitoruje ścieżka do pliku tekstowego i powiadamia o pamięci podręcznej, jeśli występują zmiany. W tym przykładzie wpis pamięci podręcznej wygaśnie, jeśli zmieni się zawartość pliku.

9. Po kodzie dodanym w poprzednim kroku dodaj następujący kod, aby odczytać zawartość pliku tekstowego:

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     Sygnatura czasowa daty i godziny jest dodawany, dzięki czemu będą mogli zobaczyć po wygaśnięciu wpisu pamięci podręcznej.

10. Po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby wstawić zawartość pliku do obiektu pamięci podręcznej jako <xref:System.Runtime.Caching.CacheItem> wystąpienie:

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     Określ informacje o jak wykluczyć wpisu pamięci podręcznej, przekazując <xref:System.Runtime.Caching.CacheItemPolicy> obiektu, który został utworzony wcześniej jako parametr.

11. Po `if/then` zablokować, Dodaj następujący kod, aby wyświetlić zawartość pliku pamięci podręcznej w oknie komunikatu:

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. W **kompilacji** menu, kliknij przycisk **kompilacji WPFCaching** do kompilowania projektu.

## <a name="testing-caching-in-the-wpf-application"></a>Testowanie buforowania w aplikacji WPF
 Teraz można przetestować aplikację.

#### <a name="to-test-caching-in-the-wpf-application"></a>Aby przetestować buforowania w aplikacji WPF

1. Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.

     `MainWindow` Zostanie wyświetlone okno.

2. Kliknij przycisk **Pobieranie pamięci podręcznej**.

     Zawartości w pamięci podręcznej w pliku tekstowym jest wyświetlany w oknie komunikatu. Zwróć uwagę, znacznik czasu: w pliku.

3. Zamknij okno komunikatu, a następnie kliknij przycisk **Pobieranie pamięci podręcznej** ponownie.

     Sygnatura czasowa pozostaje bez zmian. Oznacza to, że jest wyświetlana zawartość z pamięci podręcznej.

4. Poczekaj 10 sekund lub więcej, a następnie kliknij przycisk **Pobieranie pamięci podręcznej** ponownie.

     Tym razem zostanie wyświetlona nowa sygnatura czasowa. Oznacza to, że zasady umożliwiają wygaśnięcia wpisu pamięci podręcznej i czy jest wyświetlana nowa zawartość pamięci podręcznej.

5. W edytorze tekstu Otwórz plik tekstowy, który został utworzony. Jeszcze nie wprowadzaj żadnych zmian.

6. Zamknij okno komunikatu, a następnie kliknij przycisk **Pobieranie pamięci podręcznej** ponownie.

     Ponownie Zwróć uwagę sygnaturę czasową.

7. Wprowadź zmianę do pliku tekstowego, a następnie zapisz plik.

8. Zamknij okno komunikatu, a następnie kliknij przycisk **Pobieranie pamięci podręcznej** ponownie.

     To okno komunikatu zawiera zaktualizowaną zawartość z pliku tekstowego i Nowa sygnatura czasowa. Oznacza to, że monitor zmiany pliku hosta wykluczona wpisu pamięci podręcznej natychmiast, gdy zmienisz plik, mimo że nie wygasło bezwzględny limit czasu.

    > [!NOTE]
    >  Możesz zwiększyć czas eksmisji 20 sekund lub więcej, aby dać więcej czasu, możesz wprowadzać zmiany w pliku.

## <a name="code-example"></a>Przykład kodu
 Po zakończeniu tego instruktażu kodu dla projektu, który został utworzony będą podobne do następującego przykładu.

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [Buforowanie w aplikacjach .NET Framework](../../performance/caching-in-net-framework-applications.md)
