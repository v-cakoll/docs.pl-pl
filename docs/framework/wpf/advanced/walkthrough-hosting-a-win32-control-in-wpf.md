---
title: Hostowanie formantu Win32 w wytęchnieniu WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 5185e60640c652b79bd105db54830ac3acc57129
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186740"
---
# <a name="walkthrough-host-a-win32-control-in-wpf"></a>Instruktaż: Hostowanie formantu Win32 w wywrzeć WPF
Windows Presentation Foundation (WPF) zapewnia bogate środowisko do tworzenia aplikacji. Jednak jeśli masz znaczne inwestycje w kodZie Win32, może być bardziej skuteczne, aby ponownie użyć co najmniej niektóre z tego kodu w aplikacji WPF, a nie przepisać go całkowicie. WPF WPF zapewnia prosty mechanizm hostowania okna Win32, na stronie WPF.  
  
 W tym temacie przeprowadzi Cię przez aplikację Hosting [Win32 ListBox Control w WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), który obsługuje kontrolkę pola listy Win32. Tę ogólną procedurę można rozszerzyć na hostowanie dowolnego okna Usługi Win32.  

<a name="requirements"></a>
## <a name="requirements"></a>Wymagania  
 W tym temacie przyjęto założenie, że podstawowe znajomości programowania interfejsu API WPF i systemu Windows. Aby zapoznać się z podstawowym wprowadzeniem do programowania WPF, zobacz [Wprowadzenie](../getting-started/index.md). Aby uzyskać wprowadzenie do programowania interfejsu API systemu Windows, zobacz dowolną z licznych książek na ten temat, w szczególności *programowanie systemu Windows* przez Charlesa Petzolda.  
  
 Ponieważ przykład, który towarzyszy ten temat jest zaimplementowana w języku C#, korzysta z usług wywoływania platformy (PInvoke) w celu uzyskania dostępu do interfejsu API systemu Windows. Niektóre znajomości PInvoke jest pomocne, ale nie istotne.  
  
