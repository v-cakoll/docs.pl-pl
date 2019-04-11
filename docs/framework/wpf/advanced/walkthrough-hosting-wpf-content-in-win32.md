---
title: 'Przewodnik: hostowanie zawartości WPF w Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: ad31d5f58ae3d22ce8760a396b1f9696912dc475
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296111"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Przewodnik: hostowanie zawartości WPF w Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferuje rozbudowane środowisko do tworzenia aplikacji. Jednak jeśli masz znaczne inwestycje [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu, może być bardziej efektywne dodać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje do aplikacji, zamiast ponownego zapisywania adresów oryginalnego kodu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia prosty mechanizm do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
 W tym samouczku opisano sposób pisania aplikacji przykładowej, [Hosting zawartości WPF w przykładzie oknie Win32](https://go.microsoft.com/fwlink/?LinkID=160004), które hosty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Możesz rozszerzyć ten przykład do obsługi dowolnej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Ponieważ spowodowałoby to łączenie kodu zarządzanego i niezarządzanego, aplikacja została napisana [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)].  

<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym samouczku założono podstawowe znajomość zarówno [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programowania. Aby uzyskać wstęp do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania, zobacz [wprowadzenie](../getting-started/index.md). Wprowadzenie do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programowania, możesz powinny odwoływać się dowolny wiele książek, w tym temacie, w szczególności *programowania Windows* przez Charles Petzold.  
  
 Ponieważ znajdująca się w tym samouczku przykład jest zaimplementowana w [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], w tym samouczku założono znajomość użytkowania [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] programu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)][!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] plus znajomości programowania kodu zarządzanego. Znajomość [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] jest przydatna, ale nie są niezbędne.  
  
