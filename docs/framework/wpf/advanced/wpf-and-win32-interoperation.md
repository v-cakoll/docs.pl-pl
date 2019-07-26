---
title: WPF i Win32 — Współdziałanie
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: a942d72f27d394d31a52fd02ecaa158add4d2e0f
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484630"
---
# <a name="wpf-and-win32-interoperation"></a>WPF i Win32 — Współdziałanie
Ten temat zawiera omówienie współpracy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje bogate środowisko do tworzenia aplikacji. Jeśli jednak masz znaczną inwestycję w [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kod, może być bardziej efektywne ponowne użycie części tego kodu.  

<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>Podstawowe informacje dotyczące WPF i Win32  
 Istnieją dwie podstawowe techniki komunikacji między programami [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]  
  
- Zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hosta[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w oknie. Dzięki tej metodzie można korzystać z zaawansowanych możliwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafiki w ramach standardowego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna i aplikacji.  
  
- Hostowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna w zawartości. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Korzystając z tej techniki, można użyć istniejącej kontrolki [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] niestandardowej w kontekście innej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i przekazać dane między granicami.  
  
 Każda z tych technik jest koncepcyjnie wprowadzana w tym temacie. Aby zapoznać się z bardziej zorientowanym na kod ilustracją hostingu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w [programie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], zobacz Przewodnik: Hosting zawartości WPF w Win32](walkthrough-hosting-wpf-content-in-win32.md). Aby zapoznać się z bardziej zorientowanym na kod ilustracją hostingu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w [programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz Przewodnik: Hostowanie kontrolki Win32 w](walkthrough-hosting-a-win32-control-in-wpf.md)WPF.  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>Projekty międzyoperacyjności WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Interfejsy API są kodem zarządzanym, ale [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] większość istniejących programów jest zapisywana jako niezarządzana. C++  Nie można wywoływać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsów API z poziomu prawdziwy program niezarządzany. Jednak korzystając `/clr` [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] z opcji z kompilatorem, można utworzyć niezarządzany program, który pozwala bezproblemowo mieszać zarządzane i niezarządzane wywołania interfejsów API.  
  
 Jedną skomplikowanie na poziomie projektu jest to, że nie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] można kompilować plików C++ w projekcie.  Istnieje kilka technik dzielenia projektu, aby zrekompensować te.  
  
- Utwórz C# bibliotekę DLL, która zawiera wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony jako skompilowany zestaw, a następnie umieść C++ [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] plik wykonywalny jako odwołanie.  
  
- Utwórz C# plik wykonywalny dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i odwołuje C++ [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] się do niego, który zawiera [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartość.  
  
