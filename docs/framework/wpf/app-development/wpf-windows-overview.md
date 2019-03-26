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
ms.openlocfilehash: ab9b36857e2508190a212844f3c6b53d777c0552
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466221"
---
# <a name="wpf-windows-overview"></a>Przegląd Okna WPF
Użytkownicy wchodzić w interakcje z aplikacjami autonomicznego Windows Presentation Foundation (WPF) za pośrednictwem systemu windows. Głównym celem okna jest do hostowania zawartości, która wizualizuje dane oraz umożliwia użytkownikom na interakcję z danymi. Autonomiczny [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje zapewniają własne systemu windows przy użyciu <xref:System.Windows.Window> klasy. W tym temacie przedstawiono <xref:System.Windows.Window> przed obejmujące podstawowe informacje dotyczące tworzenia i zarządzania systemem windows w aplikacje autonomiczne.  
  
> [!NOTE]
>  Hostowana w przeglądarce [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, w tym [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i utracić wprowadzone [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stron, nie udostępniają ich własnych systemu windows. Zamiast tego są hostowane w systemie windows, dostarczone przez [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]. Zobacz [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).  
  
  
<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Klasy okna  
 Na poniższym rysunku przedstawiono części składowe okna:  
  
 ![Zrzut ekranu pokazujący elementy okna.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Okno jest podzielony na dwóch obszarach: obszaru nieklienckiego i obszaru klienta.  
  
 *Obszaru nieklienckiego* okna jest implementowany przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i zawiera elementy okna, które są wspólne dla większości windows, w tym następujące czynności:  
  
-   Obramowanie.  
  
-   Pasek tytułu.  
  
-   Ikona.  
  
-   Minimalizuj, Maksymalizuj i przywrócić przycisków.  
  
-   Przycisk Zamknij.  
  
-   Menu systemowe z elementami menu, które umożliwiają użytkownikom zminimalizować, zmaksymalizować, przywracania, przenoszenie, zmienianie rozmiaru i zamknąć okno.  
  
 *Obszaru klienckiego* okna jest obszar w obrębie obszaru nieklienckiego okna i używanych przez deweloperów, aby dodać zawartość specyficzne dla aplikacji, takich jak paski menu i pasków narzędzi, formantów.  
  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], okno jest hermetyzowany przez <xref:System.Windows.Window> klasę, która umożliwia wykonaj następujące czynności:  
  
-   Wyświetla okno.  
  
-   Skonfiguruj rozmiarem, pozycją i wygląd okna.  
  
-   Zawartość specyficzną dla aplikacji hosta.  
  
-   Zarządzanie okresem istnienia okna.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Implementowanie okna  
 Implementacja typowego okna składa się z wyglądem i zachowaniem, gdzie *wygląd* definiuje wygląd okna dla użytkowników i *zachowanie* definiuje sposób, w oknie funkcje, jak użytkownicy wchodzą w interakcję z nim. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], można zaimplementować wygląd i zachowanie przy użyciu okna albo kod lub [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 Ogólnie rzecz biorąc, jednak wygląd okna jest implementowany przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i jego zachowanie jest implementowany przy użyciu związanym z kodem, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Aby włączyć [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku znaczników i pliku związanego z kodem pracy zespołowej, wymagane są następujące:  
  
-   W znaczniku `Window` element musi zawierać `x:Class` atrybutu. Podczas kompilowania aplikacji, istnienie `x:Class` w znaczniku pliku powoduje, że [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] utworzyć `partial` klasę pochodzącą od <xref:System.Windows.Window> i ma nazwę, która jest określona przez `x:Class` atrybutu. Wymaga to dodania [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklarację przestrzeni nazw dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schematu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Wygenerowany `partial` klasy implementuje `InitializeComponent` metody, która jest wywoływana, aby rejestrować zdarzenia i ustawić właściwości, które są implementowane w znacznikach.  
  
-   Związane z kodem, klasy musi być `partial` klasy o takiej samej nazwie, który jest określony przez `x:Class` atrybutu w kodzie znaczników oraz jego musi pochodzić od klasy <xref:System.Windows.Window>. Dzięki temu pliku związanego z kodem, który ma zostać skojarzony z `partial` klasy, który jest generowany dla pliku znaczników Po skompilowaniu aplikację (zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)).  
  
-   W związanym z kodem <xref:System.Windows.Window> klasy należy zaimplementować konstruktora, który wywołuje `InitializeComponent` metody. `InitializeComponent` jest implementowana przez znaczniki użytkownika wygenerowany plik `partial` klasy, aby rejestrować zdarzenia i ustawić właściwości, które są zdefiniowane w znacznikach.  
  
> [!NOTE]
>  Po dodaniu nowego <xref:System.Windows.Window> do projektu przy użyciu [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> jest implementowany przy użyciu znaczników i związane z kodem i zawiera niezbędną konfigurację, aby utworzyć skojarzenie między plikami znaczników i związane z kodem jako opisane w tym miejscu.  
  
 W przypadku tej konfiguracji w miejscu możesz skupić się na temat definiowania wygląd okna [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i wdrażanie jej zachowanie w związanym z kodem. W poniższym przykładzie pokazano okna za pomocą przycisku, zaimplementować w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i program obsługi zdarzeń dla przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń, zaimplementowane w związanym z kodem.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurowanie definicji okna dla programu MSBuild  
 Określa sposób implementacji okna, jak została ona skonfigurowana do [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]. Okna, która jest zdefiniowana przy użyciu zarówno [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i związane z kodem:  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki znaczników są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementów.  
  
-   Pliki związane z kodem są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` elementów.  
  
 Jest to pokazane w następującym [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] pliku projektu.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Aby uzyskać informacje dotyczące tworzenia aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Okres istnienia okna  
 Jak za pomocą dowolnej klasy okna ma okres istnienia, który rozpoczyna się, gdy najpierw zostanie uruchomiony, po upływie którego otwarte, aktywowane i dezaktywowane i zamknięte po pewnym czasie.  
  
  
<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Otwierając okno  
 Aby otworzyć okno, należy najpierw utworzyć jego wystąpienie, które przedstawiono w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 W tym przykładzie `MarkupAndCodeBehindWindow` zostanie uruchomiony podczas uruchamiania aplikacji, która pojawia się po <xref:System.Windows.Application.Startup> zdarzenie jest wywoływane.  
  
 Podczas tworzenia wystąpienia okna odwołanie do niej jest automatycznie dodawane do listy systemu windows, który jest zarządzany przez <xref:System.Windows.Application> obiekt (zobacz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>). Ponadto pierwsze okno z myślą o uruchamianiu domyślnie ustawione <xref:System.Windows.Application> jako okna głównego aplikacji (zobacz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 Na koniec otwierania okna przez wywołanie metody <xref:System.Windows.Window.Show%2A> metody; wynik jest wyświetlany na poniższej ilustracji.  
  
 ![Okno otwarte przez wywołanie metody Window.Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Okno, w którym jest otwarta przez wywołanie <xref:System.Windows.Window.Show%2A> jest oknem niemodalnym, co oznacza, że aplikacja działa w trybie który pozwala użytkownikom na uaktywnienie innych okien w tej samej aplikacji.  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A> jest wywoływana, aby otworzyć systemu windows, takich jak okna dialogowe w trybie modalnym. Zobacz [Przegląd okien dialogowych](dialog-boxes-overview.md) Aby uzyskać więcej informacji.  
  
 Gdy <xref:System.Windows.Window.Show%2A> jest wywoływana, okno wykonuje pracę inicjowania z przed wyświetleniem ustanowienia infrastruktury, który umożliwia odbieranie danych wejściowych użytkownika. Po zainicjowaniu okna <xref:System.Windows.Window.SourceInitialized> zdarzenie jest zgłaszane i pokazaniem okna.  
  
 Jako skrót <xref:System.Windows.Application.StartupUri%2A> można ustawić, aby określić pierwsze okno, który jest otwierany automatycznie podczas uruchamiania aplikacji.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Po uruchomieniu aplikacji, okna określony przez wartość <xref:System.Windows.Application.StartupUri%2A> jest otwarty modelessly; wewnętrznie, okno jest otwierane przez wywołanie jego <xref:System.Windows.Window.Show%2A> metody.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Własność okna  
 Okno, który jest otwierany przy użyciu <xref:System.Windows.Window.Show%2A> metoda nie ma niejawnych relacji z okna, w której został utworzony; interakcji użytkowników z dowolnym z okien niezależnie od innych, co oznacza, że którekolwiek okno można wykonać następujące czynności:  
  
-   Zakrywała drugą (chyba że jeden z systemu windows ma jego <xref:System.Windows.Window.Topmost%2A> właściwością `true`).  
  
-   Można zminimalizować, w trybie zmaksymalizowanym i przywrócenie bez wpływu na drugi.  
  
 Niektóre okna wymagają relacji z oknem, które otwiera je. Na przykład [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] aplikacja może otworzyć właściwości systemu windows i okien narzędzi, których typowe zachowanie ma na celu obejmują okna, w której zostały utworzone. Ponadto tych okien powinien zawsze zamknąć, zminimalizować, maksymalizacji i przywracania w połączeniu z okna, w której zostały utworzone. Takiej relacji można nawiązać, wprowadzając jedno okno *własnych* inny i odbywa się przez ustawienie <xref:System.Windows.Window.Owner%2A> właściwość *należące do okna* z odwołaniem do *właściciela okno*. Jest to pokazane w poniższym przykładzie.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Po ustanowieniu własności:  
  
-   Należących do okna może odwoływać się okna jego właściciela, sprawdzając wartość jego <xref:System.Windows.Window.Owner%2A> właściwości.  
  
-   Okno właściciela może odnajdować wszystkich okien jest właścicielem, sprawdzając wartość jego <xref:System.Windows.Window.OwnedWindows%2A> właściwości.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Zapobieganie aktywacji okna  
 Istnieją scenariusze, w której systemu windows nie należy aktywować, gdy wyświetlana, takiego jak windows konwersacji stosowania stylu messenger Internet lub windows powiadomienia z aplikacji poczty e-mail.  
  
 Jeśli aplikacja ma okno które nie powinny być aktywowany, gdy wyświetlany, możesz ustawić jej <xref:System.Windows.Window.ShowActivated%2A> właściwości `false` przed wywołaniem <xref:System.Windows.Window.Show%2A> metoda po raz pierwszy. W rezultacie:  
  
-   Okno nie jest aktywna.  
  
-   W oknie <xref:System.Windows.Window.Activated> zdarzenie jest zgłaszane w nie.  
  
-   Obecnie aktywowane okno pozostaje aktywowane.  
  
 Okno zostanie stają się aktywowane, jednak zaraz po użytkownik aktywuje go, klikając klienta lub obszaru nieklienckiego. W takim przypadku:  
  
-   Okno jest aktywowane.  
  
-   W oknie <xref:System.Windows.Window.Activated> zdarzenie jest wywoływane.  
  
-   Wcześniej aktywowane okno jest zdezaktywowane.  
  
-   W oknie <xref:System.Windows.Window.Deactivated> i <xref:System.Windows.Window.Activated> zdarzenia są wywoływane później, zgodnie z oczekiwaniami w odpowiedzi na działania użytkownika.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Okno aktywacji  
 Przy pierwszym otwarciu okna, staje się aktywnym oknem (o ile nie jest wyświetlana przy użyciu <xref:System.Windows.Window.ShowActivated%2A> równa `false`). *Aktywne okno* jest oknem, które aktualnie przechwytuje dane wejściowe użytkownika, takie jak naciśniętych klawiszy i myszą. Gdy okno staje się aktywny, zgłasza <xref:System.Windows.Window.Activated> zdarzeń.  
  
> [!NOTE]
>  Przy pierwszym otwarciu okna, <xref:System.Windows.FrameworkElement.Loaded> i <xref:System.Windows.Window.ContentRendered> zdarzenia są wywoływane tylko po <xref:System.Windows.Window.Activated> zdarzenie jest wywoływane. Pamiętając o tym, okno skutecznie jest uznawana za otwarte po <xref:System.Windows.Window.ContentRendered> jest wywoływane.  
  
 Po uaktywnieniu okna użytkownik może aktywować innego okna w tej samej aplikacji lub Aktywuj innej aplikacji. Jeśli tak się stanie, aktualnie aktywne okno staje się dezaktywowane i zgłasza <xref:System.Windows.Window.Deactivated> zdarzeń. Podobnie, gdy użytkownik wybierze obecnie dezaktywowane okna, okno ponownie staje się aktywny i <xref:System.Windows.Window.Activated> jest wywoływane.  
  
 Jednym z typowych powodów obsługi <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated> jest pozwala włączać i wyłączać funkcje, które można uruchamiać tylko, gdy okno jest aktywne. Na przykład niektóre okna wyświetlania zawartości interaktywnej, która wymaga danych wejściowych użytkownika stałej lub uwagi, łącznie z gier i odtwarzacze wideo. Poniższy przykład to uproszczona odtwarzacz wideo, który pokazuje, jak obsługiwać <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated> Aby zaimplementować to zachowanie.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Innych typów aplikacji nadal może uruchomić kod w tle, gdy okno jest dezaktywowany. Na przykład klienta poczty e-mail mogą nadal sondowania na serwerze poczty e-mail, gdy użytkownik korzysta z innych aplikacji. Aplikacje, takie jak te często udostępniają inne lub dodatkowe zachowanie podczas dezaktywacji głównego okna. W odniesieniu do domyślnego programu poczty może to oznaczać zarówno dodawania nowego elementu poczty w skrzynce odbiorczej i ikona powiadomień na pasku zadań. Ikona powiadomień muszą wyświetlane tylko wtedy, gdy okno poczty nie jest aktywne, w którym można ustalić, sprawdzając <xref:System.Windows.Window.IsActive%2A> właściwości.  
  
 Po ukończeniu zadania w tle, okno może być bardziej pilnie powiadomienie użytkownika, wywołując <xref:System.Windows.Window.Activate%2A> metody. Jeśli użytkownik prowadzi interakcję z innej aplikacji aktywowane gdy <xref:System.Windows.Window.Activate%2A> nosi okna przycisk na pasku zadań miga. Jeśli użytkownik prowadzi interakcję z bieżącej aplikacji, podczas wywoływania <xref:System.Windows.Window.Activate%2A> zostanie wyświetlone okno na pierwszy plan.  
  
> [!NOTE]
>  Może obsługiwać aktywacji zakresu aplikacji przy użyciu <xref:System.Windows.Application.Activated?displayProperty=nameWithType> i <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> zdarzenia.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Zamknięcie okna  
 Czas życia okna uruchamia pochodzące-to-end, gdy użytkownik zamknie go. Okno może zostać zamknięty przy użyciu elementów w obszaru nieklienckiego, takie jak następujące:  
  
-   **Zamknij** elementu **systemu** menu.  
  
-   Naciskając klawisze ALT + F4.  
  
-   Naciśnięcie klawisza **Zamknij** przycisku.  
  
 Możesz podać dodatkowe mechanizmy obszaru klienta, aby zamknąć to okno, częściej stosowana, które są następujące:  
  
-   **Zakończenia** pozycja **pliku** menu, zwykle dla głównej aplikacji systemu windows.  
  
-   A **Zamknij** pozycja **pliku** menu, zazwyczaj w oknie drugą aplikację.  
  
-   A **anulować** przycisk, zazwyczaj w modalne okno dialogowe.  
  
-   A **Zamknij** przycisk, zazwyczaj w niemodalnego okna dialogowego.  
  
 Aby zamknąć okno w odpowiedzi na jeden z tych mechanizmów niestandardowe, należy wywołać <xref:System.Windows.Window.Close%2A> metody. Poniższy przykład implementuje możliwości, aby zamknąć okno, wybierając **zakończenia** na **pliku** menu.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Po zamknięciu okna, zgłasza dwa zdarzenia: <xref:System.Windows.Window.Closing> i <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing> jest wywoływane przed okno zostanie zamknięte i zapewnia mechanizm, w jakim oknie można zapobiec zamknięcia. Jednym z typowych powodów zapobiec zamknięcia okna jest, czy zawartości okna zawiera zmodyfikowanych danych. W takiej sytuacji <xref:System.Windows.Window.Closing> zdarzenia mogą być obsługiwane w celu ustalenia, czy danych został zmieniony, a jeśli tak, aby poprosić użytkownika, czy kontynuować zamknięciu okna bez zapisywania danych do anulowania zamknięcia okna. W poniższym przykładzie przedstawiono kluczowe aspekty obsługi <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  
 
  
 <xref:System.Windows.Window.Closing> Programu obsługi zdarzeń jest przekazywany <xref:System.ComponentModel.CancelEventArgs>, który implementuje `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość, która jest ustawiona na `true` zapobiegające zamknięcia okna.  
  
 Jeśli <xref:System.Windows.Window.Closing> nie jest obsługiwany lub jest obsługiwane, ale nie zostało anulowane, okno zostanie zamknięte. Tuż przed, w rzeczywistości powoduje zamknięcie okna <xref:System.Windows.Window.Closed> jest wywoływane. W tym momencie okna nie można zablokować zamknięcia.  
  
> [!NOTE]
>  Aplikację można skonfigurować w celu zamknięcia automatycznie, gdy okna głównego aplikacji zamyka (zobacz <xref:System.Windows.Application.MainWindow%2A>) lub ostatni okno zostanie zamknięte. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Gdy okno może być jawnie zamknięty przy użyciu mechanizmów udostępnianych w obszarach i bez klienta, okna może także zostać niejawnie zamknięty wyniku zachowanie w innych częściach aplikacji lub [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], w tym następujące czynności:  
  
-   Użytkownik wyloguje się lub kończy pracę Windows.  
  
-   Zamyka okno właściciela (zobacz <xref:System.Windows.Window.Owner%2A>).  
  
-   Zamknięto okna głównego aplikacji i <xref:System.Windows.Application.ShutdownMode%2A> jest <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
-   <xref:System.Windows.Application.Shutdown%2A> jest wywoływana.  
  
> [!NOTE]
>  Nie można ponownie otworzyć okno, po jego zamknięciu.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>Zdarzenia okresu istnienia okna  
 Poniższa ilustracja przedstawia kolejność zdarzeń główną w trakcie trwania okna:  
  
 ![Diagram pokazujący zdarzenia w okresie istnienia okna.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Poniższa ilustracja przedstawia kolejność zdarzeń jednostki w okres istnienia okna, która jest wyświetlana bez aktywacji (<xref:System.Windows.Window.ShowActivated%2A> ustawiono `false` przed pokazaniem okna):  
  
 ![Diagram pokazujący zdarzenia w okresie istnienia okna, bez aktywacji.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Położenie okna  
 Gdy okno jest otwarte, ma miejsce w x i y wymiarach pulpitu. Ta lokalizacja można ustalić, sprawdzając <xref:System.Windows.Window.Left%2A> i <xref:System.Windows.Window.Top%2A> właściwości, odpowiednio. Możesz ustawić te właściwości, aby zmienić położenie okna.  
  
 Można również określić początkową lokalizację <xref:System.Windows.Window> , gdy najpierw pojawia się przez ustawienie <xref:System.Windows.Window.WindowStartupLocation%2A> właściwości o jedną z następujących <xref:System.Windows.WindowStartupLocation> wartości wyliczenia:  
  
-   <xref:System.Windows.WindowStartupLocation.CenterOwner> (ustawienie domyślne)  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Jeśli lokalizacja uruchamiania jest określona jako <xref:System.Windows.WindowStartupLocation.Manual>i <xref:System.Windows.Window.Left%2A> i <xref:System.Windows.Window.Top%2A> nie ustawiono właściwości <xref:System.Windows.Window> poprosi Windows dla lokalizacji, które będą wyświetlane na.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>Windows najwyższego poziomu i porządek osi z  
 Oprócz znaku x i y lokalizacji, okno również ma miejsce w przypadku wymiaru z określa jej położenie w pionie względem innych okien. Jest to nazywane okna porządek osi z, a istnieją dwa typy: Normalny porządek i porządek najwyższego poziomu. Położenie okna w *normalne porządek* zależy od tego, czy jest aktualnie aktywne lub nie. Domyślnie okno znajduje się w normalnej kolejności. Położenie okna w *najwyższym porządku* również zależy od tego, czy jest aktualnie aktywne lub nie. Ponadto systemu windows w najwyższym porządku zawsze znajdują się powyżej systemu windows w normalnej kolejności. Okno znajduje się w najwyższym porządku, ustawiając jego <xref:System.Windows.Window.Topmost%2A> właściwość `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 W ramach każdej kolejności z aktualnie aktywnego okna pojawi się przede wszystkim innych okien w tej samej kolejności.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Rozmiar okna  
 Oprócz zainstalowanej w lokalizacji pulpitu, okno ma rozmiar, który jest określany przez kilka właściwości, w tym różne właściwości width i height i <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, i <xref:System.Windows.FrameworkElement.MaxWidth%2A> służą do zarządzania zakresem szerokości, które mogą mieć jego okres istnienia okna i są skonfigurowane, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Wysokość okna jest zarządzana przez <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, i <xref:System.Windows.FrameworkElement.MaxHeight%2A>i są skonfigurowane, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Ponieważ różne wartości szerokości, jak i wysokość wartości należy określić zakres, jest możliwe dla szerokości i wysokości okna z możliwością zmiany rozmiaru się znajdować w dowolnym miejscu w obrębie określonego zakresu dla odpowiedniego wymiaru. Aby wykryć, jego bieżące szerokość i wysokość, należy sprawdzić <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A>, odpowiednio.  
  
 Jeśli chcesz, szerokość i wysokość okna do rozmiaru, która pasuje do rozmiaru okna zawartości, można użyć <xref:System.Windows.Window.SizeToContent%2A> właściwość, która ma następujące wartości:  
  
-   <xref:System.Windows.SizeToContent.Manual>. Brak wpływu (ustawienie domyślne).  
  
-   <xref:System.Windows.SizeToContent.Width>. Dopasuj do szerokości zawartości, która ma ten sam efekt jak ustawienie oba <xref:System.Windows.FrameworkElement.MinWidth%2A> i <xref:System.Windows.FrameworkElement.MaxWidth%2A> szerokość zawartości.  
  
-   <xref:System.Windows.SizeToContent.Height>. Dopasuj do wysokości zawartości, która ma ten sam efekt jak ustawienie oba <xref:System.Windows.FrameworkElement.MinHeight%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> do wysokości elementu zawartości.  
  
-   <xref:System.Windows.SizeToContent.WidthAndHeight>. Dopasuj do zawartości szerokość i wysokość, który ma ten sam efekt jak ustawienie oba <xref:System.Windows.FrameworkElement.MinHeight%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> do wysokości elementu zawartości i ustawienie oba <xref:System.Windows.FrameworkElement.MinWidth%2A> i <xref:System.Windows.FrameworkElement.MaxWidth%2A> szerokość zawartości.  
  
 Poniższy przykład pokazuje okno automatycznie rozmiarów do określonych jego zawartość w pionie i poziomie, przy pierwszym wyświetleniu.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Window.SizeToContent%2A> właściwości w kodzie, aby określić, jak zmienia rozmiar okna dopasowana do jego zawartości.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Kolejność pierwszeństwa właściwości ustalania rozmiaru  
 Zasadniczo różne właściwości rozmiary okna są łączone w celu zdefiniowania zakresu szerokości i wysokości okna o zmiennym rozmiarze. Aby zapewnić prawidłowy zakres jest utrzymywana, <xref:System.Windows.Window> oblicza wartości właściwości rozmiaru przy użyciu następujących zamówień pierwszeństwo.  
  
 **Dla właściwości wysokości:**  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3.  <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Dla właściwości szerokości:**  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3.  <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Kolejność pierwszeństwa można również określić rozmiaru okna, jeśli go jest zmaksymalizowane, która jest zarządzana przy użyciu <xref:System.Windows.Window.WindowState%2A> właściwości.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>Stanu okna  
 W okresie istnienia okna o zmiennym rozmiarze, mogą mieć trzy stany: Normalny, zminimalizowany i zmaksymalizowane. Okno z *normalne* stanu jest domyślny stan okna. Okno z tego stanu umożliwia użytkownikowi przenoszenie i zmienianie rozmiaru go za pomocą uchwyt zmiany rozmiaru lub obramowania, jeśli o zmiennym rozmiarze.  
  
 Okno z *zminimalizowane* stanu jest ustawiana na jego przycisk paska zadań Jeśli <xref:System.Windows.Window.ShowInTaskbar%2A> jest równa `true`; w przeciwnym razie go jest ustawiana na możliwie jak najmniejszego rozmiaru może być i przenosi się na lewym dolnym rogu pulpitu. Ani typ zminimalizowane okno rozmiar można zmieniać za pomocą obramowanie lub zmień rozmiar uchwytu, mimo że zminimalizowane okno, który nie jest wyświetlany na pasku zadań mogą być przeciągnięte na pulpicie.  
  
 Okno z *zmaksymalizowane* stanu rozwija się do maksymalnego rozmiaru może być tylko będzie tak duże jak jego <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, i <xref:System.Windows.Window.SizeToContent%2A> dyktować właściwości. Podobnie jak zminimalizowane okno zmaksymalizowane okno nie można zmienić rozmiaru za pomocą uchwyt zmiany rozmiaru lub przeciągając obramowania.  
  
> [!NOTE]
>  Wartości <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, i <xref:System.Windows.FrameworkElement.Height%2A> właściwości okna zawsze reprezentują wartości to normalny stan nawet wtedy, gdy okno jest obecnie zmaksymalizowany lub zminimalizowany.  
  
 Stan okna można skonfigurować, ustawiając jego <xref:System.Windows.Window.WindowState%2A> właściwość, która może mieć jedną z następujących <xref:System.Windows.WindowState> wartości wyliczenia:  
  
-   <xref:System.Windows.WindowState.Normal> (ustawienie domyślne)  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 Poniższy przykład pokazuje, jak utworzyć okno które zostanie wyświetlone jako zmaksymalizowany po jego otwarciu.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Ogólnie rzecz biorąc, należy ustawić <xref:System.Windows.Window.WindowState%2A> skonfigurować początkowy stan okna. Gdy zostanie wyświetlone okno o zmiennym rozmiarze, użytkownicy można naciśnij przycisk Minimalizuj, maksymalizować i przywracać przycisków na pasku tytułu okna, aby zmienić stan okna.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Wygląd okna  
 Możesz zmienić wygląd obszaru klienckiego okna przez dodanie zawartości określonego okna, takie jak przyciski, etykiety i pola tekstowe. Aby skonfigurować obszaru nieklienckiego <xref:System.Windows.Window> udostępnia kilka właściwości, które zawierają <xref:System.Windows.Window.Icon%2A> można ustawić ikonę okna i <xref:System.Windows.Window.Title%2A> można ustawić tytułu.  
  
 Możesz również zmienić wygląd i zachowanie obramowania obszaru nieklienckiego, konfigurując tryb zmiany rozmiaru okna, styl okna, czy jest on wyświetlany jako przycisk na pasku zadań pulpitu.  
  
  
<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Zmiana rozmiaru w trybie  
 W zależności od <xref:System.Windows.Window.WindowStyle%2A> właściwości, można kontrolować, jak (i czy) użytkownicy mogą zmieniać rozmiar okna. Wybór styl okna wpływa na, czy użytkownik może zmienić rozmiar okna, przeciągając jego obramowania przy użyciu myszy czy **Minimalizuj**, **Maksymalizuj**, i **rozmiar** przycisków pojawiają się na obszaru nieklienckiego i, jeśli pojawią się, czy są włączone.  
  
 Można skonfigurować, jak okno zmienia rozmiar przez ustawienie jego <xref:System.Windows.Window.ResizeMode%2A> właściwość, która może być jedną z następujących <xref:System.Windows.ResizeMode> wartości wyliczenia:  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <xref:System.Windows.ResizeMode.CanResize> (ustawienie domyślne)  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Podobnie jak w przypadku <xref:System.Windows.Window.WindowStyle%2A>, tryb zmiany rozmiaru okna jest mało prawdopodobne zmienić jego okres istnienia, oznacza to, czy będzie prawdopodobnie ustawisz go z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Należy zauważyć, że może wykryć, czy okno jest zmaksymalizowane, zminimalizowane lub przywrócone, sprawdzając <xref:System.Windows.Window.WindowState%2A> właściwości.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Styl okna  
 Obramowanie, która jest widoczna przy użyciu obszaru nieklienckiego okna jest odpowiedni dla większości aplikacji. Istnieją jednak okoliczności, w którym różnego rodzaju obramowania są potrzebne lub brak obramowania są potrzebne, w zależności od typu okna.  
  
 Do kontrolowania, jaki typ obramowania okna pobiera, ustawia jego <xref:System.Windows.Window.WindowStyle%2A> właściwości przy użyciu jednego z następujących wartości <xref:System.Windows.WindowStyle> wyliczenia:  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <xref:System.Windows.WindowStyle.SingleBorderWindow> (ustawienie domyślne)  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Efekt te style okna ramowego zostały zilustrowane na poniższym rysunku:  
  
 ![Ilustracja style obramowania okna.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Możesz ustawić <xref:System.Windows.Window.WindowStyle%2A> za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników lub innego kodu; ponieważ jest to raczej nie ulegnie zmianie w okresie istnienia okna, najprawdopodobniej skonfigurujesz go za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Styl okna niż prostokątny  
 Istnieją również sytuacji, w którym obramowania style, które <xref:System.Windows.Window.WindowStyle%2A> umożliwia posiadania nie są wystarczające. Na przykład, warto utworzyć aplikację z innych niż prostokątne obramowania, takich jak [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] używa.  
  
 Na przykład należy wziąć pod uwagę okna bąbelków mowy pokazano na poniższej ilustracji:  
  
 ![Okno bąbelków mowy, które mówi mnie przeciągania.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Okna tego typu mogą być tworzone przez ustawienie <xref:System.Windows.Window.WindowStyle%2A> właściwości <xref:System.Windows.WindowStyle.None>i za pomocą specjalnych obsługują <xref:System.Windows.Window> ma przezroczystości.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Ta kombinacja wartości powoduje, że okno do renderowania całkowicie przezroczysty. W tym stanie nie można użyć okna obszaru nieklienckiego zakończeń (Zamknij menu, przyciski Minimalizuj, Maksymalizuj i przywracania i tak dalej). W związku z tym należy podać własne.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Obecność na pasku zadań  

Domyślny wygląd okna zawiera przycisk na pasku zadań, tak jak pokazano na poniższej ilustracji:

 ![Zrzut ekranu pokazujący okno z przyciskiem paska zadań.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Niektóre typy systemu windows nie mają przycisk paska zadań, takich jak komunikatów i okien dialogowych (zobacz [Przegląd okien dialogowych](dialog-boxes-overview.md)). Można kontrolować, czy przycisk paska zadań dla okna jest pokazywane, ustawiając <xref:System.Windows.Window.ShowInTaskbar%2A> właściwości (`true` domyślnie).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 <xref:System.Windows.Window> wymaga `UnmanagedCode` uprawnienie zabezpieczeń należy utworzyć wystąpienie. W przypadku aplikacji zainstalowanym i uruchomić z komputera lokalnego to mieści się w zestaw uprawnień przypisanych do aplikacji.  
  
 Jednak to znajduje się poza zestaw uprawnień udzielonych aplikacji, które są uruchomione w Internet lub lokalny intranet strefy przy użyciu [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]. W związku z tym, użytkownicy będą otrzymywać [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] ostrzeżenie o zabezpieczeniach i konieczne będzie podniesienie poziomu zestawu uprawnień dla aplikacji na w pełni zaufany.  
  
 Ponadto [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] domyślnie nie można wyświetlić systemu windows lub w oknach dialogowych. Do dyskusji na temat zagadnień dotyczących zabezpieczeń aplikacji autonomicznych, zobacz [strategia zabezpieczeń WPF - zabezpieczenia platformy](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Inne rodzaje Windows  
 <xref:System.Windows.Navigation.NavigationWindow> to okno, który jest przeznaczony do hostowania zawartości można nawigować. Aby uzyskać więcej informacji, zobacz [Nawigacja — omówienie](navigation-overview.md)).  
  
 Okna dialogowe są okna, które są często używane do zbierania informacji od użytkownika do ukończenia funkcji. Na przykład, gdy użytkownik chce, aby otworzyć plik, **Otwórz plik** okno dialogowe jest zwykle wyświetlany przez aplikację można pobrać nazwy pliku od użytkownika. Aby uzyskać więcej informacji, zobacz [Przegląd okien dialogowych](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Okna dialogowe — omówienie](dialog-boxes-overview.md)
- [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)