> [!NOTE]
> Ten temat zawiera kilka przykładów kodu z skojarzonego przykładu. Jednak dla czytelności nie zawiera pełnego przykładowego kodu. Możesz uzyskać lub wyświetlić pełny kod z [hostingu kontrolki Listy Skrzynka Win32 w WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>Podstawowa procedura  
 W tej sekcji przedstawiono podstawową procedurę hostowania okna Win32 na stronie WPF. Pozostałe sekcje przechodzą przez szczegóły każdego kroku.  
  
 Podstawowa procedura hostingu to:  
  
1. Zaimplementuj stronę WPF, aby hostować okno. Jedną z technik <xref:System.Windows.Controls.Border> jest utworzenie elementu, aby zarezerwować sekcję strony dla hostowanego okna.  
  
2. Zaimplementuj klasę do <xref:System.Windows.Interop.HwndHost>obsługi formantu, który dziedziczy po .  
  
3. W tej klasie zastąpomij element członkowski <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>klasy .  
  
4. Utwórz hostowane okno jako element podrzędny okna zawierającego stronę WPF. Chociaż konwencjonalne programowanie WPF nie musi jawnie z niego korzystać, strona hostingu jest oknem z dojściem (HWND). Otrzymujesz stronę HWND `hwndParent` za pomocą <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> parametru metody. Hostowane okno powinno zostać utworzone jako dziecko tego HWND.  
  
5. Po utworzeniu okna hosta, zwraca hwnd hosta okna. Jeśli chcesz hostować jeden lub więcej formantów Win32, zazwyczaj tworzysz okno hosta jako element podrzędny HWND i tworzy elementy podrzędne formanty tego okna hosta. Zawijanie formantów w oknie hosta zapewnia prosty sposób dla strony WPF do odbierania powiadomień z formantów, który zajmuje się niektóre określone problemy Win32 z powiadomień w granicach HWND.  
  
6. Obsługa wybranych wiadomości wysłanych do okna hosta, takich jak powiadomienia z formantów podrzędnych. Istnieją dwa sposoby, aby to zrobić.  
  
    - Jeśli wolisz obsługiwać wiadomości w klasie hostingu, należy zastąpić <xref:System.Windows.Interop.HwndHost.WndProc%2A> metodę <xref:System.Windows.Interop.HwndHost> klasy.  
  
    - Jeśli wolisz mieć WPF obsługi wiadomości, <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.MessageHook> obsłużyć zdarzenie klasy w kodzie. To zdarzenie występuje dla każdej wiadomości odebranej przez okno hostowane. Jeśli wybierzesz tę opcję, nadal <xref:System.Windows.Interop.HwndHost.WndProc%2A>należy zastąpić , ale potrzebujesz tylko minimalnej implementacji.  
  
7. Zastądić <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> i <xref:System.Windows.Interop.HwndHost.WndProc%2A> metody . <xref:System.Windows.Interop.HwndHost> Należy zastąpić te metody, aby <xref:System.Windows.Interop.HwndHost> spełnić umowy, ale może być konieczne tylko zapewnienie minimalnej implementacji.  
  
8. W pliku związanym z kodem utwórz wystąpienie klasy hostingu <xref:System.Windows.Controls.Border> formantu i spraw, aby była ona elementem podrzędnym elementu przeznaczonego do hostowania okna.  
  
9. Komunikuj się z hostowanym oknem, wysyłając do niego wiadomości systemu Microsoft Windows i obsługując wiadomości z okien podrzędnych, takie jak powiadomienia wysyłane przez formanty.  
  
<a name="page_layout"></a>
## <a name="implement-the-page-layout"></a>Implementowanie układu strony  
 Układ strony WPF, która obsługuje Formant ListBox składa się z dwóch regionów. Po lewej stronie strony obsługuje kilka formantów WPF, które zapewniają, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] który pozwala manipulować Win32 kontroli. W prawym górnym rogu strony znajduje się kwadratowy region dla hostowanego formantu ListBox.  
  
 Kod do zaimplementowania tego układu jest dość prosty. Element główny jest <xref:System.Windows.Controls.DockPanel> elementem, który ma dwa elementy podrzędne. Pierwszy z <xref:System.Windows.Controls.Border> nich jest elementem, który obsługuje Formant ListBox. Zajmuje kwadrat 200x200 w prawym górnym rogu strony. Drugi jest <xref:System.Windows.Controls.StackPanel> elementem, który zawiera zestaw formanty WPF, które wyświetlają informacje i umożliwiają manipulowanie Formant ListBox przez ustawienie właściwości narażonych interoperacyjności. Dla każdego z elementów, <xref:System.Windows.Controls.StackPanel>które są elementami podrzędnymi , zobacz materiał referencyjny dla różnych elementów używanych do szczegółowych informacji na temat tego, co te elementy są lub co robią, są one wymienione w poniższym przykładowym kodzie, ale nie zostaną wyjaśnione tutaj (podstawowy model interoperacyjności nie wymaga żadnego z nich, są one dostarczane w celu dodania pewnej interaktywności do próbki).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementowanie klasy do hostowania kontrolki Microsoft Win32  
 Rdzeń tego przykładu jest klasą, która faktycznie obsługuje formant, ControlHost.cs. Dziedziczy po <xref:System.Windows.Interop.HwndHost>. Konstruktor przyjmuje dwa parametry, wysokość i szerokość, które <xref:System.Windows.Controls.Border> odpowiadają wysokości i szerokości elementu, który obsługuje Formant ListBox. Te wartości są używane później, aby upewnić <xref:System.Windows.Controls.Border> się, że rozmiar formantu pasuje do elementu.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Istnieje również zestaw stałych. Te stałe są w dużej mierze zaczerpnięte z Winuser.h i pozwalają na używanie konwencjonalnych nazw podczas wywoływania funkcji Win32.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Zastępowanie programu BuildWindowCore w celu utworzenia okna usługi Microsoft Win32  
 Należy zastąpić tę metodę, aby utworzyć okno Win32, które będzie hostowane przez stronę i nawiązać połączenie między oknem a stroną. Ponieważ ten przykład obejmuje hosting Formant ListBox, dwa okna są tworzone. Pierwszym z nich jest okno, które jest faktycznie hostowane przez stronę WPF. Formant ListBox jest tworzony jako podrzędny tego okna.  
  
 Powodem takiego podejścia jest uproszczenie procesu otrzymywania powiadomień od kontroli. Klasa <xref:System.Windows.Interop.HwndHost> umożliwia przetwarzanie wiadomości wysyłanych do okna, które jest hosting. Jeśli hostujesz formant Win32 bezpośrednio, otrzymasz wiadomości wysłane do wewnętrznej pętli komunikatów formantu. Można wyświetlić formant i wysłać go wiadomości, ale nie otrzymasz powiadomienia, które formant wysyła do okna nadrzędnego. Oznacza to, między innymi, że nie masz możliwości wykrycia, gdy użytkownik wchodzi w interakcję z formantem. Zamiast tego należy utworzyć okno hosta i uczynić formant podrzędnym tego okna. Dzięki temu można przetwarzać wiadomości dla okna hosta, w tym powiadomienia wysyłane do niego przez formant. Dla wygody, ponieważ okno hosta jest niewiele więcej niż proste otoki dla formantu, pakiet będzie określany jako Formant ListBox.  
  
