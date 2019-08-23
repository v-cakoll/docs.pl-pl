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
ms.openlocfilehash: cc27189afd2185d5f0a1eeacccf4c537dd3d9c2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917545"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Przewodnik: hostowanie kontrolki Win32 w WPF
Windows Presentation Foundation (WPF) oferuje bogate środowisko do tworzenia aplikacji. Jeśli jednak masz znaczną inwestycję w kod Win32, może być bardziej efektywne ponowne użycie co najmniej jednego z tych kodów w aplikacji WPF, a nie wielokrotne pisanie. WPF udostępnia prosty mechanizm hostingu okna Win32 na stronie WPF.  
  
 Ten temat przeprowadzi Cię przez aplikację, która [obsługuje formant ListBox elementu Win32 w przykładzie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), który hostuje kontrolkę pole listy Win32. Ta ogólna procedura może zostać rozszerzona o obsługę dowolnego okna Win32.  

<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym temacie założono podstawową znajomość programów WPF i Windows API. Aby zapoznać się z podstawowymi wprowadzeniem do programowania WPF, zobacz [wprowadzenie](../getting-started/index.md). Aby zapoznać się z wprowadzeniem do programowania interfejsu API systemu Windows, zobacz dowolną z wielu książek w temacie, w szczególności *programowanie systemu Windows* przez Charles Petzold.  
  
 Ponieważ przykład, który towarzyszy temu tematowi, jest C#zaimplementowany w programie, umożliwia dostęp do interfejsu API systemu Windows za pomocą usług wywołań platformy (PInvoke). Znajomość funkcji PInvoke jest przydatna, ale nie jest istotna.  
  
