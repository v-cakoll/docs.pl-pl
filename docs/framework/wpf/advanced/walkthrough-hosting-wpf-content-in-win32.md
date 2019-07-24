---
title: 'Przewodnik: hostowanie zawartości WPF w Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 02f0831b46b8087c48b86e83a4b20f94bf3b79d0
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401582"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Przewodnik: hostowanie zawartości WPF w Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje bogate środowisko do tworzenia aplikacji. Jeśli jednak masz znaczną inwestycję w [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kod, bardziej efektywne może być dodanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji do aplikacji zamiast ponownego pisania oryginalnego kodu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia prosty mechanizm do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w oknie.  
  
 W tym samouczku opisano sposób pisania przykładowej aplikacji, która udostępnia [zawartość WPF w przykładowym oknie Win32](https://go.microsoft.com/fwlink/?LinkID=160004), [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] która hostuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartość w oknie. Ten przykład można rozwinąć, aby hostować [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dowolne okno. Ponieważ obejmuje mieszanie kodu zarządzanego i niezarządzanego, aplikacja jest zapisywana [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)].  

<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym samouczku założono podstawową znajomość obu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programowania. Aby zapoznać się z podstawowymi wprowadzeniem do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania, zobacz [wprowadzenie](../getting-started/index.md). Aby zapoznać się z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] wprowadzeniem do programowania, należy odwołać się do dowolnej z wielu książek w temacie, w szczególności do *programowania systemu Windows* przez Charles Petzold.  
  
 Ponieważ przykład, który obejmuje ten samouczek, jest zaimplementowany w [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]programie, w tym samouczku założono, że [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] korzystanie z programu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]do obsługi interfejsu API i zrozumienie programowania kodu zarządzanego. Znajomość programu [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] jest przydatna, ale nie jest istotna.  
  
> [!NOTE]
>  Ten samouczek zawiera wiele przykładów kodu ze skojarzonego przykładu. Jednak w celu zapewnienia czytelności nie obejmuje kompletny kod przykładowy. Aby uzyskać kompletny przykładowy kod, zobacz [hosting zawartości WPF w przykładzie okna Win32](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Podstawowa procedura  
 Ta sekcja zawiera opis podstawowej procedury używanej do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w oknie. Pozostałe sekcje zawierają szczegółowe informacje o każdym z kroków.  
  
 Kluczem do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w oknie jest <xref:System.Windows.Interop.HwndSource> Klasa. Ta klasa otacza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, umożliwiając umieszczenie go [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] w oknie jako podrzędnego. Poniższe podejście łączy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w pojedynczej aplikacji.  
  
1. Zaimplementuj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jako klasę zarządzaną.  
  
2. Implementowanie [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]aplikacji za pomocą programu. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Jeśli zaczynasz od istniejącej aplikacji i niezarządzanego [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] kodu, możesz zwykle włączyć ją do wywoływania kodu zarządzanego, zmieniając ustawienia projektu w celu `/clr` uwzględnienia flagi kompilatora.  
  
3. Ustaw model wątkowości na Apartament jednowątkowy (STA).  
  
4. Obsługuj powiadomienie [WM_CREATE](/windows/desktop/winmsg/wm-create)w procedurze okna i wykonaj następujące czynności:  
  
    1. Utwórz nowy <xref:System.Windows.Interop.HwndSource> obiekt z oknem nadrzędnym `parent` jako parametr.  
  
    2. Utwórz wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy zawartości.  
  
    3. Przypisz odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu Content <xref:System.Windows.Interop.HwndSource.RootVisual%2A> do właściwości <xref:System.Windows.Interop.HwndSource>.  
  
    4. Pobierz Właściwość HWND dla zawartości. <xref:System.Windows.Interop.HwndSource.Handle%2A> Właściwość<xref:System.Windows.Interop.HwndSource> obiektu zawiera uchwyt okna (HWND). Aby uzyskać Właściwość HWND, która może być używana w niezarządzanej części aplikacji, Rzutowanie `Handle.ToPointer()` na Właściwość HWND.  
  
5. Zaimplementuj zarządzaną klasę, która zawiera pole statyczne, aby pomieścić odwołanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do zawartości. Ta klasa pozwala uzyskać odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości z Twojego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu.  
  
6. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Przypisz zawartość do pola statycznego.  
  
7. Odbieraj powiadomienia z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości przez dołączenie programu obsługi do jednego lub większej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] liczby zdarzeń.  
  