<a name="create_the_window_and_listbox"></a>
#### <a name="create-the-host-window-and-listbox-control"></a>Tworzenie okna hosta i kontrolki ListBox  
 Za pomocą PInvoke można utworzyć okno hosta dla formantu, tworząc i rejestrując klasę okna i tak dalej. Jednak znacznie prostsze podejście jest utworzenie okna z wstępnie zdefiniowane "statyczne" klasa okna. Zapewnia to procedurę okna, której potrzebujesz, aby otrzymywać powiadomienia z formantu i wymaga minimalnego kodowania.  
  
 HWND formantu jest narażony za pośrednictwem właściwości tylko do odczytu, tak, że strona hosta można go używać do wysyłania wiadomości do formantu.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Formant ListBox jest tworzony jako podrzędny okna hosta. Wysokość i szerokość obu okien są ustawione na wartości przekazywane do konstruktora, omówione powyżej. Gwarantuje to, że rozmiar okna hosta i formantu jest identyczny z zarezerwowanym obszarem na stronie.  Po utworzeniu okien przykład zwraca <xref:System.Runtime.InteropServices.HandleRef> obiekt zawierający HWND okna hosta.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>
### <a name="implement-destroywindow-and-wndproc"></a>Implementowanie DestroyWindow i WndProc  
 Oprócz <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, należy również zastąpić <xref:System.Windows.Interop.HwndHost.WndProc%2A> i <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> metody . <xref:System.Windows.Interop.HwndHost> W tym przykładzie komunikaty dla formantu są obsługiwane przez <xref:System.Windows.Interop.HwndHost.MessageHook> program obsługi, w związku z tym implementacji <xref:System.Windows.Interop.HwndHost.WndProc%2A> i <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> jest minimalny. W przypadku <xref:System.Windows.Interop.HwndHost.WndProc%2A>, `handled` ustawić, aby `false` wskazać, że wiadomość nie została obsłużona i zwraca 0. Dla <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, po prostu zniszczyć okno.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>
## <a name="host-the-control-on-the-page"></a>Hostuj formant na stronie  
 Aby hostować formant na stronie, należy najpierw `ControlHost` utworzyć nowe wystąpienie klasy. Przekazać wysokość i szerokość elementu obramowania,`ControlHostElement`który `ControlHost` zawiera formant ( ) do konstruktora. Gwarantuje to, że listbox jest rozmiar poprawnie. Następnie hostujesz formant na stronie, `ControlHost` przypisując <xref:System.Windows.Controls.Decorator.Child%2A> obiekt do <xref:System.Windows.Controls.Border>właściwości hosta .  
  
 Przykład dołącza program obsługi <xref:System.Windows.Interop.HwndHost.MessageHook> do zdarzenia `ControlHost` do odbierania wiadomości z formantu. To zdarzenie jest wywoływane dla każdej wiadomości wysłanej do hostowanego okna. W takim przypadku są to komunikaty wysyłane do okna, który zawija rzeczywisty formant ListBox, w tym powiadomienia z formantu. Przykładowy wywołanie SendMessage, aby uzyskać informacje z formantu i zmodyfikować jego zawartość. Szczegóły dotyczące sposobu komunikowania się strony z formantem są omówione w następnej sekcji.  
  