> [!NOTE]
> Ten temat zawiera kilka przykładów kodu ze skojarzonego przykładu. Jednak w celu zapewnienia czytelności nie obejmuje kompletny kod przykładowy. Możesz uzyskać lub wyświetlić kompletny kod z [hostingu kontrolki ListBox Win32 w przykładzie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Podstawowa procedura  
 W tej sekcji opisano podstawową procedurę hostingu okna Win32 na stronie WPF. Pozostałe sekcje zawierają szczegółowe informacje o każdym z kroków.  
  
 Podstawowa procedura hostingu:  
  
1. Zaimplementuj stronę WPF, aby hostować okno. Jedną z technik jest utworzenie <xref:System.Windows.Controls.Border> elementu w celu zarezerwowania sekcji strony dla hostowanego okna.  
  
2. Zaimplementuj klasę, aby hostować kontrolkę, <xref:System.Windows.Interop.HwndHost>która dziedziczy z.  
  
3. W tej klasie Przesłoń <xref:System.Windows.Interop.HwndHost> element członkowski <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>klasy.  
  
4. Utwórz hostowane okno jako element podrzędny okna zawierającego stronę WPF. Chociaż konwencjonalne programowanie WPF nie musi jawnie korzystać z niego, Strona hostingu jest oknem z dojściem (HWND). Wartość `hwndParent` parametru HWND zostanie wyświetlona przez parametr <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> metody. Hostowane okno powinno być tworzone jako element podrzędny tego parametru HWND.  
  
5. Po utworzeniu okna hosta Zwróć wartość HWND okna hostowanego. Jeśli chcesz hostować co najmniej jedną kontrolkę Win32, zazwyczaj tworzysz okno hosta jako element podrzędny HWND i kontroluje elementy podrzędne tego okna tego hosta. Zawijanie formantów w oknie hosta zapewnia prostą metodę otrzymywania powiadomień z formantów, które pomogą w przypadku niektórych określonych problemów Win32 z powiadomieniami na granicy HWND.  
  
6. Obsługa wybranych komunikatów wysyłanych do okna hosta, takich jak powiadomienia z formantów podrzędnych. Istnieją dwa sposoby, aby to zrobić.  
  
    - Jeśli wolisz obsługiwać komunikaty w klasie hostingu, Zastąp <xref:System.Windows.Interop.HwndHost.WndProc%2A> metodę <xref:System.Windows.Interop.HwndHost> klasy.  
  
    - Jeśli wolisz, aby program WPF obsłużył komunikaty, należy <xref:System.Windows.Interop.HwndHost> obsłużyć zdarzenie klasy <xref:System.Windows.Interop.HwndHost.MessageHook> w kodzie. To zdarzenie występuje dla każdego komunikatu, który jest odbierany przez hostowane okno. W przypadku wybrania tej opcji należy nadal przesłonić <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ale potrzebna jest tylko minimalna implementacja.  
  
7. Zastąp metody <xref:System.Windows.Interop.HwndHost.WndProc%2A> <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>i. <xref:System.Windows.Interop.HwndHost> Należy zastąpić te metody, aby spełnić <xref:System.Windows.Interop.HwndHost> umowę, ale może być konieczne jedynie dostarczenie minimalnej implementacji.  
  
8. W pliku związanym z kodem Utwórz wystąpienie klasy hostingu kontrolki i Uczyń ją elementem podrzędnym <xref:System.Windows.Controls.Border> elementu, który jest przeznaczony do hostowania okna.  
  
9. Komunikuj się z hostowanym oknem przez wysłanie komunikatów IT [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] i obsługę komunikatów z okien podrzędnych, takich jak powiadomienia wysyłane przez formanty.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implementowanie układu strony  
 Układ strony WPF, która hostuje formant ListBox, składa się z dwóch regionów. Lewa strona na stronie zawiera kilka formantów WPF, które zapewniają [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , że można manipulować kontrolką Win32. Prawy górny róg strony ma kwadratowy region dla hostowanej kontrolki ListBox.  
  
 Kod do zaimplementowania tego układu jest bardzo prosty. Element <xref:System.Windows.Controls.DockPanel> główny ma dwa elementy podrzędne. Pierwszy to <xref:System.Windows.Controls.Border> element, który hostuje formant ListBox. W prawym górnym rogu strony zajmuje się 200x200 kwadrat. Drugi to <xref:System.Windows.Controls.StackPanel> element, który zawiera zestaw kontrolek WPF, które wyświetlają informacje i umożliwiają manipulowanie formantem ListBox przez ustawienie uwidocznionych właściwości operacji międzyoperacyjnego. Dla każdego elementu, który jest elementem podrzędnym <xref:System.Windows.Controls.StackPanel>, Zobacz materiał referencyjny dla różnych elementów używanych do szczegółowych informacji na temat tego, czym są te elementy lub co robią, są one wymienione w poniższym przykładowym kodzie, ale nie zostaną wyjaśnione w tym miejscu (podstawowa Model międzyoperacyjny nie wymaga żadnej z nich, dlatego można dodać część interaktywną do przykładu).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementowanie klasy do hostowania kontrolki Win32 firmy Microsoft  
 Rdzeń tego przykładu jest klasą, która faktycznie hostuje kontrolkę, ControlHost.cs. Dziedziczy po <xref:System.Windows.Interop.HwndHost>. Konstruktor przyjmuje dwa parametry, Wysokość i szerokość, które odnoszą się do wysokości i szerokości <xref:System.Windows.Controls.Border> elementu, który hostuje formant ListBox. Te wartości są używane później, aby upewnić się, że rozmiar kontrolki <xref:System.Windows.Controls.Border> pasuje do elementu.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Istnieje również zestaw stałych. Te stałe są znacznie pobierane z Winuser. h i umożliwiają używanie konwencjonalnych nazw podczas wywoływania funkcji Win32.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Zastąp BuildWindowCore, aby utworzyć okno Microsoft Win32  
 Ta metoda zostanie zastąpiona, aby utworzyć okno Win32, które będzie hostowane na stronie, i nawiązać połączenie między oknem a stroną. Ponieważ ten przykład obejmuje hostowanie kontrolki ListBox, tworzone są dwa okna. Pierwszy jest oknem, które jest przechowywane na stronie WPF. Formant ListBox jest tworzony jako element podrzędny tego okna.  
  
 Przyczyną tego podejścia jest uproszczenie procesu otrzymywania powiadomień z formantu. <xref:System.Windows.Interop.HwndHost> Klasa umożliwia przetwarzanie komunikatów wysyłanych do okna, które obsługuje. W przypadku bezpośredniej obsługi kontrolki Win32 można odbierać komunikaty wysyłane do wewnętrznej pętli komunikatów formantu. Możesz wyświetlić formant i wysłać wiadomości IT, ale nie otrzymujesz powiadomień wysyłanych przez formant do okna nadrzędnego. Oznacza to między innymi, że nie ma możliwości wykrywania, kiedy użytkownik współdziała z kontrolką. Zamiast tego Utwórz okno hosta i uczyń formant elementem podrzędnym tego okna. Dzięki temu można przetwarzać komunikaty dla okna hosta, w tym powiadomienia wysyłane do niego przez formant. Dla wygody, ponieważ okno hosta jest nieco więcej niż prosta otoka dla kontrolki, pakiet będzie określany jako formant ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Utwórz okno hosta i formant ListBox  
 Za pomocą funkcji PInvoke można utworzyć okno hosta dla kontrolki, tworząc i rejestrując klasę okna i tak dalej. Jednak znacznie prostsze podejście polega na utworzeniu okna ze wstępnie zdefiniowaną klasą okna "static". Zapewnia to procedurę okna, która jest wymagana w celu otrzymywania powiadomień z kontrolki i wymaga minimalnego kodowania.  
  
 Właściwość HWND formantu jest uwidaczniana za pomocą właściwości tylko do odczytu, dzięki czemu Strona hosta może jej używać do wysyłania komunikatów do kontrolki.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Formant ListBox jest tworzony jako element podrzędny okna hosta. Wysokość i szerokość obu okien są ustawiane na wartości przesyłane do konstruktora, omówione powyżej. Dzięki temu rozmiar okna i kontrolki hosta jest identyczny z zastrzeżonym obszarem na stronie.  Po utworzeniu systemu Windows, przykład zwraca <xref:System.Runtime.InteropServices.HandleRef> obiekt, który zawiera właściwość HWND okna hosta.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Implementacja DestroyWindow i WndProc  
 Oprócz <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>programu należy również <xref:System.Windows.Interop.HwndHost.WndProc%2A> zastąpić <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> metody<xref:System.Windows.Interop.HwndHost>i. W tym przykładzie komunikaty dla formantu są obsługiwane przez <xref:System.Windows.Interop.HwndHost.MessageHook> program obsługi, więc <xref:System.Windows.Interop.HwndHost.WndProc%2A> implementacja i <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> jest minimalny. W przypadku <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ustaw `handled` na `false` , aby wskazać, że wiadomość nie została obsłużona i zwrócić 0. Dla <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, wystarczy zniszczyć okno.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Hostowanie kontrolki na stronie  
 Aby hostować formant na stronie, należy najpierw utworzyć nowe wystąpienie `ControlHost` klasy. Przekaż wysokość i Szerokość elementu obramowania, który zawiera kontrolkę (`ControlHostElement`) `ControlHost` do konstruktora. Daje to pewność, że rozmiar elementu ListBox jest prawidłowy. Następnie można hostować kontrolę na stronie, przypisując `ControlHost` obiekt <xref:System.Windows.Controls.Decorator.Child%2A> do właściwości hosta <xref:System.Windows.Controls.Border>.  
  
 Przykład dołącza procedurę obsługi do <xref:System.Windows.Interop.HwndHost.MessageHook> zdarzenia, `ControlHost` aby odbierać komunikaty z formantu. To zdarzenie jest zgłaszane dla każdej wiadomości wysyłanej do hostowanego okna. W takim przypadku komunikaty wysyłane do okna, które zawijają rzeczywistą kontrolkę ListBox, w tym powiadomienia z formantu. Przykład wywołuje SendMessage, aby uzyskać informacje z kontrolki i modyfikować jej zawartość. Szczegóły dotyczące sposobu komunikowania się strony z kontrolką zostały omówione w następnej sekcji.  
  
> [!NOTE]
> Zwróć uwagę, że istnieją dwie deklaracje PInvoke dla SendMessage. Jest to konieczne, ponieważ jeden używa `wParam` parametru do przekazania ciągu, a drugi używa go do przekazywania liczby całkowitej. Wymagana jest osobna Deklaracja dla każdego podpisu, aby upewnić się, że dane są organizowane prawidłowo.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementowanie komunikacji między kontrolką a stroną  
 Formant można manipulować przez wysłanie komunikatów systemu Windows. Kontrolka powiadamia użytkownika, gdy użytkownik współdziała z nim, wysyłając powiadomienia do okna hosta. [Formant ListBox w systemie Win32 w przykładzie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) zawiera interfejs użytkownika, który zawiera kilka przykładów tego, jak to działa:  
  
- Dołącz element do listy.  
  
- Usuń wybrany element z listy  
  
- Wyświetla tekst aktualnie zaznaczonego elementu.  
  
- Wyświetl liczbę elementów na liście.  
  
 Użytkownik może również wybrać element w polu listy, klikając go, podobnie jak w przypadku konwencjonalnej aplikacji Win32. Wyświetlane dane są aktualizowane za każdym razem, gdy użytkownik zmienia stan pola listy przez wybranie, dodanie lub dołączenie elementu.  
  
 Aby dołączyć elementy, Wyślij pole [ `LB_ADDSTRING` ](/windows/desktop/Controls/lb-addstring)listy do komunikatu. Aby usunąć elementy, Wyślij [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) , aby pobrać indeks bieżącego zaznaczenia, a następnie [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) usunąć element. Przykład wysyła [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)również i używa zwracanej wartości, aby zaktualizować ekran, który pokazuje liczbę elementów. Oba te wystąpienia [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) korzystają z jednej z deklaracji PInvoke omówionych w poprzedniej sekcji.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Gdy użytkownik wybierze element lub zmieni wybór, formant powiadamia okno hosta <xref:System.Windows.Interop.HwndHost.MessageHook> , wysyłając do niego [ `WM_COMMAND` komunikat](/windows/desktop/menurc/wm-command), który wywołuje zdarzenie dla strony. Program obsługi otrzymuje te same informacje, co procedura okna głównego okna hosta. Przekazuje także odwołanie do wartości `handled`logicznej. Ustawisz `handled` wartość `true` tak, aby wskazywała, że komunikat został obsłużony, a dalsze przetwarzanie nie jest potrzebne.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)jest wysyłany z różnych powodów, dlatego należy sprawdzić identyfikator powiadomienia, aby określić, czy jest to zdarzenie, które ma zostać obsłużone. Identyfikator jest zawarty w wysokim słowie `wParam` parametru. W przykładzie zastosowano operatory bitowe do wyodrębnienia identyfikatora. Jeśli użytkownik wprowadził lub zmienił wybór, identyfikator będzie [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange).  
  
 Gdy [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) jest odbierany, próbka Pobiera indeks wybranego elementu przez wysłanie [ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel)kontrolki komunikatu. Aby uzyskać tekst, należy najpierw utworzyć <xref:System.Text.StringBuilder>. Następnie wysyłasz kontrolkę [ `LB_GETTEXT` komunikat](/windows/desktop/Controls/lb-gettext). Przekaż pusty <xref:System.Text.StringBuilder> obiekt `wParam` jako parametr. Gdy [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) zwraca<xref:System.Text.StringBuilder> , będzie zawierać tekst wybranego elementu. To użycie [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) wymaga jeszcze innej deklaracji PInvoke.  
  
 Na koniec Ustaw `handled` `true` pozycję na, aby wskazać, że komunikat został obsłużony.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndHost>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Przewodnik: Moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
