---
title: "WPF i Win32 — Współdziałanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f762751da94d25a934d038c1da5adf4a7b88439b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-and-win32-interoperation"></a>WPF i Win32 — Współdziałanie
Ten temat zawiera omówienie sposobu współdziałać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]udostępnia bogate środowisko do tworzenia aplikacji. Jednak jeśli masz znaczących inwestycji [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu, może być bardziej efektywną ponowne części kodu.  
  

  
<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>WPF i współdziałanie podstawy Win32  
 Istnieją dwie podstawowe metody współdziałanie między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu.  
  
-   Host [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. W przypadku tej techniki, można użyć funkcji zaawansowanych graficznych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w ramach standardowego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna i aplikacji.  
  
-   Host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. W przypadku tej techniki, można użyć istniejącego niestandardowe [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kontroli w kontekście innych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i przekazywanie danych poza granicami.  
  
 Każdy z tych metod jest koncepcyjnie opisanymi w tym temacie. Ilustracyjną więcej zorientowane na kod obsługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], zobacz [wskazówki: Obsługa zawartości WPF w Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md). Ilustracyjną więcej zorientowane na kod obsługi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [wskazówki: hostowanie formantu Win32 na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md).  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>Projekty współdziałanie z WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] kodu zarządzanego, ale większość istniejące [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programy są zapisywane niezarządzanych [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Nie można wywołać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] z rzeczywistego niezarządzanych program. Jednak przy użyciu `/clr` opcję z [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] kompilatora, można utworzyć mieszanych niezarządzany zarządzany program gdzie bezproblemowo można łączyć zarządzanych i niezarządzanych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] wywołania.  
  
 Jeden poziom projektu complication jest, że nie można skompilować [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliki do [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] projektu.  Istnieje kilka technik dzielenia projektu to kompensacji.  
  
-   Utwórz [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] biblioteki DLL, który zawiera wszystkie Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony jako skompilowanym zestawie, a następnie z [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] obejmują plik wykonywalny, który [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako odwołanie.  
  
-   Utwórz [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] pliku wykonywalnego dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i jego odwołania [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] zawierający [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartości.  
  
-   Użyj <xref:System.Windows.Markup.XamlReader.Load%2A> załadować żadnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w czasie wykonywania, zamiast kompilowanie programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
-   Nie używaj [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i zapisanie wszystkich sieci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w kodzie, tworzenie drzewa elementu z <xref:System.Windows.Application>.  
  
 Użyj dowolnej metody działa najlepiej dla Ciebie.  
  
> [!NOTE]
>  Jeśli nie używasz [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] przed, takich jak można zauważyć pewne "new" słów kluczowych `gcnew` i `nullptr` w przykładach współdziałanie kodu. Słowa kluczowe zastępowania starszych składni podkreślenia o podwójnej precyzji (`__gc`) i zapewnić bardziej naturalne składni dla kodu zarządzanego w [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Aby dowiedzieć się więcej o [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] zarządzanego funkcji, zobacz [Component Extensions dla platform środowiska uruchomieniowego](/cpp/windows/component-extensions-for-runtime-platforms) i [Hello C + +/ CLI](http://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>Jak WPF używa parametrów hWnd  
 Aby w pełni wykorzystać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "HWND interop", należy zrozumieć sposób [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa parametrów hWnd. Dla dowolnego HWND nie można mieszać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania z [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] renderowania lub [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]  /  [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] renderowania. Ma to liczba skutki. Przede wszystkim aby można było w ogóle mieszać te modele renderowania, należy utworzyć współdziałanie rozwiązania i użyj wyznaczonych segmenty współdziałanie dla każdego modelu renderowania, który chcesz użyć. Ponadto sposób renderowania tworzy ograniczenie "powietrznej" co można zrobić współdziałanie rozwiązania. Pojęcie "powietrznej" objaśniono szczegółowo w temacie [omówienie technologii regionów](../../../../docs/framework/wpf/advanced/technology-regions-overview.md).  
  
 Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy na ekranie ostatecznie bazują na HWND. Po utworzeniu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzy HWND najwyższego poziomu i używa <xref:System.Windows.Interop.HwndSource> umieścić <xref:System.Windows.Window> i jego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości wewnątrz HWND.  Pozostała część programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tego pojedynczej HWND udostępnia zawartość w aplikacji. Wyjątkiem jest menu, kombi pole listy rozwijane i innych wyskakujące okienka. Te elementy utworzyć własne okno najwyższego poziomu, które jest dlaczego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] menu potencjalnie może przejść poza krawędź okna HWND, który go zawiera. Jeśli używasz <xref:System.Windows.Interop.HwndHost> umieścić HWND wewnątrz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informuje o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] położenie nowe podrzędne HWND względem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 Pojęciem do HWND jest przezroczystość wewnątrz i między każdym HWND. Jest to również omówione w tym temacie [omówienie technologii regionów](../../../../docs/framework/wpf/advanced/technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hostowanie zawartości WPF w oknie Microsoft Win32  
 Klucz do hostingu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno jest <xref:System.Windows.Interop.HwndSource> klasy. Ta klasa jest zawijana [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości można włączyć do Twojej [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako okna podrzędnego. Następujące podejścia łączy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w pojedynczej aplikacji.  
  
1.  Wdrożenie programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości (element główny zawartości) jako zarządzanej klasy. Zazwyczaj klasa dziedziczy z jednej z klas, które może zawierać wielu elementów podrzędnych i/lub użyć jako element główny, takich jak <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.Controls.Page>. W kolejnych krokach tej klasy jest nazywane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy zawartości i wystąpień klasy są określane jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektów.  
  
2.  Implementowanie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacja o [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)]. Jeśli uruchamiasz z istniejącym niezarządzanych [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] aplikacji, możesz je zwykle włączyć do wywoływania z kodu zarządzanego, zmieniając ustawienia projektu, aby uwzględnić `/clr` flagi kompilatora (pełny zakres co mogą być niezbędne do obsługi `/clr`kompilacja nie została opisana w tym temacie).  
  
3.  Ustaw model wątkowy do pojedynczego wątku Apartment (STA). [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]używa tego modelu wątkowości.  
  
4.  Obsługa powiadomień WM_CREATE w odpowiedniej procedury okna.  
  
5.  W ramach obsługi (lub funkcję, która wywołuje program obsługi) wykonaj następujące czynności:  
  
    1.  Utwórz nową <xref:System.Windows.Interop.HwndSource> okno nadrzędne HWND obiektu jako jego `parent` parametru.  
  
    2.  Utwórz wystąpienie programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości klasy.  
  
    3.  Odwołanie do przypisywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektu do <xref:System.Windows.Interop.HwndSource> obiektu <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwości.  
  
    4.  <xref:System.Windows.Interop.HwndSource> Obiektu <xref:System.Windows.Interop.HwndSource.Handle%2A> właściwość zawiera uchwyt okna (HWND). Aby dokonać HWND używanego w niezarządzanych część aplikacji, `Handle.ToPointer()` do HWND.  
  
6.  Implementowanie zarządzanych klasę, która zawiera pola statycznego, który zawiera odwołanie do użytkownika [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektu. Tej klasy można pobrać odwołania do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu zawartości z Twojego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu, ale bardziej istotne uniemożliwia Twojej <xref:System.Windows.Interop.HwndSource> przed przypadkowo bezużytecznych.  
  
7.  Odbieranie powiadomień z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektu dołączając obsługi do co najmniej jeden z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości zdarzenia obiektu.  
  
8.  Komunikować się z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu zawartości za pomocą odwołania, który przechowywany w polu statycznym do zestawu właściwości, metody wywołania itp.  
  
> [!NOTE]
>  Można wykonać niektóre lub wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości definicji klasy dla w jednym kroku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przy użyciu domyślnej klasy częściowej klasy zawartości, jeśli możesz utworzyć osobny zestaw i odwoływanie się. Mimo że zwykle zawierają <xref:System.Windows.Application> obiektu jako część kompilowanie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w zestawie nie na końcu za pomocą którego <xref:System.Windows.Application> jako część współdziałanie, możesz użyć przynajmniej jednej klasy głównym dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki określonego Aby aplikacja i odwołuje się ich klas częściowych. W pozostałej części procedura jest zasadniczo podobna do opisanych powyżej.  
>   
>  Każdy z tych kroków przedstawiono przez kod w temacie [wskazówki: Obsługa zawartości WPF w Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md).  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hosting okna Microsoft Win32 na platformie WPF  
 Klucz do hostingu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna w innych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jest <xref:System.Windows.Interop.HwndHost> klasy. Ta klasa jest zawijana okna w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu, którego można dodać do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element drzewa. <xref:System.Windows.Interop.HwndHost>obsługuje również [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] który umożliwiają wykonywanie zadań takich jak przetwarzanie komunikatów hostowanej okna. Podstawowa procedura jest:  
  
1.  Utwórz drzewo elementu dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji (może być za pomocą kodu lub znacznik). Znaleźć punktu odpowiednie, a dopuszczalna w drzewie element gdzie <xref:System.Windows.Interop.HwndHost> implementacja może być dodany jako element podrzędny. W pozostałej części następujące kroki ten element jest nazywane rezerwacją elementu.  
  
2.  Pochodzić od <xref:System.Windows.Interop.HwndHost> do utworzenia obiektu, który zawiera Twoje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartości.  
  
3.  W tej grupie hostów, należy zastąpić <xref:System.Windows.Interop.HwndHost> metody <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Zwróć HWND hostowanej okna. Możesz chcieć zawijać rzeczywiste doświadczeniach kontrolnych jako okna podrzędnego okna zwrócony; Zawijanie formantów w oknie hosta zapewnia prostą metodę dla Twojego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości otrzymywać powiadomienia z formantów. Ta technika pozwala rozwiązać dla niektórych [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kwestiami dotyczącymi komunikat — Obsługa na granicy formantu hostowanej.  
  
4.  Zastąpienie <xref:System.Windows.Interop.HwndHost> metody <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> i <xref:System.Windows.Interop.HwndHost.WndProc%2A>. W tym miejscu jest przetwarzanie oczyszczania i usunąć odwołania do zawartości hostowanej, zwłaszcza w przypadku, gdy utworzono odwołania do obiektów niezarządzane.  
  
5.  W pliku CodeBehind utworzyć wystąpienia formantu hosting klasy i Uczyń elementem podrzędnym elementu rezerwacją. Zwykle takie jak należy użyć programu obsługi zdarzeń <xref:System.Windows.FrameworkElement.Loaded>, lub użyj konstruktora klasy częściowej. Ale można również dodać współdziałanie zawartości za pomocą zachowania w czasie wykonywania.  
  
6.  Proces wybranych komunikatów okien, takich jak powiadomień dotyczących formantu karty. Istnieją dwie metody. Zarówno udostępniają identyczne dostęp do strumienia komunikatów, więc wybór jest przede wszystkim programowania wygody.  
  
    -   Przetwarzania dla wszystkich wiadomości (nie tylko komunikatów zamknięcia) w zastąpienia z komunikatu wdrożenie <xref:System.Windows.Interop.HwndHost> metody <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
    -   Obsługujący [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element przetwarzania komunikatów Obsługa <xref:System.Windows.Interop.HwndHost.MessageHook> zdarzeń. To zdarzenie jest wywoływane dla każdego komunikatu wysyłanego do procedury okna głównego okna hostowanej.  
  
    -   Nie można przetworzyć wiadomości z systemu windows, które są poza przy użyciu procesu <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
7.  Komunikować się z okna hostowanej przy użyciu platformy wywołania do wywołania niezarządzanej `SendMessage` funkcji.  
  
 Poniższe kroki tworzy aplikację, która współdziała z myszą. Można dodać obsługę tabulacji hostowanej okna zaimplementowanie <xref:System.Windows.Interop.IKeyboardInputSink> interfejsu.  
  
 Każdy z tych kroków przedstawiono przez kod w temacie [wskazówki: hostowanie formantu Win32 na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md).  
  
### <a name="hwnds-inside-wpf"></a>Wewnątrz parametrów hWnd WPF  
 Można potraktować <xref:System.Windows.Interop.HwndHost> jako formant specjalnych. (Z technicznego punktu widzenia <xref:System.Windows.Interop.HwndHost> jest <xref:System.Windows.FrameworkElement> nie pochodzi z klasy, <xref:System.Windows.Controls.Control> klasy, ale mogą zostać uwzględnione formantu do celów współdziałanie.) <xref:System.Windows.Interop.HwndHost> abstracts odpowiadającego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] rodzaj hostowaną zawartość tak, aby w pozostałej części [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uwzględnia hostowanej zawartości innego obiektu typu formantu, który powinien renderować i przetworzyć danych wejściowych. <xref:System.Windows.Interop.HwndHost>Ogólnie rzecz biorąc zachowuje się jak każdy inny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, chociaż istnieją pewne różnice ważne wokół danych wyjściowych (rysowania i grafiki) oraz danych wejściowych (myszy i klawiatury) opartych na ograniczenia jakie podstawowych parametrów hWnd może obsługiwać.  
  
#### <a name="notable-differences-in-output-behavior"></a>Istotnych różnic w zachowaniu danych wyjściowych  
  
-   <xref:System.Windows.FrameworkElement>, która jest <xref:System.Windows.Interop.HwndHost> klasy podstawowej, ma kilka właściwości, które określają zmiany do interfejsu użytkownika. Te właściwości obejmują takie jak <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, który zmienia układ elementów wewnątrz tego elementu jako elementu nadrzędnego. Jednak większość tych właściwości nie są mapowane na możliwości [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ekwiwalenty, nawet jeśli ekwiwalentu może istnieć. Zbyt wiele z tych właściwości i ich znaczenie są zbyt technologii renderowania specyficzne dla mapowań praktyczne. W związku z tym, takie jak ustawienie właściwości <xref:System.Windows.FrameworkElement.FlowDirection%2A> na <xref:System.Windows.Interop.HwndHost> nie ma wpływu.  
  
-   <xref:System.Windows.Interop.HwndHost>nie może być obracany, skalowana, spowodowałoby zafałszowanie lub w inny sposób wpływ transformacji.  
  
-   <xref:System.Windows.Interop.HwndHost>nie obsługuje <xref:System.Windows.UIElement.Opacity%2A> właściwości (przenikanie alfa). Jeśli zawartości wewnątrz <xref:System.Windows.Interop.HwndHost> wykonuje <xref:System.Drawing> operacje, które zawierają dane alfa, który sam nie jest to naruszenie, ale <xref:System.Windows.Interop.HwndHost> jako całość obsługuje tylko nieprzezroczystość = 1.0 (100%).  
  
-   <xref:System.Windows.Interop.HwndHost>pojawi się na drugim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów w tym samym oknie najwyższego poziomu. Jednak <xref:System.Windows.Controls.ToolTip> lub <xref:System.Windows.Controls.ContextMenu> wygenerowanego menu jest osobnym oknie najwyższego poziomu, a więc będzie działać prawidłowo z <xref:System.Windows.Interop.HwndHost>.  
  
-   <xref:System.Windows.Interop.HwndHost>nie przestrzega obszaru przycinania nadrzędnego <xref:System.Windows.UIElement>. Prawdopodobnie jest to problem, jeśli próba umieszczenia <xref:System.Windows.Interop.HwndHost> klasy w regionie przewijania lub <xref:System.Windows.Controls.Canvas>.  
  
#### <a name="notable-differences-in-input-behavior"></a>Istotnych różnic w zachowaniu wejściowych  
  
-   Ogólnie, gdy urządzenia wejściowe do zakresu w ramach <xref:System.Windows.Interop.HwndHost> hostowane [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] regionu, zdarzenia wejściowe przejść bezpośrednio do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Gdy wskaźnik myszy znajduje się nad <xref:System.Windows.Interop.HwndHost>, aplikacja nie otrzyma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia myszy, a wartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości <xref:System.Windows.UIElement.IsMouseOver%2A> będzie `false`.  
  
-   Podczas <xref:System.Windows.Interop.HwndHost> ma fokus klawiatury, aplikacja nie będzie odbierać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klawiatury zdarzenia i wartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> będzie `false`.  
  
-   Gdy fokus jest w <xref:System.Windows.Interop.HwndHost> i zmiany inny formant wewnątrz <xref:System.Windows.Interop.HwndHost>, aplikacja nie będzie odbierać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia <xref:System.Windows.UIElement.GotFocus> lub <xref:System.Windows.UIElement.LostFocus>.  
  
-   Związane z pióro właściwości i zdarzeń są podobne i nie będą zgłaszać informacji, gdy pióro znajduje się nad <xref:System.Windows.Interop.HwndHost>.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Klawisza TAB, klawiszy skrótu i akceleratorami  
 <xref:System.Windows.Interop.IKeyboardInputSink> i <xref:System.Windows.Interop.IKeyboardInputSite> interfejsów pozwala na tworzenie środowisko bezproblemowe klawiatury dla mieszanym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji:  
  
-   Przełączania między [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] składników  
  
-   Klawiszy skrótu i akceleratorów, które działa zarówno, gdy fokus jest w składniku Win32 i jest w składniku WPF.  
  
 <xref:System.Windows.Interop.HwndHost> i <xref:System.Windows.Interop.HwndSource> klasy zarówno zawierać implementacje używanych <xref:System.Windows.Interop.IKeyboardInputSink>, ale ich nie może obsługiwać wszystkie komunikaty wejściowe dla bardziej zaawansowanych scenariuszy. Zastąpienie odpowiedniej metody w celu uzyskania zachowanie klawiatury, który ma.  
  
 Interfejsy tylko zapewnić obsługę co się dzieje w przypadku przejścia między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] regionów. W ramach [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] regionu, klawisza TAB zachowanie jest całkowicie kontrolowane przez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zaimplementowana logikę klawisza TAB, jeśli istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.HwndHost>  
 <xref:System.Windows.Interop.HwndSource>  
 <xref:System.Windows.Interop>  
 [Przewodnik: hosting kontrolki Win32 w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)  
 [Przewodnik: hosting zawartości WPF w Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)
