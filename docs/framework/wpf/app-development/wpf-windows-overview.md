---
title: Przegląd Okna WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: b9aa3f4e386ca5de79fe028b10d0d68343aba06b
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920032"
---
# <a name="wpf-windows-overview"></a>Przegląd Okna WPF
Użytkownicy pracują z autonomicznymi aplikacjami Windows Presentation Foundation (WPF) za pomocą systemu Windows. Głównym celem okna jest hostowanie zawartości, która wizualizuje dane i umożliwia użytkownikom współdziałanie z danymi. Autonomiczne aplikacje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewniają własne okna przy użyciu klasy <xref:System.Windows.Window>. Ten temat zawiera wprowadzenie <xref:System.Windows.Window> przed rozpoczęciem omawiania podstaw tworzenia i zarządzania oknami w aplikacjach autonomicznych.  
  
> [!NOTE]
> Obsługiwane przez przeglądarkę [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje, w tym [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i luźne [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony, nie zapewniają własnych okien. Zamiast tego są one hostowane w systemie Windows udostępnianym przez program Windows Internet Explorer. Zobacz [Omówienie aplikacji przeglądarki XAML w języku WPF](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Klasa okna  
 Na poniższej ilustracji przedstawiono części składowe okna:  
  
 ![Zrzut ekranu pokazujący elementy okna.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Okno jest podzielone na dwa obszary: obszar niebędący klientem i obszar klienta.  
  
 *Obszar niekliencki* okna jest implementowany przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i obejmuje części okna, które są wspólne dla większości systemu Windows, w tym następujące:  
  
- Obramowanie.  
  
- Pasek tytułu.  
  
- Ikona.  
  
- Przyciski Minimalizuj, Maksymalizuj i Przywróć.  
  
- Przycisk Zamknij.  
  
- Menu systemowe z elementami menu, które umożliwiają użytkownikom minimalizowanie, maksymalizowanie, przywracanie, przenoszenie, zmienianie rozmiaru i zamykanie okna.  
  
 *Obszar klienta* okna to obszar w obszarze nieklienckim okna, który jest używany przez deweloperów do dodawania zawartości specyficznej dla aplikacji, takiej jak paski menu, paski narzędzi i formanty.  
  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]okno jest hermetyzowane przez klasę <xref:System.Windows.Window>, za pomocą której można wykonać następujące czynności:  
  
- Wyświetl okno.  
  
- Skonfiguruj rozmiar, położenie i wygląd okna.  
  
- Hostowanie zawartości specyficznej dla aplikacji.  
  
- Zarządzanie okresem istnienia okna.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Implementowanie okna  
 Implementacja typowego okna składa się zarówno z wyglądu, jak i zachowania, w którym *wygląd* okna jest przeszukiwany użytkownikom i *zachowanie* definiuje sposób, w jaki okno działa jak użytkownicy. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]można zaimplementować wygląd i zachowanie okna przy użyciu kodu lub [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 Ogólnie rzecz biorąc, wygląd okna jest implementowany przy użyciu znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a jego zachowanie jest implementowane za pomocą kodu, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Aby umożliwić współdziałanie pliku znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i pliku związanego z kodem, wymagane są następujące elementy:  
  
- W znaczniku element `Window` musi zawierać atrybut `x:Class`. Po skompilowaniu aplikacji istnienie `x:Class` w pliku znaczników powoduje, że program Microsoft Build Engine (MSBuild) tworzy klasę `partial`, która pochodzi od <xref:System.Windows.Window> i ma nazwę określoną przez atrybut `x:Class`. Wymaga to dodania deklaracji przestrzeni nazw [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dla schematu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`). Wygenerowana Klasa `partial` implementuje metodę `InitializeComponent`, która jest wywoływana, aby zarejestrować zdarzenia i ustawić właściwości zaimplementowane w znaczniku.  
  
- W kodzie, Klasa musi być klasą `partial` o tej samej nazwie, która jest określona przez atrybut `x:Class` w znaczniku i musi pochodzić od <xref:System.Windows.Window>. Pozwala to skojarzyć plik związany z kodem z klasą `partial`, która jest generowana dla pliku znaczników podczas kompilowania aplikacji (zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)).  
  
- W kodzie, Klasa <xref:System.Windows.Window> musi implementować konstruktora, który wywołuje metodę `InitializeComponent`. `InitializeComponent` jest implementowana przez wygenerowaną przez plik znaczników `partial` klasę, aby zarejestrować zdarzenia i ustawić właściwości zdefiniowane w znaczniku.  
  
> [!NOTE]
> Po dodaniu nowego <xref:System.Windows.Window> do projektu przy użyciu programu Visual Studio, <xref:System.Windows.Window> jest implementowane przy użyciu znaczników i kodu, i zawiera konfigurację niezbędną do utworzenia skojarzenia między plikami znaczników i kodu, zgodnie z opisem w tym miejscu.  
  
 W przypadku tej konfiguracji można skupić się na definiowaniu wyglądu okna w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznika i implementacji jego zachowania w kodzie. W poniższym przykładzie pokazano okno z przyciskiem, zaimplementowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Markup i program obsługi zdarzeń dla zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click> przycisku zaimplementowanego w kodzie.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurowanie definicji okna dla programu MSBuild  
 Sposób implementacji okna decyduje o sposobie jego konfiguracji dla programu MSBuild. Dla okna, które jest zdefiniowane przy użyciu zarówno [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników, jak i kodu:  
  
- Pliki znaczników XAML są konfigurowane jako elementy `Page` programu MSBuild.  
  
- Pliki związane z kodem są konfigurowane jako elementy `Compile` programu MSBuild.  
  
 Jest to pokazane w następującym pliku projektu programu MSBuild.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Aby uzyskać informacje na temat tworzenia aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Okres istnienia okna  
 Podobnie jak w przypadku każdej klasy, okno ma okres istnienia rozpoczynający się po pierwszym utworzeniu wystąpienia, po którym jest otwierane, uaktywniane i dezaktywowane i ostatecznie zamknięte.  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Otwieranie okna  
 Aby otworzyć okno, należy najpierw utworzyć jego wystąpienie, które jest zademonstrowane w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 W tym przykładzie `MarkupAndCodeBehindWindow` jest tworzone podczas uruchamiania aplikacji, która występuje, gdy zdarzenie <xref:System.Windows.Application.Startup> zostanie zgłoszone.  
  
 Po utworzeniu wystąpienia okna odwołanie do niego jest automatycznie dodawane do listy systemu Windows, która jest zarządzana przez obiekt <xref:System.Windows.Application> (zobacz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>). Ponadto pierwsze okno, które ma zostać utworzone, jest domyślnie ustawiane przez <xref:System.Windows.Application> jako główne okno aplikacji (zobacz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 Okno jest ostatecznie otwarte przez wywołanie metody <xref:System.Windows.Window.Show%2A>; wyniki są pokazane na poniższym rysunku.  
  
 ![Okno otwarte przez wywołanie okna. show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Okno otwierane przez wywołanie <xref:System.Windows.Window.Show%2A> jest oknem niemodalnym, co oznacza, że aplikacja działa w trybie, który umożliwia użytkownikom aktywowanie innych okien w tej samej aplikacji.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A> jest wywoływana, aby otwierać okna, takie jak okna dialogowe modalnie. Aby uzyskać więcej informacji, zobacz [Omówienie okien](dialog-boxes-overview.md) dialogowych.  
  
 Gdy <xref:System.Windows.Window.Show%2A> jest wywoływana, okno wykonuje działanie inicjalizacji przed wyświetleniem infrastruktury, która pozwala na odbieranie danych przez użytkownika. Po zainicjowaniu okna zdarzenie <xref:System.Windows.Window.SourceInitialized> jest wywoływane i wyświetlane jest okno.  
  
 Jako skrót <xref:System.Windows.Application.StartupUri%2A> można ustawić, aby określić pierwsze okno, które jest otwierane automatycznie podczas uruchamiania aplikacji.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Po uruchomieniu aplikacji okno określone przez wartość <xref:System.Windows.Application.StartupUri%2A> jest otwierane niemodalnie; wewnętrznie okno jest otwierane przez wywołanie jego metody <xref:System.Windows.Window.Show%2A>.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Własność okna  
 Okno otwierane za pomocą metody <xref:System.Windows.Window.Show%2A> nie ma niejawnej relacji z oknem, które je utworzyło; Użytkownicy mogą korzystać z dowolnego okna niezależnie od siebie, co oznacza, że oba okna mogą wykonać następujące czynności:  
  
- Należy pokryć drugą (chyba że jeden z okien ma właściwość <xref:System.Windows.Window.Topmost%2A> ustawioną na `true`).  
  
- Być zminimalizowane, zmaksymalizowane i przywrócone bez wpływu na pozostałe.  
  
 Niektóre okna wymagają relacji z oknem, które je otwiera. Na przykład aplikacja zintegrowanego środowiska programistycznego (IDE) może otworzyć okno właściwości i okna narzędzi, których typowe zachowanie dotyczy tworzonego okna. Ponadto takie okna powinny zawsze zamykać, minimalizować, maksymalizować i przywracać w połączeniu z oknem, które je utworzyło. Tę relację można ustalić przez utworzenie jednego *okna innego i jest ono realizowane* przez ustawienie właściwości <xref:System.Windows.Window.Owner%2A> *należącego do okna* z odwołaniem do *okna właściciela*. Pokazano to w poniższym przykładzie.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Po ustanowieniu własności:  
  
- Posiadane okno może odwoływać się do swojego okna właściciela, sprawdzając wartość jego właściwości <xref:System.Windows.Window.Owner%2A>.  
  
- Okno właściciela może odnaleźć wszystkie okna, do których należy, sprawdzając wartość właściwości <xref:System.Windows.Window.OwnedWindows%2A>.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Zapobieganie aktywacji okna  
 Istnieją scenariusze, w których nie należy aktywować systemu Windows, na przykład w oknach konwersacji w aplikacji w stylu programu Messenger lub oknach powiadomień aplikacji poczty e-mail.  
  
 Jeśli aplikacja zawiera okno, które nie powinno być aktywowane, gdy jest wyświetlany, można ustawić jego właściwość <xref:System.Windows.Window.ShowActivated%2A> na `false` przed wywołaniem <xref:System.Windows.Window.Show%2A> metody po raz pierwszy. W związku z tym:  
  
- Okno nie zostało aktywowane.  
  
- Zdarzenie <xref:System.Windows.Window.Activated> okna nie zostało zgłoszone.  
  
- Uaktywnione okno zostanie uaktywnione.  
  
 Okno zostanie aktywowane, jednak natychmiast po jego aktywowaniu przez kliknięcie w obszarze klienta lub nieklienckiego. W takim przypadku:  
  
- Okno zostało aktywowane.  
  
- Zdarzenie <xref:System.Windows.Window.Activated> okna zostało zgłoszone.  
  
- Poprzednio aktywowane okno zostało zdezaktywowane.  
  
- Zdarzenia <xref:System.Windows.Window.Deactivated> i <xref:System.Windows.Window.Activated> okna są następnie podnoszone zgodnie z oczekiwaniami w odpowiedzi na akcje użytkownika.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Aktywacja okna  
 Gdy okno jest otwierane po raz pierwszy, przechodzi do aktywnego okna (chyba że jest wyświetlane z <xref:System.Windows.Window.ShowActivated%2A> ustawionym na `false`). *Aktywne okno* to okno, które aktualnie przechwytywa dane wprowadzane przez użytkownika, takie jak naciśnięcia klawiszy i kliknięć myszą. Gdy okno zostanie uaktywnione, wywołuje zdarzenie <xref:System.Windows.Window.Activated>.  
  
> [!NOTE]
> Po pierwszym otwarciu okna zdarzenia <xref:System.Windows.FrameworkElement.Loaded> i <xref:System.Windows.Window.ContentRendered> są wywoływane dopiero po podniesieniu zdarzenia <xref:System.Windows.Window.Activated>. Z tego względu okno może być efektywnie uważane za otwarte, gdy zostanie zgłoszone <xref:System.Windows.Window.ContentRendered>.  
  
 Gdy okno zostanie uaktywnione, użytkownik może aktywować inne okno w tej samej aplikacji lub aktywować inną aplikację. W takim przypadku aktywne okno zostanie zdezaktywowane i wygeneruje zdarzenie <xref:System.Windows.Window.Deactivated>. Podobnie, gdy użytkownik wybierze aktualnie dezaktywowane okno, okno zostanie ponownie aktywowane i zostanie zgłoszone <xref:System.Windows.Window.Activated>.  
  
 Jednym z typowych przyczyn obsługi <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated> jest włączenie i wyłączenie funkcji, która może być uruchamiana tylko wtedy, gdy okno jest aktywne. Na przykład niektóre okna wyświetlają zawartość interaktywną, która wymaga stałego wprowadzania danych przez użytkownika lub uwagi, w tym gier i odtwarzaczy wideo. Poniższy przykład to uproszczony odtwarzacz wideo, który pokazuje, jak obsłużyć <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated>, aby zaimplementować to zachowanie.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Inne typy aplikacji mogą nadal uruchamiać kod w tle, gdy okno zostanie zdezaktywowane. Na przykład klient poczty e-mail może kontynuować sondowanie serwera poczty, gdy użytkownik korzysta z innych aplikacji. Aplikacje takie jak często zapewniają różne lub dodatkowe zachowanie podczas dezaktywacji okna głównego. W odniesieniu do programu poczty może to oznaczać zarówno dodanie nowego elementu poczty do skrzynki odbiorczej, jak i dodanie ikony powiadomienia do paska zadań. Ikona powiadomienia musi być wyświetlana tylko wtedy, gdy okno poczty nie jest aktywne, które można określić, sprawdzając Właściwość <xref:System.Windows.Window.IsActive%2A>.  
  
 Jeśli zadanie w tle zakończy pracę, okno może chcieć pilnie powiadomić użytkownika przez wywołanie metody <xref:System.Windows.Window.Activate%2A>. Jeśli użytkownik korzysta z innej aplikacji aktywowanej po wywołaniu <xref:System.Windows.Window.Activate%2A>, zostanie uaktywniony przycisk paska zadań okna. Jeśli użytkownik korzysta z bieżącej aplikacji, wywołanie <xref:System.Windows.Window.Activate%2A> spowoduje przełączenie okna do pierwszego planu.  
  
> [!NOTE]
> Aktywację zakresu aplikacji można obsługiwać przy użyciu zdarzeń <xref:System.Windows.Application.Activated?displayProperty=nameWithType> i <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Zamykanie okna  
 Okres istnienia okna przechodzi do końca, gdy użytkownik go zamknie. Okno może być zamknięte przy użyciu elementów w obszarze nieklienckim, w tym:  
  
- Element **zamknięcia** menu **systemowego** .  
  
- Naciśnij klawisze ALT + F4.  
  
- Naciśnij przycisk **Zamknij** .  
  
 Do obszaru klienckiego można zapewnić dodatkowe mechanizmy zamykania okna, tym częściej są następujące:  
  
- Element **wyjścia** w menu **plik** , zazwyczaj dla głównych okien aplikacji.  
  
- **Zamknij** element w menu **plik** , zazwyczaj w oknie aplikacji dodatkowej.  
  
- Przycisk **Anuluj** , zazwyczaj na modalnym oknie dialogowym.  
  
- Przycisk **Zamknij** , zazwyczaj w niemodalnym oknie dialogowym.  
  
 Aby zamknąć okno w odpowiedzi na jeden z tych niestandardowych mechanizmów, należy wywołać metodę <xref:System.Windows.Window.Close%2A>. W poniższym przykładzie jest implementowana możliwość zamykania okna przez wybranie polecenia **Wyjdź** z menu **plik** .  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Gdy okno zostanie zamknięte, wywołuje dwa zdarzenia: <xref:System.Windows.Window.Closing> i <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing> jest wywoływane przed zamknięciem okna i udostępnia mechanizm, za pomocą którego można zablokować zamknięcie okna. Jednym z najczęstszych powodów, aby uniknąć zamykania okna, jest to, że zawartość okna zawiera zmodyfikowane dane. W takiej sytuacji można obsłużyć zdarzenie <xref:System.Windows.Window.Closing>, aby określić, czy dane są zanieczyszczone, a jeśli tak, to w celu poproszenia użytkownika o kontynuowanie zamykania okna bez zapisywania danych lub anulowania zamknięcia okna. W poniższym przykładzie przedstawiono kluczowe aspekty obsługi <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 Procedura obsługi zdarzeń <xref:System.Windows.Window.Closing> została przeniesiona <xref:System.ComponentModel.CancelEventArgs>, która implementuje Właściwość `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> ustawioną na `true`, aby zapobiec zamykaniu okna.  
  
 Jeśli <xref:System.Windows.Window.Closing> nie jest obsługiwana lub jest obsługiwana, ale nie została anulowana, okno zostanie zamknięte. Tuż przed faktycznym zamknięciem okna zostanie zgłoszone <xref:System.Windows.Window.Closed>. W tym momencie nie można uniemożliwić zamykania okna.  
  
> [!NOTE]
> Aplikację można skonfigurować tak, aby była automatycznie zamykana podczas zamykania okna aplikacji głównej (zobacz <xref:System.Windows.Application.MainWindow%2A>) lub ostatniego zamknięcia okna. Aby uzyskać szczegółowe informacje, zobacz <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Okno może być jawnie zamykane za pomocą mechanizmów dostępnych w obszarach nieklienta i klienta, a okno może być również niejawnie zamknięte w wyniku zachowania w innych częściach aplikacji lub systemu Windows, w tym:  
  
- Użytkownik wylogowuje się lub zamknie system Windows.  
  
- Zamknięcie właściciela okna (zobacz <xref:System.Windows.Window.Owner%2A>).  
  
- Okno aplikacji głównej jest zamknięte, a <xref:System.Windows.Application.ShutdownMode%2A> jest <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
- <xref:System.Windows.Application.Shutdown%2A> jest wywoływana.  
  
> [!NOTE]
> Nie można otworzyć ponownie okna po jego zamknięciu.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>Zdarzenia okresu istnienia okna  
 Na poniższej ilustracji przedstawiono sekwencję zdarzeń głównych w okresie istnienia okna:  
  
 ![Diagram przedstawiający zdarzenia w okresie istnienia okna.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Poniższa ilustracja przedstawia sekwencję zdarzeń głównych w okresie istnienia okna, które jest wyświetlane bez aktywacji (<xref:System.Windows.Window.ShowActivated%2A> jest ustawiona na `false` przed wyświetleniem okna):  
  
 ![Diagram przedstawiający zdarzenia w okresie istnienia bez aktywacji.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Lokalizacja okna  
 Gdy okno jest otwarte, ma miejsce w wymiarach x i y względem pulpitu. Tę lokalizację można określić, sprawdzając odpowiednio <xref:System.Windows.Window.Left%2A> i <xref:System.Windows.Window.Top%2A> właściwości. Można ustawić te właściwości, aby zmienić lokalizację okna.  
  
 Możesz również określić początkową lokalizację <xref:System.Windows.Window>, gdy po raz pierwszy pojawia się, ustawiając właściwość <xref:System.Windows.Window.WindowStartupLocation%2A> z jedną z następujących <xref:System.Windows.WindowStartupLocation> wartości wyliczenia:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (wartość domyślna)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Jeśli lokalizacja początkowa jest określona jako <xref:System.Windows.WindowStartupLocation.Manual>, a właściwości <xref:System.Windows.Window.Left%2A> i <xref:System.Windows.Window.Top%2A> nie zostały ustawione, <xref:System.Windows.Window> zostanie poproszony o podanie systemu Windows o lokalizację, w której ma się pojawić.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>System Windows i porządek Z góry  
 Poza lokalizacją x i y okno zawiera również lokalizację w wymiarze z, która określa położenie w pionie w odniesieniu do innych okien. Jest to znane jako porządek osi z okna, a istnieją dwa typy: normalna kolejność z i kolejność z góry. Lokalizacja okna w *normalnej kolejności z* jest określana na podstawie tego, czy jest ona obecnie aktywna, czy nie. Domyślnie okno znajduje się w normalnej kolejności z. Lokalizacja okna w *górnym porządku osi z* jest również określana na podstawie tego, czy jest ona obecnie aktywna, czy nie. Co więcej, okna w najwyższej kolejności z są zawsze zlokalizowane powyżej systemu Windows w normalnej kolejności z. Okno znajduje się w najwyższym porządku osi z, ustawiając właściwość <xref:System.Windows.Window.Topmost%2A> na `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 W każdym porządku osi z aktywne okno jest wyświetlane nad wszystkimi innymi oknami w tej samej kolejności z.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Rozmiar okna  
 Poza lokalizacją pulpitu okno ma rozmiar, który jest określany przez kilka właściwości, w tym różne właściwości width i height oraz <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>i <xref:System.Windows.FrameworkElement.MaxWidth%2A> są używane do zarządzania zakresem szerokości, które okno może mieć w okresie istnienia, i są skonfigurowane tak, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Wysokość okna jest zarządzana przez <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>i <xref:System.Windows.FrameworkElement.MaxHeight%2A>i są skonfigurowane, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Ponieważ różne wartości szerokości i wysokości określają zakres, możliwe jest, aby szerokość i wysokość okna o zmiennym rozmiarze znajdować się w dowolnym miejscu w określonym zakresie dla odpowiedniego wymiaru. Aby wykryć bieżącą szerokość i wysokość, należy odpowiednio zbadać <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A>.  
  
 Jeśli chcesz, aby szerokość i wysokość okna miały rozmiar, który pasuje do rozmiaru zawartości okna, możesz użyć właściwości <xref:System.Windows.Window.SizeToContent%2A>, która ma następujące wartości:  
  
- <xref:System.Windows.SizeToContent.Manual>., Brak efektu (wartość domyślna).  
  
- <xref:System.Windows.SizeToContent.Width>., Dopasuj do szerokości zawartości, która ma taki sam efekt jak ustawienie zarówno <xref:System.Windows.FrameworkElement.MinWidth%2A>, jak i <xref:System.Windows.FrameworkElement.MaxWidth%2A> do szerokości zawartości.  
  
- <xref:System.Windows.SizeToContent.Height>., Dopasuj do wysokości zawartości, która ma taki sam efekt jak ustawienie zarówno <xref:System.Windows.FrameworkElement.MinHeight%2A>, jak i <xref:System.Windows.FrameworkElement.MaxHeight%2A> do wysokości zawartości.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>., Dopasuj do szerokości i wysokości zawartości, która ma taki sam skutek jak ustawienie zarówno <xref:System.Windows.FrameworkElement.MinHeight%2A>, jak i <xref:System.Windows.FrameworkElement.MaxHeight%2A> do wysokości zawartości, i Ustawianie zarówno <xref:System.Windows.FrameworkElement.MinWidth%2A>, jak i <xref:System.Windows.FrameworkElement.MaxWidth%2A> do szerokości zawartości.  
  
 W poniższym przykładzie pokazano okno, które automatycznie dopasowuje rozmiar do jego zawartości, zarówno w pionie, jak i w poziomie.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Poniższy przykład pokazuje, jak ustawić właściwość <xref:System.Windows.Window.SizeToContent%2A> w kodzie, aby określić, jak zmienia się rozmiar okna w celu dopasowania do jego zawartości.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Kolejność pierwszeństwa we właściwościach ustalania wielkości  
 Zasadniczo różne rozmiary okna łączą się, aby zdefiniować zakres szerokości i wysokości okna o zmiennym rozmiarze. Aby zapewnić zachowanie prawidłowego zakresu, <xref:System.Windows.Window> oblicza wartości właściwości rozmiaru przy użyciu następujących kolejności pierwszeństwa.  
  
 **Dla właściwości wysokości:**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Dla właściwości width:**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Kolejność pierwszeństwa może również określać rozmiar okna, gdy jest zmaksymalizowane, które jest zarządzane za pomocą właściwości <xref:System.Windows.Window.WindowState%2A>.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>Stan okna  
 W okresie istnienia okna o zmiennym rozmiarze może istnieć trzy stany: normalny, zminimalizowany i zmaksymalizowany. Okno z *normalnym* stanem jest domyślnym stanem okna. Okno z tym stanem umożliwia użytkownikowi przeniesienie i zmianę jego rozmiaru przy użyciu uchwytu zmiany rozmiaru lub obramowania, jeśli zostanie on zmieniony.  
  
 Okno ze *zminimalizowanym* stanem jest zwijane do jego przycisku paska zadań, jeśli <xref:System.Windows.Window.ShowInTaskbar%2A> jest ustawiony na `true`; w przeciwnym razie zwija do najmniejszego możliwego rozmiaru, który może być i odszukany w lewym dolnym rogu pulpitu. Nie można zmienić rozmiaru okna zminimalizowanego za pomocą obramowania ani uchwytu zmiany rozmiaru, chociaż zminimalizowane okno, które nie jest wyświetlane na pasku zadań, może być przeciągane wokół pulpitu.  
  
 Okno z *zmaksymalizowanym* stanem rozwija się do maksymalnego rozmiaru, który może być, co będzie tak duże, jak <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>i <xref:System.Windows.Window.SizeToContent%2A> właściwości. Jak okno zminimalizowane, nie można zmienić rozmiaru zmaksymalizowanego okna przy użyciu uchwytu zmiany rozmiaru lub przeciągając obramowanie.  
  
> [!NOTE]
> Wartości właściwości <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>i <xref:System.Windows.FrameworkElement.Height%2A> okna zawsze reprezentują wartości dla normalnego stanu, nawet gdy okno jest obecnie zmaksymalizowane lub zminimalizowane.  
  
 Stan okna można skonfigurować przez ustawienie jego właściwości <xref:System.Windows.Window.WindowState%2A>, która może mieć jedną z następujących <xref:System.Windows.WindowState> wartości wyliczenia:  
  
- <xref:System.Windows.WindowState.Normal> (wartość domyślna)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 Poniższy przykład pokazuje, jak utworzyć okno, które jest wyświetlane jako zmaksymalizowane, gdy zostanie otwarte.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Ogólnie rzecz biorąc, należy ustawić <xref:System.Windows.Window.WindowState%2A>, aby skonfigurować stan początkowy okna. Po pobraniu okna o zmiennym rozmiarze użytkownicy mogą nacisnąć przyciski Minimalizuj, Maksymalizuj i Przywróć na pasku tytułu okna, aby zmienić stan okna.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Wygląd okna  
 Aby zmienić wygląd obszaru klienta okna, można dodać do niego zawartość specyficzną dla okna, taką jak przyciski, etykiety i pola tekstowe. Aby skonfigurować obszar niebędący klientem, <xref:System.Windows.Window> zawiera kilka właściwości, które obejmują <xref:System.Windows.Window.Icon%2A> do ustawiania ikony okna i <xref:System.Windows.Window.Title%2A> w celu ustawienia jej tytułu.  
  
 Możesz również zmienić wygląd i zachowanie obramowania obszaru nieklienckiego, konfigurując tryb zmiany rozmiaru okna, styl okna i czy jest on wyświetlany jako przycisk na pasku zadań pulpitu.  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Tryb zmiany rozmiaru  
 W zależności od właściwości <xref:System.Windows.Window.WindowStyle%2A> można kontrolować sposób, w jaki użytkownicy mogą zmieniać rozmiar okna. Wybór stylu okna ma wpływ na to, czy użytkownik może zmienić rozmiar okna, przeciągając jego obramowanie przy użyciu myszy, czy przyciski **Minimalizuj**, **Maksymalizuj**i **Zmień rozmiar** pojawiają się w obszarze nieklienckim i, jeśli są wyświetlane, niezależnie od tego, czy są dostępny.  
  
 Można skonfigurować sposób zmiany rozmiaru okna przez ustawienie jego właściwości <xref:System.Windows.Window.ResizeMode%2A>, która może być jedną z następujących <xref:System.Windows.ResizeMode> wartości wyliczenia:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (wartość domyślna)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Podobnie jak w przypadku <xref:System.Windows.Window.WindowStyle%2A>, tryb zmiany rozmiaru okna jest mało prawdopodobne, aby można go było zmienić w okresie istnienia, co oznacza, że najprawdopodobniej ustawisz go z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Należy zauważyć, że można wykryć, czy okno jest zmaksymalizowane, zminimalizowane lub przywrócone, sprawdzając Właściwość <xref:System.Windows.Window.WindowState%2A>.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Styl okna  
 Obramowanie, które jest widoczne z obszaru nieklienckiego okna, jest odpowiednie dla większości aplikacji. Istnieją jednak sytuacje, w których są zbędne różne typy obramowań lub nie są w ogóle stosowane żadne obramowania, w zależności od typu okna.  
  
 Aby sterować typem obramowania pobieranym przez okno, ustaw jej Właściwość <xref:System.Windows.Window.WindowStyle%2A> na jedną z następujących wartości wyliczenia <xref:System.Windows.WindowStyle>:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (wartość domyślna)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Efekt tych stylów okna przedstawiono na poniższej ilustracji:  
  
 ![Ilustracja stylów obramowania okna.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Można ustawić <xref:System.Windows.Window.WindowStyle%2A> przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników lub kodu; ponieważ nie można jej zmienić w okresie istnienia okna, najprawdopodobniej skonfigurujesz go przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Styl okna bez prostokąta  
 Istnieją również sytuacje, w których style obramowania, które <xref:System.Windows.Window.WindowStyle%2A> mogą być niewystarczające. Na przykład możesz chcieć utworzyć aplikację z obramowaniem nieprostokątnym, np. [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)].  
  
 Rozważmy na przykład okno dymek mowy pokazane na poniższym rysunku:  
  
 ![Okno bąbelka mowy z tekstem przeciągnij mnie.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Ten typ okna można utworzyć, ustawiając właściwość <xref:System.Windows.Window.WindowStyle%2A> na <xref:System.Windows.WindowStyle.None>i używając specjalnej pomocy technicznej, która <xref:System.Windows.Window> ma dla przezroczystości.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Ta kombinacja wartości powoduje, że okno jest renderowane całkowicie przezroczyste. W tym stanie nie można używać modułów definiowania układu nieklienckiego (zamknięcie menu, minimalizowania, maksymalizowania i przywracania). W związku z tym należy podać własny.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Obecność paska zadań  

Domyślny wygląd okna zawiera przycisk paska zadań, tak jak pokazano na poniższym rysunku:

 ![Zrzut ekranu pokazujący okno z przyciskiem paska zadań.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Niektóre typy okien nie mają przycisku paska zadań, takiego jak okna dialogowe komunikatów i okien dialogowych (zobacz [okna dialogowe — Omówienie](dialog-boxes-overview.md)). Można kontrolować, czy przycisk paska zadań dla okna jest pokazywany przez ustawienie właściwości <xref:System.Windows.Window.ShowInTaskbar%2A> (domyślnie`true`).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 <xref:System.Windows.Window> wymaga uprawnień zabezpieczeń `UnmanagedCode`, aby można było utworzyć wystąpienie. W przypadku aplikacji zainstalowanych na komputerze lokalnym i uruchamianych z niej jest to zestaw uprawnień, które są przyznawane aplikacji.  
  
 Jednak jest to poza zestawem uprawnień przyznanym aplikacjom, które są uruchamiane z Internetu lub lokalnej strefy intranetowej przy użyciu technologii ClickOnce. W związku z tym użytkownicy otrzymają ostrzeżenie o zabezpieczeniach technologii ClickOnce i będą musieli podnieść poziom uprawnień dla aplikacji do pełnego zaufania.  
  
 Ponadto [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nie może domyślnie pokazać okien ani okna dialogowego. Aby zapoznać się z zagadnieniami dotyczącymi zabezpieczeń aplikacji autonomicznych, zobacz [strategia zabezpieczeń WPF — zabezpieczenia platformy](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Inne typy okien  
 <xref:System.Windows.Navigation.NavigationWindow> to okno, które jest przeznaczone do hostowania zawartości nawigacji. Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](navigation-overview.md)).  
  
 Okna dialogowe to okna, które są często używane do zbierania informacji od użytkownika w celu ukończenia funkcji. Na przykład, gdy użytkownik chce otworzyć plik, okno dialogowe **Otwórz plik** jest zwykle wyświetlane przez aplikację w celu uzyskania nazwy pliku od użytkownika. Aby uzyskać więcej informacji, zobacz [okna dialogowe przegląd](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Okna dialogowe — omówienie](dialog-boxes-overview.md)
- [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)
