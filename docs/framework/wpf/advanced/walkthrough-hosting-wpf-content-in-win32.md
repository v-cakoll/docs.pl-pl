---
title: Hostowanie zawartości WPF w Win32
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 418c5a4708a7842e5e441235738b73a009c9c956
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124550"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Wskazówki: Hosting zawartości WPF w Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia rozbudowane środowisko do tworzenia aplikacji. Jeśli jednak masz znaczną inwestycję w kod Win32, może być bardziej efektywne Dodawanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji do aplikacji zamiast ponownego zapisywania oryginalnego kodu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia bezpośredni mechanizm hostingu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w oknie Win32.  
  
 W tym samouczku opisano sposób pisania przykładowej aplikacji, która udostępnia [zawartość WPF w przykładzie okna Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage), która hostuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość w oknie Win32. Ten przykład można rozwinąć, aby hostować dowolne okna Win32. Ponieważ obejmuje mieszanie kodu zarządzanego i niezarządzanego, aplikacja jest zapisywana C++w/CLI.  

<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym samouczku założono podstawową wiedzę na temat programowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i środowiska Win32. Aby uzyskać podstawowe wprowadzenie do programowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [wprowadzenie](../getting-started/index.md). Aby zapoznać się z wprowadzeniem do programowania Win32, należy odwołać się do dowolnej z wielu książek w temacie, w szczególności do *programowania systemu Windows* przez Charles Petzold.  
  
 Ponieważ przykład, który obejmuje ten samouczek, jest zaimplementowany w C++/CLI, w tym samouczku założono, że korzystanie C++ z programu do obsługi interfejsu API systemu Windows oraz zrozumienie programowania kodu zarządzanego. Znajomość C++/CLI jest przydatna, ale nie jest istotna.  
  
