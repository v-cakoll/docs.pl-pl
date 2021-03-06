---
title: Przegląd systemu Windows
description: Zapoznaj się z podstawowymi informacjami na temat tworzenia i zarządzania oknami dla aplikacji autonomicznych w Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: e1ad3c118fbaea8f1e23d012721f0cf3c2c50015
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622890"
---
# <a name="wpf-windows-overview"></a>Przegląd Okna WPF
Użytkownicy pracują z autonomicznymi aplikacjami Windows Presentation Foundation (WPF) za pomocą systemu Windows. Głównym celem okna jest hostowanie zawartości, która wizualizuje dane i umożliwia użytkownikom współdziałanie z danymi. Autonomiczne aplikacje WPF zapewniają własne okna przy użyciu <xref:System.Windows.Window> klasy. Ten temat wprowadza <xref:System.Windows.Window> przede wszystkim podstawowe informacje na temat tworzenia i zarządzania oknami w aplikacjach autonomicznych.  
  
> [!NOTE]
> Hostowane w przeglądarce aplikacje WPF, w tym aplikacje przeglądarki XAML (XBAP) i luźne [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony, nie zapewniają własnych okien. Zamiast tego są one hostowane w systemie Windows udostępnianym przez program Windows Internet Explorer. Zobacz [Omówienie aplikacji przeglądarki XAML w języku WPF](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>Klasa okna  
 Na poniższej ilustracji przedstawiono części składowe okna:  
  
 ![Zrzut ekranu pokazujący elementy okna.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Okno jest podzielone na dwa obszary: obszar niebędący klientem i obszar klienta.  
  
 *Obszar niebędący klientem* okna jest implementowany przez WPF i zawiera części okna, które są wspólne dla większości systemu Windows, w tym:  
  
- Obramowanie.  
  
- Pasek tytułu.  
  
- Ikona.  
  
- Przyciski Minimalizuj, Maksymalizuj i Przywróć.  
  
- Przycisk Zamknij.  
  
- Menu systemowe z elementami menu, które umożliwiają użytkownikom minimalizowanie, maksymalizowanie, przywracanie, przenoszenie, zmienianie rozmiaru i zamykanie okna.  
  
 *Obszar klienta* okna to obszar w obszarze nieklienckim okna, który jest używany przez deweloperów do dodawania zawartości specyficznej dla aplikacji, takiej jak paski menu, paski narzędzi i formanty.  
  
 W WPF, okno jest hermetyzowane przez <xref:System.Windows.Window> klasę, która jest używana do wykonywania następujących czynności:  
  
- Wyświetl okno.  
  
- Skonfiguruj rozmiar, położenie i wygląd okna.  
  
- Hostowanie zawartości specyficznej dla aplikacji.  
  
- Zarządzanie okresem istnienia okna.  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>Implementowanie okna  
 Implementacja typowego okna składa się zarówno z wyglądu, jak i zachowania, w którym *wygląd* okna jest przeszukiwany użytkownikom i *zachowanie* definiuje sposób, w jaki okno działa jak użytkownicy. W WPF można zaimplementować wygląd i zachowanie okna przy użyciu kodu lub [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 Ogólnie rzecz biorąc, wygląd okna jest implementowany przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i jego zachowanie jest implementowane za pomocą kodu, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Aby umożliwić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wspólne współdziałanie pliku znaczników i pliku związanego z kodem, wymagane są następujące elementy:  
  
- W znaczniku `Window` element musi zawierać `x:Class` atrybut. Po skompilowaniu aplikacji istnienie `x:Class` w pliku znaczników powoduje, że program Microsoft Build Engine (MSBuild) tworzy `partial` klasę, która pochodzi od <xref:System.Windows.Window> i ma nazwę, która jest określona przez `x:Class` atrybut. Wymaga to dodania deklaracji przestrzeni nazw XML dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schematu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Wygenerowana `partial` Klasa implementuje `InitializeComponent` metodę, która jest wywoływana, aby zarejestrować zdarzenia i ustawić właściwości zaimplementowane w znaczniku.  
  
- W kodzie, Klasa musi być `partial` klasą o tej samej nazwie, która jest określona przez `x:Class` atrybut w znaczniku i musi pochodzić od <xref:System.Windows.Window> . Pozwala to skojarzyć plik związany z kodem z `partial` klasą wygenerowaną dla pliku znaczników podczas kompilowania aplikacji (zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)).  
  
- W kodzie, <xref:System.Windows.Window> Klasa musi implementować konstruktora, który wywołuje `InitializeComponent` metodę. `InitializeComponent`jest implementowana przez wygenerowaną klasę pliku znaczników `partial` do rejestrowania zdarzeń i ustawiania właściwości, które są zdefiniowane w znaczniku.  
  
> [!NOTE]
> Po dodaniu nowego elementu <xref:System.Windows.Window> do projektu przy użyciu programu Visual Studio, <xref:System.Windows.Window> jest zaimplementowany przy użyciu znaczników i kodu, i zawiera konfigurację niezbędną do utworzenia skojarzenia między plikami znaczników i kodu, zgodnie z opisem w tym miejscu.  
  
 W przypadku tej konfiguracji można skupić się na definiowaniu wyglądu okna w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczniku i wdrażaniu jego zachowania w kodzie. W poniższym przykładzie pokazano okno z przyciskiem, zaimplementowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczniku i program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia przycisku zaimplementowanego w kodzie.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurowanie definicji okna dla programu MSBuild  
 Sposób implementacji okna decyduje o sposobie jego konfiguracji dla programu MSBuild. Dla okna, które jest zdefiniowane przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i kodu:  
  
- Pliki znaczników XAML są konfigurowane jako elementy programu MSBuild `Page` .  
  
- Pliki związane z kodem są konfigurowane jako elementy programu MSBuild `Compile` .  
  
 Jest to pokazane w następującym pliku projektu programu MSBuild.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Aby uzyskać informacje na temat tworzenia aplikacji WPF, zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>Okres istnienia okna  
 Podobnie jak w przypadku każdej klasy, okno ma okres istnienia rozpoczynający się po pierwszym utworzeniu wystąpienia, po którym jest otwierane, uaktywniane i dezaktywowane i ostatecznie zamknięte.  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>Otwieranie okna  
 Aby otworzyć okno, należy najpierw utworzyć jego wystąpienie, które jest zademonstrowane w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 W tym przykładzie `MarkupAndCodeBehindWindow` jest tworzone wystąpienie podczas uruchamiania aplikacji, która występuje po <xref:System.Windows.Application.Startup> wywołaniu zdarzenia.  
  
 Po utworzeniu wystąpienia okna odwołanie do niego jest automatycznie dodawane do listy systemu Windows, która jest zarządzana przez <xref:System.Windows.Application> obiekt (zobacz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType> ). Ponadto pierwsze okno, które ma zostać utworzone, jest domyślnie ustawiane <xref:System.Windows.Application> jako główne okno aplikacji (zobacz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> ).  
  
 Okno jest ostatecznie otwarte przez wywołanie <xref:System.Windows.Window.Show%2A> metody; wynik jest pokazywany na poniższej ilustracji.  
  
 ![Okno otwarte przez wywołanie okna. show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Okno otwierane przez wywołanie <xref:System.Windows.Window.Show%2A> jest oknem niemodalnym, co oznacza, że aplikacja działa w trybie, który umożliwia użytkownikom aktywowanie innych okien w tej samej aplikacji.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>jest wywoływana, aby otworzyć okna, takie jak okna dialogowe modalnie. Aby uzyskać więcej informacji, zobacz [Omówienie okien](dialog-boxes-overview.md) dialogowych.  
  
 Gdy <xref:System.Windows.Window.Show%2A> jest wywoływana, okno wykonuje działanie inicjalizacji przed wyświetleniem infrastruktury, która pozwala na odbieranie danych przez użytkownika. Po zainicjowaniu okna <xref:System.Windows.Window.SourceInitialized> zdarzenie jest wywoływane i wyświetlane jest okno.  
  
 Jako skrót, <xref:System.Windows.Application.StartupUri%2A> można ustawić, aby określić pierwsze okno, które jest otwierane automatycznie podczas uruchamiania aplikacji.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Po uruchomieniu aplikacji okno określone przez wartość <xref:System.Windows.Application.StartupUri%2A> jest otwierane niemodalnie; wewnętrznie okno jest otwierane przez wywołanie jego <xref:System.Windows.Window.Show%2A> metody.  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>Własność okna  
 Okno, które jest otwierane za pomocą <xref:System.Windows.Window.Show%2A> metody, nie ma niejawnej relacji z oknem, które je utworzyło; użytkownicy mogą współdziałać z dowolnym oknem niezależnie od siebie, co oznacza, że oba okna mogą wykonać następujące czynności:  
  
- Należy pokryć drugą (chyba że jeden z okien ma swoją <xref:System.Windows.Window.Topmost%2A> Właściwość ustawioną na `true` ).  
  
- Być zminimalizowane, zmaksymalizowane i przywrócone bez wpływu na pozostałe.  
  
 Niektóre okna wymagają relacji z oknem, które je otwiera. Na przykład aplikacja zintegrowanego środowiska programistycznego (IDE) może otworzyć okno właściwości i okna narzędzi, których typowe zachowanie dotyczy tworzonego okna. Ponadto takie okna powinny zawsze zamykać, minimalizować, maksymalizować i przywracać w połączeniu z oknem, które je utworzyło. Tę relację można ustalić przez utworzenie jednego *okna innego i jest ono realizowane* przez ustawienie <xref:System.Windows.Window.Owner%2A> właściwości *okna należącego* do *okna właściciela*. Pokazano to w poniższym przykładzie.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Po ustanowieniu własności:  
  
- Posiadane okno może odwoływać się do swojego okna właściciela, sprawdzając wartość jego <xref:System.Windows.Window.Owner%2A> właściwości.  
  
- Okno właściciela może odnaleźć wszystkie okna, do których należy, sprawdzając wartość <xref:System.Windows.Window.OwnedWindows%2A> właściwości.  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>Zapobieganie aktywacji okna  
 Istnieją scenariusze, w których nie należy aktywować systemu Windows, na przykład w oknach konwersacji w aplikacji w stylu programu Messenger lub oknach powiadomień aplikacji poczty e-mail.  
  
 Jeśli aplikacja zawiera okno, które nie powinno być aktywowane, gdy jest wyświetlany, można ustawić jego <xref:System.Windows.Window.ShowActivated%2A> Właściwość na `false` przed wywołaniem <xref:System.Windows.Window.Show%2A> metody po raz pierwszy. W związku z tym:  
  
- Okno nie zostało aktywowane.  
  
- <xref:System.Windows.Window.Activated>Zdarzenie okna nie zostało zgłoszone.  
  
- Uaktywnione okno zostanie uaktywnione.  
  
 Okno zostanie aktywowane, jednak natychmiast po jego aktywowaniu przez kliknięcie w obszarze klienta lub nieklienckiego. W takim przypadku:  
  
- Okno zostało aktywowane.  
  
- <xref:System.Windows.Window.Activated>Zdarzenie okna zostało zgłoszone.  
  
- Poprzednio aktywowane okno zostało zdezaktywowane.  
  
- <xref:System.Windows.Window.Deactivated>Zdarzenia okna i <xref:System.Windows.Window.Activated> są następnie wywoływane zgodnie z oczekiwaniami w odpowiedzi na akcje użytkownika.  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>Aktywacja okna  
 Gdy okno jest otwierane po raz pierwszy, przechodzi do aktywnego okna (chyba że jest wyświetlane z <xref:System.Windows.Window.ShowActivated%2A> ustawioną na `false` ). *Aktywne okno* to okno, które aktualnie przechwytywa dane wprowadzane przez użytkownika, takie jak naciśnięcia klawiszy i kliknięć myszą. Gdy okno zostanie uaktywnione, wywołuje <xref:System.Windows.Window.Activated> zdarzenie.  
  
> [!NOTE]
> Gdy okno jest otwierane po raz pierwszy <xref:System.Windows.FrameworkElement.Loaded> , <xref:System.Windows.Window.ContentRendered> zdarzenia i są wywoływane dopiero po <xref:System.Windows.Window.Activated> wywołaniu zdarzenia. Z tego względu okno może być efektywnie uważane za otwarte, gdy <xref:System.Windows.Window.ContentRendered> zostanie zgłoszone.  
  
 Gdy okno zostanie uaktywnione, użytkownik może aktywować inne okno w tej samej aplikacji lub aktywować inną aplikację. W takim przypadku aktywne okno zostanie zdezaktywowane i wygeneruje <xref:System.Windows.Window.Deactivated> zdarzenie. Podobnie, gdy użytkownik wybierze aktualnie dezaktywowane okno, okno zostanie ponownie uaktywnione i <xref:System.Windows.Window.Activated> zostanie zgłoszone.  
  
 Jednym z typowych przyczyn obsługi <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated> jest włączenie i wyłączenie funkcji, która może być uruchamiana tylko wtedy, gdy okno jest aktywne. Na przykład niektóre okna wyświetlają zawartość interaktywną, która wymaga stałego wprowadzania danych przez użytkownika lub uwagi, w tym gier i odtwarzaczy wideo. Poniższy przykład to uproszczony odtwarzacz wideo, który pokazuje, jak obsłużyć <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated> zaimplementować to zachowanie.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Inne typy aplikacji mogą nadal uruchamiać kod w tle, gdy okno zostanie zdezaktywowane. Na przykład klient poczty e-mail może kontynuować sondowanie serwera poczty, gdy użytkownik korzysta z innych aplikacji. Aplikacje takie jak często zapewniają różne lub dodatkowe zachowanie podczas dezaktywacji okna głównego. W odniesieniu do programu poczty może to oznaczać zarówno dodanie nowego elementu poczty do skrzynki odbiorczej, jak i dodanie ikony powiadomienia do paska zadań. Ikona powiadomienia musi być wyświetlana tylko wtedy, gdy okno poczty nie jest aktywne, co można określić przez sprawdzenie <xref:System.Windows.Window.IsActive%2A> właściwości.  
  
 Jeśli zadanie w tle zakończy pracę, okno może chcieć pilnie powiadomić użytkownika przez wywołanie <xref:System.Windows.Window.Activate%2A> metody. Jeśli użytkownik jest w trakcie działania z inną aplikacją aktywowaną <xref:System.Windows.Window.Activate%2A> , gdy jest wywoływana, zostanie uaktywniony przycisk paska zadań okna. Jeśli użytkownik korzysta z bieżącej aplikacji, <xref:System.Windows.Window.Activate%2A> nastąpi przełączenie okna na pierwszy plan.  
  
> [!NOTE]
> Aktywację zakresu aplikacji można obsługiwać przy użyciu <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> zdarzeń i.  
  
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
  
 Aby zamknąć okno w odpowiedzi na jeden z tych niestandardowych mechanizmów, należy wywołać <xref:System.Windows.Window.Close%2A> metodę. W poniższym przykładzie jest implementowana możliwość zamykania okna przez wybranie polecenia **Wyjdź** z menu **plik** .  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Gdy okno zostanie zamknięte, wywołuje dwa zdarzenia: <xref:System.Windows.Window.Closing> i <xref:System.Windows.Window.Closed> .  
  
 <xref:System.Windows.Window.Closing>jest uruchamiany przed zamknięciem okna i udostępnia mechanizm, za pomocą którego można zapobiec zamknięciu okna. Jednym z najczęstszych powodów, aby uniknąć zamykania okna, jest to, że zawartość okna zawiera zmodyfikowane dane. W takiej sytuacji <xref:System.Windows.Window.Closing> można obsłużyć zdarzenie, aby określić, czy dane są zanieczyszczone, a jeśli tak, to w celu poproszenia użytkownika o kontynuowanie zamykania okna bez zapisywania danych ani do anulowania zamknięcia okna. W poniższym przykładzie przedstawiono kluczowe aspekty obsługi <xref:System.Windows.Window.Closing> .  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <xref:System.Windows.Window.Closing>Procedura obsługi zdarzeń jest przenoszona a <xref:System.ComponentModel.CancelEventArgs> , która implementuje `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Właściwość, która została ustawiona na, `true` Aby zapobiec zamykaniu okna.  
  
 Jeśli <xref:System.Windows.Window.Closing> program nie jest obsługiwany lub jest obsługiwany, ale nie został anulowany, okno zostanie zamknięte. Tuż przed faktycznym zamknięciem okna <xref:System.Windows.Window.Closed> jest zgłaszane. W tym momencie nie można uniemożliwić zamykania okna.  
  
> [!NOTE]
> Aplikację można skonfigurować do automatycznego zamykania w momencie zamknięcia okna aplikacji głównej (zobacz <xref:System.Windows.Application.MainWindow%2A> ) lub ostatniego zamknięcia okna. Aby uzyskać szczegółowe informacje, zobacz <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Okno może być jawnie zamykane za pomocą mechanizmów dostępnych w obszarach nieklienta i klienta, a okno może być również niejawnie zamknięte w wyniku zachowania w innych częściach aplikacji lub systemu Windows, w tym:  
  
- Użytkownik wylogowuje się lub zamknie system Windows.  
  
- Zamknięcie właściciela okna (zobacz <xref:System.Windows.Window.Owner%2A> ).  
  
- Okno główne aplikacji jest zamknięte i <xref:System.Windows.Application.ShutdownMode%2A> ma wartość <xref:System.Windows.ShutdownMode.OnMainWindowClose> .  
  
- <xref:System.Windows.Application.Shutdown%2A>jest wywoływana.  
  
> [!NOTE]
> Nie można otworzyć ponownie okna po jego zamknięciu.  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>Zdarzenia okresu istnienia okna  
 Na poniższej ilustracji przedstawiono sekwencję zdarzeń głównych w okresie istnienia okna:  
  
 ![Diagram przedstawiający zdarzenia w okresie istnienia okna.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Na poniższej ilustracji przedstawiono sekwencję głównych zdarzeń w okresie istnienia okna, które jest wyświetlane bez aktywacji ( <xref:System.Windows.Window.ShowActivated%2A> ustawiono przed wyświetleniem `false` okna):  
  
 ![Diagram przedstawiający zdarzenia w okresie istnienia bez aktywacji.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>Lokalizacja okna  
 Gdy okno jest otwarte, ma miejsce w wymiarach x i y względem pulpitu. Tę lokalizację można określić <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> , sprawdzając odpowiednio właściwości i. Można ustawić te właściwości, aby zmienić lokalizację okna.  
  
 Możesz również określić początkową lokalizację, <xref:System.Windows.Window> gdy po raz pierwszy pojawia się, ustawiając <xref:System.Windows.Window.WindowStartupLocation%2A> Właściwość z jedną z następujących <xref:System.Windows.WindowStartupLocation> wartości wyliczenia:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner>wartooć  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Jeśli lokalizacja początkowa została określona jako <xref:System.Windows.WindowStartupLocation.Manual> , a <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> właściwości i nie zostały ustawione, <xref:System.Windows.Window> program wyświetli do systemu Windows lokalizację, w której ma się pojawić.  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>System Windows i porządek Z góry  
 Poza lokalizacją x i y okno zawiera również lokalizację w wymiarze z, która określa położenie w pionie w odniesieniu do innych okien. Jest to znane jako porządek osi z okna, a istnieją dwa typy: normalna kolejność z i kolejność z góry. Lokalizacja okna w *normalnej kolejności z* jest określana na podstawie tego, czy jest ona obecnie aktywna, czy nie. Domyślnie okno znajduje się w normalnej kolejności z. Lokalizacja okna w *górnym porządku osi z* jest również określana na podstawie tego, czy jest ona obecnie aktywna, czy nie. Co więcej, okna w najwyższej kolejności z są zawsze zlokalizowane powyżej systemu Windows w normalnej kolejności z. Okno znajduje się w najwyższym porządku osi z, ustawiając jego <xref:System.Windows.Window.Topmost%2A> Właściwość na `true` .  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 W każdym porządku osi z aktywne okno jest wyświetlane nad wszystkimi innymi oknami w tej samej kolejności z.  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>Rozmiar okna  
 Poza lokalizacją pulpitu okno ma rozmiar, który jest określany przez kilka właściwości, w tym różne właściwości width i Height i <xref:System.Windows.Window.SizeToContent%2A> .  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.MaxWidth%2A> są używane do zarządzania zakresem szerokości, które okno może mieć w okresie istnienia, i są skonfigurowane tak, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Wysokość okna jest zarządzana przez <xref:System.Windows.FrameworkElement.MinHeight%2A> , <xref:System.Windows.FrameworkElement.Height%2A> , i <xref:System.Windows.FrameworkElement.MaxHeight%2A> i są skonfigurowane, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Ponieważ różne wartości szerokości i wysokości określają zakres, możliwe jest, aby szerokość i wysokość okna o zmiennym rozmiarze znajdować się w dowolnym miejscu w określonym zakresie dla odpowiedniego wymiaru. Aby wykryć bieżącą szerokość i wysokość, należy <xref:System.Windows.FrameworkElement.ActualWidth%2A> odpowiednio zbadać i <xref:System.Windows.FrameworkElement.ActualHeight%2A> .  
  
 Jeśli chcesz, aby szerokość i wysokość okna miały rozmiar, który pasuje do rozmiaru zawartości okna, możesz użyć <xref:System.Windows.Window.SizeToContent%2A> właściwości, która ma następujące wartości:  
  
- <xref:System.Windows.SizeToContent.Manual>. Brak efektu (wartość domyślna).  
  
- <xref:System.Windows.SizeToContent.Width>. Dopasuj do szerokości zawartości, która ma taki sam efekt jak ustawienie <xref:System.Windows.FrameworkElement.MinWidth%2A> i <xref:System.Windows.FrameworkElement.MaxWidth%2A> Szerokość zawartości.  
  
- <xref:System.Windows.SizeToContent.Height>. Dopasuj do wysokości zawartości, która ma taki sam efekt jak ustawienie zarówno <xref:System.Windows.FrameworkElement.MinHeight%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> wysokość zawartości.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. Dopasuj do szerokości i wysokości zawartości, która ma taki sam skutek jak ustawienie zarówno, jak <xref:System.Windows.FrameworkElement.MinHeight%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> do wysokości zawartości, oraz ustawienie wartości <xref:System.Windows.FrameworkElement.MinWidth%2A> i <xref:System.Windows.FrameworkElement.MaxWidth%2A> szerokości zawartości.  
  
 W poniższym przykładzie pokazano okno, które automatycznie dopasowuje rozmiar do jego zawartości, zarówno w pionie, jak i w poziomie.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Window.SizeToContent%2A> Właściwość w kodzie, aby określić, jak zmienia się rozmiar okna w celu dopasowania do jego zawartości.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>Kolejność pierwszeństwa we właściwościach ustalania wielkości  
 Zasadniczo różne rozmiary okna łączą się, aby zdefiniować zakres szerokości i wysokości okna o zmiennym rozmiarze. Aby zapewnić zachowanie prawidłowego zakresu, program <xref:System.Windows.Window> oblicza wartości właściwości rozmiaru przy użyciu następujących kolejności pierwszeństwa.  
  
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
  
 Kolejność pierwszeństwa może również określać rozmiar okna, gdy jest zmaksymalizowane, które jest zarządzane za pomocą <xref:System.Windows.Window.WindowState%2A> właściwości.  
  
<a name="WindowState"></a>
## <a name="window-state"></a>Stan okna  
 W okresie istnienia okna o zmiennym rozmiarze może istnieć trzy stany: normalny, zminimalizowany i zmaksymalizowany. Okno z *normalnym* stanem jest domyślnym stanem okna. Okno z tym stanem umożliwia użytkownikowi przeniesienie i zmianę jego rozmiaru przy użyciu uchwytu zmiany rozmiaru lub obramowania, jeśli zostanie on zmieniony.  
  
 Okno ze *zminimalizowanym* stanem jest zwijane do jego przycisku paska zadań <xref:System.Windows.Window.ShowInTaskbar%2A> , jeśli jest ustawiona na `true` ; w przeciwnym razie zostanie zwinięte do najmniejszego możliwego rozmiaru, który może być w lewym dolnym rogu pulpitu. Nie można zmienić rozmiaru okna zminimalizowanego za pomocą obramowania ani uchwytu zmiany rozmiaru, chociaż zminimalizowane okno, które nie jest wyświetlane na pasku zadań, może być przeciągane wokół pulpitu.  
  
 Okno z *zmaksymalizowanym* stanem rozwija się do maksymalnego rozmiaru, który może być, co będzie tak duże, jak jego <xref:System.Windows.FrameworkElement.MaxWidth%2A> właściwości, <xref:System.Windows.FrameworkElement.MaxHeight%2A> i <xref:System.Windows.Window.SizeToContent%2A> . Jak okno zminimalizowane, nie można zmienić rozmiaru zmaksymalizowanego okna przy użyciu uchwytu zmiany rozmiaru lub przeciągając obramowanie.  
  
> [!NOTE]
> Wartości <xref:System.Windows.Window.Top%2A> ,, <xref:System.Windows.Window.Left%2A> <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> Właściwości okna zawsze reprezentują wartości dla normalnego stanu, nawet gdy okno jest obecnie zmaksymalizowane lub zminimalizowane.  
  
 Stan okna można skonfigurować przez ustawienie jego <xref:System.Windows.Window.WindowState%2A> właściwości, która może mieć jedną z następujących <xref:System.Windows.WindowState> wartości wyliczenia:  
  
- <xref:System.Windows.WindowState.Normal>wartooć  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 Poniższy przykład pokazuje, jak utworzyć okno, które jest wyświetlane jako zmaksymalizowane, gdy zostanie otwarte.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Ogólnie rzecz biorąc, należy ustawić, <xref:System.Windows.Window.WindowState%2A> Aby skonfigurować początkowy stan okna. Po pobraniu okna o zmiennym rozmiarze użytkownicy mogą nacisnąć przyciski Minimalizuj, Maksymalizuj i Przywróć na pasku tytułu okna, aby zmienić stan okna.  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>Wygląd okna  
 Aby zmienić wygląd obszaru klienta okna, można dodać do niego zawartość specyficzną dla okna, taką jak przyciski, etykiety i pola tekstowe. Aby skonfigurować obszar niebędący klientem, program <xref:System.Windows.Window> udostępnia kilka właściwości, które obejmują <xref:System.Windows.Window.Icon%2A> Ustawianie ikony okna i <xref:System.Windows.Window.Title%2A> Ustawianie jej tytułu.  
  
 Możesz również zmienić wygląd i zachowanie obramowania obszaru nieklienckiego, konfigurując tryb zmiany rozmiaru okna, styl okna i czy jest on wyświetlany jako przycisk na pasku zadań pulpitu.  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>Tryb zmiany rozmiaru  
 W zależności od <xref:System.Windows.Window.WindowStyle%2A> właściwości można kontrolować sposób, w jaki użytkownicy mogą zmieniać rozmiar okna. Wybór stylu okna ma wpływ na to, czy użytkownik może zmienić rozmiar okna, przeciągając jego obramowanie przy użyciu myszy, czy przyciski **Minimalizuj**, **Maksymalizuj**i **Zmień rozmiar** pojawiają się w obszarze nieklienckim i, jeśli są wyświetlane, niezależnie od tego, czy są włączone.  
  
 Można skonfigurować sposób zmiany rozmiaru okna przez ustawienie jego <xref:System.Windows.Window.ResizeMode%2A> właściwości, która może być jedną z następujących <xref:System.Windows.ResizeMode> wartości wyliczenia:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize>wartooć  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Podobnie jak w przypadku <xref:System.Windows.Window.WindowStyle%2A> , tryb zmiany rozmiaru okna nie może ulec zmianie w okresie istnienia, co oznacza, że najprawdopodobniej ustawisz go na podstawie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznika.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Należy zauważyć, że można wykryć, czy okno jest zmaksymalizowane, zminimalizowane lub przywrócone, sprawdzając <xref:System.Windows.Window.WindowState%2A> Właściwość.  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>Styl okna  
 Obramowanie, które jest widoczne z obszaru nieklienckiego okna, jest odpowiednie dla większości aplikacji. Istnieją jednak sytuacje, w których są zbędne różne typy obramowań lub nie są w ogóle stosowane żadne obramowania, w zależności od typu okna.  
  
 Aby sterować typem obramowania pobieranym przez okno, należy ustawić jego <xref:System.Windows.Window.WindowStyle%2A> Właściwość z jedną z następujących wartości <xref:System.Windows.WindowStyle> wyliczenia:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow>wartooć  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Efekt tych stylów okna przedstawiono na poniższej ilustracji:  
  
 ![Ilustracja stylów obramowania okna.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Możesz ustawić <xref:System.Windows.Window.WindowStyle%2A> przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznika lub kodu, ponieważ nie można go zmienić w okresie istnienia okna, najprawdopodobniej skonfigurujesz go przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznika.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Styl okna bez prostokąta  
 Istnieją również sytuacje, w których style obramowania, które <xref:System.Windows.Window.WindowStyle%2A> nie są wystarczające. Na przykład możesz chcieć utworzyć aplikację z nieprostokątnym obramowaniem, np. Microsoft Windows Media Player.  
  
 Rozważmy na przykład okno dymek mowy pokazane na poniższym rysunku:  
  
 ![Okno bąbelka mowy z tekstem przeciągnij mnie.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Ten typ okna można utworzyć przez ustawienie <xref:System.Windows.Window.WindowStyle%2A> właściwości na <xref:System.Windows.WindowStyle.None> , a przy użyciu specjalnego wsparcia, który ma być <xref:System.Windows.Window> przezroczysty.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Ta kombinacja wartości powoduje, że okno jest renderowane całkowicie przezroczyste. W tym stanie nie można używać modułów definiowania układu nieklienckiego (zamknięcie menu, minimalizowania, maksymalizowania i przywracania). W związku z tym należy podać własny.  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>Obecność paska zadań  

Domyślny wygląd okna zawiera przycisk paska zadań, tak jak pokazano na poniższym rysunku:

 ![Zrzut ekranu pokazujący okno z przyciskiem paska zadań.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Niektóre typy okien nie mają przycisku paska zadań, takiego jak okna dialogowe komunikatów i okien dialogowych (zobacz [okna dialogowe — Omówienie](dialog-boxes-overview.md)). Można kontrolować, czy przycisk paska zadań dla okna jest pokazywany przez ustawienie <xref:System.Windows.Window.ShowInTaskbar%2A> właściwości ( `true` domyślnie).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami  
 <xref:System.Windows.Window>wymaga `UnmanagedCode` uprawnień zabezpieczeń, aby można było utworzyć wystąpienie. W przypadku aplikacji zainstalowanych na komputerze lokalnym i uruchamianych z niej jest to zestaw uprawnień, które są przyznawane aplikacji.  
  
 Jednak jest to poza zestawem uprawnień przyznanym aplikacjom, które są uruchamiane z Internetu lub lokalnej strefy intranetowej przy użyciu technologii ClickOnce. W związku z tym użytkownicy otrzymają ostrzeżenie o zabezpieczeniach technologii ClickOnce i będą musieli podnieść poziom uprawnień dla aplikacji do pełnego zaufania.  
  
 Ponadto aplikacje XBAP nie mogą domyślnie wyświetlać okien ani okna dialogowego. Aby zapoznać się z zagadnieniami dotyczącymi zabezpieczeń aplikacji autonomicznych, zobacz [strategia zabezpieczeń WPF — zabezpieczenia platformy](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>Inne typy okien  
 <xref:System.Windows.Navigation.NavigationWindow>jest oknem, które jest przeznaczone do hostowania zawartości nawigacji. Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](navigation-overview.md)).  
  
 Okna dialogowe to okna, które są często używane do zbierania informacji od użytkownika w celu ukończenia funkcji. Na przykład, gdy użytkownik chce otworzyć plik, okno dialogowe **Otwórz plik** jest zwykle wyświetlane przez aplikację w celu uzyskania nazwy pliku od użytkownika. Aby uzyskać więcej informacji, zobacz [okna dialogowe przegląd](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Okna dialogowe — omówienie](dialog-boxes-overview.md)
- [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)
