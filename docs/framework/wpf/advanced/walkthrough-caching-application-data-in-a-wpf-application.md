---
title: 'Wskazówki: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: 7a4f84281da78068b5c6f7a505c8cb9225b31a39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548902"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>Wskazówki: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF
Buforowanie umożliwia przechowywanie danych w pamięci, aby uzyskać szybki dostęp. Dostępie do danych ponownie, aplikacje można pobrać danych z pamięci podręcznej, zamiast tego podczas pobierania z oryginalnego źródła. Może to poprawić wydajność i skalowalność. Ponadto buforowanie sprawia, że nie są dostępne dane, gdy źródłem danych jest tymczasowo niedostępna.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Udostępnia klasy, które umożliwiają używanie buforowania w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji. Te klasy znajdują się w <xref:System.Runtime.Caching> przestrzeni nazw.  
  
> [!NOTE]
>  <xref:System.Runtime.Caching> Przestrzeń nazw jest nowa w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. Ta przestrzeń nazw sprawia, że buforowanie jest dostępna dla wszystkich [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji. W poprzednich wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], buforowanie była dostępna tylko w <xref:System.Web> przestrzeni nazw i w związku z tym wymagana zależność klasy ASP.NET.  
  
 W tym przewodniku przedstawiono sposób korzystać z funkcji buforowania, która jest dostępna w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jako część [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. W tym przewodnikiem pamięci podręcznej zawartość pliku tekstowego.  
  
 Zadania przedstawione w niniejszym przewodniku to m.in.:  
  
-   Tworzenie nowego projektu aplikacji WPF.  
  
-   Dodawanie odwołania do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
-   Inicjowanie pamięci podręcznej.  
  
-   Dodanie wpisu pamięci podręcznej, którego zawartość pliku tekstowego.  
  
-   Zapewnienie zasad eksmisji dla wpisu pamięci podręcznej.  
  
-   Monitorowanie ścieżkę pliku pamięci podręcznej i powiadamiania wystąpienia pamięci podręcznej o zmiany monitorowania elementów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu potrzebne są:  
  
-   Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Plik tekstowy zawierający mała ilość tekstu. (W oknie komunikatu zostanie wyświetlona zawartość pliku tekstowego). Kod przedstawiony przewodnika zakłada użytkownik pracuje z następującego pliku:  
  
     `c:\cache\cacheText.txt`  
  
     Można jednak użyć dowolnego pliku tekstowego i wprowadzić niewielkich zmian w kodzie w tym przewodniku.  
  
## <a name="creating-a-wpf-application-project"></a>Tworzenie nowego projektu aplikacji WPF  
 Zostanie rozpoczyna się od utworzenia projektu aplikacji WPF.  
  
#### <a name="to-create-a-wpf-application"></a>Aby utworzyć aplikację programu WPF  
  
1.  Uruchom program Visual Studio.  
  
2.  W **pliku** menu, kliknij przycisk **nowy**, a następnie kliknij przycisk **nowy projekt**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
3.  W obszarze **zainstalowane szablony**, wybierz język programowania, którego chcesz użyć (**Visual Basic** lub **Visual C#**).  
  
4.  W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji WPF**.  
  
    > [!NOTE]
    >  Jeśli nie widzisz **aplikacji WPF** szablonu, upewnij się, że ma być przeznaczona dla wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obsługującej WPF. W **nowy projekt** okno dialogowe, wybierz opcję [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] z listy.  
  
5.  W **nazwa** tekst Wprowadź nazwę dla projektu. Na przykład można wprowadzić **WPFCaching**.  
  
6.  Wybierz **Utwórz katalog rozwiązania** pole wyboru.  
  
7.  Kliknij przycisk **OK**.  
  
     Zostanie otwarty projektant WPF w **projekt** wyświetlanie i wyświetla plik MainWindow.xaml. Program Visual Studio tworzy **mój projekt** folder, plik Application.xaml i plik MainWindow.xaml.  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>Docelowy program .NET Framework i dodawanie odwołania do pamięci podręcznej zestawów  
 Domyślnie docelowej aplikacji WPF [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]. Aby użyć <xref:System.Runtime.Caching> przestrzeni nazw w aplikacji WPF, aplikacja musi wskazywać [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (nie [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) i musi zawierać odwołanie do przestrzeni nazw.  
  
 W związku z tym, następnym krokiem jest Zmień docelowy .NET Framework i Dodaj odwołanie do <xref:System.Runtime.Caching> przestrzeni nazw.  
  
> [!NOTE]
>  Procedura docelowy .NET Framework zmieniania różni się w projektach Visual Basic i w projektach Visual C#.  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Aby zmienić docelowej platformy .NET Framework w języku Visual Basic  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.  
  
     Zostanie wyświetlone okno właściwości dla aplikacji.  
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  W dolnej części okna kliknij **zaawansowane opcje kompilacji...** .  
  
     **Zaawansowane ustawienia kompilatora** zostanie wyświetlone okno dialogowe.  
  
4.  W **platformy docelowej (wszystkie konfiguracje)** listy, wybierz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Nie należy wybierać [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)  
  
5.  Kliknij przycisk **OK**.  
  
     **Zmianie docelowego Framework** zostanie wyświetlone okno dialogowe.  
  
6.  W **zmianie docelowego Framework** okno dialogowe, kliknij przycisk **tak**.  
  
     Projekt zostanie zamknięte, a następnie otwarciu.  
  
7.  Dodaj odwołanie do zestawu buforowania, wykonaj następujące czynności:  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
    2.  Wybierz **.NET** wybierz opcję `System.Runtime.Caching`, a następnie kliknij przycisk **OK**.  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Aby zmienić docelowej platformy .NET Framework w projektach Visual C#  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.  
  
     Zostanie wyświetlone okno właściwości dla aplikacji.  
  
2.  Kliknij przycisk **aplikacji** kartę.  
  
3.  W **platformy docelowej** listy, wybierz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Nie należy wybierać **.NET Framework 4 Client Profile**.)  
  
4.  Dodaj odwołanie do zestawu buforowania, wykonaj następujące czynności:  
  
    1.  Kliknij prawym przyciskiem myszy **odwołania** folder, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
    2.  Wybierz **.NET** wybierz opcję `System.Runtime.Caching`, a następnie kliknij przycisk **OK**.  
  
## <a name="adding-a-button-to-the-wpf-window"></a>Dodawanie przycisku do okna WPF  
 Następnie zostanie dodać kontrolkę przycisku i utworzyć program obsługi zdarzeń dla przycisku `Click` zdarzeń. Później będzie Dodaj kod, więc po kliknięciu przycisku zawartość pliku tekstowego są buforowane i wyświetlane.  
  
#### <a name="to-add-a-button-control"></a>Aby dodać kontrolkę przycisku  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie plik MainWindow.xaml, aby go otworzyć.  
  
2.  Z **przybornika**w obszarze **wspólnych formantów WPF**, przeciągnij `Button` formant `MainWindow` okna.  
  
3.  W **właściwości** ustaw `Content` właściwość `Button` formant **pobrać pamięci podręcznej**.  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a>Inicjowanie pamięci podręcznej i buforowania wpis  
 Następnie dodasz kod do wykonania następujących zadań:  
  
-   Tworzenie wystąpienia klasy pamięci podręcznej — to znaczy będzie wystąpienia nowy <xref:System.Runtime.Caching.MemoryCache> obiektu.  
  
-   Określ, czy korzysta z pamięci podręcznej <xref:System.Runtime.Caching.HostFileChangeMonitor> obiektu do monitorowania zmian w pliku tekstowym.  
  
-   Odczytywanie pliku tekstowego i pamięci podręcznej zawartości jako wpis pamięci podręcznej.  
  
-   Wyświetl zawartość pliku tekstowego w pamięci podręcznej.  
  
#### <a name="to-create-the-cache-object"></a>Można utworzyć obiektu pamięci podręcznej  
  
1.  Kliknij dwukrotnie przycisk, który właśnie został dodany w celu utworzenia programu obsługi zdarzeń w pliku MainWindow.xaml.cs lub MainWindow.Xaml.vb.  
  
2.  W górnej części pliku (przed deklaracją klasy), Dodaj następujący `Imports` (Visual Basic) lub `using` — instrukcje (C#):  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  W obsłudze zdarzeń Dodaj następujący kod, aby utworzyć wystąpienia obiektu pamięci podręcznej:  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <xref:System.Runtime.Caching.ObjectCache> Klasa jest klasą wbudowana zapewniająca obiektu w pamięci podręcznej.  
  
4.  Dodaj następujący kod do odczytu treści wpis pamięci podręcznej o nazwie `filecontents`:  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  Dodaj następujący kod, aby sprawdzić, czy wpis pamięci podręcznej o nazwie `filecontents` istnieje:  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     Wpis pamięci podręcznej określony nie istnieje, należy odczytać pliku tekstowego, dodaj go jako wpis pamięci podręcznej w pamięci podręcznej.  
  
6.  W `if/then` bloków, Dodaj następujący kod, aby utworzyć nową <xref:System.Runtime.Caching.CacheItemPolicy> obiekt, który określa, że wpis pamięci podręcznej wygasa po 10 sekundach.  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     Jeśli podano żadnych informacji wykluczenia i wygaśnięcia, wartością domyślną jest <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, co oznacza, że wpisy w pamięci podręcznej nigdy nie wygasa oparte tylko na bezwzględnego czasu. Zamiast tego wpisy w pamięci podręcznej wygasa tylko w przypadku wykorzystania pamięci. Jako najlepsze rozwiązanie należy zawsze jawnie Podaj bezwzględną lub wygaśnięcia elewacji.  
  
7.  Wewnątrz `if/then` blokować i po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby utworzyć kolekcję dla ścieżki do plików, które chcesz monitorować i Dodaj ścieżkę do pliku tekstowego do kolekcji:  
  
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
  
8.  Po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby dodać nowy <xref:System.Runtime.Caching.HostFileChangeMonitor> obiektu do kolekcji zmiany monitoruje wpisu pamięci podręcznej:  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <xref:System.Runtime.Caching.HostFileChangeMonitor> Obiekt monitoruje ścieżka pliku tekstowego i powiadamia pamięci podręcznej w przypadku wystąpienia zmian. W tym przykładzie wpis pamięci podręcznej wygasa w przypadku zmiany zawartości pliku.  
  
9. Po kodzie dodanym w poprzednim kroku dodaj następujący kod, aby odczytać zawartości pliku tekstowego:  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     Data i godzina sygnatury czasowej jest dodawany, dzięki czemu można będzie wyświetlić wygaśnięcia wpisu pamięci podręcznej.  
  
10. Po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby wstawić zawartość pliku do obiektu pamięci podręcznej jako <xref:System.Runtime.Caching.CacheItem> wystąpienie:  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     Określ informacje o sposobie wykluczyć wpisu pamięci podręcznej przez przekazanie <xref:System.Runtime.Caching.CacheItemPolicy> obiekt, który został utworzony wcześniej jako parametr.  
  
11. Po `if/then` bloków, Dodaj następujący kod, aby wyświetlić zawartość plików w pamięci podręcznej w oknie komunikatu:  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. W **kompilacji** menu, kliknij przycisk **kompilacji WPFCaching** Aby skompilować projekt.  
  
## <a name="testing-caching-in-the-wpf-application"></a>Testowanie buforowanie w aplikacji WPF  
 Teraz możesz przetestować aplikację.  
  
#### <a name="to-test-caching-in-the-wpf-application"></a>Aby przetestować buforowanie w aplikacji WPF  
  
1.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
     `MainWindow` Okno jest wyświetlane.  
  
2.  Kliknij przycisk **pobrać pamięci podręcznej**.  
  
     Zawartości w pamięci podręcznej z pliku tekstowego jest wyświetlany w oknie komunikatu. Zwróć uwagę, znacznik czasu pliku.  
  
3.  Zamknij okno komunikatu, a następnie kliknij przycisk **pobrać pamięci podręcznej** ponownie **.**  
  
     Sygnatura czasowa nie ulega zmianie. Oznacza to, że jest wyświetlany zawartości w pamięci podręcznej.  
  
4.  Zaczekaj 10 sekund lub więcej, a następnie kliknij przycisk **pobrać pamięci podręcznej** ponownie.  
  
     Teraz zostanie wyświetlony nowy znacznik czasu. Oznacza to, że zasady pozwalają wygaśnięcia wpisu pamięci podręcznej oraz czy jest wyświetlany nowej zawartości w pamięci podręcznej.  
  
5.  W edytorze tekstów otwórz plik tekstowy, który został utworzony. Jeszcze nie wprowadzaj żadnych zmian.  
  
6.  Zamknij okno komunikatu, a następnie kliknij przycisk **pobrać pamięci podręcznej** ponownie **.**  
  
     Zwróć uwagę sygnatura czasowa ponownie.  
  
7.  Zmiany w pliku tekstowym, a następnie zapisz plik.  
  
8.  Zamknij okno komunikatu, a następnie kliknij przycisk **pobrać pamięci podręcznej** ponownie.  
  
     Ten komunikat zawiera zaktualizowaną zawartość z pliku tekstowego i Nowa sygnatura czasowa. Oznacza to, że monitor zmiany pliku hosta wykluczony wpisu pamięci podręcznej natychmiast po zmianie plików, nawet jeśli nie wygasło bezwzględny limit czasu.  
  
    > [!NOTE]
    >  Można zwiększyć czas wykluczenia 20 sekund lub więcej należy poczekać do wprowadzania zmian w pliku.  
  
## <a name="code-example"></a>Przykład kodu  
 Po ukończeniu tego przewodnika, kodu dla projektu, utworzony zostanie podobne do następującego przykładu.  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [Buforowanie w aplikacjach .NET Framework](../../../../docs/framework/performance/caching-in-net-framework-applications.md)
