---
title: 'Wskazówki: hosting formantu Win32 w WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: af8491a2887f4a35e2cd9926304948c12a67623a
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314981"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Wskazówki: hosting formantu Win32 w WPF
Windows Presentation Foundation (WPF) zawiera rozbudowane środowisko do tworzenia aplikacji. Jednak gdy znaczących inwestycji w kodzie Win32, może być bardziej skuteczne ponownie wykorzystać przynajmniej część tego kodu w aplikacji WPF, zamiast ponownego zapisywania całkowicie. WPF udostępnia proste mechanizm hosting okna Win32, na stronie WPF.  
  
 Ten temat przeprowadzi Cię przez aplikację, [Hosting kontrolki ListBox Win32 w przykładowym WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), aby kontrolować Win32 pole listy hostów. Ta procedura ogólne można rozszerzyć hosting dowolnego okna Win32.  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym temacie założono podstawowa znajomość programowania zarówno WPF i Win32. Aby uzyskać podstawowe wprowadzenie do programowania WPF, zobacz [wprowadzenie](../../../../docs/framework/wpf/getting-started/index.md). Wprowadzenie do programowania Win32, użytkownik powinien odwoływać się żadnego wiele książek na ten temat, w szczególności *programowania Windows* przez Petzold Charlesa.  
  
 Ponieważ dołączony w tym temacie próbki jest zaimplementowana w języku C#, powoduje użycie usług wywołania platformy (PInvoke) w celu dostępu do interfejsu API Win32. Masz pewną znajomość programu PInvoke jest przydatne, ale nie są niezbędne.  
  
