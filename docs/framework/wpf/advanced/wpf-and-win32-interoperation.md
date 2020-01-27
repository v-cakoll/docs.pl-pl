---
title: WPF i Win32 Interop
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: 7b7c3ed8f9833094ce1e836c11f84132ae84def2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735226"
---
# <a name="wpf-and-win32-interoperation"></a>WPF i Win32 — Współdziałanie

Ten temat zawiera omówienie sposobu współdziałania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i kodu Win32. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia rozbudowane środowisko do tworzenia aplikacji. Jeśli jednak masz znaczną inwestycję w kod Win32, może być bardziej efektywne ponowne użycie niektórych z tych kodów.

<a name="basics"></a>

## <a name="wpf-and-win32-interoperation-basics"></a>Podstawowe informacje dotyczące WPF i Win32

Istnieją dwie podstawowe techniki do współdziałania między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i kodem Win32.

- Hostowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w oknie Win32. Korzystając z tej techniki, można użyć zaawansowanych możliwości graficznych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w ramach standardowego okna i aplikacji Win32.

- Hostowanie okna Win32 w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Content. Korzystając z tej techniki, można użyć istniejącej niestandardowej kontrolki Win32 w kontekście innej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Content i przekazać dane przez granice.

Każda z tych technik jest koncepcyjnie wprowadzana w tym temacie. Aby zapoznać się z bardziej zorientowanym na kod ilustracją hostingu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w Win32, zobacz [Przewodnik: hosting zawartości WPF w Win32](walkthrough-hosting-wpf-content-in-win32.md). Aby zapoznać się z bardziej zorientowanym na kod ilustracją hostingu Win32 w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Przewodnik: hosting kontrolki Win32 w WPF](walkthrough-hosting-a-win32-control-in-wpf.md).

<a name="projects"></a>

## <a name="wpf-interoperation-projects"></a>Projekty międzyoperacyjności WPF

Interfejsy API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są kodem zarządzanym, ale większość istniejących programów Win32 jest zapisywana jako niezarządzana C++.  Nie można wywoływać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsów API z poziomu prawdziwy program niezarządzany. Jednak przy użyciu opcji `/clr` z kompilatorem wizualnym C++ firmy Microsoft można utworzyć niezarządzany program zarządzany, w którym można bezproblemowo mieszać zarządzane i niezarządzane wywołania interfejsów API.