8. Komunikuj się z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartością przy użyciu odwołania przechowywanego w polu statycznym, aby ustawić właściwości i tak dalej.  
  
> [!NOTE]
>  Możesz również użyć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zaimplementować zawartość. Konieczne będzie jednak skompilowanie go niezależnie [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] od [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programu i odwołania do aplikacji. Pozostała część procedury jest podobna do przedstawionej powyżej.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implementowanie aplikacji hosta
 W tej sekcji opisano, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostować zawartość w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji podstawowej. Sama zawartość jest implementowana w [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] postaci klasy zarządzanej. W większości przypadków jest to proste [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowanie. Kluczowe aspekty implementacji zawartości zostały omówione w temacie implementowanie [zawartości WPF](#implementing_the_wpf_page).

<a name="autoNestedSectionsOUTLINE1"></a>
- [Podstawowa aplikacja](#the_basic_application)

- [Hosting zawartości WPF](#hosting_the_wpf_page)

- [Przechowywanie odwołania do zawartości WPF](#holding_a_reference)

- [Komunikacja z zawartością WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Podstawowa aplikacja
 Punktem początkowym aplikacji hosta było utworzenie szablonu programu Visual Studio 2005.

1. Otwórz program Visual Studio 2005 i wybierz pozycję **Nowy projekt** z menu **plik** .

2. Z  listy [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] typów projektów wybierz opcję Win32. Jeśli językiem domyślnym nie [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)]jest, te typy projektów są dostępne w **innych językach**.

3. Wybierz szablon **projektu Win32** , przypisz nazwę do projektu, a następnie kliknij przycisk **OK** , aby uruchomić **Kreatora aplikacji Win32**.

4. Zaakceptuj ustawienia domyślne kreatora i kliknij przycisk **Zakończ** , aby uruchomić projekt.

 Szablon tworzy podstawową [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikację, w tym:

- Punkt wejścia dla aplikacji.

- Okno z skojarzoną procedurą okna (WndProc).

- Menu z nagłówkami **plików** i **pomocy** . Menu **plik** zawiera element **wyjścia** , który zamknie aplikację. Menu **Pomoc** zawiera element **o** elemencie, który powoduje uruchomienie prostego okna dialogowego.

 Przed rozpoczęciem pisania kodu w celu hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości należy wprowadzić dwie zmiany w szablonie podstawowym.

 Pierwszym jest skompilowanie projektu jako kodu zarządzanego. Domyślnie projekt kompiluje jako kod niezarządzany. Jednak ze względu na to, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest zaimplementowany w kodzie zarządzanym, projekt musi być odpowiednio skompilowany.

1. Kliknij prawym przyciskiem myszy nazwę projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości** z menu kontekstowego, aby uruchomić okno dialogowe **strony właściwości** .

2. W okienku po lewej stronie wybierz pozycję **Właściwości konfiguracji** w widoku drzewa.

3. Wybierz opcję Obsługa **środowiska uruchomieniowego** CLR z listy **wartości domyślne projektu** w okienku po prawej stronie.

4. W polu listy rozwijanej wybierz opcję **Obsługa środowiska uruchomieniowego CLR (/CLR)** .

> [!NOTE]
>  Ta flaga kompilatora umożliwia korzystanie z kodu zarządzanego w aplikacji, ale kod niezarządzany jeszcze nie zostanie skompilowany.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]używa modelu wątku jednowątkowego Apartment (STA). Aby zapewnić prawidłowe działanie z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodem zawartości, należy ustawić model wątkowości aplikacji na sta przez zastosowanie atrybutu do punktu wejścia.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hosting zawartości WPF
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawartość jest prostą aplikacją wpisu adresu. Składa się z <xref:System.Windows.Controls.TextBox> kilku kontrolek do przyłączenia nazwy użytkownika, adresu i tak dalej. Istnieją również dwie <xref:System.Windows.Controls.Button> kontrolki, **OK** i **Anuluj**. Gdy użytkownik kliknie przycisk **OK**, program obsługi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń przycisku zbiera dane z <xref:System.Windows.Controls.TextBox> formantów, przypisze je do odpowiednich właściwości i wywołuje zdarzenie `OnButtonClicked`niestandardowe. Gdy użytkownik kliknie **przycisk Anuluj**, program obsługi po prostu `OnButtonClicked`wygeneruje. Obiekt argumentu zdarzenia dla `OnButtonClicked` zawiera pole logiczne, które wskazuje, który przycisk został kliknięty.

 Kod obsługujący [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jest implementowany w programie obsługi powiadomienia [WM_CREATE](/windows/desktop/winmsg/wm-create) w oknie hosta.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 Metoda pobiera informacje o rozmiarze i pozycji oraz uchwyt okna nadrzędnego i zwraca uchwyt okna hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. `GetHwnd`

> [!NOTE]
>  Nie można użyć `#using` dyrektywy `System::Windows::Interop` dla przestrzeni nazw. Spowoduje to utworzenie kolizji nazw między <xref:System.Windows.Interop.MSG> strukturą w tej przestrzeni nazw a strukturą komunikatów zadeklarowaną w Winuser. h. Zamiast tego należy użyć w pełni kwalifikowanych nazw, aby uzyskać dostęp do zawartości tej przestrzeni nazw.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawartości nie można hostować bezpośrednio w oknie aplikacji. Zamiast tego należy najpierw utworzyć <xref:System.Windows.Interop.HwndSource> obiekt, który będzie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawijał zawartość. Ten obiekt jest w zasadzie oknem, który jest przeznaczony do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. <xref:System.Windows.Interop.HwndSource> Obiekt można hostować w oknie nadrzędnym, tworząc go jako element podrzędny [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, które jest częścią aplikacji. Parametry konstruktora zawierają wiele tych samych informacji, które można przekazać do okna, podczas [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] tworzenia okna podrzędnego. <xref:System.Windows.Interop.HwndSource>

 Następnie utworzysz wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu Content. W takim przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jest zaimplementowana jako oddzielna Klasa `WPFPage`, przy [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]użyciu. Możesz również zaimplementować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. W tym celu należy jednak skonfigurować oddzielny projekt i skompilować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]jako. Można dodać odwołanie [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] do projektu i użyć tego odwołania, aby utworzyć wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawartość w oknie podrzędnym można wyświetlić, przypisując odwołanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do zawartości <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwości <xref:System.Windows.Interop.HwndSource>.

 Następny wiersz kodu dołącza procedurę obsługi `WPFButtonClicked`zdarzeń [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do zdarzenia zawartości `OnButtonClicked` . Ta procedura obsługi jest wywoływana, gdy użytkownik kliknie przycisk **OK** lub **Anuluj** . Zobacz [zawartość communicating_with_the_WPF](#communicating_with_the_page) , aby poznać dalsze omówienie tego programu obsługi zdarzeń.

 Ostatni wiersz podanego kodu zwraca uchwyt okna (HWND), który jest skojarzony z <xref:System.Windows.Interop.HwndSource> obiektem. Tego uchwytu można użyć w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodzie do wysyłania komunikatów do hostowanego okna, chociaż nie jest to konieczne. <xref:System.Windows.Interop.HwndSource> Obiekt zgłasza zdarzenie za każdym razem, gdy odbierze komunikat. Aby przetworzyć komunikaty, należy <xref:System.Windows.Interop.HwndSource.AddHook%2A> wywołać metodę w celu dołączenia obsługi komunikatów, a następnie przetworzyć komunikaty w ramach tej procedury obsługi.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Przechowywanie odwołania do zawartości WPF
 W przypadku wielu aplikacji chcesz później komunikować się z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartością. Na przykład możesz chcieć zmodyfikować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zawartości lub <xref:System.Windows.Interop.HwndSource> być może obiekt hostuje inną [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość. W tym celu należy odwołać się do <xref:System.Windows.Interop.HwndSource> obiektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lub zawartości. Obiekt i jego skojarzona [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość pozostają w pamięci do momentu zniszczenia uchwytu okna. <xref:System.Windows.Interop.HwndSource> Jednak zmienna przypisana do <xref:System.Windows.Interop.HwndSource> obiektu wyjdzie poza zakres od razu po powrocie z procedury okna. Niestandardowy sposób obsługi tego problemu w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacjach polega na użyciu zmiennej statycznej lub globalnej. Niestety, nie można przypisać obiektu zarządzanego do tych typów zmiennych. Dojście do okna skojarzone z <xref:System.Windows.Interop.HwndSource> obiektem można przypisać do zmiennej globalnej lub statycznej, ale nie zapewnia ona dostępu do samego obiektu.

 Najprostszym rozwiązaniem tego problemu jest zaimplementowanie zarządzanej klasy, która zawiera zestaw pól statycznych do przechowywania odwołań do wszystkich obiektów zarządzanych, do których wymagany jest dostęp. Przykład używa `WPFPageHost` klasy do przechowywania odwołania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do zawartości oraz początkowych wartości liczby właściwości, które mogą zostać zmienione później przez użytkownika. Jest to zdefiniowane w nagłówku.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 Ta ostatnia część `GetHwnd` funkcji przypisuje wartości do tych pól do późniejszego użycia, `myPage` gdy nadal znajduje się w zakresie.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Komunikacja z zawartością WPF
 Istnieją dwa typy komunikacji z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartością. Aplikacja otrzymuje informacje z zawartości, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gdy użytkownik kliknie przyciski **OK** lub **Anuluj** . Aplikacja ma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] również możliwość zmiany różnych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zawartości, takich jak kolor tła lub domyślny rozmiar czcionki.

 Jak wspomniano powyżej, gdy użytkownik kliknie dowolny przycisk [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , zawartość `OnButtonClicked` zgłasza zdarzenie. Aplikacja dołącza procedurę obsługi do tego zdarzenia, aby otrzymywać te powiadomienia. Jeśli kliknięto przycisk **OK** , program obsługi pobiera informacje o użytkowniku z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i wyświetla je w zestawie formantów statycznych.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Program obsługi odbiera obiekt argumentu zdarzenia niestandardowego z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `MyPageEventArgs`zawartości. `IsOK` Właściwość obiektu jest ustawiona na `true` , gdy kliknięto przycisk **OK** , i `false` Jeśli kliknięto przycisk **Anuluj** .

 Jeśli kliknięto przycisk **OK** , program obsługi pobiera odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości z klasy kontenera. Następnie zbiera informacje o użytkowniku, które są przechowywane przez skojarzone [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zawartości i używa formantów statycznych do wyświetlania informacji w oknie nadrzędnym. Ponieważ dane [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartości są w postaci ciągu zarządzanego, musi być organizowane do użycia przez formant. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Jeśli kliknięto przycisk **Anuluj** , program obsługi wyczyści dane z kontrolek statycznych.

 Aplikacja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zawiera zestaw przycisków radiowych, które pozwalają użytkownikowi modyfikować kolor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tła zawartości i kilka właściwości związanych z czcionką. Poniższy przykład jest fragmentem z procedury okna aplikacji (WndProc) i obsługą komunikatów, która ustawia różne właściwości różnych komunikatów, w tym kolor tła. Inne są podobne i nie są wyświetlane. Zobacz kompletny przykład dla szczegółów i kontekstu.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Aby ustawić kolor tła, Pobierz odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości (`hostedPage`) z `WPFPageHost` i ustaw właściwość kolor tła na odpowiedni kolor. W przykładzie są stosowane trzy opcje koloru: oryginalny kolor, jasnozielony lub lekki. Oryginalny kolor tła jest przechowywany jako pole statyczne w `WPFPageHost` klasie. Aby ustawić pozostałe dwa, należy utworzyć nowy <xref:System.Windows.Media.SolidColorBrush> obiekt i przekazać konstruktorowi wartość statyczne kolory <xref:System.Windows.Media.Colors> z obiektu.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementowanie strony WPF
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawartość można hostować i korzystać z niej bez znajomości rzeczywistej implementacji. Jeśli zawartość została spakowana w osobnym [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], mogła zostać skompilowana w dowolnym języku środowiska uruchomieniowego języka wspólnego (CLR). [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Poniżej znajduje się krótki przewodnik [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] dotyczący implementacji, który jest używany w przykładzie. Ta sekcja zawiera następujące podsekcje.

<a name="autoNestedSectionsOUTLINE2"></a>
- [Układ](#page_layout)

- [Zwracanie danych do okna hosta](#returning_data_to_window)

- [Ustawianie właściwości WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Układ
 Elementy w zawartości składają się z pięciu <xref:System.Windows.Controls.TextBox> kontrolek ze skojarzonymi <xref:System.Windows.Controls.Label> kontrolkami: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Nazwa, adres, miasto, stan i zip. Istnieją również dwie <xref:System.Windows.Controls.Button> kontrolki, **OK** i **Anuluj**

 Zawartość jest zaimplementowana `WPFPage` w klasie. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Układ jest obsługiwany przy użyciu <xref:System.Windows.Controls.Grid> elementu układu. Klasa dziedziczy od <xref:System.Windows.Controls.Grid>, co efektywnie staje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] się elementem głównym zawartości.

 Konstruktor zawartości przyjmuje wymaganą szerokość i wysokość i <xref:System.Windows.Controls.Grid> odpowiednio zmienia rozmiar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Następnie definiuje podstawowy układ przez utworzenie zestawu <xref:System.Windows.Controls.ColumnDefinition> i <xref:System.Windows.Controls.RowDefinition> obiektów oraz dodanie ich do <xref:System.Windows.Controls.Grid> obiektu podstawowego <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> i <xref:System.Windows.Controls.Grid.RowDefinitions%2A> kolekcji. Definiuje on siatkę pięciu wierszy i siedmiu kolumn, z wymiarami określonymi przez zawartość komórek.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Następnie Konstruktor dodaje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy <xref:System.Windows.Controls.Grid>do. Pierwszy element jest tekstem tytułu, który <xref:System.Windows.Controls.Label> jest formantem, który jest wyśrodkowany w pierwszym wierszu siatki.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Następny wiersz zawiera kontrolkę nazwa <xref:System.Windows.Controls.Label> i skojarzoną <xref:System.Windows.Controls.TextBox> z nią kontrolkę. Ponieważ ten sam kod jest używany dla każdej pary Etykieta/pole tekstowe, jest umieszczany w parze metod prywatnych i używany dla wszystkich pięciu par Etykieta/pole tekstowe. Metody tworzą odpowiednią kontrolkę i wywołują <xref:System.Windows.Controls.Grid> klasy static <xref:System.Windows.Controls.Grid.SetColumn%2A> i <xref:System.Windows.Controls.Grid.SetRow%2A> Methods, aby umieścić kontrolki w odpowiedniej komórce. Po utworzeniu kontrolki, przykład wywołuje <xref:System.Windows.Controls.UIElementCollection.Add%2A> metodę <xref:System.Windows.Controls.Panel.Children%2A> właściwości, <xref:System.Windows.Controls.Grid> aby dodać formant do siatki. Kod, aby dodać pozostałe pary Etykieta/pole tekstowe jest podobny. Zobacz przykładowy kod, aby uzyskać szczegółowe informacje.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Implementacja dwóch metod jest następująca:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Na koniec przykład dodaje przyciski **OK** i **Anuluj** i dołącza procedurę obsługi zdarzeń do swoich <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Zwracanie danych do okna hosta
 Po kliknięciu dowolnego przycisku jego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie jest wywoływane. Okno hosta może po prostu dołączyć programy obsługi do tych zdarzeń i pobrać dane bezpośrednio z <xref:System.Windows.Controls.TextBox> kontrolek. W przykładzie jest stosowane nieco mniej bezpośrednie podejście. Obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> `OnButtonClicked`ona zawartość, a następnie wywołuje niestandardowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenie, aby powiadomić zawartość. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dzięki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temu zawartość może zostać zweryfikowana przed powiadomieniem hosta. Program obsługi pobiera tekst z <xref:System.Windows.Controls.TextBox> formantów i przypisuje go do właściwości publicznych, z którego host może pobrać informacje.

 Deklaracja zdarzenia w WPFPage. h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 Program <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń w WPFPage. cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Ustawianie właściwości WPF
 Host zezwala użytkownikowi na zmianę kilku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zawartości. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Po stronie jest po prostu kwestią zmiany właściwości. Implementacja w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasie zawartości jest nieco bardziej skomplikowana, ponieważ nie ma żadnej pojedynczej właściwości globalnej, która kontroluje czcionki dla wszystkich kontrolek. Zamiast tego odpowiednia właściwość dla każdej kontrolki jest zmieniana w obszarze właściwości metody dostępu. Poniższy przykład pokazuje kod `DefaultFontFamily` właściwości. Ustawienie właściwości wywołuje prywatną metodę, która z kolei ustawia <xref:System.Windows.Controls.Control.FontFamily%2A> właściwości dla różnych kontrolek.

 Z WPFPage. h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 Z WPFPage. cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndSource>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
