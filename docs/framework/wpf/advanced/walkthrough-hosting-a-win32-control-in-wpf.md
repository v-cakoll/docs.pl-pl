---
title: 'Przewodnik: hostowanie kontrolki Win32 w WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 2cfd8699afe48cb936ecf600c47508ef45781b43
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605503"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Przewodnik: hostowanie kontrolki Win32 w WPF
Windows Presentation Foundation (WPF) zapewnia rozbudowane środowisko do tworzenia aplikacji. Jednak jeśli masz znaczne inwestycje w kodzie Win32, może być bardziej efektywne ponownie użyć przynajmniej część tego kodu w aplikacji WPF, a nie jego przepisania całkowicie. WPF zapewnia prosty mechanizm do obsługi oknie Win32, na stronie programu WPF.  
  
 Ten temat przeprowadzi Cię przez aplikację, [Hosting kontrolki ListBox Win32 w przykładzie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), aby kontrolować Win32 pole listy hostów. Ta procedura ogólne można rozszerzyć z hostingiem dowolne Win32 okno.  

<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym temacie założono podstawowe umiejętność programowania WPF i Windows API. Aby uzyskać podstawowe wprowadzenie do programowania WPF, zobacz [wprowadzenie](../getting-started/index.md). Wprowadzenie do programowania interfejsu API Windows, zobacz dowolny wiele książek na ten temat, w szczególności *programowania Windows* przez Charles Petzold.  
  
 Ponieważ przykładu, który towarzyszy w tym temacie jest zaimplementowana w C#, to sprawia, że użycie platformę wywołania usług (funkcja PInvoke) dostęp do interfejsu API Windows. Pewną znajomość PInvoke jest przydatna, ale nie są niezbędne.  
  
