---
title: Host zawartości WPF w win32
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 8a5d556abf49c9c1f49e7853e752ebc5248d1101
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186066"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Wskazówki: Hosting zawartości WPF w Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia bogate środowisko do tworzenia aplikacji. Jednak jeśli masz znaczne inwestycje w kod Win32, może [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] być bardziej skuteczne, aby dodać funkcje do aplikacji, a nie przepisywanie oryginalnego kodu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia prosty mechanizm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostowania zawartości w oknie Win32.  
  
 W tym samouczku opisano sposób pisania przykładowej aplikacji [Hosting zawartości WPF w przykładzie okna Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage), która obsługuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość w oknie Win32. Można rozszerzyć ten przykład do obsługi dowolnego okna Win32. Ponieważ obejmuje mieszanie kodu zarządzanego i niezarządzanego, aplikacja jest zapisywana w języku C++/CLI.  

<a name="requirements"></a>
## <a name="requirements"></a>Wymagania  
 W tym samouczku przyjęto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] założenie, że należy zapoznać się z programowaniem obu i win32. Aby zapoznać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] się z podstawowym wprowadzeniem do programowania, zobacz [Wprowadzenie](../getting-started/index.md). Aby zapoznać się z wprowadzeniem do programowania Win32, należy odwołać się do dowolnej z licznych książek na ten temat, w szczególności *programowania systemu Windows* Przez Charles Petzold.  
  
 Ponieważ przykład, który towarzyszy ten samouczek jest zaimplementowany w języku C++/CLI, ten samouczek zakłada znajomość użycia języka C++ do programowania interfejsu API systemu Windows oraz zrozumienie programowania kodu zarządzanego. Znajomość języka C++/CLI jest pomocna, ale nie jest niezbędna.  
  