> [!NOTE]
>  Ten samouczek zawiera szereg przykładów kodu z próbki skojarzone. Jednak aby zwiększyć czytelność, nie obejmuje pełny przykładowy kod. Aby uzyskać kompletny przykładowy kod, zobacz [Hosting zawartości WPF w przykładzie oknie Win32](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Podstawowa procedura  
 W tej sekcji opisano podstawowe procedury umożliwiają hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. W pozostałych sekcjach opisano szczegóły każdego kroku.  
  
 Kluczem do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości na [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno jest <xref:System.Windows.Interop.HwndSource> klasy. Ta klasa jest zawijany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, dzięki któremu można zintegrować swoje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako okna podrzędnego. Następujące podejście łączy w sobie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w jednej aplikacji.  
  
1. Wdrożenie usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jako klasa zarządzana.  
  
2. Implementowanie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji za pomocą [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Jeśli jesteś już z istniejącą aplikacją i niezarządzane [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] kodu, można zwykle włączyć go do wywoływania z kodu zarządzanego, zmieniając ustawienia projektu w celu uwzględnienia `/clr` flagi kompilatora.  
  
3. Ustaw model wątkowy jednowątkowego apartamentu (STA).  
  
4. Obsługa [WM_CREATE](/windows/desktop/winmsg/wm-create)powiadomień w procedurę okna i wykonaj następujące czynności:  
  
    1.  Utwórz nową <xref:System.Windows.Interop.HwndSource> obiekt z okna nadrzędnego jako jego `parent` parametru.  
  
    2.  Utwórz wystąpienie usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości klasy.  
  
    3.  Odwołanie do przypisywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektu do <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwość <xref:System.Windows.Interop.HwndSource>.  
  
    4.  Uzyskaj HWND zawartości. <xref:System.Windows.Interop.HwndSource.Handle%2A> Właściwość <xref:System.Windows.Interop.HwndSource> obiekt zawiera uchwyt okna (HWND). Aby uzyskać HWND, używanego w niezarządzanych części aplikacji, należy rzutować `Handle.ToPointer()` do HWND.  
  
5. Implementowanie zarządzanych klasę, która zawiera pole statyczne do przechowywania odwołań do Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Ta klasa pozwala uzyskać odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości z usługi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu.  
  
6. Przypisz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości do pola statycznego.  
  
7. Otrzymywanie powiadomień z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, dołączając program obsługi do co najmniej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia.  
  
8. Komunikować się z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości za pomocą odwołania, która przechowywana w polu statycznym, aby ustawić właściwości i tak dalej.  
  
> [!NOTE]
>  Można również użyć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementacji usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Jednak trzeba będzie skompilować go oddzielnie jako [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] i odwołania, który [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] z Twojej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji. W pozostałej części procedura jest podobne do opisanych powyżej.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Wdrażanie aplikacji hosta
 W tej sekcji opisano sposób hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w basic [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji. Zawartość jest zaimplementowana w [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] jako klasa zarządzana. W większości przypadków jest prosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania. Omówiono kluczowe aspekty wdrożenia zawartości w [Implementowanie zawartości WPF](#implementing_the_wpf_page).

<a name="autoNestedSectionsOUTLINE1"></a>
-   [Podstawowa aplikacja](#the_basic_application)

-   [Hosting zawartości WPF](#hosting_the_wpf_page)

-   [Zawierający odwołanie do zawartości WPF](#holding_a_reference)

-   [Podczas komunikowania się z zawartości WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Podstawowa aplikacja
 Punkt początkowy dla aplikacji hosta polegało na utworzeniu szablonu programu Visual Studio 2005.

1. Otwórz program Visual Studio 2005, a następnie wybierz pozycję **nowy projekt** z **pliku** menu.

2. Wybierz **Win32** z listy [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] typów projektów. Jeśli nie jest językiem domyślnym [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)], można znaleźć tych typów projektów, w obszarze **inne języki**.

3. Wybierz **projekt systemu Win32** szablonu, Przypisz nazwę do projektu i kliknij przycisk **OK** można uruchomić **Kreatora aplikacji Win32**.

4. Zaakceptuj ustawienia domyślne kreatora, a następnie kliknij przycisk **Zakończ** Aby uruchomić projekt.

 Ten szablon tworzy podstawową [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji, w tym:

-   Punkt wejścia dla aplikacji.

-   Okno, za pomocą procedury okna skojarzone (WndProc).

-   Menu z **pliku** i **pomocy** nagłówków. **Pliku** menu zawiera **zakończenia** element, który zamyka aplikację. **Pomocy** menu zawiera **o** elementu, który uruchamia okno dialogowe proste.

 Przed rozpoczęciem pisania kodu do hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, należy wprowadzić dwie zmiany do szablonu podstawowego.

 Pierwsza to do skompilowania projektu jako kod zarządzany. Domyślnie projekt kompiluje jako kod niezarządzany. Jednak ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest implementowana w kodzie zarządzanym, projekt musi zostać skompilowany w związku z tym.

1. Kliknij prawym przyciskiem myszy nazwę projektu w **Eksploratora rozwiązań** i wybierz **właściwości** z menu kontekstowego, aby uruchomić **stron właściwości** okno dialogowe.

2. Wybierz **właściwości konfiguracji** w widoku drzewa w okienku po lewej stronie.

3. Wybierz **środowiska uruchomieniowego języka wspólnego** pomoc techniczną od **domyślne wartości projektu** listy w okienku po prawej stronie.

4. Wybierz **wsparcie CLR (/ clr)** w polu listy rozwijanej.

> [!NOTE]
>  Tej flagi kompilatora pozwala na korzystanie z kodu zarządzanego w aplikacji, ale niezarządzanego kodu będzie nadal kompilować tak jak poprzednio.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa jednowątkowego apartamentu (STA) model wątkowości. Aby zapewnić prawidłowe działanie z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości kodu, należy ustawić aplikacji modelu wątkowości STA, stosując atrybut do punktu wejścia.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hosting zawartości WPF
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawartości jest aplikacją wpis adresu proste. Składa się z kilku <xref:System.Windows.Controls.TextBox> kontrolki do wykonania, nazwę użytkownika, adres i tak dalej. Istnieją również dwa <xref:System.Windows.Controls.Button> kontrolek **OK** i **anulować**. Kiedy użytkownik kliknie **OK**, przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> programu obsługi zdarzeń służy do zbierania danych z <xref:System.Windows.Controls.TextBox> formantów, przypisuje go do odpowiednich właściwości i wywołuje zdarzenie niestandardowe `OnButtonClicked`. Kiedy użytkownik kliknie **anulować**, po prostu wywołuje program obsługi `OnButtonClicked`. Obiekt argumentu zdarzenia do `OnButtonClicked` zawiera pola logicznych, które wskazuje, której przycisk został kliknięty.

 Kod, aby host [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości jest zaimplementowana w obsłudze dla [WM_CREATE](/windows/desktop/winmsg/wm-create) powiadomienia na oknie hosta.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 `GetHwnd` Metoda przyjmuje, rozmiar i położenie informacje oraz element nadrzędny, uchwyt okna i zwraca uchwyt okna hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.

> [!NOTE]
>  Nie można użyć `#using` dyrektywy dla `System::Windows::Interop` przestrzeni nazw. Spowoduje to utworzenie kolizja nazw między <xref:System.Windows.Interop.MSG> struktury w tej przestrzeni nazw i struktura MSG zadeklarowanych w winuser.h. Należy używać w pełni kwalifikowanej nazwy dostępu do zawartości tej przestrzeni nazw.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Nie można hostować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości bezpośrednio w oknie aplikacji. Zamiast tego należy najpierw utworzyć <xref:System.Windows.Interop.HwndSource> obiekt do opakowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Ten obiekt jest zasadniczo okna, który jest przeznaczony do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Hostowanie <xref:System.Windows.Interop.HwndSource> obiektu w oknie nadrzędnym, tworząc go jako element podrzędny elementu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, które jest częścią Twojej aplikacji. <xref:System.Windows.Interop.HwndSource> Parametry konstruktora zawiera wiele tych samych informacji przejdzie CreateWindow podczas tworzenia [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna podrzędnego.

 Następnie utwórz wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektu. W tym przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości jest implementowany jako osobnej klasy `WPFPage`przy użyciu [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Można również wdrożyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Jednak w tym celu należy skonfigurować oddzielny projekt i skompiluj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jako [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]. Można dodać odwołanie do tego [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] do swojego projektu, a następnie użyj odwołujący się do utworzenia wystąpienia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.

 Możesz wyświetlić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość okna podrzędnego, przypisując odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwość <xref:System.Windows.Interop.HwndSource>.

 Następny wiersz kodu dołącza program obsługi zdarzeń `WPFButtonClicked`, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości `OnButtonClicked` zdarzeń. Ten program obsługi jest wywoływana, gdy użytkownik kliknie **OK** lub **anulować** przycisku. Zobacz [zawartości communicating_with_the_WPF](#communicating_with_the_page) Aby zapoznać się z tej obsługi zdarzeń.

 Ostatni wiersz kodu pokazano zwraca uchwyt okna (HWND), który jest skojarzony z <xref:System.Windows.Interop.HwndSource> obiektu. Można użyć tego uchwytu z Twojej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu w celu wysyłania wiadomości do okna hostowanej, mimo, że plik nie jest to. <xref:System.Windows.Interop.HwndSource> Obiektu zgłasza zdarzenie, za każdym razem, gdy odbierze komunikatu. Aby przetwarzać komunikaty, wywołaj <xref:System.Windows.Interop.HwndSource.AddHook%2A> metodę, aby dołączyć program obsługi komunikatów, a następnie przetwarzania wiadomości w tej procedurze obsługi.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Zawierający odwołanie do zawartości WPF
 W przypadku wielu aplikacji można nawiązać połączenia z usługą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości później. Na przykład możesz chcieć zmodyfikować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość właściwości lub być może masz <xref:System.Windows.Interop.HwndSource> innego hosta obiektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Aby to zrobić, potrzebujesz odwołania do <xref:System.Windows.Interop.HwndSource> obiektu lub [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. <xref:System.Windows.Interop.HwndSource> Obiekt i jego skojarzony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość pozostają w pamięci, do momentu zniszczenia uchwyt okna. Jednak zmiennej możesz przypisać do <xref:System.Windows.Interop.HwndSource> obiektu będzie wykraczają poza zakres, zaraz po powrocie z procedury okna. Zwyczajowy sposób obsługi tego problemu z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji jest użycie zmiennych statycznych lub globalnego. Niestety nie można przypisać obiektu zarządzanego do tych typów zmiennych. Możesz przypisać uchwyt okna skojarzony <xref:System.Windows.Interop.HwndSource> obiekt ze zmienną globalną lub statyczną, ale doe nie zapewniać dostępu do samego obiektu.

 Najprostszym rozwiązaniem tego problemu jest do zaimplementowania klasy zarządzanej, który zawiera zestaw pól statycznych do przechowywania odwołań do obiektów zarządzanych, którzy potrzebują dostępu do. W przykładzie użyto `WPFPageHost` utrzymywanie odwołania do klasy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości oraz wartość początkową liczbę jego właściwości, które mogą później zmienione przez użytkownika. To jest zdefiniowany w nagłówku.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 W dalszej części `GetHwnd` funkcja przypisuje wartości do tych pól do późniejszego użytku podczas `myPage` jest nadal w zakresie.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Podczas komunikowania się z zawartości WPF
 Istnieją dwa rodzaje komunikacji z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Po otrzymaniu informacji z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, gdy użytkownik kliknie **OK** lub **anulować** przycisków. Aplikacja ma również [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] umożliwiająca użytkownikowi na zmianę różnych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości właściwości, takie jak tła kolorów lub domyślny rozmiar czcionki.

 Jak wspomniano powyżej, gdy użytkownik kliknie przycisk albo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości zgłasza `OnButtonClicked` zdarzeń. Aplikacja dołącza obsługę do tego zdarzenia, aby otrzymywać te powiadomienia. Jeśli **OK** przycisk został kliknięty, klauzula obsługi przejmie informacji o użytkowniku z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i wyświetla go w zestawie formantów statycznych.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Program obsługi, otrzymuje obiekt argument zdarzenia niestandardowego z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, `MyPageEventArgs`. Obiekt `IsOK` właściwość jest ustawiona na `true` Jeśli **OK** kliknięcia przycisku i `false` Jeśli **anulować** kliknięcia przycisku.

 Jeśli **OK** przycisk został kliknięty, program obsługi pobiera odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości z klasy kontenera. Następnie zbiera informacje o użytkowniku, który jest przechowywany przez skojarzony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, właściwości i używa formantów statycznych, aby wyświetlić informacje w oknie nadrzędnym. Ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] danych zawartości znajduje się w postaci ciągu, zarządzanych, musi być przekazywane do użytku przez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kontroli. Jeśli **anulować** przycisk został kliknięty, program obsługi czyści dane z formantów statycznych.

 Aplikacja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] udostępnia zestaw przycisków radiowych, która pozwala użytkownikowi na modyfikację kolor tła [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i kilka właściwości czcionki, powiązane. Poniższy fragment procedurę okna aplikacji (WndProc), a komunikat obsługi, który ustawia różne właściwości na różne komunikaty, w tym kolor tła. Inne są podobne i nie są wyświetlane. Zobacz pełny przykład, aby uzyskać szczegółowe informacje i kontekstu.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Aby ustawić kolor tła, Pobierz odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości (`hostedPage`) z `WPFPageHost` i ustaw właściwość koloru tła na odpowiedni kolor. W przykładzie użyto trzy opcje kolorów: oryginalny kolor, jasnołososiowy zielony lub światła. Kolor tła, oryginalnym jest przechowywany jako pole statyczne w `WPFPageHost` klasy. Ustawić inne dwa, utworzysz nową <xref:System.Windows.Media.SolidColorBrush> i przekazać konstruktora statycznego kolory wartość z zakresu od <xref:System.Windows.Media.Colors> obiektu.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementowanie strony WPF
 Możesz hostować i używać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości bez konieczności znajomości rzeczywiste wdrożenie. Jeśli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość miała zostały spakowane w osobnym [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], może zostały utworzone w dowolnym [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] języka. Oto krótki przewodnik dotyczący [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] implementację, która jest używana w przykładzie. Ta sekcja zawiera następujące podsekcje.

<a name="autoNestedSectionsOUTLINE2"></a>
-   [Układ](#page_layout)

-   [Zwracanie danych do okna hosta](#returning_data_to_window)

-   [Ustawianie właściwości WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Układ
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Elementów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, składać się z pięciu <xref:System.Windows.Controls.TextBox> kontroluje, za pomocą skojarzoną <xref:System.Windows.Controls.Label> kontrolki: Nazwa, adres, Miasto, stanu i Zip. Istnieją również dwa <xref:System.Windows.Controls.Button> kontrolek **OK** i **Anuluj**

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawartości jest zaimplementowana w `WPFPage` klasy. Układ jest obsługiwane za pomocą <xref:System.Windows.Controls.Grid> elementu układu. Klasa dziedziczy <xref:System.Windows.Controls.Grid>, co skutecznie czyni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element główny zawartości.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawartości Konstruktor przyjmuje wymagany szerokość i wysokość oraz rozmiary <xref:System.Windows.Controls.Grid> odpowiednio. Następnie definiuje układ podstawowy, tworząc zestaw <xref:System.Windows.Controls.ColumnDefinition> i <xref:System.Windows.Controls.RowDefinition> obiektów oraz dodać je do <xref:System.Windows.Controls.Grid> obiektu podstawowego <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> i <xref:System.Windows.Controls.Grid.RowDefinitions%2A> kolekcji, odpowiednio. Definiuje siatki pięciu wierszy i siedmiu kolumn z wymiarami ustalany na podstawie zawartości komórek.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Następnie dodaje konstruktora [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów <xref:System.Windows.Controls.Grid>. Pierwszy element jest tekst tytułu, który jest <xref:System.Windows.Controls.Label> formant, który skupia się w pierwszym wierszu siatki.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Następny wiersz zawiera nazwę <xref:System.Windows.Controls.Label> kontroli i związanych z nią <xref:System.Windows.Controls.TextBox> kontroli. Ponieważ ten sam kod jest używany dla każdej pary etykiety/pola tekstowego, jest umieszczony w parze metody prywatne i używane dla wszystkich pięciu par etykiety/pole tekstowe. Metody tworzenia odpowiedniego sterowania, a następnie wywołaj <xref:System.Windows.Controls.Grid> klasy statycznej <xref:System.Windows.Controls.Grid.SetColumn%2A> i <xref:System.Windows.Controls.Grid.SetRow%2A> Umieść formanty w komórce odpowiedniej metody. Po utworzeniu kontrolki przykład wywołuje <xref:System.Windows.Controls.UIElementCollection.Add%2A> metody <xref:System.Windows.Controls.Panel.Children%2A> właściwość <xref:System.Windows.Controls.Grid> Aby dodać kontrolkę na siatce. Kod, aby dodać pozostałe pary etykiety/pole tekstowe jest podobny. Zobacz przykładowy kod, aby uzyskać szczegółowe informacje.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Implementacja dwie metody jest następujący:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Na koniec Przykładowa aplikacja dodaje **OK** i **anulować** przyciski i dołącza program obsługi zdarzeń, aby ich <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Zwracanie danych do okna hosta
 Po kliknięciu przycisku albo jego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie jest wywoływane. Okno hosta może po prostu Dołącz obsługi tych zdarzeń i pobieranie danych bezpośrednio z <xref:System.Windows.Controls.TextBox> kontrolki. W przykładzie użyto metody nieco mniej bezpośrednie. Obsługuje on <xref:System.Windows.Controls.Primitives.ButtonBase.Click> w ramach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, a następnie zgłasza zdarzenie niestandardowe `OnButtonClicked`, by powiadomić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Dzięki temu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w celu sprawdzania niektórych parametrów, zanim powiadomi hosta. Klauzula obsługi przejmie tekst z <xref:System.Windows.Controls.TextBox> kontroluje i przypisuje go do właściwości publiczne, z których hosta mogą pobierać informacje.

 Deklaracja zdarzenia w WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Program obsługi zdarzeń w WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Ustawianie właściwości WPF
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Hosta pozwala użytkownikowi na zmianę kilka [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości właściwości. Z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] stronie jest po prostu kwestią zmiany właściwości. Implementacja w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy zawartości jest nieco bardziej skomplikowane, ponieważ nie ma jednej właściwości globalnego kontrolujące czcionki dla wszystkich kontrolek. Zamiast tego właściwość odpowiednie dla każdego formantu jest zmieniany w metodach dostępu set właściwości. Poniższy przykład przedstawia kod dla `DefaultFontFamily` właściwości. Ustawianie właściwości wywołuje metody prywatnej to z kolei zestawy <xref:System.Windows.Controls.Control.FontFamily%2A> właściwości różne formanty.

 From WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 From WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndSource>
- [WPF i Win32 — Współdziałanie](wpf-and-win32-interoperation.md)