W przypadku jednej komplikacji na poziomie projektu nie można kompilować plików [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do C++ projektu.  Istnieje kilka technik dzielenia projektu, aby zrekompensować te.

- Utwórz C# bibliotekę DLL, która zawiera wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony jako skompilowany zestaw, a następnie Dodaj do C++ pliku wykonywalnego tę bibliotekę DLL jako odwołanie.

- Utwórz C# plik wykonywalny dla zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i odwołuje się do C++ biblioteki DLL, która zawiera zawartość Win32.

- Użyj <xref:System.Windows.Markup.XamlReader.Load%2A> do załadowania dowolnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w czasie wykonywania, zamiast kompilowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

- Nie używaj w ogóle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i napisz wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w kodzie, tworząc drzewo elementów z <xref:System.Windows.Application>.

Użyj dowolnych rozwiązań, które najlepiej sprawdzają się.

> [!NOTE]
> Jeśli wcześniej nie korzystasz C++z/CLI, możesz zauważyć kilka słów kluczowych "New", takich jak `gcnew` i `nullptr` w przykładach kodu międzyoperacyjnego. Te słowa kluczowe zastępują starszej składni podwójnego podkreślenia (`__gc`) i zapewniają bardziej naturalną składnię kodu zarządzanego C++w programie.  Aby dowiedzieć się więcej C++o funkcjach zarządzanych przez/CLI, zobacz [rozszerzenia składników dla platform środowiska uruchomieniowego](/cpp/windows/component-extensions-for-runtime-platforms).

<a name="hwnds"></a>

## <a name="how-wpf-uses-hwnds"></a>Jak WPF używa HWND

Aby w pełni wykorzystać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "HWND", należy zrozumieć, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa wartości HWND. Dla dowolnego elementu HWND nie można mieszać renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przy użyciu renderowania DirectX lub renderowania GDI/GDI+. Ma to wiele konsekwencji. Przede wszystkim, aby mieszać te modele renderingu, należy utworzyć rozwiązanie międzyoperacyjne i użyć wydzielonych segmentów międzyoperacyjnych dla każdego modelu renderowania, który będzie używany. Ponadto zachowanie renderowania tworzy ograniczenie "miejsce do obsługi" dla tego, co może być realizowane w rozwiązaniu międzyoperacyjnym. Pojęcie "miejsce w sieci" jest wyjaśnione szczegółowo w temacie [Omówienie regionów technologicznych](technology-regions-overview.md).

Wszystkie elementy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na ekranie są ostatecznie obsługiwane przez właściwość HWND. Podczas tworzenia <xref:System.Windows.Window>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzy właściwość HWND najwyższego poziomu i używa <xref:System.Windows.Interop.HwndSource>, aby umieścić <xref:System.Windows.Window> i jego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość wewnątrz elementu HWND.  Pozostała część zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w aplikacji udostępnia te pojedyncze HWND. Wyjątkiem są menu, listy rozwijane pól kombi i inne wyskakujące okienka. Te elementy tworzą własne okno najwyższego poziomu, dlatego menu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może potencjalnie przejść poza krawędź HWND okna, która go zawiera. W przypadku używania <xref:System.Windows.Interop.HwndHost>, aby ustawić właściwość HWND wewnątrz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informuje system Win32 o sposobie umieszczenia nowego elementu podrzędnego HWND względem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.

Koncepcja powiązana z elementem HWND jest przezroczysta w obrębie i między poszczególnymi elementami HWND. Jest to również omówione w temacie [Omówienie regionów technologii](technology-regions-overview.md).

<a name="hosting_a_wpf_page"></a>

## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hosting zawartości WPF w oknie Microsoft Win32

Klucz służący do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w oknie Win32 jest klasą <xref:System.Windows.Interop.HwndSource>. Ta klasa otacza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartością w oknie Win32, dzięki czemu zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może być dołączana do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako okna podrzędnego. Poniższe podejście łączy Win32 i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w pojedynczej aplikacji.

1. Zaimplementuj zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (element główny zawartości) jako klasę zarządzaną. Zazwyczaj Klasa dziedziczy z jednej z klas, które mogą zawierać wiele elementów podrzędnych i/lub użyć jako elementu głównego, takiego jak <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.Controls.Page>. W kolejnych krokach Klasa ta jest określana jako Klasa zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], a wystąpienia klasy są określane jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty zawartości.

2. Implementowanie aplikacji systemu Windows C++za pomocą/CLI. Jeśli zaczynasz korzystać z istniejącej niezarządzanej C++ aplikacji, możesz zwykle włączyć ją do wywołania kodu zarządzanego, zmieniając ustawienia projektu w celu uwzględnienia flagi kompilatora `/clr` (pełen zakres tego, co może być konieczne do obsługi `/clr` kompilacji nie jest opisany w tym temacie).