> [!NOTE]
> Ten samouczek zawiera kilka przykładów kodu z skojarzonego przykładu. Jednak dla czytelności nie zawiera pełnego przykładowego kodu. Aby uzyskać pełny przykładowy kod, zobacz [Hosting zawartości WPF w przykładzie okna Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage).  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>Podstawowa procedura  
 W tej sekcji opisano podstawową [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procedurę używaną do hosta zawartości w oknie Win32. Pozostałe sekcje wyjaśniają szczegóły każdego kroku.  
  
 Kluczem do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostowania zawartości w oknie <xref:System.Windows.Interop.HwndSource> Win32 jest klasa. Ta klasa zawija [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość w oknie Win32, dzięki [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] czemu można włączyć do okna jako dziecko. Następujące podejście łączy Win32 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i w jednej aplikacji.  
  
1. Zaimplementuj zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako klasę zarządzaną.  
  
2. Zaimplementuj aplikację systemu Windows z c++/cli. Jeśli zaczynasz z istniejącą aplikacją i niezarządzanym kodem C++, zazwyczaj możesz włączyć `/clr` go do wywołania kodu zarządzanego, zmieniając ustawienia projektu, aby uwzględnić flagę kompilatora.  
  
3. Ustaw model gwintowania na jednowątkowy (STA).  
  
4. Obsłuż [powiadomienie WM_CREATE](/windows/desktop/winmsg/wm-create)w procedurze okna i wykonaj następujące czynności:  
  
    1. Utwórz <xref:System.Windows.Interop.HwndSource> nowy obiekt z oknem nadrzędnym jako jego parametrem. `parent`  
  
    2. Utwórz wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy zawartości.  
  
    3. Przypisz odwołanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do obiektu <xref:System.Windows.Interop.HwndSource.RootVisual%2A> zawartości do <xref:System.Windows.Interop.HwndSource>właściwości pliku .  
  
    4. Pobierz HWND dla zawartości. Właściwość <xref:System.Windows.Interop.HwndSource.Handle%2A> <xref:System.Windows.Interop.HwndSource> obiektu zawiera uchwyt okna (HWND). Aby uzyskać HWND, które można użyć w niezarządzanej `Handle.ToPointer()` części aplikacji, rzutowane do HWND.  
  
5. Zaimplementuj klasę zarządzaną zawierającą pole [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] statyczne do przechowywania odwołania do zawartości. Ta klasa umożliwia uzyskanie odwołania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do zawartości z kodu Win32.  
  
6. Przypisz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość do pola statycznego.  
  
7. Odbieranie powiadomień [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z zawartości przez dołączenie programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługi do jednego lub więcej zdarzeń.  
  
8. Komunikuj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] się z zawartością za pomocą odwołania przechowywanego w polu statycznym w celu ustawienia właściwości itd.  
  
> [!NOTE]
> Można również [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] użyć do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zaimplementowania zawartości. Jednak trzeba będzie skompilować go oddzielnie jako biblioteki łącza dynamicznego (DLL) i odwołanie do biblioteki DLL z aplikacji Win32. Pozostała część procedury jest podobna do przedstawionej powyżej.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implementowanie aplikacji hosta
 W tej sekcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] opisano sposób hosta zawartości w podstawowej aplikacji Win32. Sama zawartość jest implementowana w języku C++/CLI jako klasa zarządzana. W przeważającej części jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to proste programowanie. Kluczowe aspekty implementacji zawartości są omawiane w [implementacji zawartości WPF](#implementing_the_wpf_page).

- [Podstawowa aplikacja](#the_basic_application)

- [Hostowanie zawartości WPF](#hosting_the_wpf_page)

- [Posiadanie odwołania do zawartości WPF](#holding_a_reference)

- [Komunikowanie się z zawartością WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Podstawowa aplikacja
 Punktem wyjścia dla aplikacji hosta było utworzenie szablonu programu Visual Studio 2005.

1. Otwórz program Visual Studio 2005 i wybierz **polecenie Nowy projekt** z menu **Plik.**

2. Wybierz **win32** z listy typów projektów visual c++. Jeśli domyślnym językiem nie jest język C++, te typy projektów znajdziesz w obszarze **Inne języki**.

3. Wybierz szablon **projektu Win32,** przypisz nazwę do projektu i kliknij przycisk **OK,** aby uruchomić **Kreatora aplikacji Win32**.

4. Zaakceptuj ustawienia domyślne kreatora i kliknij przycisk **Zakończ,** aby rozpocząć projekt.

 Szablon tworzy podstawową aplikację Win32, w tym:

- Punkt wejścia dla aplikacji.

- Okno z skojarzoną procedurą okna (WndProc).

- Menu z nagłówkami **Plik** i **Pomoc.** **Menu Plik** zawiera element **Exit,** który zamyka aplikację. W menu **Pomoc** jest element **Informacje,** który uruchamia proste okno dialogowe.

 Przed rozpoczęciem pisania kodu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do hosta zawartości, należy wprowadzić dwie modyfikacje szablonu podstawowego.

 Pierwszym z nich jest skompilowanie projektu jako kodu zarządzanego. Domyślnie projekt kompiluje jako kod niezarządzany. Jednak ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest zaimplementowana w kodzie zarządzanym, projekt musi zostać odpowiednio skompilowany.

1. Kliknij prawym przyciskiem myszy nazwę projektu w **Eksploratorze rozwiązań** i wybierz **polecenie Właściwości** z menu kontekstowego, aby uruchomić okno dialogowe **Strony właściwości.**

2. Wybierz **polecenie Właściwości konfiguracji** z widoku drzewa w lewym okienku.

3. Wybierz **pozycję Obsługa środowiska uruchomieniowego języka wspólnego** z listy **Domyślne projektu** w prawym okienku.

4. Z listy rozwijanej wybierz **opcję Obsługa środowiska uruchomieniowego języka wspólnego (/clr).**

> [!NOTE]
> Ta flaga kompilatora umożliwia użycie kodu zarządzanego w aplikacji, ale kod niezarządzane będzie nadal kompilować jak poprzednio.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wykorzystuje model gwintowania mieszkania jednowątkowego (STA). Aby poprawnie pracować z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodem zawartości, należy ustawić model wątków aplikacji na STA, stosując atrybut do punktu wejścia.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hostowanie zawartości WPF
 Zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest prostą aplikacją do wprowadzania adresów. Składa się <xref:System.Windows.Controls.TextBox> z kilku formantów do podjęcia nazwy użytkownika, adres i tak dalej. Istnieją również <xref:System.Windows.Controls.Button> dwa formanty, **OK** i **Anuluj**. Gdy użytkownik kliknie **przycisk OK,** program obsługi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń <xref:System.Windows.Controls.TextBox> przycisku zbiera dane z formantów, przypisuje je `OnButtonClicked`do odpowiednich właściwości i wywołuje zdarzenie niestandardowe, . Gdy użytkownik kliknie **przycisk Anuluj,** program obsługi po prostu podnosi `OnButtonClicked`. Obiekt argumentu `OnButtonClicked` zdarzenia zawiera pole logiczne wskazujące, który przycisk został kliknięty.

 Kod do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości jest implementowany w programie obsługi dla powiadomienia [WM_CREATE](/windows/desktop/winmsg/wm-create) w oknie hosta.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 Metoda `GetHwnd` przyjmuje informacje o rozmiarze i położeniu oraz dojście [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna nadrzędnego i zwraca dojście okna hostowanej zawartości.

> [!NOTE]
> Nie można `#using` użyć dyrektywy `System::Windows::Interop` dla obszaru nazw. W ten sposób tworzy <xref:System.Windows.Interop.MSG> kolizji nazw między strukturą w tym obszarze nazw i MSG struktury zadeklarowane w winuser.h. Zamiast tego należy użyć w pełni kwalifikowanych nazw, aby uzyskać dostęp do zawartości tego obszaru nazw.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Nie można [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostować zawartości bezpośrednio w oknie aplikacji. Zamiast tego najpierw należy <xref:System.Windows.Interop.HwndSource> utworzyć obiekt, aby zawinąć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość. Ten obiekt jest w zasadzie okno, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] które jest przeznaczone do hosta zawartości. Obiekt jest <xref:System.Windows.Interop.HwndSource> hostować w oknie nadrzędnym, tworząc go jako element podrzędny okna Win32, które jest częścią aplikacji. Parametry <xref:System.Windows.Interop.HwndSource> konstruktora zawierają wiele tych samych informacji, które można przekazać do CreateWindow podczas tworzenia okna podrzędnego Win32.

 Następnie należy utworzyć wystąpienie obiektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. W takim przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jest implementowana jako `WPFPage`oddzielna klasa, używając C++/CLI. Można również zaimplementować zawartość za [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pomocą pliku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Jednak w tym celu należy skonfigurować oddzielny projekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i utworzyć zawartość jako biblioteki DLL. Można dodać odwołanie do tej biblioteki DLL do projektu i użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tego odwołania do utworzenia wystąpienia zawartości.

 Zawartość w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oknie podrzędnym jest wyświetlana przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przypisanie <xref:System.Windows.Interop.HwndSource.RootVisual%2A> odwołania <xref:System.Windows.Interop.HwndSource>do zawartości do właściwości pliku .

 Następny wiersz kodu dołącza program obsługi `WPFButtonClicked`zdarzeń, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `OnButtonClicked` do zdarzenia zawartości. Ten program obsługi jest wywoływany, gdy użytkownik kliknie przycisk **OK** lub **Anuluj.** Zobacz [communicating_with_the_WPF zawartości](#communicating_with_the_page) do dalszej dyskusji na temat tego programu obsługi zdarzeń.

 Końcowy wiersz pokazanego kodu zwraca uchwyt okna (HWND), <xref:System.Windows.Interop.HwndSource> który jest skojarzony z obiektem. Ten uchwyt z kodu Win32 służy do wysyłania wiadomości do okna hostowanego, chociaż przykład nie robi tego. Obiekt <xref:System.Windows.Interop.HwndSource> wywołuje zdarzenie za każdym razem, gdy odbiera komunikat. Aby przetworzyć wiadomości, wywołaj <xref:System.Windows.Interop.HwndSource.AddHook%2A> metodę, aby dołączyć program obsługi wiadomości, a następnie przetworzyć wiadomości w tym programie obsługi.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Posiadanie odwołania do zawartości WPF
 W przypadku wielu aplikacji należy później [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komunikować się z zawartością. Na przykład można zmodyfikować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zawartości lub być <xref:System.Windows.Interop.HwndSource> może host [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu innej zawartości. Aby to zrobić, należy odwołanie <xref:System.Windows.Interop.HwndSource> do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu lub zawartości. Obiekt <xref:System.Windows.Interop.HwndSource> i skojarzona [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z nim zawartość pozostają w pamięci do czasu zniszczenia uchwytu okna. Jednak zmienna przypisana <xref:System.Windows.Interop.HwndSource> do obiektu wyjdzie poza zakres, gdy tylko powrócisz z procedury okna. Zwyczajowym sposobem obsługi tego problemu za pomocą aplikacji Win32 jest użycie zmiennej statycznej lub globalnej. Niestety nie można przypisać obiektu zarządzanego do tych typów zmiennych. Do dojścia okna <xref:System.Windows.Interop.HwndSource> skojarzonego z obiektem można przypisać do zmiennej globalnej lub statycznej, ale nie zapewniają dostępu do samego obiektu.

 Najprostszym rozwiązaniem tego problemu jest zaimplementowanie klasy zarządzanej, która zawiera zestaw pól statycznych do przechowywania odwołań do wszystkich obiektów zarządzanych, które są potrzebne do dostępu. Przykład używa `WPFPageHost` klasy do przechowywania odwołania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do zawartości, a także wartości początkowe wielu jego właściwości, które mogą zostać zmienione później przez użytkownika. Jest to zdefiniowane w nagłówku.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 Druga część `GetHwnd` funkcji przypisuje wartości do tych pól `myPage` do późniejszego użycia, podczas gdy jest nadal w zakresie.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Komunikowanie się z zawartością WPF
 Istnieją dwa rodzaje komunikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z zawartością. Aplikacja otrzymuje informacje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z zawartości, gdy użytkownik kliknie przyciski **OK** lub **Anuluj.** Aplikacja ma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] również, który pozwala użytkownikowi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na zmianę różnych właściwości zawartości, takich jak kolor tła lub domyślny rozmiar czcionki.

 Jak wspomniano powyżej, gdy użytkownik kliknie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] albo przycisk `OnButtonClicked` zawartość wywołuje zdarzenie. Aplikacja dołącza program obsługi do tego zdarzenia, aby otrzymywać te powiadomienia. Jeśli przycisk **OK** został kliknięty, program obsługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pobiera informacje o użytkowniku z zawartości i wyświetla go w zestawie formantów statycznych.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Program obsługi odbiera obiekt niestandardowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] argumentu zdarzenia z zawartości. `MyPageEventArgs` Właściwość obiektu `IsOK` jest ustawiona `true` na to, czy kliknięno przycisk **OK** i `false` jeśli kliknięno przycisk **Anuluj.**

 Jeśli przycisk **OK** został kliknięty, program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługi pobiera odwołanie do zawartości z klasy kontenera. Następnie zbiera informacje o użytkowniku, który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest przechowywany przez skojarzone właściwości zawartości i używa statycznych formantów do wyświetlania informacji w oknie nadrzędnym. Ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dane zawartości jest w postaci ciągu zarządzanego, musi być organizowane do użycia przez kontrolkę Win32. Jeśli przycisk **Anuluj** został kliknięty, program obsługi czyści dane z formantów statycznych.

 Aplikacja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] udostępnia zestaw przycisków radiowych, które pozwalają użytkownikowi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na modyfikowanie koloru tła zawartości i kilka właściwości związanych z czcionką. Poniższy przykład jest fragment procedury okna aplikacji (WndProc) i jego obsługi komunikatów, który ustawia różne właściwości na różne komunikaty, w tym kolor tła. Pozostałe są podobne i nie są wyświetlane. Zobacz pełną próbkę, aby uzyskać szczegółowe informacje i kontekst.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Aby ustawić kolor tła, uzyskaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odwołanie`hostedPage`do `WPFPageHost` zawartości ( ) i ustaw właściwość koloru tła na odpowiedni kolor. W próbce użyto trzech opcji kolorystycznych: oryginalnego koloru, jasnozielonego lub lekkiego łososia. Oryginalny kolor tła jest przechowywany jako `WPFPageHost` pole statyczne w klasie. Aby ustawić pozostałe dwa, należy <xref:System.Windows.Media.SolidColorBrush> utworzyć nowy obiekt i przekazać konstruktora wartość kolorów statycznych z <xref:System.Windows.Media.Colors> obiektu.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementowanie strony WPF
 Zawartość można hostować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i używać bez znajomości rzeczywistej implementacji. Jeśli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość została spakowana w oddzielnej biblioteki DLL, może być zbudowany w dowolnym języku środowiska wykonawczego języka wspólnego (CLR) języka. Poniżej znajduje się krótki instruktaż implementacji C++/CLI, który jest używany w przykładzie. Ta sekcja zawiera następujące podsekcje.

- [Układ](#page_layout)

- [Zwracanie danych do okna hosta](#returning_data_to_window)

- [Ustawianie właściwości WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Układ
 Elementy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości składają <xref:System.Windows.Controls.TextBox> się z pięciu <xref:System.Windows.Controls.Label> formantów, z skojarzonymi formantami: Nazwa, Adres, Miasto, Stan i Zip. Istnieją również <xref:System.Windows.Controls.Button> dwa kontrolki, **OK** i **Anuluj**

 Zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest implementowana `WPFPage` w klasie. Układ jest obsługiwany <xref:System.Windows.Controls.Grid> z elementem układu. Klasa dziedziczy <xref:System.Windows.Controls.Grid>z , co [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] skutecznie sprawia, że element główny zawartości.

 Konstruktor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości przyjmuje wymaganą szerokość i wysokość <xref:System.Windows.Controls.Grid> i odpowiednio rozmiary. Następnie definiuje podstawowy układ, tworząc zestaw <xref:System.Windows.Controls.ColumnDefinition> i <xref:System.Windows.Controls.RowDefinition> obiektów i dodając <xref:System.Windows.Controls.Grid> je <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> <xref:System.Windows.Controls.Grid.RowDefinitions%2A> do bazy obiektu i kolekcji, odpowiednio. Definiuje siatkę pięciu wierszy i siedmiu kolumn, z wymiarami określonymi przez zawartość komórek.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Następnie konstruktor dodaje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy <xref:System.Windows.Controls.Grid>do . Pierwszy element jest tekst tytułowy, <xref:System.Windows.Controls.Label> który jest formantem, który jest wyśrodkowany w pierwszym wierszu siatki.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Następny wiersz zawiera <xref:System.Windows.Controls.Label> Name kontroli i <xref:System.Windows.Controls.TextBox> jego skojarzone kontroli. Ponieważ ten sam kod jest używany dla każdej pary etykiety/pola tekstowego, jest on umieszczany w parze metod prywatnych i używany dla wszystkich pięciu par etykiet/pól tekstowych. Metody utworzyć odpowiednią formant i <xref:System.Windows.Controls.Grid> wywołać <xref:System.Windows.Controls.Grid.SetColumn%2A> <xref:System.Windows.Controls.Grid.SetRow%2A> klasy statyczne i metody, aby umieścić formanty w odpowiedniej komórce. Po utworzeniu formantu, <xref:System.Windows.Controls.UIElementCollection.Add%2A> przykład wywołuje <xref:System.Windows.Controls.Panel.Children%2A> metodę <xref:System.Windows.Controls.Grid> na właściwości, aby dodać formant do siatki. Kod do dodania pozostałych par etykiety/pola tekstowego jest podobny. Zobacz przykładowy kod, aby uzyskać szczegółowe informacje.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Wdrożenie tych dwóch metod jest następujące:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Na koniec przykład dodaje **PRZYCISKI OK** i **Cancel** i <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dołącza program obsługi zdarzeń do ich zdarzeń.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Zwracanie danych do okna hosta
 Po kliknięciu jednego przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> jego zdarzenie jest wywoływane. Okno hosta można po prostu dołączyć programy obsługi do <xref:System.Windows.Controls.TextBox> tych zdarzeń i uzyskać dane bezpośrednio z formantów. W próbce użyto nieco mniej bezpośredniego podejścia. Obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obrębie zawartości, a następnie wywołuje `OnButtonClicked`zdarzenie niestandardowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , aby powiadomić zawartość. Dzięki temu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość zrobić niektóre sprawdzanie poprawności parametrów przed powiadomieniem hosta. Program obsługi pobiera tekst <xref:System.Windows.Controls.TextBox> z formantów i przypisuje go do właściwości publicznych, z których host może pobrać informacje.

 Deklaracja zdarzenia w WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 Program <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń w programie WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Ustawianie właściwości WPF
 Host Win32 umożliwia użytkownikowi zmianę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kilku właściwości zawartości. Od strony Win32 jest to po prostu kwestia zmiany właściwości. Implementacja w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasie zawartości jest nieco bardziej skomplikowana, ponieważ nie ma jednej właściwości globalnej, która kontroluje czcionki dla wszystkich formantów. Zamiast tego odpowiednia właściwość dla każdego formantu jest zmieniana w akcesorach zestawu właściwości. Poniższy przykład pokazuje kod `DefaultFontFamily` właściwości. Ustawienie właściwości wywołuje metodę prywatną, <xref:System.Windows.Controls.Control.FontFamily%2A> która z kolei ustawia właściwości dla różnych formantów.

 Od WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 Od WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Interop.HwndSource>
- [WPF i Win32 — Współdziałanie](wpf-and-win32-interoperation.md)