> [!NOTE]
>  Ten temat zawiera szereg przykładów kodu z próbki skojarzone. Jednak aby zwiększyć czytelność, nie obejmuje pełny przykładowy kod. Można uzyskać lub wyświetlić kompletny kod z [Hosting kontrolki ListBox Win32 w przykładzie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Podstawowa procedura  
 W tej sekcji opisano podstawowe procedury do obsługi oknie Win32 na stronie programu WPF. Pozostałe sekcje przechodzą przez szczegółowe informacje o każdym kroku.  
  
 Podstawowa procedura obsługi jest:  
  
1. Implementowanie strony WPF do hostowania okna. Jedna z technik jest utworzenie <xref:System.Windows.Controls.Border> element, aby zarezerwować części strony okna hostowanej.  
  
2. Implementowanie klasy do hostowania kontrolki, która dziedziczy <xref:System.Windows.Interop.HwndHost>.  
  
3. W tej klasie zastąpić <xref:System.Windows.Interop.HwndHost> składowej klasy <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4. Utworzyć hostowanej okno jako element podrzędny okno, które zawiera stronę WPF. Mimo że konwencjonalne programowania WPF nie trzeba jawnie wprowadzać z niej korzystać, strona macierzysta jest oknem z dojściem (HWND). Pojawi się Strona HWND za pośrednictwem `hwndParent` parametru <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> metody. Okno hostowanej powinien zostać utworzony jako element podrzędny tego HWND.  
  
5. Po utworzeniu okno hosta Zwróć HWND hostowanej okna. Jeśli chcesz udostępnić co najmniej jednej kontrolki Win32 są zazwyczaj tworzone okna hosta jako element podrzędny HWND i utworzyć formanty elementy podrzędne tego okna hosta. OPAKOWYWANIE formantów w oknie hosta zapewnia prostą metodę dla strony WPF może otrzymywać powiadomienia z formantów, które dotyczy niektóre konkretnej kwestii Win32, dzięki powiadomieniom granicę HWND.  
  
6. Obsługuj wybrane komunikaty wysyłane do okna hosta, takich jak powiadomienia z formantów podrzędnych. Istnieją dwa sposoby, aby to zrobić.  
  
    - Jeśli wolisz do obsługi wiadomości w klasie hostingu, Zastąp <xref:System.Windows.Interop.HwndHost.WndProc%2A> metody <xref:System.Windows.Interop.HwndHost> klasy.  
  
    - Jeśli chcesz mieć WPF obsługi komunikatów, obsługa <xref:System.Windows.Interop.HwndHost> klasy <xref:System.Windows.Interop.HwndHost.MessageHook> zdarzenia w swojej związanym z kodem. To zdarzenie występuje dla każdego komunikatu odebranego przez okno hostowanej. Jeśli ta opcja jest wybrana, nadal musisz przesłonić <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ale wystarczy tylko minimalne implementacji.  
  
7. Zastąp <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> i <xref:System.Windows.Interop.HwndHost.WndProc%2A> metody <xref:System.Windows.Interop.HwndHost>. Konieczne jest przesłonięcie tych metod w celu zaspokojenia <xref:System.Windows.Interop.HwndHost> kontraktu, ale może być tylko konieczne podanie minimalny implementacji.  
  
8. W pliku związanym z kodem, Utwórz wystąpienie obiektu hostingu klasy formantu, co element podrzędny elementu <xref:System.Windows.Controls.Border> element, który jest przeznaczony do obsługi oknie.  
  
9. Komunikować się z oknie hostowanej przez wysłanie go [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] komunikatów i obsługi komunikatów z jego okien podrzędnych, takich jak powiadomienia wysyłane przez formanty.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implementowanie układu strony  
 Układ strony WPF, który obsługuje kontrolki ListBox składa się z dwóch regionach. Po lewej stronie strony znajduje się kilka kontrolek WPF, które zapewniają [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pozwala manipulować formantu Win32. Prawy górny róg strony ma kwadratowy region hostowanej kontrolki ListBox.  
  
 Kod implementujący ten układ jest bardzo proste. Element główny jest <xref:System.Windows.Controls.DockPanel> zawierający dwa typy elementów podrzędnych. Pierwsza to <xref:System.Windows.Controls.Border> elementu, który jest hostem kontrolki ListBox. Zajmuje 200 x 200 cali kwadratowy prawy górny róg strony. Drugi to <xref:System.Windows.Controls.StackPanel> element, który zawiera zestaw kontrolek WPF, wyświetlane informacje, które umożliwiają manipulowanie kontrolki ListBox, ustawiając udostępniane współdziałanie właściwości. Dla każdego z elementów, które są elementami podrzędnymi <xref:System.Windows.Controls.StackPanel>, zobacz materiały referencyjne dla różnych elementów, które są używane szczegółowe informacje na temat tych elementów są lub co zrobić, te są wymienione w poniższym przykładowym kodzie, ale nie są opisane w tym miejscu (podstawowa współdziałanie modelu nie wymaga żadnej z nich, są one udostępniane niektóre interakcyjności do przykładu).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementowanie klasy do hostowania kontrolki Microsoft Win32  
 Podstawowe w tym przykładzie jest to klasa, która faktycznie obsługuje formant ControlHost.cs. Dziedziczy <xref:System.Windows.Interop.HwndHost>. Konstruktor przyjmuje dwa parametry, wysokości i szerokości, które odnoszą się do wysokości i szerokości <xref:System.Windows.Controls.Border> elementu, który jest hostem kontrolki ListBox. Wartości te są używane, później, upewnij się, że rozmiar dopasowania kontroli <xref:System.Windows.Controls.Border> elementu.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Istnieje również zestaw stałych. Te stałe dużej mierze są pobierane z Winuser.h i umożliwiają używanie konwencjonalnej nazwy podczas wywoływania funkcji Win32.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Zastąp BuildWindowCore można utworzyć okna Microsoft Win32  
 Możesz zastąpić tę metodę, aby utworzyć w oknie Win32, w którym będzie hostowana przez stronę i nawiązywanie połączenia między oknem i strony. Ponieważ ten przykład obejmuje hosting kontrolki ListBox, są tworzone dwa okna. Pierwsza to okno, które faktycznie jest hostowana przez stronę WPF. ListBox — formant jest tworzony jako element podrzędny tego okna.  
  
 Przyczyną tego podejścia jest w celu uproszczenia procesu odbierania powiadomień w formancie. <xref:System.Windows.Interop.HwndHost> Klasa służy do przetwarzania komunikatów wysłanych do okna, które obsługuje on. Jeśli host systemu Win32 kontrolować bezpośrednio, zostanie wyświetlony komunikaty wysyłane do pętli komunikatów wewnętrznej kontrolki. Możesz wyświetlić kontroli i wyślij go komunikaty, ale nie otrzymasz powiadomienia, które kontrolki wysyła do okna nadrzędnego. Oznacza to, między innymi, że nie ma możliwości wykrywania, gdy użytkownik wchodzi w interakcję z kontrolką. Zamiast tego należy utworzyć okno hosta i sprawić, że formant z elementem podrzędnym tego okna. Umożliwia to przetwarzanie wiadomości dla okna hosta, w tym powiadomień wysyłanych przez kontrolkę. Dla wygody ponieważ host jest nieco więcej niż prosty otoki dla formantu, pakiet zostanie określane jako kontrolce ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Utwórz okno hosta i ListBox, kontrolka  
 Użyj funkcji PInvoke, aby utworzyć okna dla kontrolki hosta przez tworzenie i rejestrowanie klasy okna i tak dalej. Jednak znacznie prostsze jest można utworzyć okna przy użyciu klasy wstępnie zdefiniowanych okna "statyczny". Zawiera procedurę okna niezbędna, aby otrzymywać powiadomienia z formantu i wymaga minimalnego kodowania.  
  
 HWND formantu jest dostępna za pośrednictwem właściwości tylko do odczytu, tak, aby strony hosta służy do wysyłania komunikatów do formantu.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox — formant jest tworzony jako element podrzędny okno hosta. Wysokość i szerokość oba okna są ustawione na wartości przekazane do konstruktora omówione powyżej. Dzięki temu, rozmiar okna hosta i kontroli są identyczne z zarezerwowanym obszarem, na stronie.  Po utworzeniu systemu windows, zwraca próbkę <xref:System.Runtime.InteropServices.HandleRef> obiekt, który zawiera HWND okna hosta.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Destroywindow — Implementowanie i WndProc  
 Oprócz <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, konieczne jest również przesłonięcie <xref:System.Windows.Interop.HwndHost.WndProc%2A> i <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> metody <xref:System.Windows.Interop.HwndHost>. W tym przykładzie wiadomości dla formantu są obsługiwane przez <xref:System.Windows.Interop.HwndHost.MessageHook> obsługi, dlatego implementacja <xref:System.Windows.Interop.HwndHost.WndProc%2A> i <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> jest minimalny. W przypadku właściwości <xref:System.Windows.Interop.HwndHost.WndProc%2A>ustaw `handled` do `false` wskazują, że komunikat nie został obsłużony i zwracają 0. Aby uzyskać <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, po prostu zniszczyć okna.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Kontrolki na stronie hosta  
 Aby obsługiwać formantu na stronie, należy najpierw utworzyć nowe wystąpienie klasy `ControlHost` klasy. Przekaż wysokość i szerokość elementu obramowania, który zawiera kontrolkę (`ControlHostElement`) do `ControlHost` konstruktora. Daje to gwarancję, że pole listy jest mały rozmiar. Następnie Hostuj formantu na stronie, przypisując `ControlHost` obiekt <xref:System.Windows.Controls.Decorator.Child%2A> właściwości hosta <xref:System.Windows.Controls.Border>.  
  
 Przykład dołącza obsługę do <xref:System.Windows.Interop.HwndHost.MessageHook> zdarzenia `ControlHost` do odbierania komunikatów z formantu. To zdarzenie jest wywoływane dla każdej wiadomości wysyłane do okna hostowanej. W tym przypadku są to komunikaty wysyłane do okna, który otacza rzeczywistego formantu ListBox, łącznie z powiadomień z poziomu kontroli. Przykład wywołuje SendMessage do uzyskania informacji z formantu i modyfikowania jego zawartości. Szczegółowe informacje o jak strona komunikuje się za pomocą kontrolki są omówione w następnej sekcji.  
  
> [!NOTE]
>  Należy zauważyć, że nie istnieją dwie deklaracje funkcji PInvoke dla SendMessage. Jest to konieczne, ponieważ korzysta z jednego `wParam` parametr do przekazania ciąg, a druga używa go w celu przekazania liczbą całkowitą. Potrzebujesz oddzielnych deklarację dla każdego podpisu upewnić się, że danych jest organizowana poprawnie.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementowanie komunikacji między formantem i strony  
 Kontrolki można manipulować wysyłając komunikaty Windows. Kontrolki powiadamia, gdy użytkownik wchodzi w interakcję z nią przez wysłanie powiadomienia do okna hosta. [Hosting kontrolki ListBox Win32 w WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) przykład obejmuje interfejs użytkownika, który zawiera kilka przykładów jak to działa:  
  
- Dołącz element do listy.  
  
- Usuń wybrany element z listy  
  
- Wyświetl tekst aktualnie wybranego elementu.  
  
- Wyświetl liczbę elementów na liście.  
  
 Użytkownik może również wybrać element w polu listy, klikając ją, tak samo, jak w przypadku konwencjonalnych aplikacji Win32. Dane wyświetlane aktualizowane wówczas, gdy użytkownik zmieni stan pola listy, wybierając, dodając lub dołączanie elementu.  
  
 Aby dołączyć elementy, Wyślij pole listy [ `LB_ADDSTRING` komunikat](/windows/desktop/Controls/lb-addstring). Aby usunąć elementy, Wyślij [ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel) uzyskać indeks bieżącego zaznaczenia i następnie [ `LB_DELETESTRING` ](/windows/desktop/Controls/lb-deletestring) można usunąć elementu. Przykład wysyła również [ `LB_GETCOUNT` ](/windows/desktop/Controls/lb-getcount)i używa zwracanej wartości, aby zaktualizować ekran, który pokazuje liczbę elementów. Oba te wystąpienia [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) użyj jednej z deklaracjami funkcji PInvoke opisanych w poprzedniej sekcji.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Gdy użytkownik wybierze element lub zmieni się ich wyboru, formantu powiadamia okno hosta przez wysłanie go [ `WM_COMMAND` komunikat](/windows/desktop/menurc/wm-command), co powoduje zdarzenie <xref:System.Windows.Interop.HwndHost.MessageHook> zdarzeń dla strony. Program obsługi otrzymuje te same informacje jak procedura okno główne okno hosta. Przekazuje odwołanie na wartość logiczną `handled`. Możesz ustawić `handled` do `true` oznacza, że zapewnienia obsługi wiadomości i żadne dalsze przetwarzanie nie jest wymagana.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command) są wysyłane z różnych powodów, więc należy zbadać identyfikator powiadomień do określenia, czy to zdarzenie, którą chcesz obsługiwać. Identyfikator znajduje się w wyższe słowo `wParam` parametru. W przykładzie użyto operatory bitowe można wyodrębnić identyfikatora. Jeśli wprowadzone przez użytkownika lub zmianie ich wyboru, będzie identyfikator [ `LBN_SELCHANGE` ](/windows/desktop/Controls/lbn-selchange).  
  
 Gdy [ `LBN_SELCHANGE` ](/windows/desktop/Controls/lbn-selchange) jest odbierane, przykładowy kod pobiera indeks zaznaczonego elementu, wysyłając kontrolki [ `LB_GETCURSEL` komunikat](/windows/desktop/Controls/lb-getcursel). Aby uzyskać tekst, należy najpierw utworzyć <xref:System.Text.StringBuilder>. Następnie wyślij kontrolki [ `LB_GETTEXT` komunikat](/windows/desktop/Controls/lb-gettext). Przekaż pustą <xref:System.Text.StringBuilder> obiektu jako `wParam` parametru. Gdy [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) zwraca, <xref:System.Text.StringBuilder> będzie zawierać tekst wybranego elementu. Użycie tego [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) wymaga kolejny deklaracji funkcji PInvoke.  
  
 Wreszcie, ustaw `handled` do `true` do wskazania obsługiwania wiadomości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndHost>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Przewodnik: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