3. Ustaw model wątkowości na Apartament wielowątkowy (STA). [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa tego modelu wątkowości.

4. Obsłuż powiadomienie WM_CREATE w procedurze okna.

5. W ramach procedury obsługi (lub funkcji, która wywołuje program obsługi), wykonaj następujące czynności:

    1. Utwórz nowy obiekt <xref:System.Windows.Interop.HwndSource> z elementem nadrzędnym% HWND jako parametr `parent`.

    2. Utwórz wystąpienie klasy zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

    3. Przypisz odwołanie do obiektu zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do właściwości <xref:System.Windows.Interop.HwndSource> obiektu <xref:System.Windows.Interop.HwndSource.RootVisual%2A>.

    4. Właściwość <xref:System.Windows.Interop.HwndSource.Handle%2A> obiektu <xref:System.Windows.Interop.HwndSource> zawiera uchwyt okna (HWND). Aby uzyskać Właściwość HWND, której można użyć w niezarządzanej części aplikacji, Rzutowanie `Handle.ToPointer()` na Właściwość HWND.

6. Zaimplementuj zarządzaną klasę, która zawiera pole statyczne, które przechowuje odwołanie do obiektu zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ta klasa pozwala uzyskać odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu zawartości z kodu Win32, ale co ważniejsze, zapobiega przypadkowemu wykorzystaniu <xref:System.Windows.Interop.HwndSource>.

7. Otrzymywanie powiadomień z obiektu zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przez dołączenie programu obsługi do co najmniej jednego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń obiektu zawartości.

8. Komunikuj się z obiektem zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przy użyciu odwołania przechowywanego w polu statycznym, aby ustawić właściwości, wywołać metody itd.

> [!NOTE]
> Można wykonać niektóre lub wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definicji klasy zawartości dla kroku jeden w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przy użyciu domyślnej klasy częściowej klasy zawartości, jeśli tworzysz oddzielny zestaw, a następnie odwołując się do niego. Mimo że zwykle dołączysz obiekt <xref:System.Windows.Application> w ramach kompilowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do zestawu, nie kończysz korzystania z tego <xref:System.Windows.Application> w ramach operacji międzyoperacyjnych, wystarczy użyć jednej lub więcej klas głównych dla plików [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], do których odwołuje się aplikacja i odniesienia do ich klas częściowych. Pozostała część procedury jest zasadniczo podobna do przedstawionej powyżej.
>
> Każdy z tych kroków ilustruje kod w [przewodniku tematu: hosting zawartości WPF w Win32](walkthrough-hosting-wpf-content-in-win32.md).

<a name="hosting_an_hwnd"></a>

## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hosting okna środowiska Microsoft Win32 w WPF

Klucz służący do hostowania okna Win32 w innej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Content jest klasą <xref:System.Windows.Interop.HwndHost>. Ta klasa otacza okno w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element, który można dodać do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] drzewa elementów. <xref:System.Windows.Interop.HwndHost> obsługuje także interfejsy API, które umożliwiają wykonywanie takich zadań jako komunikatów przetwarzanych dla hostowanego okna. Podstawowa procedura:

1. Utwórz drzewo elementów dla aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (może to być za pomocą kodu lub znaczników). Znajdź odpowiedni i dopuszczalny punkt w drzewie elementów, w którym można dodać implementację <xref:System.Windows.Interop.HwndHost> jako element podrzędny. W pozostałej części tych kroków ten element jest określany jako rezerwowy element.

2. Utwórz element pochodzący z <xref:System.Windows.Interop.HwndHost>, aby utworzyć obiekt, który przechowuje zawartość systemu Win32.

3. W tej klasie hosta Przesłoń <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>metody <xref:System.Windows.Interop.HwndHost>. Zwraca wartość HWND okna hostowanego. Możesz chcieć otoczyć rzeczywiste formanty jako oknem podrzędnym zwróconego okna; Zawijanie kontrolek w oknie hosta zapewnia prostą metodę otrzymywania powiadomień przez zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ta technika pomaga poprawić niektóre problemy z Win32 dotyczące obsługi komunikatów na granicy obsługiwanej kontroli.

4. Zastąp metody <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> i <xref:System.Windows.Interop.HwndHost.WndProc%2A>. Zamiarem tego procesu jest przetworzenie oczyszczania i usunięcie odwołań do hostowanej zawartości, szczególnie w przypadku utworzenia odwołań do obiektów niezarządzanych.

5. W pliku związanym z kodem Utwórz wystąpienie klasy hostingu kontrolki i Uczyń ją elementem podrzędnym elementu. Zazwyczaj można użyć programu obsługi zdarzeń, takiego jak <xref:System.Windows.FrameworkElement.Loaded>, lub użyć konstruktora klasy częściowej. Możesz również dodać zawartość międzyoperacyjną za pomocą zachowania środowiska uruchomieniowego.