> [!NOTE]
>  Ten temat zawiera wiele przykładów kodu z skojarzone próbki. Jednak aby zwiększyć czytelność, go nie ma kompletnego przykładowego kodu. Można uzyskać lub wyświetlić pełny kod z [Hosting kontrolki ListBox Win32 w przykładowym WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Podstawowe procedury  
 W tej sekcji opisano procedurę hosting okna Win32 na stronie WPF. Pozostałe sekcje przejść przez szczegóły każdego kroku.  
  
 Podstawowa procedura obsługi jest:  
  
1.  Implementuje stronę WPF do hostowania okna. Co metoda polega na utworzeniu <xref:System.Windows.Controls.Border> element do zarezerwowania części strony hostowanej okna.  
  
2.  Implementowanie do hostowania formantu, który dziedziczy z klasy <xref:System.Windows.Interop.HwndHost>.  
  
3.  W tej klasie zastąpienie <xref:System.Windows.Interop.HwndHost> elementu członkowskiego klasy <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4.  Tworzenie hostowanej okno jako element podrzędny okna zawierającego strony WPF. Mimo że konwencjonalnej programowania WPF nie należy jawnie z niej korzystać, strona hostingu jest okno z dojściem (HWND). Pojawi się Strona HWND za pośrednictwem `hwndParent` parametr <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> metody. Okno hostowanej powinny być tworzone jako element podrzędny tego HWND.  
  
5.  Po utworzeniu okno hosta zwraca HWND hostowanej okna. Jeśli chcesz udostępnić co najmniej jeden formant Win32 są zazwyczaj tworzone okno hosta jako element podrzędny HWND i wprowadzić formanty elementy podrzędne tego okna hosta. Zawijanie formantów w oknie hosta zapewnia prostą metodę strony WPF do odbierania powiadomień od formantów, którego dotyczy konkretnego Win32 problemy z powiadomieniami granicy HWND.  
  
6.  Obsługa wybrane wiadomości wysyłane do okna hosta, takich jak powiadomienia z formantów podrzędnych. Istnieją dwa sposoby, w tym celu.  
  
    -   Jeśli wolisz obsługi wiadomości w klasie hostingu zastępują <xref:System.Windows.Interop.HwndHost.WndProc%2A> metody <xref:System.Windows.Interop.HwndHost> klasy.  
  
    -   Jeśli preferujesz WPF obsługi wiadomości i obsługiwać <xref:System.Windows.Interop.HwndHost> klasy <xref:System.Windows.Interop.HwndHost.MessageHook> zdarzenie z kodem. To zdarzenie występuje dla każdy komunikat jest odbierany przez okno hostowanej. Jeśli wybierzesz tę opcję, należy zastąpić nadal <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ale wymagane jest tylko minimalny implementacji.  
  
7.  Zastąpienie <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> i <xref:System.Windows.Interop.HwndHost.WndProc%2A> metody <xref:System.Windows.Interop.HwndHost>. Musi zastępować te metody do zaspokojenia <xref:System.Windows.Interop.HwndHost> kontraktu, ale może być tylko konieczne minimalnego implementacji.  
  
8.  W pliku CodeBehind utworzyć wystąpienia formantu hosting klasy i była elementem podrzędnym <xref:System.Windows.Controls.Border> element, który jest przeznaczony do obsługi okna.  
  
9. Komunikować się z okna hostowanej przez wysłanie ich [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] komunikatów i obsługi komunikatów z jego okno podrzędne, takich jak powiadomienia wysyłane przez formanty.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Zastosuj układ strony  
 Układ strony WPF, który obsługuje kontrolki ListBox składa się z dwóch regionach. W lewej części strony znajduje się kilka formantów WPF, które zapewniają [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] można manipulować kontroli Win32. Prawym górnym rogu strony ma kwadratowy region hostowanej kontrolki ListBox.  
  
 Kod do implementacji tego układu jest bardzo proste. Element główny jest <xref:System.Windows.Controls.DockPanel> która ma dwa elementy podrzędne. Pierwsza to <xref:System.Windows.Controls.Border> element, który obsługuje kontrolki ListBox. Przypada 200 x 200 cali kwadratowych prawym górnym rogu strony. Druga <xref:System.Windows.Controls.StackPanel> element, który zawiera zbiór formantów WPF, wyświetlane informacje, które umożliwia manipulowanie kontrolki ListBox ustawiając widoczne współdziałanie właściwości. Dla każdego z elementów, które są elementami podrzędnymi <xref:System.Windows.Controls.StackPanel>, zobacz materiał odwołania dla różnych elementów używane szczegółowe informacje dotyczące tych elementów są co zrobić, te są wyświetlane w poniższym przykładowym kodzie, ale nie będzie omówione (podstawowe współdziałanie modelu nie wymaga żadnej z nich, są one udostępniane niektórych interakcyjności w przykładzie).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementowanie klasy do obsługi sterowania Microsoft Win32  
 Podstawowe w tym przykładzie jest klasa, która faktycznie obsługuje formantu ControlHost.cs. Dziedziczy on z <xref:System.Windows.Interop.HwndHost>. Konstruktor przyjmuje dwa parametry, wysokości i szerokości, które odpowiadają wysokość i szerokość <xref:System.Windows.Controls.Border> element, który obsługuje kontrolki ListBox. Te wartości są używane, później, upewnij się, że rozmiar formantu dopasowań <xref:System.Windows.Controls.Border> elementu.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Istnieje również zestaw stałych. Te stałe przede wszystkim są pobierane z Winuser.h i będzie można korzystać z konwencjonalnej nazwy podczas wywoływania funkcji Win32.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Zastąpienie metoda BuildWindowCore do tworzenia okna Microsoft Win32  
 Należy przesłonić tę metodę można utworzyć okna Win32, w którym będzie hostowana przez stronę i tworzenie połączenia między okna i na stronie. Ponieważ ten przykład obejmuje hosting kontrolki ListBox, są tworzone dwa okna. Pierwsza to okno faktycznie jest hostowana przez stronę WPF. ListBox — formant jest tworzone jako element podrzędny tego okna.  
  
 Przyczyna tego podejścia jest uprościć proces odbieranie powiadomień w formancie. <xref:System.Windows.Interop.HwndHost> Klasa umożliwia przetwarzanie wiadomości wysyłane do okna, które obsługuje on. Jeśli host Win32 kontrolować bezpośrednio, pojawi się komunikaty wysłane do pętli komunikatów wewnętrzny formantu. Można wyświetlić kontroli i wysyłania, który go wiadomości, ale nie otrzymasz powiadomień, które kontrolki wysyła do jej okna nadrzędnego. Oznacza to, między innymi, że nie ma możliwości wykrycia, gdy użytkownik wchodzi w interakcję z formantem. Zamiast tego należy utworzyć okno hosta i ustaw kontrolkę elementem podrzędnym tego okna. Dzięki temu można przetworzyć wiadomości dla okna hosta, w tym powiadomienia wysyłane do niej przez formant. Dla wygody ponieważ okno hosta to po prostu niż proste otoki dla formantu, pakiet zostanie określane jako kontrolki ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Utwórz okno hosta i ListBox — formant  
 Można utworzyć hosta okna dla formantu, tworząc i rejestrowanie klasy okna za pomocą funkcji PInvoke i tak dalej. Jednak znacznie prostsze jest można utworzyć okna z klasy wstępnie zdefiniowane okna "statyczny". Udostępnia procedurę okna niezbędną do odbierania powiadomień w formancie i wymaga minimalnego kodowania.  
  
 HWND formantu jest uwidaczniany za pośrednictwem właściwości tylko do odczytu, tak, aby strona hosta służy do wysyłania komunikatów do formantu.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox — formant jest tworzone jako element podrzędny okna hosta. Wysokość i szerokość zarówno systemu Windows są ustawiane na wartości przekazanych do konstruktora opisanych wyżej. Dzięki temu, że rozmiar okna hosta i kontroli jest identyczny z zastrzeżonego obszaru na stronie.  Po utworzeniu systemu windows, zwraca próbki <xref:System.Runtime.InteropServices.HandleRef> obiekt, który zawiera HWND okna hosta.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>DestroyWindow wdrożenie i WndProc  
 Oprócz <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, musi także zastępować <xref:System.Windows.Interop.HwndHost.WndProc%2A> i <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> metody <xref:System.Windows.Interop.HwndHost>. W tym przykładzie wiadomości dla formantu są obsługiwane przez <xref:System.Windows.Interop.HwndHost.MessageHook> obsługi, w związku z tym implementacja <xref:System.Windows.Interop.HwndHost.WndProc%2A> i <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> jest minimalny. W przypadku liczby <xref:System.Windows.Interop.HwndHost.WndProc%2A>ustaw `handled` do `false` wskazują, że komunikat nie został obsłużony i zwraca 0. Aby uzyskać <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, po prostu zniszczyć okna.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Kontrolki na stronie hosta  
 Aby kontrolki na stronie hosta, należy najpierw utworzyć nowe wystąpienie klasy `ControlHost` klasy. Przekaż wysokość i szerokość elementu obramowanie z formantem (`ControlHostElement`) do `ControlHost` konstruktora. Dzięki temu, że pole listy jest mały rozmiar. Następnie hosta kontrolki na stronie przypisując `ControlHost` do obiektu <xref:System.Windows.Controls.Decorator.Child%2A> właściwość hosta <xref:System.Windows.Controls.Border>.  
  
 Przykład dołącza program obsługi do <xref:System.Windows.Interop.HwndHost.MessageHook> zdarzenie `ControlHost` odbierać komunikaty z formantu. To zdarzenie jest wywoływane dla każdej wiadomości wysyłane do okna hostowanej. W tym przypadku są komunikaty wysyłane do okna, który opakowuje rzeczywiste formantu ListBox, w tym powiadomienia z formantu. Przykład wywołuje SendMessage uzyskać informacji z formantu i zmodyfikuj jego zawartość. W następnej sekcji omówiono szczegóły jak strony komunikuje się za pomocą formantu.  
  
> [!NOTE]
>  Zwróć uwagę, że istnieją dwa deklaracje funkcji PInvoke dla SendMessage. Jest to konieczne, ponieważ korzysta z jednego `wParam` parametr do przekazania ciąg, a drugi używa go do przekazania liczbą całkowitą. Potrzebujesz oddzielnych deklaracji dla każdego podpisu upewnić się, że dane jest poprawnie przekazywane.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Komunikacja między formantem a strony  
 Formant manipulować wysyłając komunikaty systemu Windows. Formant powiadamia, gdy użytkownik wchodzi w interakcję z nią poprzez wysłanie powiadomienia do okno hosta. [Hosting kontrolki ListBox Win32 na platformie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) próbki obejmuje interfejsu użytkownika, który zawiera kilka przykładów jak to działa:  
  
-   Dołącz element do listy.  
  
-   Usuń wybrany element z listy  
  
-   Wyświetl tekst aktualnie wybranego elementu.  
  
-   Wyświetlenia liczba elementów na liście.  
  
 Użytkownik może również wybrać element w polu listy, klikając go, tak samo, jak w przypadku konwencjonalnych aplikacją systemu Win32. Dane wyświetlane jest aktualizowana każdorazowo użytkownik zmieni stan pola listy przez zaznaczenie, dodając lub dołączanie elementu.  
  
 Aby dołączyć elementy, Wyślij pola listy [ `LB_ADDSTRING` komunikat](https://msdn.microsoft.com/library/windows/desktop/bb775181(v=vs.85).aspx). Aby usunąć elementy, Wyślij [ `LB_GETCURSEL` ](https://msdn.microsoft.com/library/windows/desktop/bb775197(v=vs.85).aspx) uzyskać indeks bieżącego zaznaczenia, a następnie [ `LB_DELETESTRING` ](https://msdn.microsoft.com/library/windows/desktop/bb775183(v=vs.85).aspx) można usunąć elementu. Wysyła również próbki [ `LB_GETCOUNT` ](https://msdn.microsoft.com/library/windows/desktop/bb775195(v=vs.85).aspx)i używa zwracanej wartości, aby zaktualizować ekran, który pokazuje liczbę elementów. Oba te wystąpienia [ `SendMessage` ](https://msdn.microsoft.com/library/windows/desktop/ms644950(v=vs.85).aspx) użyj jednej z deklaracjami funkcji PInvoke opisanych w poprzedniej sekcji.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Gdy użytkownik wybiera element lub zmiany ich wyboru, formantu powiadamia okno hosta przez wysłanie ich [ `WM_COMMAND` komunikat](https://msdn.microsoft.com/library/windows/desktop/ms647591(v=vs.85).aspx), które generuje <xref:System.Windows.Interop.HwndHost.MessageHook> zdarzenia dla strony. Program obsługi odbiera te same informacje jak procedura okno główne okno hosta. Przekazuje ono również odwołania na wartość logiczną `handled`. Możesz ustawić `handled` do `true` oznacza, że zapewnienia obsługi wiadomości i żadne dalsze przetwarzanie nie jest niezbędne.  
  
 [`WM_COMMAND`](https://msdn.microsoft.com/library/windows/desktop/ms647591(v=vs.85).aspx) są wysyłane z różnych powodów, dlatego należy zbadać identyfikator powiadomień do ustalenia, czy zdarzenie, które chcesz obsługiwać. Identyfikator jest zawarta w wysokiej wyrazu `wParam` parametru. W przykładzie użyto operatory bitowe można wyodrębnić identyfikatora. Jeśli wprowadzone przez użytkownika lub zmienić ich wyboru, będzie identyfikator [ `LBN_SELCHANGE` ](https://msdn.microsoft.com/library/windows/desktop/bb775161(v=vs.85).aspx).  
  
 Gdy [ `LBN_SELCHANGE` ](https://msdn.microsoft.com/library/windows/desktop/bb775161(v=vs.85).aspx) jest odebrane próbki pobiera indeks wybranego elementu, wysyłając formantu [ `LB_GETCURSEL` komunikat](https://msdn.microsoft.com/library/windows/desktop/bb775197(v=vs.85).aspx). Aby uzyskać tekst, należy najpierw utworzyć <xref:System.Text.StringBuilder>. Następnie należy wysłać formantu [ `LB_GETTEXT` komunikat](https://msdn.microsoft.com/library/windows/desktop/bb761313(v=vs.85).aspx). Przekaż pustych <xref:System.Text.StringBuilder> obiekt jako `wParam` parametru. Gdy [ `SendMessage` ](https://msdn.microsoft.com/library/windows/desktop/ms644950(v=vs.85).aspx) zwraca, <xref:System.Text.StringBuilder> będzie zawierać tekst wybranego elementu. To [ `SendMessage` ](https://msdn.microsoft.com/library/windows/desktop/ms644950(v=vs.85).aspx) wymaga jeszcze innej deklaracji funkcji PInvoke.  
  
 Wreszcie, ustaw `handled` do `true` aby wskazać, że komunikat został obsłużony.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.HwndHost>  
 [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