> [!NOTE]
> Ten samouczek zawiera wiele przykładów kodu ze skojarzonego przykładu. Jednak w celu zapewnienia czytelności nie obejmuje kompletny kod przykładowy. Aby uzyskać kompletny przykładowy kod, zobacz [hosting zawartości WPF w przykładzie okna Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Podstawowa procedura  
 W tej sekcji opisano podstawową procedurę służącą do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość w oknie Win32. Pozostałe sekcje zawierają szczegółowe informacje o każdym z kroków.  
  
 Klucz służący do hostowania zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w oknie Win32 jest klasą <xref:System.Windows.Interop.HwndSource>. Ta klasa otacza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartością w oknie Win32, umożliwiając umieszczenie jej w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako okna podrzędnego. Poniższe podejście łączy Win32 i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w pojedynczej aplikacji.  
  
1. Zaimplementuj zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako klasę zarządzaną.  
  
2. Implementowanie aplikacji systemu Windows C++za pomocą/CLI. Jeśli zaczynasz od istniejącej aplikacji i niezarządzanego C++ kodu, możesz zwykle włączyć ją do wywoływania kodu zarządzanego, zmieniając ustawienia projektu tak, aby zawierała flagę kompilatora `/clr`.  
  
3. Ustaw model wątkowości na Apartament jednowątkowy (STA).  
  
4. Obsługuj powiadomienie [WM_CREATE](/windows/desktop/winmsg/wm-create)w procedurze okna i wykonaj następujące czynności:  
  
    1. Utwórz nowy obiekt <xref:System.Windows.Interop.HwndSource> z oknem nadrzędnym jako parametr `parent`.  
  
    2. Utwórz wystąpienie klasy zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Przypisz odwołanie do obiektu zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do właściwości <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource>.  
  
    4. Pobierz Właściwość HWND dla zawartości. Właściwość <xref:System.Windows.Interop.HwndSource.Handle%2A> obiektu <xref:System.Windows.Interop.HwndSource> zawiera uchwyt okna (HWND). Aby uzyskać Właściwość HWND, której można użyć w niezarządzanej części aplikacji, Rzutowanie `Handle.ToPointer()` na Właściwość HWND.  
  
5. Zaimplementuj zarządzaną klasę, która zawiera pole statyczne, aby pomieścić odwołanie do zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ta klasa pozwala uzyskać odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości z kodu Win32.  
  
6. Przypisz zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do pola statycznego.  
  
7. Odbieraj powiadomienia z zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dołączając procedurę obsługi do jednego lub kilku zdarzeń [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
8. Komunikuj się z zawartością [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przy użyciu odwołania przechowywanego w polu statycznym, aby ustawić właściwości i tak dalej.  
  
> [!NOTE]
> Możesz również użyć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], aby zaimplementować zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Należy jednak skompilować ją oddzielnie jako bibliotekę dołączaną dynamicznie (DLL) i odwołać się do tej biblioteki DLL z aplikacji Win32. Pozostała część procedury jest podobna do przedstawionej powyżej.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implementowanie aplikacji hosta
 W tej sekcji opisano, jak hostować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość w podstawowej aplikacji Win32. Sama zawartość jest implementowana w C++/CLI jako Klasa zarządzana. W większości przypadków jest to proste [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowanie. Kluczowe aspekty implementacji zawartości zostały omówione w temacie [implementowanie zawartości WPF](#implementing_the_wpf_page).

- [Podstawowa aplikacja](#the_basic_application)

- [Hosting zawartości WPF](#hosting_the_wpf_page)

- [Przechowywanie odwołania do zawartości WPF](#holding_a_reference)

- [Komunikacja z zawartością WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Podstawowa aplikacja
 Punktem początkowym aplikacji hosta było utworzenie szablonu programu Visual Studio 2005.

1. Otwórz program Visual Studio 2005 i wybierz pozycję **Nowy projekt** z menu **plik** .

2. Wybierz pozycję **Win32** z listy typów projektów C++ Visual. Jeśli językiem domyślnym nie C++jest, te typy projektów są dostępne w **innych językach**.

3. Wybierz szablon **projektu Win32** , przypisz nazwę do projektu, a następnie kliknij przycisk **OK** , aby uruchomić **Kreatora aplikacji Win32**.

4. Zaakceptuj ustawienia domyślne kreatora i kliknij przycisk **Zakończ** , aby uruchomić projekt.

 Szablon tworzy podstawową aplikację Win32, w tym:

- Punkt wejścia dla aplikacji.

- Okno z skojarzoną procedurą okna (WndProc).

- Menu z nagłówkami **plików** i **pomocy** . Menu **plik** zawiera element **wyjścia** , który zamknie aplikację. Menu **Pomoc** zawiera element **o** elemencie, który powoduje uruchomienie prostego okna dialogowego.

 Przed rozpoczęciem pisania kodu w celu hostowania zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] należy wprowadzić dwie zmiany w szablonie podstawowym.

 Pierwszym jest skompilowanie projektu jako kodu zarządzanego. Domyślnie projekt kompiluje jako kod niezarządzany. Jednak ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest zaimplementowana w kodzie zarządzanym, należy odpowiednio skompilować projekt.

1. Kliknij prawym przyciskiem myszy nazwę projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości** z menu kontekstowego, aby uruchomić okno dialogowe **strony właściwości** .

2. W okienku po lewej stronie wybierz pozycję **Właściwości konfiguracji** w widoku drzewa.

3. Wybierz opcję Obsługa **środowiska uruchomieniowego** CLR z listy **wartości domyślne projektu** w okienku po prawej stronie.

4. W polu listy rozwijanej wybierz opcję **Obsługa środowiska uruchomieniowego CLR (/CLR)** .

> [!NOTE]
> Ta flaga kompilatora umożliwia korzystanie z kodu zarządzanego w aplikacji, ale kod niezarządzany jeszcze nie zostanie skompilowany.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa modelu wątkowości jednowątkowego apartamentu (STA). Aby zapewnić prawidłowe działanie z kodem zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], należy ustawić model wątkowości aplikacji na STA przez zastosowanie atrybutu do punktu wejścia.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hosting zawartości WPF
 Zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest prostą aplikacją wpisu adresu. Składa się z kilku <xref:System.Windows.Controls.TextBox>ch kontrolek, które mogą mieć nazwę użytkownika, adres i tak dalej. Istnieją również dwa <xref:System.Windows.Controls.Button> kontrolki, **OK** i **Anuluj**. Gdy użytkownik kliknie przycisk **OK**, program obsługi zdarzeń <xref:System.Windows.Controls.Primitives.ButtonBase.Click>u zbiera dane z kontrolek <xref:System.Windows.Controls.TextBox>, przypisze je do odpowiednich właściwości i wywołuje zdarzenie niestandardowe, `OnButtonClicked`. Gdy użytkownik kliknie **przycisk Anuluj**, program obsługi po prostu podnosi `OnButtonClicked`. Obiekt argumentu zdarzenia dla `OnButtonClicked` zawiera pole logiczne, które wskazuje, który przycisk został kliknięty.

 Kod do hostowania zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest implementowany w programie obsługi dla powiadomienia [WM_CREATE](/windows/desktop/winmsg/wm-create) w oknie hosta.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 Metoda `GetHwnd` przyjmuje informacje o rozmiarze i pozycji oraz uchwyt okna nadrzędnego i zwraca uchwyt okna hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.

> [!NOTE]
> Nie można użyć dyrektywy `#using` dla przestrzeni nazw `System::Windows::Interop`. Spowoduje to utworzenie kolizji nazw między strukturą <xref:System.Windows.Interop.MSG> w tej przestrzeni nazw i strukturą komunikatów zadeklarowaną w Winuser. h. Zamiast tego należy użyć w pełni kwalifikowanych nazw, aby uzyskać dostęp do zawartości tej przestrzeni nazw.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie można hostować bezpośrednio w oknie aplikacji. Zamiast tego należy najpierw utworzyć obiekt <xref:System.Windows.Interop.HwndSource>, aby otoczyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość. Ten obiekt jest w zasadzie oknem, który jest przeznaczony do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ej zawartości. Obiekt <xref:System.Windows.Interop.HwndSource> można hostować w oknie nadrzędnym, tworząc go jako element podrzędny okna Win32, który jest częścią aplikacji. Parametry konstruktora <xref:System.Windows.Interop.HwndSource> zawierają wiele tych samych informacji, które można przekazać do okienka, podczas tworzenia podrzędnego okna Win32.

 Następnie utworzysz wystąpienie obiektu zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. W takim przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jest implementowana jako oddzielna Klasa, `WPFPage`przy użyciu C++/CLI. Możesz również zaimplementować zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. W tym celu należy jednak skonfigurować oddzielny projekt i skompilować zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako bibliotekę DLL. Do projektu można dodać odwołanie do tego pliku DLL i użyć tego odwołania do utworzenia wystąpienia zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Możesz wyświetlić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość w oknie podrzędnym, przypisując odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości do właściwości <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource>.

 Następny wiersz kodu dołącza procedurę obsługi zdarzeń `WPFButtonClicked`do zdarzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Content `OnButtonClicked`. Ta procedura obsługi jest wywoływana, gdy użytkownik kliknie przycisk **OK** lub **Anuluj** . Zobacz [communicating_with_the_WPF zawartości](#communicating_with_the_page) , aby uzyskać więcej informacji na temat tej procedury obsługi zdarzeń.

 Ostatni wiersz podanego kodu zwraca uchwyt okna (HWND), który jest skojarzony z obiektem <xref:System.Windows.Interop.HwndSource>. Tego uchwytu można użyć w kodzie Win32 do wysyłania komunikatów do hostowanego okna, chociaż nie jest to konieczne. Obiekt <xref:System.Windows.Interop.HwndSource> zgłasza zdarzenie za każdym razem, gdy odbierze komunikat. Aby przetworzyć komunikaty, wywołaj metodę <xref:System.Windows.Interop.HwndSource.AddHook%2A>, aby dołączyć procedurę obsługi komunikatów, a następnie przetworzyć komunikaty w ramach tej procedury obsługi.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Przechowywanie odwołania do zawartości WPF
 W przypadku wielu aplikacji użytkownik chce później komunikować się z zawartością [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Na przykład może zajść potrzeba zmodyfikowania właściwości zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lub za<xref:System.Windows.Interop.HwndSource>, że ma ona różne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość. W tym celu należy odwołać się do obiektu <xref:System.Windows.Interop.HwndSource> lub zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Obiekt <xref:System.Windows.Interop.HwndSource> i jego skojarzona zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pozostają w pamięci do momentu zniszczenia uchwytu okna. Jednak zmienna przypisana do obiektu <xref:System.Windows.Interop.HwndSource> wyjdzie poza zakres od razu po powrocie z procedury okna. Niestandardowym sposobem obsługi tego problemu w aplikacjach Win32 jest użycie zmiennej statycznej lub globalnej. Niestety, nie można przypisać obiektu zarządzanego do tych typów zmiennych. Dojście do okna powiązane z obiektem <xref:System.Windows.Interop.HwndSource> można przypisać do zmiennej globalnej lub statycznej, ale nie zapewnia ona dostępu do samego obiektu.

 Najprostszym rozwiązaniem tego problemu jest zaimplementowanie zarządzanej klasy, która zawiera zestaw pól statycznych do przechowywania odwołań do wszystkich obiektów zarządzanych, do których wymagany jest dostęp. Przykład używa klasy `WPFPageHost` do przechowywania odwołania do zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oraz początkowych wartości liczby właściwości, które mogą zostać zmienione później przez użytkownika. Jest to zdefiniowane w nagłówku.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 Ta ostatnia część funkcji `GetHwnd` przypisuje wartości do tych pól do późniejszego użycia, podczas gdy `myPage` nadal należy do zakresu.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Komunikacja z zawartością WPF
 Istnieją dwa typy komunikacji z zawartością [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aplikacja otrzymuje informacje z zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], gdy użytkownik kliknie przyciski **OK** lub **Anuluj** . Aplikacja ma również [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], która pozwala użytkownikowi zmieniać różne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zawartości, takie jak kolor tła lub domyślny rozmiar czcionki.

 Jak wspomniano powyżej, gdy użytkownik kliknie jeden z przycisków, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość zgłasza zdarzenie `OnButtonClicked`. Aplikacja dołącza procedurę obsługi do tego zdarzenia, aby otrzymywać te powiadomienia. Jeśli kliknięto przycisk **OK** , program obsługi pobiera informacje o użytkowniku z zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i wyświetla je w zestawie formantów statycznych.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Program obsługi odbiera obiekt argumentu zdarzenia niestandardowego z zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], `MyPageEventArgs`. Właściwość `IsOK` obiektu jest ustawiona na `true`, jeśli kliknięto przycisk **OK** , i `false` Jeśli kliknięto przycisk **Anuluj** .

 Jeśli kliknięto przycisk **OK** , program obsługi pobiera odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości z klasy kontenera. Następnie zbiera informacje o użytkowniku, które są przechowywane przez skojarzone właściwości zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i używa formantów statycznych do wyświetlania informacji w oknie nadrzędnym. Ponieważ dane zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są w postaci ciągu zarządzanego, musi być organizowane do użycia przez formant Win32. Jeśli kliknięto przycisk **Anuluj** , program obsługi wyczyści dane z kontrolek statycznych.

 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacji udostępnia zestaw przycisków radiowych, które pozwalają użytkownikowi modyfikować kolor tła [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i kilka właściwości związanych z czcionkami. Poniższy przykład jest fragmentem z procedury okna aplikacji (WndProc) i obsługą komunikatów, która ustawia różne właściwości różnych komunikatów, w tym kolor tła. Inne są podobne i nie są wyświetlane. Zobacz kompletny przykład dla szczegółów i kontekstu.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Aby ustawić kolor tła, Pobierz odwołanie do zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (`hostedPage`) z `WPFPageHost` i ustaw właściwość kolor tła na odpowiedni kolor. W przykładzie są stosowane trzy opcje koloru: oryginalny kolor, jasnozielony lub lekki. Oryginalny kolor tła jest przechowywany jako pole statyczne w klasie `WPFPageHost`. Aby ustawić pozostałe dwa, należy utworzyć nowy obiekt <xref:System.Windows.Media.SolidColorBrush> i przekazać konstruktorowi wartość statyczne kolory z obiektu <xref:System.Windows.Media.Colors>.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementowanie strony WPF
 Zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można hostować i korzystać z niej bez znajomości rzeczywistej implementacji. Jeśli zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] została spakowana w oddzielnej bibliotece DLL, może ona zostać skompilowana w dowolnym języku środowiska uruchomieniowego języka wspólnego (CLR). Poniżej znajduje się krótki przewodnik implementacji C++/CLI, który jest używany w przykładzie. Ta sekcja zawiera następujące podsekcje.

- [Układ](#page_layout)

- [Zwracanie danych do okna hosta](#returning_data_to_window)

- [Ustawianie właściwości WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Układ
 Elementy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości składają się z pięciu <xref:System.Windows.Controls.TextBox> kontrolek ze skojarzonymi kontrolkami <xref:System.Windows.Controls.Label>: nazwa, adres, miasto, Województwo i zip. Istnieją również dwa <xref:System.Windows.Controls.Button> kontrolki, **OK** i **Anuluj**

 Zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest zaimplementowana w klasie `WPFPage`. Układ jest obsługiwany przy użyciu elementu układu <xref:System.Windows.Controls.Grid>. Klasa dziedziczy po <xref:System.Windows.Controls.Grid>, co efektywnie sprawia, że jest to [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element główny zawartości.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Konstruktor zawartości przyjmuje wymaganą szerokość i wysokość i odpowiednio dopasowuje <xref:System.Windows.Controls.Grid>. Następnie definiuje podstawowy układ przez utworzenie zestawu <xref:System.Windows.Controls.ColumnDefinition> i <xref:System.Windows.Controls.RowDefinition> obiektów, a następnie dodanie ich do <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> <xref:System.Windows.Controls.Grid> bazowego obiektu i kolekcji <xref:System.Windows.Controls.Grid.RowDefinitions%2A>. Definiuje on siatkę pięciu wierszy i siedmiu kolumn, z wymiarami określonymi przez zawartość komórek.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Następnie Konstruktor dodaje do <xref:System.Windows.Controls.Grid>elementy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Pierwszy element jest tekstem tytułu, który jest formantem <xref:System.Windows.Controls.Label>, który jest wyśrodkowany w pierwszym wierszu siatki.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Następny wiersz zawiera nazwę kontrolki <xref:System.Windows.Controls.Label> i skojarzonej z nią kontrolki <xref:System.Windows.Controls.TextBox>. Ponieważ ten sam kod jest używany dla każdej pary Etykieta/pole tekstowe, jest umieszczany w parze metod prywatnych i używany dla wszystkich pięciu par Etykieta/pole tekstowe. Metody tworzą odpowiednią kontrolkę i wywołują metody <xref:System.Windows.Controls.Grid.SetColumn%2A> statycznej klasy <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.Grid.SetRow%2A> do umieszczania kontrolek w odpowiedniej komórce. Po utworzeniu kontrolki, przykład wywołuje metodę <xref:System.Windows.Controls.UIElementCollection.Add%2A> właściwości <xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.Grid>, aby dodać formant do siatki. Kod, aby dodać pozostałe pary Etykieta/pole tekstowe jest podobny. Zobacz przykładowy kod, aby uzyskać szczegółowe informacje.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Implementacja dwóch metod jest następująca:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Na koniec przykład dodaje przyciski **OK** i **Anuluj** i dołącza procedurę obsługi zdarzeń do swoich zdarzeń <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Zwracanie danych do okna hosta
 Po kliknięciu dowolnego przycisku zostanie zgłoszone jego zdarzenie <xref:System.Windows.Controls.Primitives.ButtonBase.Click>. Okno hosta może po prostu dołączyć programy obsługi do tych zdarzeń i pobrać dane bezpośrednio z formantów <xref:System.Windows.Controls.TextBox>. W przykładzie jest stosowane nieco mniej bezpośrednie podejście. Obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> w ramach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, a następnie podnosi `OnButtonClicked`zdarzeń niestandardowych w celu powiadomienia zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Dzięki temu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość może wykonać weryfikację parametrów przed powiadomieniem hosta. Program obsługi pobiera tekst z formantów <xref:System.Windows.Controls.TextBox> i przypisuje go do właściwości publicznych, z którego host może pobrać te informacje.

 Deklaracja zdarzenia w WPFPage. h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 Program obsługi zdarzeń <xref:System.Windows.Controls.Primitives.ButtonBase.Click> w WPFPage. cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Ustawianie właściwości WPF
 Host Win32 umożliwia użytkownikowi zmianę kilku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zawartości. Po stronie Win32 jest po prostu kwestią zmiany właściwości. Implementacja klasy zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest nieco bardziej skomplikowana, ponieważ nie ma żadnej pojedynczej właściwości globalnej, która kontroluje czcionki dla wszystkich kontrolek. Zamiast tego odpowiednia właściwość dla każdej kontrolki jest zmieniana w obszarze właściwości metody dostępu. Poniższy przykład pokazuje kod właściwości `DefaultFontFamily`. Ustawienie właściwości wywołuje prywatną metodę, która z kolei ustawia właściwości <xref:System.Windows.Controls.Control.FontFamily%2A> dla różnych kontrolek.

 Z WPFPage. h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 Z WPFPage. cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Interop.HwndSource>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