> [!NOTE]
> Należy zauważyć, że istnieją dwie deklaracje PInvoke dla SendMessage. Jest to konieczne, ponieważ `wParam` jeden używa parametru do przekazania ciągu, a drugi używa go do przekazania liczby całkowitej. Potrzebujesz osobnej deklaracji dla każdego podpisu, aby upewnić się, że dane są poprawnie zorganizowane.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementowanie komunikacji między formantem a stroną  
 Możesz manipulować formantem, wysyłając go wiadomości systemu Windows. Formant powiadamia użytkownika, gdy użytkownik wchodzi w interakcję z nim, wysyłając powiadomienia do okna hosta. [Hosting kontrolki listy Win32 w WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) w próbce zawiera interfejs użytkownika, który zawiera kilka przykładów, jak to działa:  
  
- Dołącz element do listy.  
  
- Usuwanie zaznaczonego elementu z listy  
  
- Wyświetl tekst aktualnie zaznaczonego elementu.  
  
- Wyświetl liczbę elementów na liście.  
  
 Użytkownik może również wybrać element w polu listy, klikając na niego, tak jak w przypadku konwencjonalnej aplikacji Win32. Wyświetlane dane są aktualizowane za każdym razem, gdy użytkownik zmienia stan pola listy, zaznaczając, dodając lub dołączając element.  
  
 Aby dołączyć elementy, wyślij pole listy z [ `LB_ADDSTRING` wiadomością](/windows/desktop/Controls/lb-addstring). Aby usunąć elementy, wyślij, [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) aby uzyskać indeks [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) bieżącego zaznaczenia, a następnie usunąć element. Próbka wysyła [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)również i używa zwróconej wartości do aktualizacji wyświetlania, który pokazuje liczbę elementów. Oba te wystąpienia [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) użycia jednej z deklaracji PInvoke omówione w poprzedniej sekcji.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Gdy użytkownik wybierze element lub zmieni jego wybór, formant powiadamia okno hosta, wysyłając <xref:System.Windows.Interop.HwndHost.MessageHook> [ `WM_COMMAND` do](/windows/desktop/menurc/wm-command)niego wiadomość , która wywołuje zdarzenie dla strony. Program obsługi otrzymuje te same informacje, co procedura okna głównego okna hosta. Przekazuje również odwołanie do wartości logicznej, `handled`. `handled` Ustawiono, `true` aby wskazać, że masz obsługiwane wiadomości i nie dalsze przetwarzanie jest potrzebne.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)jest wysyłany z różnych powodów, więc należy sprawdzić identyfikator powiadomienia, aby ustalić, czy jest to zdarzenie, które chcesz obsłużyć. Identyfikator znajduje się w wysokim słowie parametru. `wParam` Próbka używa operatorów bitowych do wyodrębnienia identyfikatora. Jeśli użytkownik dokonał lub zmienił swój wybór, [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)identyfikatorem będzie .  
  
 Po [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) odebraniu próbka pobiera indeks wybranego elementu, wysyłając formantu [ `LB_GETCURSEL` komunikat](/windows/desktop/Controls/lb-getcursel). Aby uzyskać tekst, należy <xref:System.Text.StringBuilder>najpierw utworzyć plik . Następnie wysyłasz formancie [ `LB_GETTEXT` wiadomość](/windows/desktop/Controls/lb-gettext). Przekaż pusty <xref:System.Text.StringBuilder> obiekt `wParam` jako parametr. Po [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) zwróceniu <xref:System.Text.StringBuilder> będzie zawierać tekst zaznaczonego elementu. To użycie [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) wymaga jeszcze innej deklaracji PInvoke.  
  
 Na koniec, `handled` `true` aby wskazać, że wiadomość została obsłużona.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Interop.HwndHost>
- [WPF i Win32 — Współdziałanie](wpf-and-win32-interoperation.md)
- [Instruktaż: Moja pierwsza aplikacja komputerowa WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
