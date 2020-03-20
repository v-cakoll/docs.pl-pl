---
title: Omówienie systemu Windows
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
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145543"
---
# <a name="wpf-windows-overview"></a>Przegląd Okna WPF
Użytkownicy wchodzą w interakcje z autonomicznymi aplikacjami Programu Windows Presentation Foundation (WPF) za pośrednictwem systemu Windows. Głównym celem okna jest hostowanie zawartości, która wizualizuje dane i umożliwia użytkownikom interakcję z danymi. Autonomiczne aplikacje WPF zapewniają własne <xref:System.Windows.Window> okna przy użyciu klasy. W tym <xref:System.Windows.Window> temacie przedstawiono przed pokryciem podstaw tworzenia okien i zarządzania nimi w aplikacjach autonomicznych.  
  
> [!NOTE]
> Aplikacje WPF hostowane przez przeglądarkę, w tym aplikacje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przeglądarki XAML (XBAPs) i luźne strony, nie udostępniają własnych okien. Zamiast tego są one hostowane w oknach dostarczonych przez program Windows Internet Explorer. Zobacz [Przegląd aplikacji przeglądarki WPF XAML](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>Klasa Window  
 Poniższy rysunek ilustruje części składowe okna:  
  
 ![Zrzut ekranu przedstawiający elementy okna.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Okno jest podzielone na dwa obszary: obszar niebędący klientem i obszar klienta.  
  
 *Obszar niebędący klientem* okna jest implementowany przez WPF I zawiera części okna, które są wspólne dla większości okien, w tym następujące:  
  
- Obramowanie.  
  
- Pasek tytułu.  
  
- Ikona.  
  
- Minimalizuj, maksymalizuj i przywracaj przyciski.  
  
- Przycisk Zamknij.  
  
- Menu System z elementami menu, które umożliwiają użytkownikom minimalizowanie, maksymalizację, przywracanie, przenoszenie, przenoszenie rozmiaru i zamykanie okna.  
  
 *Obszar klienta* okna jest obszarem w obszarze nienależącym do okna i jest używany przez deweloperów do dodawania zawartości specyficznej dla aplikacji, takich jak paski menu, paski narzędzi i formanty.  
  
 W WPF WPF okno jest hermetyzowany przez <xref:System.Windows.Window> klasę, która służy do wykonywania następujących czynności:  
  
- Wyświetl okno.  
  
- Skonfiguruj rozmiar, położenie i wygląd okna.  
  
- Hostuj zawartość specyficzną dla aplikacji.  
  
- Zarządzanie okresem istnienia okna.  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>Implementowanie okna  
 Implementacja okna typowe obejmuje zarówno wygląd i zachowanie, gdzie *wygląd* definiuje, jak okno wygląda dla użytkowników i *zachowanie* definiuje sposób, w jaki okno działa, jak użytkownicy wchodzą z nim interakcji. W WPF WPF, można zaimplementować wygląd [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i zachowanie okna przy użyciu kodu lub znaczników.  
  
 Ogólnie rzecz biorąc jednak wygląd okna jest [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementowany przy użyciu znaczników, a jego zachowanie jest implementowane przy użyciu kodu, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Aby włączyć [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do współpracy plik znaczników i plik związany z kodem, wymagane są następujące czynności:  
  
- W znacznikach `Window` element musi `x:Class` zawierać atrybut. Po utworzeniu aplikacji, istnienie `x:Class` w pliku znaczników powoduje, że aparat kompilacji `partial` firmy Microsoft (MSBuild) do utworzenia klasy, która pochodzi od <xref:System.Windows.Window> i ma nazwę, która jest określona przez `x:Class` atrybut. Wymaga to dodania deklaracji obszaru nazw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XML `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` dla schematu ( ). Wygenerowana `partial` klasa implementuje `InitializeComponent` metodę, która jest wywoływana do rejestrowania zdarzeń i ustawiania właściwości, które są implementowane w znacznikach.  
  
- W kodzie po zakoduje `partial` się klasa musi być klasą o tej samej nazwie, która jest określona przez `x:Class` atrybut w znacznikach i musi pochodzić od <xref:System.Windows.Window>. Dzięki temu plik związany z kodem `partial` ma być skojarzony z klasą, która jest generowana dla pliku znaczników podczas tworzenia aplikacji (zobacz [Tworzenie aplikacji WPF](building-a-wpf-application-wpf.md)).  
  
- W przypadku kodu <xref:System.Windows.Window> po zakodowaniu klasa musi `InitializeComponent` implementować konstruktora, który wywołuje metodę. `InitializeComponent`jest implementowana przez klasę wygenerowaną `partial` pliku znaczników, aby zarejestrować zdarzenia i ustawić właściwości, które są zdefiniowane w znacznikach.  
  
> [!NOTE]
> Po dodaniu <xref:System.Windows.Window> nowego do projektu przy użyciu <xref:System.Windows.Window> programu Visual Studio, jest zaimplementowana przy użyciu znaczników i związanych z kodem i zawiera konfigurację niezbędną do utworzenia skojarzenia między znaczników i plików związanych z kodem, jak opisano poniżej.  
  
 Z tej konfiguracji w miejscu, można skupić się [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na definiowaniu wygląd okna w znacznikach i implementacji jego zachowanie w kodzie. Poniższy przykład pokazuje okno z przyciskiem, zaimplementowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznikach <xref:System.Windows.Controls.Primitives.ButtonBase.Click> i program obsługi zdarzeń dla zdarzenia przycisku, zaimplementowane w kodzie.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurowanie definicji okna dla usługi MSBuild  
 Sposób implementowania okna określa, jak jest skonfigurowany dla MSBuild. Dla okna, które jest [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zdefiniowane przy użyciu znaczników i związanych z kodem:  
  
- Pliki znaczników XAML są skonfigurowane `Page` jako elementy MSBuild.  
  
- Pliki związane z kodem są skonfigurowane jako elementy MSBuild. `Compile`  
  
 Jest to pokazane w następującym pliku projektu MSBuild.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Aby uzyskać informacje na temat tworzenia aplikacji WPF, zobacz [Tworzenie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>Okres istnienia okna  
 Podobnie jak w przypadku każdej klasy, okno ma okres istnienia, który rozpoczyna się, gdy jest po raz pierwszy wystąpienia, po czym jest otwierany, aktywowany i dezaktywowany, a ostatecznie zamknięty.  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>Otwieranie okna  
 Aby otworzyć okno, należy najpierw utworzyć jego wystąpienie, co zostanie zademonstrowane w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 W tym przykładzie `MarkupAndCodeBehindWindow` jest tworzone podczas uruchamiania aplikacji, <xref:System.Windows.Application.Startup> która występuje, gdy zdarzenie jest wywoływane.  
  
 Po wystąpieniu okna odwołanie do niego jest automatycznie dodawane do listy okien <xref:System.Windows.Application> zarządzanych <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>przez obiekt (patrz ). Ponadto pierwsze okno, które ma zostać utworzone, jest <xref:System.Windows.Application> domyślnie ustawione jako <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>główne okno aplikacji (patrz ).  
  
 Okno jest ostatecznie otwierane <xref:System.Windows.Window.Show%2A> przez wywołanie metody; wynik jest pokazany na poniższym rysunku.  
  
 ![Okno otwarte przez wywołanie Window.Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Okno, które jest <xref:System.Windows.Window.Show%2A> otwierane przez wywołanie jest niemodne okno, co oznacza, że aplikacja działa w trybie, który umożliwia użytkownikom aktywowanie innych okien w tej samej aplikacji.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>jest wywoływana do otwierania okien, takich jak okna dialogowe modnie. Zobacz [omówienie okien dialogowych, aby](dialog-boxes-overview.md) uzyskać więcej informacji.  
  
 Po <xref:System.Windows.Window.Show%2A> wywołaniu okno wykonuje pracę inicjowania, zanim zostanie wyświetlone do ustanowienia infrastruktury, która umożliwia odbieranie danych wejściowych użytkownika. Po zainicjowaniu okna <xref:System.Windows.Window.SourceInitialized> zdarzenie jest wywoływane i wyświetlane jest okno.  
  
 Jako skrót <xref:System.Windows.Application.StartupUri%2A> można ustawić, aby określić pierwsze okno, które jest otwierane automatycznie po uruchomieniu aplikacji.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Po uruchomieniu aplikacji okno określone przez wartość <xref:System.Windows.Application.StartupUri%2A> jest otwierane bez trybu; wewnętrznie okno jest otwierane przez <xref:System.Windows.Window.Show%2A> wywołanie jego metody.  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>Własność okna  
 Okno, które jest otwierane przy użyciu <xref:System.Windows.Window.Show%2A> metody nie ma niejawnej relacji z oknem, które go utworzyło; użytkownicy mogą wchodzić w interakcje z każdym z okien niezależnie od drugiego, co oznacza, że w każdym oknie można wykonać następujące czynności:  
  
- Zakryj drugi (chyba że <xref:System.Windows.Window.Topmost%2A> jedno z `true`okien ma ustawioną właściwość).  
  
- Być zminimalizowane, zmaksymalizowane i przywrócone bez wpływu na inne.  
  
 Niektóre okna wymagają relacji z oknem, które je otwiera. Na przykład aplikacja ide (Integrated Development Environment) może otworzyć okna właściwości i okna narzędzi, których typowym zachowaniem jest pokrycie okna, które je tworzy. Ponadto takie okna powinny zawsze zamykać, minimalizować, maksymalizować i przywracać w porozumieniu z utworzonym ich oknem. Taki związek można ustanowić, tworząc jedno okno *własne* drugie i <xref:System.Windows.Window.Owner%2A> uzyskuje się poprzez ustawienie właściwości *okna należącego* do właściciela z odniesieniem do *okna właściciela*. Jest to pokazane w poniższym przykładzie.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Po ustanowieniu własności:  
  
- Okno należące do właściciela może odwoływać się <xref:System.Windows.Window.Owner%2A> do okna właściciela, sprawdzając wartość jego właściwości.  
  
- Okno właściciela może odnajdować wszystkie okna, <xref:System.Windows.Window.OwnedWindows%2A> które posiada, sprawdzając wartość jego właściwości.  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>Zapobieganie aktywacji okna  
 Istnieją scenariusze, w których okna nie powinny być aktywowane, gdy są wyświetlane, takie jak okna konwersacji aplikacji w stylu komunikatora internetowego lub okna powiadomień aplikacji poczty e-mail.  
  
 Jeśli aplikacja ma okno, które nie powinny być aktywowane, <xref:System.Windows.Window.ShowActivated%2A> gdy `false` jest <xref:System.Windows.Window.Show%2A> wyświetlany, można ustawić jego właściwości przed wywołaniem metody po raz pierwszy. W konsekwencji:  
  
- Okno nie jest aktywowane.  
  
- <xref:System.Windows.Window.Activated> Zdarzenie okna nie jest wywoływane.  
  
- Aktualnie aktywowane okno pozostaje aktywowane.  
  
 Okno zostanie aktywowane, jednak, jak tylko użytkownik aktywuje go, klikając albo klienta lub obszaru nie-klienta. W takim przypadku:  
  
- Okno jest aktywne.  
  
- <xref:System.Windows.Window.Activated> Zdarzenie okna jest wywoływane.  
  
- Wcześniej aktywowane okno zostanie wyłączone.  
  
- Okna <xref:System.Windows.Window.Deactivated> i <xref:System.Windows.Window.Activated> zdarzenia są następnie wywoływane zgodnie z oczekiwaniami w odpowiedzi na akcje użytkownika.  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>Aktywacja okna  
 Po pierwszym otwarciu okna staje się ono aktywnym <xref:System.Windows.Window.ShowActivated%2A> oknem (chyba że jest wyświetlane z ustawionym na `false`). *Aktywne okno* jest oknem, które aktualnie przechwytuje dane wejściowe użytkownika, takie jak naciśnięcia klawiszy i kliknięcia myszą. Gdy okno staje się aktywne, <xref:System.Windows.Window.Activated> wywołuje zdarzenie.  
  
> [!NOTE]
> Po pierwszym otwarciu okna <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.Window.ContentRendered> i zdarzenia są <xref:System.Windows.Window.Activated> wywoływane tylko po wywoływaniu zdarzenia. Mając to na uwadze, okno można <xref:System.Windows.Window.ContentRendered> skutecznie uznać za otwarte, gdy jest podnoszone.  
  
 Gdy okno stanie się aktywne, użytkownik może aktywować inne okno w tej samej aplikacji lub aktywować inną aplikację. W takim przypadku aktualnie aktywne okno zostanie dezaktywowane i wywołuje <xref:System.Windows.Window.Deactivated> zdarzenie. Podobnie, gdy użytkownik wybierze aktualnie dezaktywowane okno, <xref:System.Windows.Window.Activated> okno staje się aktywne ponownie i jest wywoływane.  
  
 Jednym z typowych powodów do obsługi <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated> jest włączenie i wyłączenie funkcji, które można uruchomić tylko wtedy, gdy okno jest aktywne. Na przykład niektóre systemy Windows wyświetlają interaktywną zawartość, która wymaga stałego wprowadzania danych przez użytkownika lub uwagi, w tym gier i odtwarzaczy wideo. Poniższy przykład jest uproszczony odtwarzacz wideo, <xref:System.Windows.Window.Activated> który <xref:System.Windows.Window.Deactivated> pokazuje, jak obsługiwać i zaimplementować to zachowanie.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Inne typy aplikacji mogą nadal uruchamiać kod w tle, gdy okno jest dezaktywowane. Na przykład klient poczty może kontynuować sondowanie serwera poczty, gdy użytkownik korzysta z innych aplikacji. Aplikacje takie jak te często zapewniają różne lub dodatkowe zachowanie, gdy okno główne jest dezaktywowane. W odniesieniu do programu pocztowego może to oznaczać zarówno dodanie nowego elementu poczty do skrzynki odbiorczej, jak i dodanie ikony powiadomień do zasobnika systemowego. Ikona powiadomień musi być wyświetlana tylko wtedy, gdy okno poczty nie <xref:System.Windows.Window.IsActive%2A> jest aktywne, co można określić, sprawdzając właściwość.  
  
 Jeśli zadanie w tle zostanie ukończone, okno może chcieć <xref:System.Windows.Window.Activate%2A> powiadomić użytkownika pilniej, wywołując metodę. Jeśli użytkownik wchodzi w interakcję z <xref:System.Windows.Window.Activate%2A> inną aplikacją aktywowany, gdy jest wywoływana, przycisk paska zadań okna miga. Jeśli użytkownik wchodzi w interakcję z <xref:System.Windows.Window.Activate%2A> bieżącą aplikacją, wywołanie spowoduje wyświetlenie okna na pierwszym planie.  
  
> [!NOTE]
> Można obsługiwać aktywacji zakresu <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> aplikacji przy użyciu i zdarzeń.  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a>Zamykanie okna  
 Życie okna zaczyna się kończyć, gdy użytkownik go zamknie. Okno można zamknąć przy użyciu elementów w obszarze nienakładowym, w tym następujących:  
  
- Pozycja **Zamknij** menu **System.**  
  
- Naciśnięcie klawisza ALT+F4.  
  
- Naciśnięcie przycisku **Zamknij.**  
  
 Można podać dodatkowe mechanizmy do obszaru klienta, aby zamknąć okno, z których bardziej powszechne są następujące:  
  
- Element **Zakończ** w menu **Plik,** zazwyczaj dla okien aplikacji głównej.  
  
- A **Zamknij** element w **menu Plik,** zazwyczaj w oknie aplikacji pomocniczej.  
  
- Przycisk **Anuluj,** zazwyczaj w oknie dialogowym modalnego.  
  
- Przycisk **Zamknij,** zazwyczaj w niemodytnym oknie dialogowym.  
  
 Aby zamknąć okno w odpowiedzi na jeden z tych <xref:System.Windows.Window.Close%2A> mechanizmów niestandardowych, należy wywołać metodę. Poniższy przykład implementuje możliwość zamknięcia okna, wybierając **Exit** w **menu Plik.**  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Po zamknięciu okna wywołuje dwa <xref:System.Windows.Window.Closing> zdarzenia: <xref:System.Windows.Window.Closed>i .  
  
 <xref:System.Windows.Window.Closing>jest podniesiona przed zamknięciem okna i zapewnia mechanizm, za pomocą którego można zapobiec zamknięciu okna. Częstym powodem, aby zapobiec zamknięciu okna jest, jeśli zawartość okna zawiera zmodyfikowane dane. W tej sytuacji <xref:System.Windows.Window.Closing> zdarzenie może być obsługiwane w celu ustalenia, czy dane są zabrudzone, a jeśli tak, aby zapytać użytkownika, czy kontynuować zamykanie okna bez zapisywania danych lub anulować zamknięcie okna. W poniższym przykładzie przedstawiono kluczowe aspekty obsługi <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 Program <xref:System.Windows.Window.Closing> obsługi zdarzeń <xref:System.ComponentModel.CancelEventArgs>jest przekazywany `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> a , `true` który implementuje właściwość, która jest ustawiona, aby zapobiec zamknięciu okna.  
  
 Jeśli <xref:System.Windows.Window.Closing> nie jest obsługiwany lub jest obsługiwany, ale nie został anulowany, okno zostanie zamknięte. Tuż przed zamknięciem okna, <xref:System.Windows.Window.Closed> jest podniesiony. W tym momencie nie można zapobiec zamknięciu okna.  
  
> [!NOTE]
> Aplikację można skonfigurować tak, aby zamykała się automatycznie po zamknięciu głównego okna aplikacji (patrz) <xref:System.Windows.Application.MainWindow%2A>lub zamknięciu ostatniego okna. Aby uzyskać szczegółowe informacje, zobacz <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Podczas gdy okno może być jawnie zamknięte za pomocą mechanizmów podanych w obszarach innych niż klient i klient, okno może być również niejawnie zamknięte w wyniku zachowania w innych częściach aplikacji lub systemu Windows, w tym następujące:  
  
- Użytkownik wylogowuje się lub wyłącza system Windows.  
  
- Właściciel okna zamyka (patrz <xref:System.Windows.Window.Owner%2A>).  
  
- Główne okno aplikacji jest <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>zamknięte i jest .  
  
- <xref:System.Windows.Application.Shutdown%2A>nazywa się.  
  
> [!NOTE]
> Nie można ponownie otworzyć okna po jego zamknięciu.  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>Zdarzenia okresu istnienia okna  
 Na poniższej ilustracji przedstawiono sekwencję głównych zdarzeń w okresie istnienia okna:  
  
 ![Diagram, który pokazuje zdarzenia w okresie istnienia okna.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Na poniższej ilustracji przedstawiono sekwencję głównych zdarzeń w okresie<xref:System.Windows.Window.ShowActivated%2A> istnienia okna, które jest wyświetlane bez aktywacji ( jest ustawiona na `false` przed wyświetleniem okna):  
  
 ![Diagram, który pokazuje zdarzenia w okresie istnienia okna bez aktywacji.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>Lokalizacja okna  
 Gdy okno jest otwarte, ma lokalizację w wymiarach x i y względem pulpitu. Lokalizację tę można określić, <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> sprawdzając odpowiednio właściwości i. Można ustawić te właściwości, aby zmienić lokalizację okna.  
  
 Można również określić początkową <xref:System.Windows.Window> lokalizację, kiedy pojawia <xref:System.Windows.Window.WindowStartupLocation%2A> się po raz <xref:System.Windows.WindowStartupLocation> pierwszy, ustawiając właściwość z jedną z następujących wartości wyliczenia:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner>(domyślnie)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Jeśli lokalizacja uruchamiania <xref:System.Windows.WindowStartupLocation.Manual>jest określona <xref:System.Windows.Window.Top%2A> jako , a <xref:System.Windows.Window> <xref:System.Windows.Window.Left%2A> właściwości i właściwości nie zostały ustawione, poprosi system Windows o wyświetlenie lokalizacji.  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>Najwyższa część systemu Windows i z-order  
 Oprócz lokalizacji x i y, okno ma również lokalizację w wymiarze z, która określa jego pionową pozycję względem innych okien. Jest to znane jako okno z-order i istnieją dwa typy: normalny z-order i najwyższej kolejności z. Lokalizacja okna w *normalnej kolejności z* zależy od tego, czy jest ono aktualnie aktywne, czy nie. Domyślnie okno znajduje się w normalnej kolejności z. Lokalizacja okna w *najwyższej kolejności z* zależy również od tego, czy jest ono aktualnie aktywne, czy nie. Ponadto okna w najwyższej kolejności z zawsze znajdują się nad oknami w normalnej kolejności z. Okno znajduje się w najwyższej kolejności z, ustawiając jego <xref:System.Windows.Window.Topmost%2A> właściwość na `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 W ramach każdego zamówienia z aktualnie aktywne okno pojawia się nad wszystkimi innymi oknami w tej samej kolejności z.  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>Rozmiar okna  
 Oprócz lokalizacji pulpitu, okno ma rozmiar, który jest określany przez kilka właściwości, <xref:System.Windows.Window.SizeToContent%2A>w tym różne właściwości szerokości i wysokości i .  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>i <xref:System.Windows.FrameworkElement.MaxWidth%2A> są używane do zarządzania zakresem szerokości, które okno może mieć w okresie jego istnienia i są skonfigurowane w sposób pokazany w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Wysokość okna jest <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Height%2A>zarządzana <xref:System.Windows.FrameworkElement.MaxHeight%2A>przez program , i , i są skonfigurowane w sposób pokazany w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Ponieważ różne wartości szerokości i wartości wysokości określają zakres, możliwe jest, aby szerokość i wysokość okna o zmiennym rozmiarze były dostępne w dowolnym miejscu w określonym zakresie dla odpowiedniego wymiaru. Aby wykryć jego aktualną szerokość i wysokość, należy sprawdzić <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A>, odpowiednio.  
  
 Jeśli chcesz, aby szerokość i wysokość okna miały rozmiar, który pasuje do rozmiaru zawartości okna, <xref:System.Windows.Window.SizeToContent%2A> możesz użyć właściwości, która ma następujące wartości:  
  
- <xref:System.Windows.SizeToContent.Manual>. Brak efektu (domyślnie).  
  
- <xref:System.Windows.SizeToContent.Width>. Dopasuj do szerokości zawartości, która <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> ma taki sam efekt jak ustawienie zarówno do szerokości zawartości.  
  
- <xref:System.Windows.SizeToContent.Height>. Dopasuj do wysokości zawartości, która <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> ma taki sam efekt jak ustawienie zarówno na wysokości zawartości.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. Dopasuj do szerokości i wysokości zawartości, <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> która ma taki sam efekt <xref:System.Windows.FrameworkElement.MinWidth%2A> jak <xref:System.Windows.FrameworkElement.MaxWidth%2A> ustawienie zarówno na wysokości zawartości, jak i ustawienie zarówno szerokości, jak i szerokości zawartości.  
  
 W poniższym przykładzie przedstawiono okno, które automatycznie rozmiary, aby dopasować jego zawartość, zarówno w pionie, jak i w poziomie, po raz pierwszy pokazano.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 W poniższym przykładzie <xref:System.Windows.Window.SizeToContent%2A> pokazano, jak ustawić właściwość w kodzie, aby określić, jak okno jest resizes, aby dopasować jego zawartość .
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>Kolejność pierwszeństwa dla właściwości zmiany rozmiaru  
 Zasadniczo różne rozmiary właściwości okna łączą się w celu zdefiniowania zakresu szerokości i wysokości dla okna o zmiennym rozmiarze. Aby upewnić się, <xref:System.Windows.Window> że prawidłowy zakres jest utrzymywany, ocenia wartości właściwości rozmiaru przy użyciu następujących zamówień pierwszeństwa.  
  
 **Dla właściwości wysokości:**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **W przypadku właściwości szerokości:**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Kolejność pierwszeństwa można również określić rozmiar okna, gdy jest zmaksymalizowane, <xref:System.Windows.Window.WindowState%2A> który jest zarządzany z właściwością.  
  
<a name="WindowState"></a>
## <a name="window-state"></a>Stan okna  
 W okresie istnienia okna o zmiennym rozmiarze może mieć trzy stany: normalny, zminimalizowany i zmaksymalizowany. Okno o stanie *normalnym* jest domyślnym stanem okna. Okno z tym stanem umożliwia użytkownikowi przenoszenie i zmienianie jego rozmiaru za pomocą uchwytu o rozmiarze lub obramowania, jeśli można go zmienić rozmiar.  
  
 Okno z *zminimalizowanym* stanem zwija się <xref:System.Windows.Window.ShowInTaskbar%2A> do przycisku paska zadań, jeśli jest ustawione na `true`; w przeciwnym razie zwija się do najmniejszego możliwego rozmiaru i przenosi się do lewego dolnego rogu pulpitu. Żaden typ zminimalizowanego okna nie może być przesunięty za pomocą obramowania lub uchwytu o rozmiarze, chociaż zminimalizowane okno, które nie jest wyświetlane na pasku zadań, można przeciągać wokół pulpitu.  
  
 Okno o *stanie zmaksymalizowanym* rozszerza się do maksymalnego rozmiaru, który może <xref:System.Windows.FrameworkElement.MaxWidth%2A>być, który będzie tylko tak duży, jak jego , <xref:System.Windows.FrameworkElement.MaxHeight%2A>i <xref:System.Windows.Window.SizeToContent%2A> właściwości dyktować. Podobnie jak zminimalizowane okno, zmaksymalizowanego okna nie można zmienić rozmiaru za pomocą uchwytu zmienić rozmiar lub przeciągając obramowanie.  
  
> [!NOTE]
> Wartości <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>i <xref:System.Windows.FrameworkElement.Height%2A> właściwości okna zawsze reprezentują wartości dla stanu normalnego, nawet wtedy, gdy okno jest obecnie zmaksymalizowane lub zminimalizowane.  
  
 Stan okna można skonfigurować, ustawiając <xref:System.Windows.Window.WindowState%2A> jego właściwość, która <xref:System.Windows.WindowState> może mieć jedną z następujących wartości wyliczenia:  
  
- <xref:System.Windows.WindowState.Normal>(domyślnie)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 W poniższym przykładzie pokazano, jak utworzyć okno, które jest wyświetlane jako zmaksymalizowane po otwarciu.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Ogólnie rzecz biorąc <xref:System.Windows.Window.WindowState%2A> należy ustawić, aby skonfigurować stan początkowy okna. Po wyświetleniu okna o zmiennym rozmiarze użytkownicy mogą nacisnąć przyciski minimalizowanie, maksymalizacja i przywracanie na pasku tytułu okna, aby zmienić stan okna.  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>Wygląd okna  
 Wygląd obszaru klienta okna można zmienić, dodając do niego zawartość specyficzną dla okien, taką jak przyciski, etykiety i pola tekstowe. Aby skonfigurować obszar nie-klient, <xref:System.Windows.Window> zawiera kilka <xref:System.Windows.Window.Icon%2A> właściwości, które obejmują, <xref:System.Windows.Window.Title%2A> aby ustawić ikonę okna i ustawić jego tytuł.  
  
 Można również zmienić wygląd i zachowanie obramowania obszaru nienaksingowego, konfigurując tryb zmiany rozmiaru okna, styl okna i to, czy jest on wyświetlany jako przycisk na pasku zadań pulpitu.  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>Tryb ponownego rozmiaru  
 W zależności <xref:System.Windows.Window.WindowStyle%2A> od właściwości można kontrolować, jak (i czy) użytkownicy mogą zmienić rozmiar okna. Wybór stylu okna wpływa na to, czy użytkownik może zmienić rozmiar okna, przeciągając jego obramowanie za pomocą myszy, czy przyciski **Minimalizuj**, **Maksymalizuj**i **Zmienić rozmiar** są wyświetlane w obszarze nienawidalnym, a jeśli są wyświetlane, czy są włączone.  
  
 Można skonfigurować sposób ponownego rozmiaru okna, <xref:System.Windows.Window.ResizeMode%2A> ustawiając jego właściwość, <xref:System.Windows.ResizeMode> która może być jedną z następujących wartości wyliczenia:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize>(domyślnie)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Podobnie <xref:System.Windows.Window.WindowStyle%2A>jak w przypadku trybu zmiany rozmiaru okna jest mało prawdopodobne, aby zmienić w okresie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jego istnienia, co oznacza, że najprawdopodobniej ustawić go z znaczników.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Należy zauważyć, że można wykryć, czy okno jest zmaksymalizowane, zminimalizowane lub przywrócone przez sprawdzenie <xref:System.Windows.Window.WindowState%2A> właściwości.  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>Styl okna  
 Obramowanie, które jest widoczne z obszaru nie-klienta okna jest odpowiedni dla większości aplikacji. Istnieją jednak okoliczności, w których potrzebne są różne rodzaje granic lub w ogóle nie są potrzebne granice, w zależności od rodzaju okna.  
  
 Aby kontrolować typ obramowania okna, <xref:System.Windows.Window.WindowStyle%2A> należy ustawić jego właściwość <xref:System.Windows.WindowStyle> z jedną z następujących wartości wyliczenia:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow>(domyślnie)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Efekt tych stylów okien są zilustrowane na poniższym rysunku:  
  
 ![Ilustracja stylów obramowania okien.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Można ustawić <xref:System.Windows.Window.WindowStyle%2A> za [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocą znaczników lub kodu; ponieważ jest mało prawdopodobne, aby zmienić w okresie istnienia okna, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] najprawdopodobniej skonfigurujesz go przy użyciu znaczników.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Styl okna niekularnego  
 Istnieją również sytuacje, w <xref:System.Windows.Window.WindowStyle%2A> których style obramowania, które pozwala mieć nie są wystarczające. Na przykład można utworzyć aplikację z niesektorycznym obramowaniem, na przykład używa microsoft Windows Media Player.  
  
 Rozważmy na przykład okno dymka pokazane na poniższym rysunku:  
  
 ![Okno dymne z napisem Przeciągnij mnie.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Ten typ okna można utworzyć, <xref:System.Windows.Window.WindowStyle%2A> ustawiając właściwość na <xref:System.Windows.WindowStyle.None> <xref:System.Windows.Window> , i używając specjalnej obsługi, która ma przezroczystość.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Ta kombinacja wartości nakazuje okno do renderowania całkowicie przezroczyste. W tym stanie nie można używać ozdób obszaru nienakładowego okna (menu Zamknij, Minimalizuj, Maksymalizuj i Przywróć i przywróć) itd.In this state the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used. W związku z tym, trzeba podać własne.  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>Obecność paska zadań  

Domyślny wygląd okna zawiera przycisk paska zadań, taki jak pokazany na poniższym rysunku:

 ![Zrzut ekranu przedstawiający okno z przyciskiem paska zadań.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Niektóre typy okien nie mają przycisku paska zadań, na przykład okien komunikatów i okien dialogowych (zobacz [Omówienie okien dialogowych](dialog-boxes-overview.md)). Można kontrolować, czy przycisk paska zadań dla <xref:System.Windows.Window.ShowInTaskbar%2A> okna`true` jest wyświetlany, ustawiając właściwość (domyślnie).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami  
 <xref:System.Windows.Window>wymaga `UnmanagedCode` uzyskania uprawnień zabezpieczających do wystąpienia. W przypadku aplikacji zainstalowanych i uruchomionych z komputera lokalnego mieszczą się w zestawie uprawnień przyznanych aplikacji.  
  
 Jednak nie mieści się to w zestawie uprawnień przyznanych aplikacjom uruchamianym z Internetu lub lokalnej strefy intranetu przy użyciu ClickOnce. W związku z tym użytkownicy otrzymają ostrzeżenie zabezpieczeń ClickOnce i będzie musiał podnieść zestaw uprawnień dla aplikacji do pełnego zaufania.  
  
 Ponadto xbaps nie może domyślnie wyświetlać okien ani okien dialogowych. Aby zapoznać się z omówieniem zagadnień dotyczących bezpieczeństwa aplikacji autonomicznych, zobacz [Strategia zabezpieczeń WPF — Zabezpieczenia platformy](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>Inne typy systemu Windows  
 <xref:System.Windows.Navigation.NavigationWindow>to okno przeznaczone do obsługi zawartości żeglownej. Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](navigation-overview.md)).  
  
 Okna dialogowe są okna, które są często używane do zbierania informacji od użytkownika, aby zakończyć funkcję. Na przykład, gdy użytkownik chce otworzyć plik, okno dialogowe **Otwórz plik** jest zwykle wyświetlane przez aplikację, aby uzyskać nazwę pliku od użytkownika. Aby uzyskać więcej informacji, zobacz [Omówienie okien dialogowych](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Okna dialogowe — omówienie](dialog-boxes-overview.md)
- [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)