- Użyj <xref:System.Windows.Markup.XamlReader.Load%2A> ,aby[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] załadować dowolne w czasie wykonywania, zamiast kompilować. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
- Nie używaj [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wcale i napisz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cały kod w kodzie, tworząc drzewo elementów z <xref:System.Windows.Application>.  
  
 Użyj dowolnych rozwiązań, które najlepiej sprawdzają się.  
  
> [!NOTE]
>  Jeśli wcześniej nie korzystasz C++z/CLI, możesz zauważyć kilka słów kluczowych "New", takich `gcnew` jak `nullptr` i w przykładach kodu międzyoperacyjnego. Te słowa kluczowe zastępują starszej składni podwójnego podkreślenia`__gc`() i zapewniają bardziej naturalną składnię kodu zarządzanego C++w programie.  Aby dowiedzieć się więcej C++o funkcjach zarządzanych przez/CLI, zobacz [rozszerzenia składników dla platform środowiska uruchomieniowego](/cpp/windows/component-extensions-for-runtime-platforms) i [Hello, C++/CLI](https://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>Jak WPF używa HWND  
 Aby najlepiej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykorzystać wartość "HWND Interop", musisz zrozumieć, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używać HWND. Dla dowolnego elementu HWND nie można mieszać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania z [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] renderowaniem [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] lub  /  [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] renderowaniem. Ma to wiele konsekwencji. Przede wszystkim, aby mieszać te modele renderingu, należy utworzyć rozwiązanie międzyoperacyjne i użyć wydzielonych segmentów międzyoperacyjnych dla każdego modelu renderowania, który będzie używany. Ponadto zachowanie renderowania tworzy ograniczenie "miejsce do obsługi" dla tego, co może być realizowane w rozwiązaniu międzyoperacyjnym. Pojęcie "miejsce w sieci" jest wyjaśnione szczegółowo w temacie [Omówienie regionów technologicznych](technology-regions-overview.md).  
  
 Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy na ekranie są ostatecznie obsługiwane przez właściwość HWND. <xref:System.Windows.Interop.HwndSource> Gdytworzysz<xref:System.Windows.Window> , program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzy właściwość HWND najwyższego poziomu i używa do umieszczania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i jego zawartości wewnątrz elementu HWND. <xref:System.Windows.Window> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  Pozostała część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w aplikacji ma udział w pojedynczej wartości HWND. Wyjątkiem są menu, listy rozwijane pól kombi i inne wyskakujące okienka. Te elementy tworzą własne okno najwyższego poziomu, dlatego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] menu może potencjalnie przejść do krawędzi HWND okna, która go zawiera. Gdy <xref:System.Windows.Interop.HwndHost> używasz, aby umieścić Właściwość HWND wewnątrz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] , jak ustawić położenie nowego elementu podrzędnego HWND względem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 Koncepcja powiązana z elementem HWND jest przezroczysta w obrębie i między poszczególnymi elementami HWND. Jest to również omówione w temacie [Omówienie regionów technologii](technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hosting zawartości WPF w oknie Microsoft Win32  
 Kluczem do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w oknie jest <xref:System.Windows.Interop.HwndSource> Klasa. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ta klasa otacza [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zawartość [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, dzięki czemu zawartośćmożebyćdołączanadooknajakopodrzędnego.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Poniższe podejście łączy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w pojedynczej aplikacji.  
  
1. Zaimplementuj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość (element główny zawartości) jako klasę zarządzaną. Zazwyczaj Klasa dziedziczy z jednej z klas, które mogą zawierać wiele elementów podrzędnych i/lub użyć jako elementu głównego, takiego jak <xref:System.Windows.Controls.DockPanel> lub. <xref:System.Windows.Controls.Page> W kolejnych krokach Klasa ta jest nazywana [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasą zawartości, a wystąpienia klasy są określane jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty zawartości.  
  
2. Implementowanie aplikacji systemu Windows C++za pomocą/CLI. Jeśli zaczynasz od istniejącej niezarządzanej C++ aplikacji, możesz zwykle włączyć ją do wywołania kodu zarządzanego, zmieniając ustawienia projektu w celu uwzględnienia `/clr` flagi kompilatora (pełen zakres tego, co może być niezbędne do obsługi `/clr` kompilacja nie została opisana w tym temacie).  
  
3. Ustaw model wątkowości na Apartament wielowątkowy (STA). [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]używa tego modelu wątków.  
  
4. Obsługuj powiadomienie WM_CREATE w procedurze okna.  
  
5. W ramach procedury obsługi (lub funkcji, która wywołuje program obsługi), wykonaj następujące czynności:  
  
    1. Utwórz nowy <xref:System.Windows.Interop.HwndSource> obiekt z HWND okna nadrzędnego jako jego `parent` parametru.  
  
    2. Utwórz wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy zawartości.  
  
    3. Przypisz odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu Content <xref:System.Windows.Interop.HwndSource> do właściwości Object <xref:System.Windows.Interop.HwndSource.RootVisual%2A> .  
  
    4. Właściwość <xref:System.Windows.Interop.HwndSource> Object<xref:System.Windows.Interop.HwndSource.Handle%2A> zawiera uchwyt okna (HWND). Aby uzyskać Właściwość HWND, która może być używana w niezarządzanej części aplikacji, Rzutowanie `Handle.ToPointer()` na Właściwość HWND.  
  
6. Zaimplementuj zarządzaną klasę, która zawiera pole statyczne, które przechowuje odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu zawartości. Ta klasa pozwala uzyskać odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu zawartości [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] z kodu, ale co <xref:System.Windows.Interop.HwndSource> ważniejsze, zapobiega przypadkowemu wykorzystaniu elementów bezużytecznych.  
  
7. Odbieraj powiadomienia z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu Content, dołączając procedurę obsługi do co najmniej jednego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia obiektu zawartości.  
  
8. Komunikuj się z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektem Content przy użyciu odwołania przechowywanego w polu statycznym, aby ustawić właściwości, wywołać metody itd.  
  
> [!NOTE]
>  Można wykonać niektóre lub wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definicje klas zawartości dla kroku jeden w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , używając domyślnej klasy częściowej klasy zawartości, jeśli tworzysz oddzielny zestaw, a następnie odwołując się do niego. Mimo że zwykle zawierany <xref:System.Windows.Application> jest obiekt w ramach [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kompilowania do zestawu, nie można zakończyć korzystania z tego <xref:System.Windows.Application> elementu w ramach operacji międzyoperacyjnego. wystarczy użyć co najmniej jednej klasy głównej dla plików o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] określonych do aplikacji i odwoływanie się do ich klas częściowych. Pozostała część procedury jest zasadniczo podobna do przedstawionej powyżej.  
>   
>  Każdy z tych kroków ilustruje kod w instruktażu tematu [: Hosting zawartości WPF w Win32](walkthrough-hosting-wpf-content-in-win32.md).  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hosting okna środowiska Microsoft Win32 w WPF  
 Kluczem do hostowania [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna w innej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości jest <xref:System.Windows.Interop.HwndHost> Klasa. Ta klasa otacza okno w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemencie, który można dodać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do drzewa elementów. <xref:System.Windows.Interop.HwndHost>Program obsługuje również interfejsy API, które umożliwiają wykonywanie takich zadań jako komunikatów przetwarzanych dla hostowanego okna. Podstawowa procedura:  
  
1. Utwórz drzewo elementów dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji (może być za pomocą kodu lub znaczników). Znajdź odpowiedni i dopuszczalny punkt w drzewie elementów, w którym <xref:System.Windows.Interop.HwndHost> można dodać implementację jako element podrzędny. W pozostałej części tych kroków ten element jest określany jako rezerwowy element.  
  
2. Utwórz obiekt, który [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] przechowuje zawartość. <xref:System.Windows.Interop.HwndHost>  
  
3. W tej klasie hosta Zastąp <xref:System.Windows.Interop.HwndHost> metodę. <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> Zwraca wartość HWND okna hostowanego. Możesz chcieć otoczyć rzeczywiste formanty jako oknem podrzędnym zwróconego okna; Zawijanie formantów w oknie hosta zapewnia prostą metodę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] otrzymywania powiadomień z kontrolek. Ta technika ułatwia rozwiązywanie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] problemów dotyczących obsługi komunikatów na granicy hostowanej kontroli.  
  
4. Zastąp <xref:System.Windows.Interop.HwndHost> metody <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> i <xref:System.Windows.Interop.HwndHost.WndProc%2A>. Zamiarem tego procesu jest przetworzenie oczyszczania i usunięcie odwołań do hostowanej zawartości, szczególnie w przypadku utworzenia odwołań do obiektów niezarządzanych.  
  
5. W pliku związanym z kodem Utwórz wystąpienie klasy hostingu kontrolki i Uczyń ją elementem podrzędnym elementu. Zazwyczaj można użyć programu obsługi zdarzeń, takiego jak <xref:System.Windows.FrameworkElement.Loaded>lub użyć konstruktora klasy częściowej. Możesz również dodać zawartość międzyoperacyjną za pomocą zachowania środowiska uruchomieniowego.  
  
6. Przetwarzaj wybrane komunikaty okna, takie jak powiadomienia sterujące. Istnieją dwie metody. Oba zapewniają taki sam dostęp do strumienia komunikatów, dzięki czemu wybór jest w dużej mierze wygodnym programowaniem.  
  
    - Zaimplementuj przetwarzanie komunikatów dla wszystkich komunikatów (nie tylko komunikaty zamknięcia) w przesłonięciu <xref:System.Windows.Interop.HwndHost> metody <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
    - Element hostujący [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przetwarza komunikaty przez <xref:System.Windows.Interop.HwndHost.MessageHook> obsługę zdarzenia. To zdarzenie jest zgłaszane dla każdego komunikatu, który jest wysyłany do procedury okna głównego okna hostowanego.  
  
    - Nie można przetwarzać komunikatów z systemu Windows, które nie <xref:System.Windows.Interop.HwndHost.WndProc%2A>są przetwarzane przy użyciu programu.  
  
7. Komunikuj się z hostowanym oknem przy użyciu wywołania platformy, aby wywołać `SendMessage` niezarządzaną funkcję.  
  
 Wykonanie tych kroków powoduje utworzenie aplikacji, która współpracuje z myszą wejściową. Można dodać obsługę tabulacji dla hostowanego okna przez implementację <xref:System.Windows.Interop.IKeyboardInputSink> interfejsu.  
  
 Każdy z tych kroków ilustruje kod w instruktażu tematu [: Hostowanie kontrolki Win32 w](walkthrough-hosting-a-win32-control-in-wpf.md)WPF.  
  
### <a name="hwnds-inside-wpf"></a>Funkcja HWND wewnątrz WPF  
 Można traktować <xref:System.Windows.Interop.HwndHost> jako specjalną kontrolę. (Technicznie <xref:System.Windows.Interop.HwndHost> , <xref:System.Windows.FrameworkElement> jest klasą <xref:System.Windows.Controls.Control> pochodną, a nie klasą pochodną, ale może być traktowana jako kontrolka do celów międzyoperacyjnych). abstrakcyjny podstawowy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] charakter hostowanej zawartości w taki sposób, że pozostała część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozważania hostowanej zawartości jest innym obiektem podobnym do kontrolki, który powinien renderować i przetwarzać dane wejściowe. <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost>zwykle zachowuje się jak inne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, chociaż istnieją pewne istotne różnice dotyczące danych wyjściowych (rysowania i grafiki) oraz danych wejściowych (myszy i klawiatury) na podstawie ograniczeń, jakie mogą być obsługiwane przez bazowe HWND.  
  
#### <a name="notable-differences-in-output-behavior"></a>Istotne różnice w zachowaniu danych wyjściowych  
  
- <xref:System.Windows.FrameworkElement>, która jest <xref:System.Windows.Interop.HwndHost> klasą bazową, ma dość kilka właściwości, które oznaczają zmiany w interfejsie użytkownika. Należą do nich właściwości, <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>takie jak, które zmieniają układ elementów w tym elemencie jako element nadrzędny. Jednak większość z tych właściwości nie jest zamapowana na możliwe [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] odpowiedniki, nawet jeśli takie odpowiedniki mogą istnieć. Zbyt wiele z tych właściwości, a ich znaczenie jest zbyt nieprzydatne, aby mapowania były praktyczne. W związku z tym Ustawianie właściwości <xref:System.Windows.FrameworkElement.FlowDirection%2A> , <xref:System.Windows.Interop.HwndHost> takich jak on, nie ma żadnego wpływu.  
  
- <xref:System.Windows.Interop.HwndHost>Przekształcanie nie może być obrócone, skalowane, skośne lub w inny sposób.  
  
- <xref:System.Windows.Interop.HwndHost>nie obsługuje <xref:System.Windows.UIElement.Opacity%2A> właściwości (Blend alfa). Jeśli zawartość wewnątrz <xref:System.Windows.Interop.HwndHost> wykonuje <xref:System.Drawing> operacje, które zawierają informacje alfa, które nie są naruszeniem, ale wartość <xref:System.Windows.Interop.HwndHost> jako całość obsługuje tylko nieprzezroczystość = 1,0 (100%).  
  
- <xref:System.Windows.Interop.HwndHost>pojawi się nad innymi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementami w tym samym oknie najwyższego poziomu. Jednak wygenerowane menu jest osobnym oknem najwyższego poziomu i dlatego będzie działać poprawnie z <xref:System.Windows.Interop.HwndHost>. <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Interop.HwndHost>nie respektują regionu wycinka elementu nadrzędnego <xref:System.Windows.UIElement>. Jest to potencjalnie problem w przypadku próby umieszczenia <xref:System.Windows.Interop.HwndHost> klasy wewnątrz regionu przewijania lub. <xref:System.Windows.Controls.Canvas>  
  
#### <a name="notable-differences-in-input-behavior"></a>Znaczące różnice w zachowaniu danych wejściowych  
  
- Ogólnie rzecz biorąc, gdy urządzenia wejściowe są objęte zakresem <xref:System.Windows.Interop.HwndHost> w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hostowanym regionie, zdarzenia wejściowe przechodzą bezpośrednio do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
- Gdy wskaźnik myszy znajduje się nad <xref:System.Windows.Interop.HwndHost>, aplikacja nie odbiera [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń myszy, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a wartość właściwości <xref:System.Windows.UIElement.IsMouseOver%2A> będzie `false`.  
  
- `false` <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Gdy ma fokus klawiatury, aplikacja nie będzie odbierać zdarzeń klawiatury, a wartość właściwości będzie. <xref:System.Windows.Interop.HwndHost>  
  
- Gdy fokus znajduje się w <xref:System.Windows.Interop.HwndHost> obrębie i zmieni się na inną kontrolkę <xref:System.Windows.Interop.HwndHost>wewnątrz, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja nie będzie odbierać zdarzeń <xref:System.Windows.UIElement.GotFocus> ani <xref:System.Windows.UIElement.LostFocus>.  
  
- Powiązane właściwości i zdarzenia pióra są analogiczne i nie raportują informacji, gdy pióro <xref:System.Windows.Interop.HwndHost>jest w stanie.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Tabulacja, skróty i akceleratory  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Interfejsy i umożliwiają<xref:System.Windows.Interop.IKeyboardInputSite> tworzenie płynnych funkcji klawiatury dla mieszanych i aplikacji: <xref:System.Windows.Interop.IKeyboardInputSink>  
  
- Tabulacja między [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] składnikami  
  
- Skróty i akceleratory, które działają zarówno wtedy, gdy fokus znajduje się w składniku Win32 i gdy znajduje się w składniku WPF.  
  
 Klasy <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.IKeyboardInputSink>i <xref:System.Windows.Interop.HwndSource> umożliwiają implementację programu, ale mogą nie obsługiwać wszystkich komunikatów wejściowych, które są potrzebne w przypadku bardziej zaawansowanych scenariuszy. Zastąp odpowiednie metody, aby uzyskać żądane zachowanie klawiatury.  
  
 Interfejsy zapewniają obsługę tylko tego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , co dzieje się na przejściu między regionami i. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] W regionie zachowanie tabulacji jest całkowicie kontrolowane [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] przez zaimplementowaną logikę do tabulacji (jeśli istnieje). [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Przewodnik: Hosting kontrolki Win32 w WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Przewodnik: Hosting zawartości WPF w Win32](walkthrough-hosting-wpf-content-in-win32.md)
