---
title: Przegląd Okna WPF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 65
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c379a1db6b825a8ede7866661c11bdbf43cd630c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="wpf-windows-overview"></a>Przegląd Okna WPF
Użytkownicy korzystają z aplikacji autonomicznej Windows Presentation Foundation (WPF) za pośrednictwem systemu windows. Głównym celem okna jest zawartość hosta, wizualizuje danych, które umożliwia użytkownikom na interakcję z danymi. Autonomiczny [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji zapewniają własne systemu windows przy użyciu <xref:System.Windows.Window> klasy. W tym temacie przedstawiono <xref:System.Windows.Window> przed obejmujące podstawowe informacje dotyczące tworzenia i zarządzania systemu windows w autonomicznej aplikacji.  
  
> [!NOTE]
>  Obsługiwane w przeglądarce [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, w tym [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i utracić [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony, nie zapewniają własne systemu windows. Zamiast tego są obsługiwane w systemie windows pochodzącymi [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]. Zobacz [przeglądu aplikacje przeglądarki WPF XAML](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
  
<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Klasy okien  
 Na poniższym rysunku przedstawiono elementów składowych okna.  
  
 ![Elementy okna](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")  
  
 Okno jest podzielony na dwa obszary: obszaru nieklienckiego i obszaru klienckiego.  
  
 *Obszaru nieklienckiego* okna jest implementowany przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i zawiera elementy okna, które są wspólne dla większości systemu windows, w tym następujące:  
  
-   Obramowanie.  
  
-   Pasek tytułu.  
  
-   Ikona.  
  
-   Minimalizuj, Maksymalizuj i przywracanie przycisków.  
  
-   Przycisk Zamknij.  
  
-   Menu systemowe z elementów menu, które umożliwiają użytkownikom zminimalizować, zmaksymalizować, przywracania, przenieść, zmienianie rozmiaru i zamknąć okno.  
  
 *Obszaru klienckiego* okna jest obszar wewnątrz obszaru nieklienckiego okna i jest używany przez deweloperów w celu dodania zawartości specyficzne dla aplikacji, takich jak paski menu, pasków narzędzi i formantów.  
  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], okno jest hermetyzowany przez <xref:System.Windows.Window> klasy, która umożliwia wykonaj następujące czynności:  
  
-   Wyświetl okno.  
  
-   Skonfiguruj rozmiar, położenie i wyglądu okna.  
  
-   Zawartość aplikacji hosta.  
  
-   Zarządzanie okresem istnienia okna.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Implementowanie okna  
 Implementacja typowego okna obejmuje zarówno wygląd i zachowanie, gdy *wygląd* definiuje wygląd okna dla użytkowników i *zachowanie* definiuje sposób okno działa jak użytkownicy wchodzą w interakcje z nim. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], można zaimplementować wygląd i zachowanie przy użyciu okna albo kodu lub [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 Ogólnie rzecz biorąc, jednak wygląd okna jest implementowane za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i jego zachowanie jest implementowane za pomocą kodem, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Aby włączyć [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku znaczników i plik CodeBehind współdziałają ze sobą, wymagane są następujące:  
  
-   W znaczniku `Window` musi zawierać element `x:Class` atrybutu. Gdy aplikacja utworzeniu istnienie `x:Class` w znaczniku pliku powoduje, że [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] do utworzenia `partial` klasą pochodzącą z <xref:System.Windows.Window> i ma przypisaną nazwę określonego przez `x:Class` atrybutu. Wymaga to dodanie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklaracji przestrzeni nazw dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schematu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Wygenerowany `partial` klasa implementuje `InitializeComponent` metodę, która jest wywoływana, aby rejestrować zdarzenia i ustawić właściwości, które są wdrażane w znaczniku.  
  
-   W kodem, musi być klasa `partial` klasa o takiej samej nazwie, która jest określona przez `x:Class` atrybutu w kodzie znaczników oraz jego musi pochodzić od <xref:System.Windows.Window>. Dzięki temu plik CodeBehind ma być skojarzone z `partial` klasy, która jest generowane dla pliku znaczników, podczas tworzenia aplikacji (zobacz [kompilowania aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
-   W kodem <xref:System.Windows.Window> klasa musi implementować konstruktora, który wywołuje `InitializeComponent` metody. `InitializeComponent` jest implementowany przez kod znaczników na wygenerowany plik `partial` klasę, aby rejestrować zdarzenia i ustawić właściwości, które są zdefiniowane w znaczniku.  
  
> [!NOTE]
>  Po dodaniu nowego <xref:System.Windows.Window> do projektu przy użyciu [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> jest implementowane za pomocą zarówno znaczników i związane z kodem i zawiera niezbędną konfigurację, aby utworzyć skojarzenie między plikami znaczników i kodu powiązanego jako opisane poniżej.  
  
 W tej konfiguracji w miejscu, można skupić się na definiowanie wygląd okna w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i wykonania jego zachowanie związane z kodem. W poniższym przykładzie przedstawiono okno z przyciskiem zaimplementowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i program obsługi zdarzeń dla przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń w CodeBehind.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurowanie definicji okna narzędzia MSBuild  
 Jak zaimplementować okno programu Windows określa, jak jest skonfigurowany do [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]. Dla okna, które zdefiniowano przy użyciu zarówno [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i związane z kodem:  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki znaczników są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementów.  
  
-   Plików z kodem są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` elementów.  
  
 Przedstawiono to w następujących [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] pliku projektu.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Aby uzyskać informacje dotyczące tworzenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, zobacz [kompilowania aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Okres istnienia okna  
 Z dowolnej klasy okna zawiera okresu istnienia, który rozpoczyna się po raz pierwszy jest wystąpienia, po upływie którego jest otwarte, aktywowane i dezaktywowane i po pewnym czasie zamknięte.  
  
  
<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Otwarcie okna  
 Aby otworzyć okno, należy najpierw utworzyć wystąpienia, które przedstawiono w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 W tym przykładzie `MarkupAndCodeBehindWindow` jest tworzone podczas uruchamiania aplikacji, która pojawia się po <xref:System.Windows.Application.Startup> zdarzenia.  
  
 Podczas tworzenia wystąpienia klasy okna odwołanie do niej jest automatycznie dodawany do listy systemu windows, który jest zarządzany przez <xref:System.Windows.Application> obiektu (zobacz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>). Ponadto pierwsze okno z myślą o uruchamianiu domyślnie ustawione <xref:System.Windows.Application> jako okno aplikacji głównej (zobacz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 Okno finally jest otwierane przez wywołanie metody <xref:System.Windows.Window.Show%2A> metody; wynik jest wyświetlany na poniższej ilustracji.  
  
 ![Okno otwierane przez wywołanie metody Window.Show](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")  
  
 Okno, która jest otwarta przez wywołanie metody <xref:System.Windows.Window.Show%2A> jest oknem niemodalnym, co oznacza, że aplikacja działa w trybie, który umożliwia użytkownikom aktywowanie innych okien w tej samej aplikacji.  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A> jest wywoływana w trybie modalnym otworzyć systemu windows, takich jak okien dialogowych. Zobacz [omówienie pola dialogowe](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md) Aby uzyskać więcej informacji.  
  
 Gdy <xref:System.Windows.Window.Show%2A> jest wywoływana, okno wykonuje inicjalizację z przed jest wyświetlany ustanowienie infrastrukturę, która pozwala na odbieranie danych wejściowych użytkownika. Po zainicjowaniu okna <xref:System.Windows.Window.SourceInitialized> zdarzenia i pokazaniem okna.  
  
 Jako skrót <xref:System.Windows.Application.StartupUri%2A> może być ustawiony na Określ pierwsze okno, która jest otwierana automatycznie po uruchomieniu aplikacji.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Po uruchomieniu aplikacji okna, określony przez wartość <xref:System.Windows.Application.StartupUri%2A> jest otwarty modelessly; wewnętrznie okna jest otwarty przez wywołanie jego <xref:System.Windows.Window.Show%2A> metody.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Własność okna  
 Okno, która została otwarta przy użyciu <xref:System.Windows.Window.Show%2A> metoda nie ma niejawne relacji w oknie, który go utworzył; interakcji użytkowników z obu okna niezależnie od drugiego, co oznacza, że albo okna można wykonywać następujące czynności:  
  
-   Obejmuje innych (chyba, że jedna z systemu windows ma jego <xref:System.Windows.Window.Topmost%2A> ustawioną właściwość `true`).  
  
-   Można zminimalizować, zmaksymalizowane i przywrócenie historii bez wpływu na drugi.  
  
 Niektóre systemu windows wymagają relacji z ich otwartym oknie. Na przykład [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] aplikacja może otworzyć właściwości systemu windows i okien narzędzi, których typowe zachowanie jest, aby pokrywał się okna, w której zostały utworzone. Ponadto takie systemu windows należy zawsze zamknąć, zminimalizować zmaksymalizować i przywrócić w połączeniu z okna, w której zostały utworzone. Takiej relacji można ustalić wykonując jedno okno *własnych* inny i jest to osiągane przez ustawienie <xref:System.Windows.Window.Owner%2A> właściwość *należące do okna* z odwołaniem do *właściciela okno*. Przedstawiono to w poniższym przykładzie.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Po ustanowieniu prawa własności:  
  
-   Należących do okna może odwoływać się jej okna nadrzędnego, sprawdzając wartość jego <xref:System.Windows.Window.Owner%2A> właściwości.  
  
-   Okno właściciela umożliwia odnalezienie wszystkich okien jest właścicielem, sprawdzając wartość jego <xref:System.Windows.Window.OwnedWindows%2A> właściwości.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Zapobieganie aktywacji okna  
 Istnieją scenariusze, w której systemu windows nie należy aktywować, gdy wyświetlana, takie jak windows konwersacji aplikacji messenger stylu Internet lub windows powiadomienia z aplikacji poczty e-mail.  
  
 Jeśli aplikacja ma okna, które nie powinny być aktywowany, gdy wyświetlany, można ustawić jej <xref:System.Windows.Window.ShowActivated%2A> właściwości `false` przed wywołaniem <xref:System.Windows.Window.Show%2A> metody po raz pierwszy. W rezultacie:  
  
-   Okno nie został aktywowany.  
  
-   W oknie <xref:System.Windows.Window.Activated> nie zdarzenia.  
  
-   Obecnie aktywowanego okno pozostaje aktywowane.  
  
 Okno zostanie stają się aktywowane, jednak zaraz po aktywowaniu przez użytkownika go, klikając klienta lub obszaru nieklienckiego. W takim przypadku:  
  
-   Okno jest aktywowane.  
  
-   W oknie <xref:System.Windows.Window.Activated> zdarzenia.  
  
-   Okno wcześniej aktywowana jest dezaktywowana.  
  
-   W oknie <xref:System.Windows.Window.Deactivated> i <xref:System.Windows.Window.Activated> zdarzenia pojawienia się później zgodnie z oczekiwaniami w odpowiedzi na działania użytkownika.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Aktywacja okna  
 Przy pierwszym otwarciu okna, staje się oknem aktywnym (chyba że jest ona wyświetlana z <xref:System.Windows.Window.ShowActivated%2A> ustawioną `false`). *Aktywne okno* okna, który jest obecnie przechwytywanie danych wejściowych użytkownika, takie jak naciśniętych klawiszy i kliknięcia myszą. Gdy okno staje się aktywny, zgłasza <xref:System.Windows.Window.Activated> zdarzeń.  
  
> [!NOTE]
>  Przy pierwszym otwarciu okna, <xref:System.Windows.FrameworkElement.Loaded> i <xref:System.Windows.Window.ContentRendered> zdarzenia są generowane tylko po <xref:System.Windows.Window.Activated> zdarzenia. Pamiętając o tym, okno skutecznie jest uznawana za otwarte po <xref:System.Windows.Window.ContentRendered> jest wywoływane.  
  
 Po uaktywnieniu okna użytkownika można uaktywnić inne okno w tej samej aplikacji, lub aktywować inną aplikację. W takim przypadku aktualnie aktywne okno staje się dezaktywowane i zgłasza <xref:System.Windows.Window.Deactivated> zdarzeń. Podobnie, gdy użytkownik wybierze aktualnie wyłączone okna, okno staje się aktywny ponownie i <xref:System.Windows.Window.Activated> jest wywoływane.  
  
 Najczęściej zdarza się do obsługi <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated> jest pozwala włączać i wyłączać funkcje, które można uruchomić tylko wtedy, gdy okno jest aktywne. Na przykład niektóre windows wyświetlanie zawartości interaktywnej, która wymaga wprowadzenia danych przez użytkownika stałej lub uwagi, łącznie z gier i odtwarzaczy wideo. Poniższy przykład jest uproszczone odtwarzacza wideo, który demonstruje sposób obsługi <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated> implementacji tego zachowania.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Innych typów aplikacji nadal może uruchomić kod w tle, gdy okno jest dezaktywowana. Na przykład klienta poczty e-mail mogą nadal sondowania serwera poczty, gdy użytkownik korzysta z innych aplikacji. Aplikacji, takich jak te często udostępniają różne lub dodatkowe zachowanie podczas dezaktywacji głównego okna. W odniesieniu do programu poczty może to oznaczać zarówno dodawania nowego elementu poczty do skrzynki odbiorczej i ikony powiadomień na pasku zadań. Ikona powiadomienia muszą wyświetlane tylko wtedy, gdy okno poczty nie jest aktywne, w którym można określić sprawdzając <xref:System.Windows.Window.IsActive%2A> właściwości.  
  
 Po zakończeniu zadania w tle, okno może być konieczne bardziej pilne powiadamia użytkownika, wywołując <xref:System.Windows.Window.Activate%2A> metody. Jeśli użytkownik prowadzi interakcję z innej aplikacji aktywowana po <xref:System.Windows.Window.Activate%2A> nosi okna zadań miga. Jeśli użytkownik prowadzi interakcję z bieżącej aplikacji, podczas wywoływania <xref:System.Windows.Window.Activate%2A> zostanie wyświetlone okno na pierwszym planie.  
  
> [!NOTE]
>  Można obsługiwać przy użyciu aktywacji zakresu aplikacji <xref:System.Windows.Application.Activated?displayProperty=nameWithType> i <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> zdarzenia.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Zamknięcie okna  
 Czas życia okna uruchamia przesyłanych do końca, gdy użytkownik zamyka go. Okna można zamknąć przy użyciu elementów w obszarze klienta z systemem innym niż, takie jak następujące:  
  
-   **Zamknij** elementu **systemu** menu.  
  
-   Naciśnięcie klawisza ALT + F4.  
  
-   Naciśnięcie przycisku **Zamknij** przycisku.  
  
 Można podać dodatkowe mechanizmy obszaru klienta, aby zamknąć okno, typowe jeden z nich są następujące:  
  
-   **Zakończenia** elementu **pliku** menu, zwykle głównej aplikacji systemu windows.  
  
-   A **Zamknij** elementu **pliku** menu, zwykle w oknie aplikacji dodatkowej.  
  
-   A **anulować** przycisku, zwykle na modalne okno dialogowe.  
  
-   A **Zamknij** przycisku, zwykle na niemodalne okno dialogowe.  
  
 Aby zamknąć okno w odpowiedzi na jeden z tych mechanizmów niestandardowe, należy wywołać <xref:System.Windows.Window.Close%2A> metody. Poniższy przykład implementuje możliwości, aby zamknąć okno, wybierając **zakończenia** na **pliku** menu.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Po zamknięciu okna, zgłasza dwa zdarzenia: <xref:System.Windows.Window.Closing> i <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing> jest wywoływane przed okno zostanie zamknięte i zapewnia mechanizm, przez które okno można zapobiec zamknięcia. Najczęściej zdarza się zapobiegające zamknięcia okna jest czy zawartości okna zawiera modyfikacji danych. W takiej sytuacji <xref:System.Windows.Window.Closing> zdarzeń mogą być obsługiwane w celu ustalenia, czy dane są zakłócone, a jeśli tak, aby zadać je użytkownikowi, czy kontynuować zamykania okna bez zapisywania danych do anulowania zamknięcia okna. W poniższym przykładzie przedstawiono kluczowe aspekty Obsługa <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  
 
  
 <xref:System.Windows.Window.Closing> Program obsługi zdarzeń jest przekazywany <xref:System.ComponentModel.CancelEventArgs>, który implementuje `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwości ustawionej dla `true` zapobiegające zamknięcia okna.  
  
 Jeśli <xref:System.Windows.Window.Closing> nie jest obsługiwany lub jest obsługiwane, ale nie została anulowana, okno zostanie zamknięte. Tuż przed, w rzeczywistości zostanie zamknięte okno <xref:System.Windows.Window.Closed> jest wywoływane. W tym momencie okna nie można zablokować zamknięcia.  
  
> [!NOTE]
>  Aplikację można skonfigurować do zamykania automatycznie, gdy okno aplikacji głównej zamyka (zobacz <xref:System.Windows.Application.MainWindow%2A>) lub ostatni okno zostanie zamknięte. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Gdy okno może zostać jawnie zamknięty przy użyciu mechanizmów udostępnianych w obszarach-klient i klient, okno również można niejawnie zamknięty wyniku zachowanie w innych częściach aplikacji lub [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], takie jak:  
  
-   Użytkownik wyloguje się lub zamyka system Windows.  
  
-   Zamyka okno właściciela (zobacz <xref:System.Windows.Window.Owner%2A>).  
  
-   Okno aplikacji głównej jest zamknięte i <xref:System.Windows.Application.ShutdownMode%2A> jest <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
-   <xref:System.Windows.Application.Shutdown%2A> jest wywoływana.  
  
> [!NOTE]
>  Nie można otworzyć ponownie okno, po jego zamknięciu.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>Okno okres istnienia zdarzeń  
 Na poniższej ilustracji przedstawiono sekwencję zdarzeń główną w trakcie trwania okna.  
  
 ![Okres istnienia okna](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")  
  
 Na poniższej ilustracji przedstawiono sekwencję zdarzeń podmiotu zabezpieczeń w okresie istnienia typu window, który jest wyświetlany bez aktywacji (<xref:System.Windows.Window.ShowActivated%2A> ustawiono `false` przed pokazaniem okna).  
  
 ![Window Lifetime &#40;Window.ShowActivated &#61; False&#41;](../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Położenie okna  
 Po otwarciu okna składa się z lokalizacji w x i y wymiarów względem pulpitu. Tej lokalizacji można ustalić sprawdzając <xref:System.Windows.Window.Left%2A> i <xref:System.Windows.Window.Top%2A> właściwości, odpowiednio. Można ustawić te właściwości, aby zmienić lokalizację okna.  
  
 Można również określić początkową lokalizację <xref:System.Windows.Window> po wyświetleniu przez ustawienie <xref:System.Windows.Window.WindowStartupLocation%2A> właściwości z jedną z następujących <xref:System.Windows.WindowStartupLocation> wartości wyliczenia:  
  
-   <xref:System.Windows.WindowStartupLocation.CenterOwner> (ustawienie domyślne)  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Jeśli lokalizacja uruchamiania jest określana jako <xref:System.Windows.WindowStartupLocation.Manual>i <xref:System.Windows.Window.Left%2A> i <xref:System.Windows.Window.Top%2A> nie ustawiono właściwości <xref:System.Windows.Window> pojawi się monit z systemu Windows dla lokalizacji w wynikach.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>Windows najwyższego poziomu i porządek osi z  
 Oprócz również posiadanie x i y lokalizacji, okno ma miejsce w przypadku wymiaru z określa jej położenie w pionie względem innych okien. Jest to nazywane okna porządek osi z, a istnieją dwa typy: normalnej kolejności i znajdujących się na górze porządek osi z. Położenie okna *normalnej kolejności z* zależy od tego, czy nie jest on obecnie aktywne. Domyślnie okno znajduje się w normalnej kolejności. Położenie okna *znajdujące się najwyżej porządek* również zależy od tego, czy nie jest on obecnie aktywne. Ponadto w najwyższym poziomie porządek osi z systemem windows zawsze znajdują się powyżej w normalnym porządek osi z systemem windows. Okno znajduje się w najwyższej kolejności przez ustawienie jej <xref:System.Windows.Window.Topmost%2A> właściwości `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 W ramach każdej kolejności z aktywnym oknie jest wyświetlany ponad wszystkimi innych okien w tej samej kolejności.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Rozmiar okna  
 Oprócz o lokalizacji pulpitu, okno ma rozmiar, który jest określany przez kilka właściwości, w tym różnych właściwości width i height i <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, i <xref:System.Windows.FrameworkElement.MaxWidth%2A> służą do zarządzania zakresem szerokości okna może mieć przez jego okres istnienia, które są skonfigurowane, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Wysokość okna jest zarządzana przez <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, i <xref:System.Windows.FrameworkElement.MaxHeight%2A>i są skonfigurowane, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Ponieważ różne wartości szerokości i wysokości wartości każdego Określ zakres, istnieje możliwość szerokość i wysokość okna o zmiennych rozmiarach do dowolnego miejsca mieścić się w zakresie określonym dla odpowiednich wymiaru. Aby wykryć bieżącego szerokości i wysokości, sprawdź <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A>odpowiednio.  
  
 Jeśli chcesz, szerokość i wysokość okna mają rozmiar, który pasuje do rozmiaru okna elementu zawartości, można użyć <xref:System.Windows.Window.SizeToContent%2A> właściwość, która ma następujące wartości:  
  
-   <xref:System.Windows.SizeToContent.Manual>. Żadnego skutku (ustawienie domyślne).  
  
-   <xref:System.Windows.SizeToContent.Width>. Dopasuj do szerokości zawartości, który działa tak samo jak ustawienie zarówno <xref:System.Windows.FrameworkElement.MinWidth%2A> i <xref:System.Windows.FrameworkElement.MaxWidth%2A> szerokość zawartości.  
  
-   <xref:System.Windows.SizeToContent.Height>. Dopasuj do wysokości zawartości, który działa tak samo jak ustawienie zarówno <xref:System.Windows.FrameworkElement.MinHeight%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> do wysokości zawartości.  
  
-   <xref:System.Windows.SizeToContent.WidthAndHeight>. Dopasuj do zawartości szerokość i wysokość, który działa tak samo jak ustawienie zarówno <xref:System.Windows.FrameworkElement.MinHeight%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> do wysokości zawartości, a ustawienie obu <xref:System.Windows.FrameworkElement.MinWidth%2A> i <xref:System.Windows.FrameworkElement.MaxWidth%2A> szerokość zawartości.  
  
 W poniższym przykładzie przedstawiono okno to automatycznie rozmiary dopasowana do jego zawartości, w pionie i w poziomie, przy pierwszym wyświetleniu.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Window.SizeToContent%2A> właściwości w kodzie, aby określić, jak zmienia rozmiar okna dopasowana do jego zawartości.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Hierarchia ważności dotyczące ustalania rozmiaru właściwości  
 Zasadniczo różne właściwości rozmiarów okna połączenie umożliwia zdefiniowanie zakresu szerokość i wysokość okna o zmiennym rozmiarze. Aby zapewnić prawidłowy zakres jest utrzymywana, <xref:System.Windows.Window> oblicza wartości właściwości rozmiar przy użyciu następujących zleceń pierwszeństwa.  
  
 **Dla właściwości wysokość:**  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Dla właściwości Width:**  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Kolejność pierwszeństwa można także określić rozmiaru okna, gdy jej jest zmaksymalizowane, który jest zarządzany z <xref:System.Windows.Window.WindowState%2A> właściwości.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>Stanu okna  
 Okres istnienia okna o zmiennym rozmiarze, może mieć trzy stany: Normalny, zminimalizowany i zmaksymalizowane. Okno z *normalne* stan jest domyślny stan okna. Okno z tego stanu umożliwia przenoszenie i zmienianie rozmiaru go za pomocą uchwyt zmiany rozmiaru lub obramowania, gdy chodzi o zmiennym rozmiarze.  
  
 Okno z *zminimalizowane* stanu zwijany do jego przycisk paska zadań, jeśli <xref:System.Windows.Window.ShowInTaskbar%2A> ustawiono `true`; w przeciwnym razie go zwijany do najmniejszy rozmiar może być i przenosi się w lewym dolnym rogu pulpitu. Ani typu zminimalizowanego okna można zmieniać za pomocą obramowanie lub zmień rozmiar uchwytu, mimo że zminimalizowanego okna, który nie jest wyświetlany na pasku zadań mogą być przeciągnięte wokół pulpitu.  
  
 Okno z *zmaksymalizowane* stan zostanie rozszerzony do maksymalnego rozmiaru może być, które będą tylko tak duże jak jego <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, i <xref:System.Windows.Window.SizeToContent%2A> dyktować właściwości. Podobnie jak zminimalizowanego okna zmaksymalizowane okno nie można zmienić rozmiaru za pomocą uchwyt zmiany rozmiaru lub przeciągając obramowanie.  
  
> [!NOTE]
>  Wartości <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, i <xref:System.Windows.FrameworkElement.Height%2A> właściwości okna zawsze reprezentują wartości normalnym stanie nawet wtedy, gdy okno jest obecnie zmaksymalizowany lub zminimalizowany.  
  
 Stan okna można skonfigurować przez ustawienie jej <xref:System.Windows.Window.WindowState%2A> właściwość, która może mieć jedną z następujących <xref:System.Windows.WindowState> wartości wyliczenia:  
  
-   <xref:System.Windows.WindowState.Normal> (ustawienie domyślne)  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 Poniższy przykład przedstawia sposób tworzenia okna, która jest wyświetlana jako zmaksymalizowany po otwarciu.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Ogólnie rzecz biorąc, należy ustawić <xref:System.Windows.Window.WindowState%2A> skonfigurować początkowy stan okna. Po o zmiennym rozmiarze okna jest widoczne, użytkownicy mogą naciśnij przycisk Minimalizuj, maksymalizowania i przywracanie przycisków na pasku tytułu okna zmiany stanu okna.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Wygląd okna  
 Możesz zmienić wygląd obszaru klienckiego okna przez dodanie zawartości określonego okna, takie jak przyciski, etykiety i pola tekstowe. Aby skonfigurować obszaru nieklienckiego <xref:System.Windows.Window> udostępnia kilka właściwości, które obejmują <xref:System.Windows.Window.Icon%2A> można ustawić ikonę okna i <xref:System.Windows.Window.Title%2A> można ustawić tytułu.  
  
 Możesz również zmienić wygląd i zachowanie obramowania obszaru nieklienckiego przez skonfigurowanie tryb zmiany rozmiaru okna, styl okna, czy jest on wyświetlany jako przycisk paska zadań pulpitu.  
  
  
<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Zmiana rozmiaru w trybie  
 W zależności od <xref:System.Windows.Window.WindowStyle%2A> właściwości, można kontrolować sposób (i jeśli) użytkownicy mogą zmieniać rozmiar okna. Wybór styl okna wpływa na, czy użytkownik może zmienić rozmiar okna przez przeciągnięcie jego krawędzi myszą, czy **Minimalizuj**, **Maksymalizuj**, i **Resize** przycisków są wyświetlane w obszarze klienta z systemem innym niż i, jeśli są one wyświetlane, czy są włączone.  
  
 Można skonfigurować, jak zmienia rozmiar okna, ustawiając jego <xref:System.Windows.Window.ResizeMode%2A> właściwość, która może być jedną z następujących <xref:System.Windows.ResizeMode> wartości wyliczenia:  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <xref:System.Windows.ResizeMode.CanResize> (ustawienie domyślne)  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Jak <xref:System.Windows.Window.WindowStyle%2A>, tryb zmiany rozmiaru okna jest mało prawdopodobne zmienić przez jego okres istnienia oznacza, że użytkownik będzie prawdopodobnie ustawiony z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Należy pamiętać, że może wykryć, czy okno jest zmaksymalizowane, zminimalizowane lub przywrócić sprawdzając <xref:System.Windows.Window.WindowState%2A> właściwości.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Styl okna  
 Obramowanie, które jest udostępniane z obszaru klienckiego z systemem innym niż okno jest odpowiednia dla większości aplikacji. Istnieją jednak sytuacji, gdy wymagane są różne typy obramowań lub bez obramowania są niezbędne, w zależności od typu okna.  
  
 Do kontrolowania, jaki typ obramowania okna pobiera, ustawia jego <xref:System.Windows.Window.WindowStyle%2A> właściwości z jedną z następujących wartości <xref:System.Windows.WindowStyle> wyliczenie:  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <xref:System.Windows.WindowStyle.SingleBorderWindow> (ustawienie domyślne)  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Efekt te style okna przedstawiono na poniższej ilustracji.  
  
 ![Style okna](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.PNG "WindowOverviewFigure6")  
  
 Można ustawić <xref:System.Windows.Window.WindowStyle%2A> za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników lub kod; ponieważ jest mało prawdopodobne zmienić okres istnienia okna, najprawdopodobniej skonfigurujesz za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Styl okna nieregularnych  
 Istnieją również sytuacje, gdy obramowanie style, które <xref:System.Windows.Window.WindowStyle%2A> umożliwia użytkownikowi są niewystarczające. Na przykład można utworzyć aplikację z nieregularnych obramowanie, takich jak [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] używa.  
  
 Rozważmy na przykład okno bąbelków mowy pokazano na poniższej ilustracji.  
  
 ![Okno nieprostokątny](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")  
  
 Ten typ okna mogą być tworzone przez ustawienie <xref:System.Windows.Window.WindowStyle%2A> właściwości <xref:System.Windows.WindowStyle.None>i przy użyciu specjalnego obsługuje <xref:System.Windows.Window> ma przezroczystości.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Ta kombinacja wartości powoduje, że okno do renderowania całkowicie niewidoczne. W tym stanie nie można użyć skojarzenia niekliencki okna (Zamknij menu, przyciski Minimalizuj, Maksymalizuj i przywracania i tak dalej). W związku z tym należy podać własne.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Obecność na pasku zadań  
 Wygląd domyślny okna zawiera przycisk paska zadań, tak jak pokazano na poniższej ilustracji.  
  
 ![Okno z przyciskiem paska zadań](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.PNG "WindowOverviewFigure7")  
  
 Niektóre typy systemu windows nie ma przycisk paska zadań, takich jak komunikatów i okien dialogowych (zobacz [omówienie pola dialogowe](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)). Można kontrolować, czy przycisk paska zadań dla okna jest wyświetlany przez ustawienie <xref:System.Windows.Window.ShowInTaskbar%2A> właściwości (`true` domyślnie).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 <xref:System.Windows.Window> wymaga `UnmanagedCode` uprawnień do można utworzyć wystąpienia. Dla aplikacji zainstalowanych na i uruchomiony na komputerze lokalnym to znajduje się w zestaw uprawnień, które są przypisywane do aplikacji.  
  
 Jednak to znajduje się poza zestaw uprawnień dla aplikacji, które będą uruchamiane z Internet lub lokalny intranet strefy przy użyciu [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]. W związku z tym, użytkownicy będą otrzymywać [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] ostrzeżenie o zabezpieczeniach i trzeba będzie podniesienie poziomu zestawu uprawnień dla aplikacji do pełnego zaufania.  
  
 Ponadto [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] domyślnie nie można wyświetlić systemu windows lub w oknach dialogowych. Omówienie zagadnienia dotyczące zabezpieczeń aplikacji autonomicznych, zobacz [strategii zabezpieczeń WPF - zabezpieczeń platformy](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Inne typy systemu Windows  
 <xref:System.Windows.Navigation.NavigationWindow> to okno jest przeznaczony do hostowania zawartości można nawigować. Aby uzyskać więcej informacji, zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md)).  
  
 Okna dialogowe są systemu windows, które są często używane do zbierania informacji od użytkownika, aby ukończyć funkcji. Na przykład gdy użytkownik chce, aby otworzyć plik, **Otwieranie pliku** zazwyczaj zostanie wyświetlone okno dialogowe przez aplikację można pobrać nazwy pliku od użytkownika. Aby uzyskać więcej informacji, zobacz [omówienie pola dialogowe](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Window>  
 <xref:System.Windows.MessageBox>  
 <xref:System.Windows.Navigation.NavigationWindow>  
 <xref:System.Windows.Application>  
 [Okna dialogowe — omówienie](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)  
 [Kompilowanie aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