6. Przetwarzaj wybrane komunikaty okna, takie jak powiadomienia sterujące. Istnieją dwie metody. Oba zapewniają taki sam dostęp do strumienia komunikatów, dzięki czemu wybór jest w dużej mierze wygodnym programowaniem.

    - Zaimplementuj przetwarzanie komunikatów dla wszystkich komunikatów (nie tylko komunikaty zamknięcia) w zastępują <xref:System.Windows.Interop.HwndHost.WndProc%2A>metody <xref:System.Windows.Interop.HwndHost>.

    - Mają element [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hosting przetwarza komunikaty przez obsługę zdarzenia <xref:System.Windows.Interop.HwndHost.MessageHook>. To zdarzenie jest zgłaszane dla każdego komunikatu, który jest wysyłany do procedury okna głównego okna hostowanego.

    - Nie można przetwarzać komunikatów z systemu Windows, które są poza procesem przy użyciu <xref:System.Windows.Interop.HwndHost.WndProc%2A>.

7. Komunikuj się z hostowanym oknem przy użyciu wywołania platformy, aby wywołać niezarządzaną funkcję `SendMessage`.

Wykonanie tych kroków powoduje utworzenie aplikacji, która współpracuje z myszą wejściową. Możesz dodać obsługę tabulacji dla hostowanego okna, implementując interfejs <xref:System.Windows.Interop.IKeyboardInputSink>.

Każdy z tych kroków ilustruje kod w [przewodniku tematu: hosting kontrolki Win32 w WPF](walkthrough-hosting-a-win32-control-in-wpf.md).

### <a name="hwnds-inside-wpf"></a>Funkcja HWND wewnątrz WPF

<xref:System.Windows.Interop.HwndHost> można traktować jako specjalną kontrolę. (Technicznie, <xref:System.Windows.Interop.HwndHost> jest klasą pochodną <xref:System.Windows.FrameworkElement>, a nie <xref:System.Windows.Controls.Control> klasą pochodną, ale można ją traktować jako kontrolkę do celów międzyoperacyjności.) <xref:System.Windows.Interop.HwndHost> abstrakcyjny podstawowy charakter Win32 dla hostowanej zawartości w taki sposób, że pozostała część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uważa, że hostowana zawartość jest innym obiektem podobnym do kontrolki, który powinien renderować i przetwarzać dane wejściowe. <xref:System.Windows.Interop.HwndHost> zwykle zachowuje się jak wszystkie inne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, chociaż istnieją pewne istotne różnice dotyczące danych wyjściowych (rysunek i grafika) oraz dane wejściowe (mysz i klawiatura) na podstawie ograniczeń, jakie mogą być obsługiwane przez bazowe HWND.

#### <a name="notable-differences-in-output-behavior"></a>Istotne różnice w zachowaniu danych wyjściowych

- <xref:System.Windows.FrameworkElement>, która jest <xref:System.Windows.Interop.HwndHost> klasą bazową, ma dość kilka właściwości, które oznaczają zmiany w interfejsie użytkownika. Należą do nich właściwości, takie jak <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, które zmieniają układ elementów w tym elemencie jako element nadrzędny. Jednak większość z tych właściwości nie jest zamapowana na możliwe odpowiedniki Win32, nawet jeśli takie odpowiedniki mogą istnieć. Zbyt wiele z tych właściwości, a ich znaczenie jest zbyt nieprzydatne, aby mapowania były praktyczne. W związku z tym Ustawianie właściwości, takich jak <xref:System.Windows.FrameworkElement.FlowDirection%2A> on <xref:System.Windows.Interop.HwndHost> nie ma żadnego wpływu.

- przekształcenie nie może być obrócone, skalowane, skośne lub w inny sposób. <xref:System.Windows.Interop.HwndHost>

- <xref:System.Windows.Interop.HwndHost> nie obsługuje właściwości <xref:System.Windows.UIElement.Opacity%2A> (Blend alfa). Jeśli zawartość wewnątrz <xref:System.Windows.Interop.HwndHost> wykonuje <xref:System.Drawing> operacji, które zawierają informacje alfa, które nie są naruszeniem, ale <xref:System.Windows.Interop.HwndHost> jako całość obsługuje tylko nieprzezroczystość = 1,0 (100%).

- <xref:System.Windows.Interop.HwndHost> pojawić się na wierzchu innych elementów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w tym samym oknie najwyższego poziomu. Jednak menu wygenerowane <xref:System.Windows.Controls.ToolTip> lub <xref:System.Windows.Controls.ContextMenu> jest osobnym oknem najwyższego poziomu i dlatego będzie działać poprawnie z <xref:System.Windows.Interop.HwndHost>.

- <xref:System.Windows.Interop.HwndHost> nie respektują regionu wycinka <xref:System.Windows.UIElement>nadrzędnego. Może to być przyczyną problemu w przypadku próby umieszczenia klasy <xref:System.Windows.Interop.HwndHost> wewnątrz regionu przewijania lub <xref:System.Windows.Controls.Canvas>.

#### <a name="notable-differences-in-input-behavior"></a>Znaczące różnice w zachowaniu danych wejściowych

- Ogólnie rzecz biorąc, gdy urządzenia wejściowe są objęte zakresem w <xref:System.Windows.Interop.HwndHost> hostowanym regionie Win32, zdarzenia wejściowe bezpośrednio do Win32.

- Gdy wskaźnik myszy znajduje się nad <xref:System.Windows.Interop.HwndHost>, aplikacja nie odbiera [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń myszy, a wartość właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.IsMouseOver%2A> zostanie `false`.

- Gdy <xref:System.Windows.Interop.HwndHost> ma fokus klawiatury, aplikacja nie będzie odbierać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń klawiatury, a wartość właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> zostanie `false`.

- Gdy fokus znajduje się w <xref:System.Windows.Interop.HwndHost> i zmiany w innej kontrolce wewnątrz <xref:System.Windows.Interop.HwndHost>, aplikacja nie będzie odbierać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń <xref:System.Windows.UIElement.GotFocus> ani <xref:System.Windows.UIElement.LostFocus>.

- Powiązane właściwości i zdarzenia pióra są analogiczne i nie raportują informacji, gdy pióro jest na <xref:System.Windows.Interop.HwndHost>.

<a name="tabbing_mnemonics_accelerators"></a>

## <a name="tabbing-mnemonics-and-accelerators"></a>Tabulacja, skróty i akceleratory

Interfejsy <xref:System.Windows.Interop.IKeyboardInputSink> i <xref:System.Windows.Interop.IKeyboardInputSite> umożliwiają tworzenie płynnych funkcji klawiatury dla mieszanych aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i Win32:

- Używanie tabulacji między składnikami Win32 i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

- Skróty i akceleratory, które działają zarówno wtedy, gdy fokus znajduje się w składniku Win32 i gdy znajduje się w składniku WPF.

Klasy <xref:System.Windows.Interop.HwndHost> i <xref:System.Windows.Interop.HwndSource> umożliwiają implementację <xref:System.Windows.Interop.IKeyboardInputSink>, ale mogą nie obsługiwać wszystkich komunikatów wejściowych, które są potrzebne w przypadku bardziej zaawansowanych scenariuszy. Zastąp odpowiednie metody, aby uzyskać żądane zachowanie klawiatury.

Interfejsy zapewniają obsługę tylko tego, co dzieje się na przejściu między regionami [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i Win32. W regionie Win32 zachowanie tabulacji jest całkowicie kontrolowane przez logikę zaimplementowaną w systemie Win32 na potrzeby tabulacji (jeśli istnieje).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Przewodnik: hosting kontrolki Win32 w WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Przewodnik: hosting zawartości WPF w Win32](walkthrough-hosting-wpf-content-in-win32.md)
