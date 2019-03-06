---
title: WPF i Win32 — Współdziałanie
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: e5a044166023069cdb6e1091339044cd7f964825
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377354"
---
# <a name="wpf-and-win32-interoperation"></a>WPF i Win32 — Współdziałanie
Ten temat zawiera omówienie sposobu współdziałania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferuje rozbudowane środowisko do tworzenia aplikacji. Jednak jeśli masz znaczne inwestycje [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu, może być bardziej efektywnej można ponownie użyć niektóre z tym kodem.  
  

  
<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>Podstaw współdziałanie Win32 i WPF  
 Istnieją dwa podstawowe techniki współdziałanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu.  
  
-   Host [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. W przypadku tej techniki, można użyć funkcji zaawansowanych graficznych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w ramach standardowej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna i aplikacji.  
  
-   Host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. W przypadku tej techniki, można użyć istniejącego niestandardowego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kontrolki w kontekście innych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości i przekazać dane między granicami.  
  
 Każda z tych metod jest koncepcyjnie opisanymi w tym temacie. Do celów ilustracyjnych bardziej zorientowane na kod hostingu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], zobacz [instruktażu: Hosting zawartości WPF w Win32](walkthrough-hosting-wpf-content-in-win32.md). Do celów ilustracyjnych bardziej zorientowane na kod hostingu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [instruktażu: Hosting kontrolki Win32 w WPF](walkthrough-hosting-a-win32-control-in-wpf.md).  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>Projekty współdziałanie WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] czy kodu zarządzanego, ale większość istniejące [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programy są zapisywane niezarządzanych [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Nie można wywołać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] z prawdziwej niezarządzanych program. Jednak przy użyciu `/clr` z opcją [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] kompilatora, można utworzyć mieszane zarządzanych niezarządzanych program której można bezproblemowo łączyć zarządzanych i niezarządzanych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] wywołania.  
  
 Jeden poziom projektu kompilacji jest, że nie można skompilować [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliki do [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] projektu.  Istnieje kilka technik dzielenia projektu w celu kompensacji to.  
  
-   Utwórz DLL języka C#, która zawiera wszystkie swoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony jako skompilowanego zestawu, a następnie swoje [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] obejmują plik wykonywalny, który [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako odwołanie.  
  
-   Tworzenie języka C# plik wykonywalny dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, a potem z łatwością odwoływać się do [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] zawierający [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartości.  
  
-   Użyj <xref:System.Windows.Markup.XamlReader.Load%2A> załadować żadnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w czasie wykonywania, zamiast kompilowania usługi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
-   Nie używaj [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i zapisuj wszystkie swoje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w kodzie, budowanie drzewo elementów z <xref:System.Windows.Application>.  
  
 Za pomocą dowolnych podejście działa najlepiej dla Ciebie.  
  
> [!NOTE]
>  Jeśli nie używasz [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] wcześniej, takich jak można zauważyć pewne "new" słowa kluczowe `gcnew` i `nullptr` w przykładach współdziałanie kodu. Te słowa kluczowe zastępują starsza składnia podwójnego podkreślenia (`__gc`) i zapewnia bardziej naturalny składni dla kodu zarządzanego w [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Aby dowiedzieć się więcej na temat [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] funkcje zarządzanych, zobacz [Component Extensions dla platform środowiska uruchomieniowego](/cpp/windows/component-extensions-for-runtime-platforms) i [Hello C + +/ CLI](https://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>Jak WPF używa parametrów hWnd  
 Aby w pełni wykorzystać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "Międzyoperacyjność HWND", które należy zrozumieć jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa parametrów hWnd. Dla dowolnego HWND, nie można mieszać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] renderowania lub [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]  /  [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] renderowania. Ma to liczba skutki. Przede wszystkim aby można było łączyć na wszystkich tych modeli renderowania, należy utworzyć rozwiązanie współdziałanie i użyj wyznaczonym segmentów współdziałanie dla każdego modelu renderowania, który chce użyć. Zachowanie renderowania tworzy ograniczenie "powietrznej" co można osiągnąć współdziałanie rozwiązania. Pojęcie "powietrznej" zostało wyjaśnione bardziej szczegółowo w temacie [regiony technologiczne — Przegląd](technology-regions-overview.md).  
  
 Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów na ekranie ostatecznie są wspierane przez HWND. Po utworzeniu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzy HWND najwyższego poziomu i używa <xref:System.Windows.Interop.HwndSource> umieścić <xref:System.Windows.Window> i jego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości wewnątrz HWND.  Pozostała część swojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w aplikacji współużytkuje tego HWND pojedynczej. Wyjątek stanowi menu, pole kombi pola listy rozwijane i innych okien podręcznych. Te elementy utworzyć własne okna najwyższego poziomu, co jest dlaczego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] menu potencjalnie może przejść w przeszłości krawędź okna HWND, który go zawiera. Kiedy używasz <xref:System.Windows.Interop.HwndHost> umieścić HWND wewnątrz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] położenie nowe podrzędne HWND względem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 Innym pojęciem do HWND jest przezroczystości wewnątrz i między każdym HWND. Jest to również omówione w temacie [regiony technologiczne — Przegląd](technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hosting zawartości WPF w oknie Win32 firmy Microsoft  
 Kluczem do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno jest <xref:System.Windows.Interop.HwndSource> klasy. Ta klasa jest zawijany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, tak, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości można zintegrować swoje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako okna podrzędnego. Następujące podejście łączy w sobie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w jednej aplikacji.  
  
1.  Wdrożenie usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości (element główny zawartości) jako klasa zarządzana. Zazwyczaj klasa dziedziczy z jednej z klas, które mogą zawierać wiele elementów podrzędnych i/lub używany jako element główny, takich jak <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.Controls.Page>. W kolejnych krokach tej klasy jest nazywane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości klasy i wystąpienia klasy są określane jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektów.  
  
2.  Implementowanie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji za pomocą [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)]. Jeśli rozpoczynasz z istniejącym niezarządzanych [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] aplikacji, można zwykle włączyć go do wywoływania z kodu zarządzanego, zmieniając ustawienia projektu w celu uwzględnienia `/clr` flagi kompilatora (co może być konieczna Obsługa pełnegozakresu`/clr`kompilacja nie została opisana w tym temacie).  
  
3.  Ustaw model wątków do pojedynczego wątku apartamentu (STA). [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa tego modelu wątkowości.  
  
4.  Obsługa powiadomień WM_CREATE w swojej procedurę okna.  
  
5.  W ramach programu obsługi (lub funkcję, która wywołuje program obsługi) wykonaj następujące czynności:  
  
    1.  Utwórz nową <xref:System.Windows.Interop.HwndSource> obiekt z okna nadrzędnego HWND jako jego `parent` parametru.  
  
    2.  Utwórz wystąpienie usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości klasy.  
  
    3.  Odwołanie do przypisywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektu do <xref:System.Windows.Interop.HwndSource> obiektu <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwości.  
  
    4.  <xref:System.Windows.Interop.HwndSource> Obiektu <xref:System.Windows.Interop.HwndSource.Handle%2A> właściwość zawiera uchwyt okna (HWND). Aby uzyskać HWND, używanego w niezarządzanych części aplikacji, należy rzutować `Handle.ToPointer()` do HWND.  
  
6.  Implementowanie zarządzanych klasę, która zawiera pole statyczne, który zawiera odwołanie do usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektu. Ta klasa pozwala uzyskać odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekt zawartości z usługi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu, ale bardziej istotne uniemożliwia swoje <xref:System.Windows.Interop.HwndSource> miałyby przypadkowo bezużyteczne.  
  
7.  Otrzymywanie powiadomień z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości obiektu, dołączając program obsługi do co najmniej jeden z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości zdarzenia obiektu.  
  
8.  Komunikować się z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekt zawartości za pomocą odwołania, która przechowywana w polu statycznym zestaw właściwości, metody wywołania, itp.  
  
> [!NOTE]
>  Można wykonać niektóre lub wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość definicji klasy dla jednego kroku w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przy użyciu domyślnej klasy częściowej klasy zawartości, jeśli utworzyć osobny zestaw, a następnie Odwołaj się do niego. Mimo że zazwyczaj zawierają <xref:System.Windows.Application> obiektu jako część kompilacji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w zespół, możesz nie znajdą się za pomocą tego <xref:System.Windows.Application> jako część współdziałanie, po prostu używasz przynajmniej jednej z klas głównych dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki określonego Aby przez aplikację i odwoływać się do ich klas częściowych. W pozostałej części procedura jest zasadniczo podobny, jak opisano powyżej.  
>   
>  Każdy z tych kroków jest zilustrowany przez kod w temacie [instruktażu: Hosting zawartości WPF w Win32](walkthrough-hosting-wpf-content-in-win32.md).  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hosting okna Microsoft Win32 w WPF  
 Kluczem do hostowania [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna w innych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość jest <xref:System.Windows.Interop.HwndHost> klasy. Ta klasa jest zawijany okna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów, które mogą być dodawane do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] drzewo elementów. <xref:System.Windows.Interop.HwndHost> obsługuje również [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] umożliwiające wykonywanie zadań takich jak przetwarzanie komunikatów dla hostowanej okna. Podstawowa procedura jest:  
  
1.  Utwórz obrębu drzewa dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji (może być za pomocą kodu lub języka znaczników). Znaleźć właściwe i dopuszczalna punktu w drzewie elementów gdzie <xref:System.Windows.Interop.HwndHost> implementacja może być dodany jako element podrzędny. W pozostałej części tych kroków ten element nazywa się z rezerwacją elementu.  
  
2.  Pochodzi od <xref:System.Windows.Interop.HwndHost> do tworzenia obiektu, który zawiera Twoje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartości.  
  
3.  W tej klasie hosta, należy zastąpić <xref:System.Windows.Interop.HwndHost> metoda <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Zwróć HWND hostowanej okna. Możesz chcieć opakować rzeczywiste kontrolkach jako okna podrzędnego okna zwracanego; OPAKOWYWANIE formantów w oknie hosta zapewnia prosty sposób swoje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości otrzymywać powiadomienia z formantów. Ta technika pozwala rozwiązać niektórych [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] problemy dotyczące obsługi komunikatów na granicy obsługiwanego formantu.  
  
4.  Zastąp <xref:System.Windows.Interop.HwndHost> metody <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> i <xref:System.Windows.Interop.HwndHost.WndProc%2A>. W tym miejscu jest przetwarzanie oczyszczania i usuń odwołania do zawartości hostowanej, szczególnie w przypadku, gdy tworzone odwołania do obiektów niezarządzanych.  
  
5.  W pliku związanym z kodem Utwórz wystąpienie obiektu hostingu klasy formantu i Uczyń elementem podrzędnym elementu z rezerwacją. Zwykle takie jak należy użyć procedury obsługi zdarzeń <xref:System.Windows.FrameworkElement.Loaded>, lub użyj konstruktora klasy częściowej. Ale można również dodawać współdziałanie zawartości za pośrednictwem zachowania w czasie wykonywania.  
  
6.  Proces wybranych komunikatów okien, takie jak powiadomień dotyczących formantu karty. Dostępne są dwie opcje. Obie udostępniają identyczne dostęp do strumienia komunikatów, więc ulubionego jest głównie kwestią programowania wygody.  
  
    -   Implementowanie przetwarzania komunikatów o dla wszystkich komunikatów (nie tylko zamknięcie wiadomości) w zastąpienie metody <xref:System.Windows.Interop.HwndHost> metoda <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
    -   Obsługujący [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element przetwarzania komunikatów, obsługa <xref:System.Windows.Interop.HwndHost.MessageHook> zdarzeń. To zdarzenie jest wywoływane dla każdego komunikatu wysyłanego do procedury okna głównego okna hostowanej.  
  
    -   Nie można przetwarzać komunikaty z systemu windows, które są spoza procesu za pomocą polecenia <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
7.  Komunikują się z oknem hostowanej przy użyciu platformy wywołania do wywoływania niezarządzanego `SendMessage` funkcji.  
  
 Wykonaj następujące kroki tworzy aplikację, która działa z danymi wejściowymi z myszy. Można dodać obsługę tabulacji okna hostowanej przez zaimplementowanie <xref:System.Windows.Interop.IKeyboardInputSink> interfejsu.  
  
 Każdy z tych kroków jest zilustrowany przez kod w temacie [instruktażu: Hosting kontrolki Win32 w WPF](walkthrough-hosting-a-win32-control-in-wpf.md).  
  
### <a name="hwnds-inside-wpf"></a>Wewnątrz parametrów hWnd WPF  
 Można potraktować <xref:System.Windows.Interop.HwndHost> jako specjalne kontrolki. (Z technicznego punktu widzenia <xref:System.Windows.Interop.HwndHost> jest <xref:System.Windows.FrameworkElement> nie pochodzi z klasy, <xref:System.Windows.Controls.Control> klasy pochodnej, ale mogą zostać uwzględnione formantu do celów międzyoperacyjności.) <xref:System.Windows.Interop.HwndHost> przenosi bazowego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] charakter hostowaną zawartość tak, aby w pozostałej części [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uwzględnia hostowaną zawartość do innego obiektu w notacji kontrolki, które powinny renderowania i przetwarzania danych wejściowych. <xref:System.Windows.Interop.HwndHost> zazwyczaj zachowuje się jak każdy inny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, chociaż istnieją pewne ważne różnice wokół danych wyjściowych (związane z rysowaniem i grafiki) oraz danych wejściowych (mysz i klawiatura) opartych na ograniczenia jakie podstawowych parametrów hWnd może obsługiwać.  
  
#### <a name="notable-differences-in-output-behavior"></a>Istotne różnice w zachowaniu danych wyjściowych  
  
-   <xref:System.Windows.FrameworkElement>, która jest <xref:System.Windows.Interop.HwndHost> klasy bazowej, ma kilka właściwości, które oznacza zmiany w interfejsie użytkownika. Obejmują one właściwości takich jak <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, który zmienia układ elementów w obrębie tego elementu jako element nadrzędny. Jednak większość tych właściwości nie są zamapowane na możliwe [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ekwiwalenty, nawet jeśli istnieją takie odpowiedniki. Zbyt wiele z tych właściwości i ich znaczenie są zbyt technologii renderowania przeznaczone dla mapowań, aby być niepraktyczne. W związku z tym, takie jak ustawienie właściwości <xref:System.Windows.FrameworkElement.FlowDirection%2A> na <xref:System.Windows.Interop.HwndHost> nie ma wpływu.  
  
-   <xref:System.Windows.Interop.HwndHost> nie może być obracany, skalowanych, niesymetryczne lub w inny sposób wpływ transformacji.  
  
-   <xref:System.Windows.Interop.HwndHost> nie obsługuje <xref:System.Windows.UIElement.Opacity%2A> właściwości (przenikaniem alfa). Jeśli zawartość wewnątrz <xref:System.Windows.Interop.HwndHost> wykonuje <xref:System.Drawing> operacji, które zawierają dane alfa, która sama nie jest to naruszenie, ale <xref:System.Windows.Interop.HwndHost> jako całości, tylko obsługuje przezroczystość = 1.0 (100%).  
  
-   <xref:System.Windows.Interop.HwndHost> pojawi się na drugim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów w tym samym oknie najwyższego poziomu. Jednak <xref:System.Windows.Controls.ToolTip> lub <xref:System.Windows.Controls.ContextMenu> wygenerowanego menu jest osobnym oknie najwyższego poziomu, a więc będzie działać poprawnie z <xref:System.Windows.Interop.HwndHost>.  
  
-   <xref:System.Windows.Interop.HwndHost> nie przestrzega obszaru przycinania jego elementu nadrzędnego <xref:System.Windows.UIElement>. Jest to potencjalnie problemu, jeśli użytkownik podejmie próbę umieścić <xref:System.Windows.Interop.HwndHost> klasy w obszarze przewijana lub <xref:System.Windows.Controls.Canvas>.  
  
#### <a name="notable-differences-in-input-behavior"></a>Istotne różnice w zachowaniu danych wejściowych  
  
-   Ogólnie rzecz biorąc, podczas gdy urządzenia wejściowe są ograniczone w ramach <xref:System.Windows.Interop.HwndHost> hostowane [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] regionu, zdarzeń wejściowych przejdź bezpośrednio do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Gdy wskaźnik myszy znajduje się nad <xref:System.Windows.Interop.HwndHost>, aplikacja nie otrzyma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia myszy, a wartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwość <xref:System.Windows.UIElement.IsMouseOver%2A> będzie `false`.  
  
-   Podczas <xref:System.Windows.Interop.HwndHost> ma fokus klawiatury, aplikacja nie będzie odbierać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klawiatury, zdarzeń i wartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwość <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> będzie `false`.  
  
-   Gdy fokus jest ustawiony w ramach <xref:System.Windows.Interop.HwndHost> i zmiany w innej kontrolce wewnątrz <xref:System.Windows.Interop.HwndHost>, aplikacja nie będzie odbierać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia <xref:System.Windows.UIElement.GotFocus> lub <xref:System.Windows.UIElement.LostFocus>.  
  
-   Związanych z pisaka właściwości i zdarzenia są analogiczne i nie będą zgłaszać informacji podczas, gdy pióro znajduje się nad <xref:System.Windows.Interop.HwndHost>.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Tabulacja, symboli i akceleratorami  
 <xref:System.Windows.Interop.IKeyboardInputSink> i <xref:System.Windows.Interop.IKeyboardInputSite> interfejsów pozwalają tworzyć środowiska bezproblemowe klawiatury dla mieszane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji:  
  
-   Przełączania między [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] składników  
  
-   Klawiszy skrótu i akceleratorów, które działa zarówno, gdy fokus znajduje się w składniku Win32 i jest w składniku WPF.  
  
 <xref:System.Windows.Interop.HwndHost> i <xref:System.Windows.Interop.HwndSource> obu klas zapewniają implementacje <xref:System.Windows.Interop.IKeyboardInputSink>, ale może to nie obsługiwać wszystkich komunikatów wejściowych, które mają dla bardziej zaawansowanych scenariuszy. Musi zostać zastąpiona odpowiedniej metody w celu uzyskania zachowanie klawiatury, który ma.  
  
 Interfejsy tylko zapewnić obsługę co się dzieje w przypadku przejścia między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] regionów. W ramach [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] regionu, TAB zachowanie jest całkowicie kontrolowana przez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zaimplementować logikę klawiszem TAB, jeśli istnieje.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Przewodnik: Hosting kontrolki Win32 w WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Przewodnik: Hosting zawartości WPF w Win32](walkthrough-hosting-wpf-content-in-win32.md)
