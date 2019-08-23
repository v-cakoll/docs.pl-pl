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
ms.openlocfilehash: 2609a54ce8ba2076c35567fe5bc1d9961f6fef3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942061"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF
Buforowanie umożliwia przechowywanie danych w pamięci w celu szybkiego dostępu. Po ponownym uzyskaniu dostępu do danych aplikacje mogą pobrać dane z pamięci podręcznej, zamiast pobierać je z oryginalnego źródła. Może to poprawić wydajność i skalowalność. Ponadto buforowanie sprawia, że dane są dostępne, gdy źródło danych jest tymczasowo niedostępne.

 .NET Framework zawiera klasy, które umożliwiają korzystanie z buforowania w aplikacjach .NET Framework. Klasy te znajdują się w <xref:System.Runtime.Caching> przestrzeni nazw.

> [!NOTE]
> <xref:System.Runtime.Caching> Przestrzeń nazw jest nowa w .NET Framework 4. Ta przestrzeń nazw sprawia, że buforowanie jest dostępne dla wszystkich aplikacji .NET Framework. W poprzednich wersjach .NET Framework buforowanie było dostępne tylko w <xref:System.Web> przestrzeni nazw i dlatego wymaga zależności od klas ASP.NET.

 W tym instruktażu pokazano, jak używać funkcji buforowania, która jest dostępna w .NET Framework w ramach [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. W tym przewodniku zawartość pliku tekstowego jest buforowana.

 Zadania przedstawione w niniejszym przewodniku to m.in.:

- Tworzenie projektu aplikacji WPF.

- Dodawanie odwołania do .NET Framework 4.

- Inicjowanie pamięci podręcznej.

- Dodawanie wpisu pamięci podręcznej, który zawiera zawartość pliku tekstowego.

- Dostarczanie zasad wykluczania dla wpisu pamięci podręcznej.

- Monitorowanie ścieżki w pliku buforowanym i powiadamianie wystąpienia pamięci podręcznej o zmianach monitorowanego elementu.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten Instruktaż, potrzebne są:

- Microsoft Visual Studio 2010.

- Plik tekstowy, który zawiera niewielką ilość tekstu. (Zawartość pliku tekstowego zostanie wyświetlona w oknie komunikatu). Kod przedstawiony w instruktażu założono, że pracujesz z następującym plikiem:

     `c:\cache\cacheText.txt`

     Można jednak użyć dowolnego pliku tekstowego i wprowadzić niewielkie zmiany w kodzie w tym instruktażu.

## <a name="creating-a-wpf-application-project"></a>Tworzenie projektu aplikacji WPF
 Zacznij od utworzenia projektu aplikacji WPF.

#### <a name="to-create-a-wpf-application"></a>Aby utworzyć aplikację WPF

1. Uruchom program Visual Studio.

2. W menu **plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **Nowy projekt**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

3. W obszarze **zainstalowane szablony**wybierz język programowania, który ma być używany (**Visual Basic** lub **C#Wizualizacja**).

4. W oknie dialogowym **Nowy projekt** wybierz pozycję **Aplikacja WPF**.

    > [!NOTE]
    > Jeśli szablon **aplikacji WPF** nie jest wyświetlany, należy się upewnić, że jest przeznaczona do wersji .NET Framework, która obsługuje platformę WPF. W oknie dialogowym **Nowy projekt** wybierz z listy .NET Framework 4.

5. W polu tekstowym **Nazwa** wprowadź nazwę projektu. Na przykład możesz wprowadzić **WPFCaching**.

6. Zaznacz pole wyboru **Utwórz katalog dla rozwiązania** .

7. Kliknij przycisk **OK**.

     Projektant WPF zostanie otwarty w widoku **projektu** i zostanie wyświetlony plik MainWindow. XAML. Program Visual Studio tworzy folder **My Project** , plik Application. XAML i plik MainWindow. XAML.

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>Kierowanie .NET Framework i Dodawanie odwołania do zestawów buforowania
 Domyślnie aplikacje WPF mają element docelowy [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]. Aby użyć <xref:System.Runtime.Caching> przestrzeni nazw w aplikacji WPF, aplikacja musi być ukierunkowana na .NET Framework 4 (nie jest [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) i musi zawierać odwołanie do przestrzeni nazw.

 W związku z tym następnym krokiem jest zmiana elementu docelowego .NET Framework i dodanie odwołania do <xref:System.Runtime.Caching> przestrzeni nazw.

> [!NOTE]
> Procedura zmiany .NET Framework celu jest inna w projekcie Visual Basic i w projekcie wizualnym C# .

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Aby zmienić .NET Framework docelowy w Visual Basic

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Właściwości**.

     Zostanie wyświetlone okno właściwości aplikacji.

2. Kliknij kartę **kompilacja** .

3. W dolnej części okna kliknij pozycję **Zaawansowane opcje kompilacji.** .

     Zostanie wyświetlone okno dialogowe **Zaawansowane ustawienia kompilatora** .

4. Na liście **platformy docelowej (wszystkie konfiguracje)** wybierz pozycję .NET Framework 4. (Nie wybieraj [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]).

5. Kliknij przycisk **OK**.

     **Zmiana platformy docelowej** zostanie wyświetlone okno dialogowe.

6. W oknie dialogowym **zmiana platformy docelowej** kliknij przycisk **tak**.

     Projekt zostanie zamknięty i ponownie otwarty.

7. Dodaj odwołanie do zestawu buforowania, wykonując następujące czynności:

    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij pozycję **Dodaj odwołanie**.

    2. Wybierz kartę **.NET** , wybierz `System.Runtime.Caching`pozycję, a następnie kliknij przycisk **OK**.

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Aby zmienić .NET Framework docelowy w projekcie wizualizacji C#

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Właściwości**.

     Zostanie wyświetlone okno właściwości aplikacji.

2. Kliknij kartę **aplikacja** .

3. Na liście **platforma** docelowa wybierz pozycję .NET Framework 4. (Nie wybieraj **.NET Framework 4 profilu klienta**).

4. Dodaj odwołanie do zestawu buforowania, wykonując następujące czynności:

    1. Kliknij prawym przyciskiem myszy folder **odwołania** , a następnie kliknij polecenie **Dodaj odwołanie**.

    2. Wybierz kartę **.NET** , wybierz `System.Runtime.Caching`pozycję, a następnie kliknij przycisk **OK**.

## <a name="adding-a-button-to-the-wpf-window"></a>Dodawanie przycisku do okna WPF
 Następnie dodasz kontrolkę Button i utworzysz procedurę obsługi zdarzeń dla `Click` zdarzenia przycisku. Później dodasz kod do tego, gdy klikniesz przycisk, zawartość pliku tekstowego jest buforowana i wyświetlana.

#### <a name="to-add-a-button-control"></a>Aby dodać kontrolkę przycisku

1. W **Eksplorator rozwiązań**kliknij dwukrotnie plik MainWindow. XAML, aby go otworzyć.

2. Z **przybornika**w obszarze **typowe formanty WPF**przeciągnij `Button` kontrolkę do `MainWindow` okna.

3. W oknie **Właściwości** Ustaw `Content` Właściwość `Button` formantu, aby **uzyskać pamięć podręczną**.

## <a name="initializing-the-cache-and-caching-an-entry"></a>Inicjowanie pamięci podręcznej i buforowanie wpisu
 Następnie dodasz kod w celu wykonania następujących zadań:

- Utwórz wystąpienie klasy pamięci podręcznej — to znaczy, że utworzysz wystąpienie nowego <xref:System.Runtime.Caching.MemoryCache> obiektu.

- Określ, że pamięć podręczna <xref:System.Runtime.Caching.HostFileChangeMonitor> używa obiektu do monitorowania zmian w pliku tekstowym.

- Przeczytaj plik tekstowy i Buforuj jego zawartość jako wpis pamięci podręcznej.

- Wyświetl zawartość pliku tekstowego w pamięci podręcznej.

#### <a name="to-create-the-cache-object"></a>Aby utworzyć obiekt pamięci podręcznej

1. Kliknij dwukrotnie dodany przycisk, aby utworzyć procedurę obsługi zdarzeń w pliku MainWindow.xaml.cs lub MainWindow. XAML. vb.

2. W górnej części pliku (przed deklaracją klasy) Dodaj następujące `Imports` instrukcje (Visual Basic) lub `using` (C#):

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. W programie obsługi zdarzeń Dodaj następujący kod, aby utworzyć wystąpienie obiektu pamięci podręcznej:

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <xref:System.Runtime.Caching.ObjectCache> Klasa jest wbudowaną klasą, która udostępnia pamięć podręczną obiektów w pamięci.

4. Dodaj następujący kod, aby odczytać zawartość wpisu pamięci podręcznej o `filecontents`nazwie:

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

     Jeśli określony wpis pamięci podręcznej nie istnieje, należy odczytać plik tekstowy i dodać go jako wpis pamięci podręcznej.

6. W bloku Dodaj następujący kod, aby utworzyć nowy <xref:System.Runtime.Caching.CacheItemPolicy> obiekt, który określa, że wpis pamięci podręcznej wygasa po 10 sekundach. `if/then`

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     Jeśli nie zostaną podane żadne informacje o wykluczeniu lub wygaśnięciu <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, wartość domyślna to, co oznacza, że wpisy pamięci podręcznej nigdy nie wygasają w oparciu o czas bezwzględny. Zamiast tego wpisy pamięci podręcznej wygasają tylko wtedy, gdy występuje wykorzystanie pamięci. Najlepszym rozwiązaniem jest zawsze jawne zapewnienie bezwzględnej lub ruchomej daty ważności.

7. `if/then` Wewnątrz bloku i po kodzie dodanym w poprzednim kroku Dodaj następujący kod, aby utworzyć kolekcję dla ścieżek plików, które mają być monitorowane, i Dodaj ścieżkę do pliku tekstowego do kolekcji:

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > Jeśli plik tekstowy, którego chcesz użyć, nie `c:\cache\cacheText.txt`jest określ ścieżkę do pliku tekstowego, którego chcesz użyć.

8. Po kodzie, który został dodany w poprzednim kroku, Dodaj następujący kod, aby dodać nowy <xref:System.Runtime.Caching.HostFileChangeMonitor> obiekt do kolekcji monitorów zmian dla wpisu pamięci podręcznej:

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <xref:System.Runtime.Caching.HostFileChangeMonitor> Obiekt monitoruje ścieżkę pliku tekstowego i powiadamia pamięć podręczną w przypadku wystąpienia zmian. W tym przykładzie wpis pamięci podręcznej utraci ważność, jeśli zawartość pliku ulegnie zmianie.

9. Po kodzie, który został dodany w poprzednim kroku, Dodaj następujący kod, aby odczytać zawartość pliku tekstowego:

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     Zostanie dodana sygnatura czasowa daty i godziny, dzięki czemu będzie można zobaczyć, kiedy wygasa wpis pamięci podręcznej.

10. Po kodzie dodanym w poprzednim kroku Dodaj następujący kod, aby wstawić zawartość pliku do obiektu pamięci podręcznej jako <xref:System.Runtime.Caching.CacheItem> wystąpienie:

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     Należy określić informacje dotyczące sposobu wykluczenia wpisu pamięci podręcznej przez przekazanie <xref:System.Runtime.Caching.CacheItemPolicy> obiektu utworzonego wcześniej jako parametr.

11. `if/then` Po bloku Dodaj następujący kod, aby wyświetlić zawartość pliku w pamięci podręcznej w oknie komunikatu:

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. W menu **kompilacja** kliknij pozycję **Kompiluj WPFCaching** , aby skompilować projekt.

## <a name="testing-caching-in-the-wpf-application"></a>Testowanie buforowania w aplikacji WPF
 Teraz można testować aplikację.

#### <a name="to-test-caching-in-the-wpf-application"></a>Aby przetestować buforowanie w aplikacji WPF

1. Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.

     Zostanie `MainWindow` wyświetlone okno.

2. Kliknij pozycję **Pobierz pamięć podręczną**.

     Zawartość z pamięci podręcznej z pliku tekstowego zostanie wyświetlona w oknie komunikatu. Zwróć uwagę na sygnaturę czasową pliku.

3. Zamknij okno komunikatu, a następnie kliknij ponownie przycisk **Pobierz pamięć podręczną** .

     Sygnatura czasowa nie została zmieniona. Wskazuje to, że buforowana zawartość jest wyświetlana.

4. Odczekaj 10 sekund lub więcej, a następnie kliknij ponownie przycisk **Pobierz pamięć podręczną** .

     Tym razem zostanie wyświetlona nowa Sygnatura czasowa. Oznacza to, że zasady pozwalają na wygaśnięcie wpisu pamięci podręcznej i wyświetlanie nowej zawartości w pamięci podręcznej.

5. W edytorze tekstów Otwórz utworzony plik tekstowy. Nie wprowadzaj jeszcze żadnych zmian.

6. Zamknij okno komunikatu, a następnie kliknij ponownie przycisk **Pobierz pamięć podręczną** .

     Zwróć uwagę na ponowną sygnaturę czasową.

7. Wprowadź zmiany do pliku tekstowego, a następnie Zapisz plik.

8. Zamknij okno komunikatu, a następnie kliknij ponownie przycisk **Pobierz pamięć podręczną** .

     To okno komunikatu zawiera zaktualizowaną zawartość z pliku tekstowego i nową sygnaturę czasową. Oznacza to, że monitor zmiany plików hosta wykluczony z wpisu pamięci podręcznej natychmiast po zmianie pliku, nawet jeśli bezwzględny limit czasu nie upłynął.

    > [!NOTE]
    > Możesz wydłużyć czas wykluczenia na 20 sekund lub więcej, aby zapewnić więcej czasu na wprowadzenie zmian w pliku.

## <a name="code-example"></a>Przykład kodu
 Po zakończeniu tego instruktażu kod utworzonego projektu będzie wyglądać podobnie do poniższego przykładu.

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [Buforowanie w aplikacjach .NET Framework](../../performance/caching-in-net-framework-applications.md)
