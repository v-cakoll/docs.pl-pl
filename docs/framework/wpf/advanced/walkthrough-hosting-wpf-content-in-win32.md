---
title: 'Wskazówki: Hosting zawartości WPF w Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 429acf6e3b37f5532e031fdef999d252a3aae3cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Wskazówki: Hosting zawartości WPF w Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia bogate środowisko do tworzenia aplikacji. Jednak jeśli masz znaczących inwestycji [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu, może być bardziej skuteczne dodać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji aplikacji, a nie ponowne zapisywanie oryginalnego kodu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia mechanizm prostego hosting [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
 Ten przewodnik opisuje sposób tworzenia aplikacji przykładowej, [Hosting zawartości WPF w przykładowym okna Win32](http://go.microsoft.com/fwlink/?LinkID=160004), że hosty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Istnieje możliwość rozszerzenia tego przykładu do przechowywania wszelkich [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Ponieważ spowodowałoby to mieszanie kodu zarządzane i niezarządzane, aplikacja została napisana [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)].  
  
 
  
<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym samouczku założono podstawowa znajomość zarówno [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programowania. Podstawowe wprowadzenie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania, zobacz [wprowadzenie](../../../../docs/framework/wpf/getting-started/index.md). Aby obejrzeć wprowadzenie do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programowania, użytkownik powinien odwoływać się żadnego wiele książek na ten temat, w szczególności *programowania Windows* przez Petzold Charlesa.  
  
 Ponieważ próbki, dołączony w tym samouczku jest zaimplementowana w [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], w tym samouczku założono znajomość stosowania [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] do programu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] oraz opis programowania kodu zarządzanego. Znajomość [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] jest pomocna, ale nie są niezbędne.  
  
> [!NOTE]
>  Ten samouczek zawiera szereg przykłady kodu z skojarzone próbki. Jednak aby zwiększyć czytelność, go nie ma kompletnego przykładowego kodu. Zakończenie przykładowy kod, zobacz [Hosting zawartości WPF w przykładowym okna Win32](http://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Podstawowe procedury  
 W tej sekcji opisano procedury podstawowa umożliwia hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. W pozostałych sekcjach opisano szczegóły każdego kroku.  
  
 Klucz do hostingu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości na [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno jest <xref:System.Windows.Interop.HwndSource> klasy. Ta klasa jest zawijana [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, dzięki któremu można włączyć do Twojej [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako okna podrzędnego. Następujące podejścia łączy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w pojedynczej aplikacji.  
  
1.  Wdrożenie programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jako zarządzanej klasy.  
  
2.  Implementowanie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacja o [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Jeśli jesteś rozpoczynających się od istniejącej aplikacji, jak i niezarządzanych [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] kodu, możesz je zwykle włączyć do wywoływania z kodu zarządzanego, zmieniając ustawienia projektu, aby uwzględnić `/clr` flagi kompilatora.  
  
3.  Wartość modelu wątkowości jednowątkowego apartamentu (STA).  
  
4.  Obsługa [WM_CREATE](http://msdn.microsoft.com/library/ms632619.aspx)powiadomień w procedurę okna i wykonaj następujące czynności:  
  
    1.  Utwórz nową <xref:System.Windows.Interop.HwndSource> obiekt z okna nadrzędnego jako jego `parent` parametru.  
  
    2.  Utwórz wystąpienie programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości klasy.  
  
    3.  Odwołanie do przypisywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektu do <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwość <xref:System.Windows.Interop.HwndSource>.  
  
    4.  Pobierz HWND zawartości. <xref:System.Windows.Interop.HwndSource.Handle%2A> Właściwość <xref:System.Windows.Interop.HwndSource> obiektu zawiera uchwyt okna (HWND). Aby dokonać HWND używanego w niezarządzanych część aplikacji, `Handle.ToPointer()` do HWND.  
  
5.  Implementowanie zarządzanych klasę, która zawiera pola statycznego do przechowywania odwołanie do użytkownika [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Ta klasa umożliwia odwołać się do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości z Twojego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu.  
  
6.  Przypisz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości do pola statycznego.  
  
7.  Odbieranie powiadomień z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości przez dołączenie obsługi do co najmniej jednego z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia.  
  
8.  Komunikować się z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości za pomocą odwołania, który przechowywany w polu statycznym, aby ustawić właściwości itd.  
  
> [!NOTE]
>  Można również użyć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do zaimplementowania programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Jednak należy go skompilować oddzielnie jako [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] i odwołać, który [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] z Twojej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji. W pozostałej części procedura jest podobna do opisanych powyżej.  
  
<a name="implementing_the_application"></a>   
## <a name="implementing-the-host-application"></a>Wdrażanie aplikacji hosta  
 W tej sekcji opisano sposób hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w basic [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji. Zawartość jest zaimplementowana w [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] jako zarządzanej klasy. W większości przypadków jest bezpośrednia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania. Omówiono kluczowe aspekty wdrożenia zawartości w [wdrażanie zawartości WPF](#implementing_the_wpf_page).  
  
<a name="autoNestedSectionsOUTLINE1"></a>   
-   [Aplikacji w warstwie podstawowa](#the_basic_application)  
  
-   [Hostowanie zawartości WPF](#hosting_the_wpf_page)  
  
-   [Zawierający odwołanie do zawartości WPF](#holding_a_reference)  
  
-   [Podczas komunikacji z zawartości WPF](#communicating_with_the_page)  
  
<a name="the_basic_application"></a>   
### <a name="the-basic-application"></a>Aplikacji w warstwie podstawowa  
 Punkt początkowy aplikacji hosta było utworzyć [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] szablonu.  
  
1.  Otwórz [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)]i wybierz **nowy projekt** z **pliku** menu.  
  
2.  Wybierz **Win32** z listy [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] typy projektów. Jeśli nie jest domyślnym językiem [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)], można znaleźć tych typów projektów, w obszarze **inne języki**.  
  
3.  Wybierz **projektu Win32** szablonu, Przypisz nazwę do projektu i kliknij przycisk **OK** można uruchomić **Kreator aplikacji Win32**.  
  
4.  Zaakceptuj domyślne ustawienia kreatora i kliknij przycisk **Zakończ** do uruchamiania projektu.  
  
 Szablon tworzy podstawowego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji, w tym:  
  
-   Punkt wejścia dla aplikacji.  
  
-   Okno programu, przy użyciu procedury okna skojarzony (WndProc).  
  
-   Menu z **pliku** i **pomocy** nagłówków. **Pliku** menu ma **zakończenia** elementu, który zamyka aplikację. **Pomocy** menu ma **o** elementu, który uruchamia prostego okna dialogowego.  
  
 Przed rozpoczęciem pisania kodu do hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, należy dokonać modyfikacji dwa podstawowe szablonu.  
  
 Pierwsza to skompilowania projektu jako kod zarządzany. Domyślnie projektu kompiluje jako kodu niezarządzanego. Jednak ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zaimplementowano w kodzie zarządzanym, projekt musi zostać odpowiednio skompilowany.  
  
1.  Kliknij prawym przyciskiem myszy nazwę projektu w **Eksploratora rozwiązań** i wybierz **właściwości** z menu kontekstowego, aby uruchomić **strony właściwości** okno dialogowe.  
  
2.  Wybierz **właściwości konfiguracji** z widoku drzewa w okienku po lewej stronie.  
  
3.  Wybierz **środowisko uruchomieniowe języka wspólnego** obsługiwać z **domyślne projektu** listy w okienku po prawej stronie.  
  
4.  Wybierz **wsparcie CLR (/ clr)** w polu listy rozwijanej.  
  
> [!NOTE]
>  Ta flaga kompilatora pozwala na stosowanie kodu zarządzanego w aplikacji, ale kodu niezarządzanego nadal Kompiluj co poprzednio.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa jednowątkowego apartamentu (STA) modelu wątków. Aby działać poprawnie ze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości kodu, musisz ustawić model wątkowości aplikacji STA przez zastosowanie atrybutu do punktu wejścia.  
  
 [!code-cpp[Win32HostingWPFPage#WinMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]  
  
<a name="hosting_the_wpf_page"></a>   
### <a name="hosting-the-wpf-content"></a>Hostowanie zawartości WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawartości jest aplikacją wpis adres proste. Składa się z kilku <xref:System.Windows.Controls.TextBox> formanty podjęcie nazwy użytkownika, adresu i tak dalej. Istnieją również dwa <xref:System.Windows.Controls.Button> formantów, **OK** i **anulować**. Po kliknięciu przez użytkownika **OK**, przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń zbiera dane z <xref:System.Windows.Controls.TextBox> kontrolki, przypisuje go do odpowiednich właściwości i zgłasza zdarzenie niestandardowe, `OnButtonClicked`. Po kliknięciu przez użytkownika **anulować**, po prostu wywołuje program obsługi `OnButtonClicked`. Dla obiekt argument zdarzenia `OnButtonClicked` zawiera pole logiczną, wskazującą, który przycisk został kliknięty.  
  
 Kod do hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości jest zaimplementowana w procedurze obsługi dla [WM_CREATE](http://msdn.microsoft.com/library/ms632619.aspx) powiadomienia na okno hosta.  
  
 [!code-cpp[Win32HostingWPFPage#WMCreate](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]  
  
 `GetHwnd` Metoda ma rozmiar i położenie informacje oraz nadrzędnego uchwytu okna i zwraca uchwyt okna hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.  
  
> [!NOTE]
>  Nie można użyć `#using` dyrektywy dla `System::Windows::Interop` przestrzeni nazw. Dzięki temu tworzy kolizję nazw między <xref:System.Windows.Interop.MSG> struktury w tej przestrzeni nazw i struktura MSG zadeklarowany w winuser.h. Zamiast niej należy użyć nazwy w pełni kwalifikowane dostępu do zawartości tej przestrzeni nazw.  
  
 [!code-cpp[Win32HostingWPFPage#GetHwnd](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]  
  
 Nie można hostować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości bezpośrednio w oknie aplikacji. Zamiast tego należy najpierw utworzyć <xref:System.Windows.Interop.HwndSource> obiekt do zakodowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Ten obiekt jest zasadniczo okna, które jest przeznaczona do obsługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. W przypadku obsługi <xref:System.Windows.Interop.HwndSource> obiektu w okno nadrzędne, tworząc jako element podrzędny [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, który jest częścią aplikacji. <xref:System.Windows.Interop.HwndSource> Parametrów konstruktora zawiera wiele tych samych informacji przejdzie właściwości CreateWindow podczas tworzenia [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna podrzędnego.  
  
 Następnie utwórz wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektu. W takim przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości jest zaimplementowany jako osobnej klasy `WPFPage`za pomocą [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Można też wdrożyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Jednak w tym celu należy skonfigurować oddzielny projekt do kompilacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jako [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]. Można dodać odwołanie do tego [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] do projektu i użyj odwołujący się do utworzenia wystąpienia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.  
  
 Możesz wyświetlić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość okna podrzędnego, przypisując odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości do <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwość <xref:System.Windows.Interop.HwndSource>.  
  
 W następnym wierszu kodu dołącza program obsługi zdarzeń `WPFButtonClicked`, do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości `OnButtonClicked` zdarzeń. Ten program obsługi jest wywoływana, gdy użytkownik kliknie **OK** lub **anulować** przycisku. Zobacz [zawartości communicating_with_the_WPF](#communicating_with_the_page) Aby zapoznać się z tej obsługi zdarzeń.  
  
 Końcowego wiersza kodu pokazano zwraca uchwyt okna (HWND), z którym skojarzony jest <xref:System.Windows.Interop.HwndSource> obiektu. Można użyć tego uchwytu z Twojej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kod do wysyłania wiadomości do okna hostowanej, mimo że próbki nie jest to. <xref:System.Windows.Interop.HwndSource> Obiektu zgłasza zdarzenie, za każdym razem, gdy odbierze komunikat. Aby przetwarzać komunikaty, wywołaj <xref:System.Windows.Interop.HwndSource.AddHook%2A> metodę, aby dołączyć obsługi wiadomości i następnie przetwarzanie wiadomości w programu obsługi.  
  
<a name="holding_a_reference"></a>   
### <a name="holding-a-reference-to-the-wpf-content"></a>Zawierający odwołanie do zawartości WPF  
 Dla wielu aplikacji, można nawiązać połączenia z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości później. Na przykład można zmodyfikować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości właściwości lub może mieć <xref:System.Windows.Interop.HwndSource> obiektu hosta innego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Aby to zrobić, należy odwołanie do <xref:System.Windows.Interop.HwndSource> obiektu lub [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. <xref:System.Windows.Interop.HwndSource> Obiekt i jego skojarzony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości pozostawać w pamięci, dopóki zniszczyć uchwytu okna. Jednak zmiennej możesz przypisać <xref:System.Windows.Interop.HwndSource> obiektu przejdzie poza zakresem zaraz po powrocie z procedurę okna. Zwyczajowe sposobem obsługi tego problemu z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji jest użycie zmiennej statyczny lub globalnego. Niestety nie można przypisać obiektu zarządzanego tych typów zmiennych. Można przypisać skojarzono uchwyt okna <xref:System.Windows.Interop.HwndSource> obiekt do zmiennej globalnej lub statycznej, ale ten Nowak nie zapewniają dostęp do danego obiektu.  
  
 Najprostszym rozwiązaniem tego problemu jest zarządzanej klasy, która zawiera zestaw pól statycznych do przechowywania odwołań do zarządzanych obiektów, które wymagają dostępu do wdrożenia. W przykładzie użyto `WPFPageHost` klasy utrzymującej odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości oraz wartości początkowej liczby jego właściwości, które można zmienić później przez użytkownika. To jest zdefiniowany w nagłówku.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageHost](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]  
  
 Ostatnie część `GetHwnd` funkcja przypisuje wartości do tych pól do późniejszego użytku podczas `myPage` jest nadal w zakresie.  
  
<a name="communicating_with_the_page"></a>   
### <a name="communicating-with-the-wpf-content"></a>Podczas komunikacji z zawartości WPF  
 Istnieją dwa typy komunikacji z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Po otrzymaniu informacji z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, gdy użytkownik kliknie **OK** lub **anulować** przycisków. Aplikacja ma również [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] który umożliwia użytkownikowi zmianę różnych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości właściwości, takie jak tła kolor lub domyślny rozmiar czcionki.  
  
 Jak wspomniano powyżej, gdy użytkownik kliknie przycisk albo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości generuje `OnButtonClicked` zdarzeń. Aplikacja dołącza program obsługi do tego zdarzenia, aby otrzymywać te powiadomienia. Jeśli **OK** przycisk został kliknięty, program obsługi pobiera informacje o użytkowniku z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i wyświetla je w zestawie formantów statycznych.  
  
 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]  
  
 Program obsługi odbiera obiekt argument niestandardowe zdarzenie z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, `MyPageEventArgs`. Obiektu `IsOK` właściwość jest ustawiona na `true` Jeśli **OK** kliknął przycisk i `false` Jeśli **anulować** przycisk został kliknięty.  
  
 Jeśli **OK** przycisk został kliknięty, program obsługi pobiera odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości z klasy kontenera. Następnie zbiera informacje o użytkowniku, który jest przechowywany przez skojarzony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości właściwości i używa formantów statycznych, aby wyświetlić informacje w oknie nadrzędnym. Ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] danych zawartości jest w formie ciągu zarządzany, musi być przekazywane do użycia przez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] formantu. Jeśli **anulować** przycisk został kliknięty, program obsługi spowoduje wyczyszczenie danych z formantów statycznych.  
  
 Aplikacja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zawiera zestaw przycisków radiowych, które umożliwiają użytkownikom modyfikowanie kolor tła [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i kilka właściwości związanych z czcionki. Poniższy przykład zawiera fragment procedurę okna aplikacji (WndProc) i jego obsługa który komunikatów ustawia różne właściwości na inne komunikaty, w tym kolor tła. Inne podobne i nie są pokazywane. Zobacz pełną próbki szczegółowe informacje i kontekstu.  
  
 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]  
  
 Aby ustawić kolor tła, pobrać odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości (`hostedPage`) z `WPFPageHost` i ustaw właściwość kolor tła na kolor odpowiednie. Próbka używa trzech opcji koloru: oryginalny kolor, światła łososia Green threshold lub prostych. Oryginalny kolor tła jest przechowywana jako pola statycznego w `WPFPageHost` klasy. Aby ustawić innych dwa, należy utworzyć nowy <xref:System.Windows.Media.SolidColorBrush> obiektu i przekazać wartości kolorów statyczne z konstruktora <xref:System.Windows.Media.Colors> obiektu.  
  
<a name="implementing_the_wpf_page"></a>   
## <a name="implementing-the-wpf-page"></a>Implementacja strony WPF  
 Możesz udostępniać i użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości bez żadnych wiedzy rzeczywistego wykonania. Jeśli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość była zostały opakowane w oddzielnej [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], można został skompilowany w żadnym [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] języka. Poniżej znajduje się krótki przewodnik [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] implementację, która jest używana w próbce. Ta sekcja zawiera następujące podsekcje.  
  
<a name="autoNestedSectionsOUTLINE2"></a>   
-   [Układ](#page_layout)  
  
-   [Przesłać dane do okna hosta](#returning_data_to_window)  
  
-   [Ustawianie właściwości WPF](#set_page_properties)  
  
<a name="page_layout"></a>   
### <a name="layout"></a>Układ  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Elementów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości składają się z pięciu <xref:System.Windows.Controls.TextBox> kontrolki, z skojarzony <xref:System.Windows.Controls.Label> kontrolki: nazwa, adres miejscowość, stan i Zip. Istnieją również dwa <xref:System.Windows.Controls.Button> formantów, **OK** i **Anuluj**  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawartości jest zaimplementowana w `WPFPage` klasy. Układ jest obsługiwany z <xref:System.Windows.Controls.Grid> elementu układu. Klasa dziedziczy <xref:System.Windows.Controls.Grid>, które skutecznie stwarza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu głównego zawartości.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawartości Konstruktor pobiera wymaganych szerokość i wysokość oraz rozmiary <xref:System.Windows.Controls.Grid> odpowiednio. Następnie definiuje podstawowy układ tworząc zestaw <xref:System.Windows.Controls.ColumnDefinition> i <xref:System.Windows.Controls.RowDefinition> obiektów oraz dodanie ich do <xref:System.Windows.Controls.Grid> obiektu podstawowego <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> i <xref:System.Windows.Controls.Grid.RowDefinitions%2A> kolekcje, odpowiednio. Definiuje siatki pięć wierszy i kolumn siedmiu o wymiarach ustaleniami zawartości komórek.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]  
  
 Następnie dodaje konstruktora [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy <xref:System.Windows.Controls.Grid>. Pierwszy element jest tekst tytułu, który jest <xref:System.Windows.Controls.Label> formant, który skupia się w pierwszym wierszu siatki.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]  
  
 Następny wiersz zawiera nazwę <xref:System.Windows.Controls.Label> kontroli i jego skojarzony <xref:System.Windows.Controls.TextBox> formantu. Ponieważ ten sam kod jest używane dla każdej pary etykiety/pola tekstowego, jest umieszczony w parze prywatnych metod i używane dla wszystkich pięciu par etykiety/textbox. Utwórz odpowiednie metody kontroli i wywołać <xref:System.Windows.Controls.Grid> klasy statycznej <xref:System.Windows.Controls.Grid.SetColumn%2A> i <xref:System.Windows.Controls.Grid.SetRow%2A> metody Umieść formanty w komórce, odpowiedni. Po utworzeniu formantu przykład wywołuje <xref:System.Windows.Controls.UIElementCollection.Add%2A> metoda <xref:System.Windows.Controls.Panel.Children%2A> właściwość <xref:System.Windows.Controls.Grid> można dodać kontrolki do siatki. Przypomina kod, aby dodać pozostałe pary etykiety/textbox. Zobacz przykładowy kod, aby uzyskać szczegółowe informacje.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]  
  
 Implementacja dwie metody jest następująca:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]  
  
 Na koniec dodaje próbki **OK** i **anulować** przyciski i dołącza program obsługi zdarzeń do ich <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]  
  
<a name="returning_data_to_window"></a>   
### <a name="returning-the-data-to-the-host-window"></a>Przesłać dane do okna hosta  
 Po kliknięciu przycisku albo jego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia. Okno hosta można po prostu Dołącz programów obsługi na te zdarzenia i Pobierz dane bezpośrednio z <xref:System.Windows.Controls.TextBox> formantów. W przykładzie użyto nieco mniej bezpośredniego podejście. Obsługuje on <xref:System.Windows.Controls.Primitives.ButtonBase.Click> w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, a następnie wywołuje zdarzenie niestandardowe `OnButtonClicked`, aby powiadomić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Dzięki temu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w celu niektóre sprawdzanie poprawności parametru przed powiadamiania hosta. Program obsługi pobiera tekst z <xref:System.Windows.Controls.TextBox> steruje i przypisuje go do właściwości publiczne, z których mogą pobrać hosta informacje.  
  
 Deklaracja zdarzenia w WPFPage.h:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Obsługi zdarzeń w WPFPage.cpp:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]  
  
<a name="set_page_properties"></a>   
### <a name="setting-the-wpf-properties"></a>Ustawianie właściwości WPF  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Hosta umożliwia użytkownikowi zmianę kilka [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zawartości. Z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] strony, jest po prostu kwestią zmiany właściwości. Implementacja w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy zawartości jest nieco bardziej skomplikowane, ponieważ nie ma jednej właściwości globalne kontrolujące czcionki dla wszystkich kontrolek. Zamiast tego odpowiednie właściwości dla każdego formantu zostanie zmieniona w metodach dostępu set właściwości. W poniższym przykładzie pokazano kod `DefaultFontFamily` właściwości. Ustawienie właściwości wywołuje metody prywatnej to z kolei zestawy <xref:System.Windows.Controls.Control.FontFamily%2A> właściwości różnych formantów.  
  
 Z WPFPage.h:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]  
  
 Z WPFPage.cpp:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
