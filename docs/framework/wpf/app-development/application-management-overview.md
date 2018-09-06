---
title: Przegląd Zarządzanie aplikacjami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: ba8d07a26b7e6abc511e5b24db26162b46a2b0a1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042260"
---
# <a name="application-management-overview"></a>Przegląd Zarządzanie aplikacjami
Wszystkie aplikacje zwykle korzystają ze wspólnego zestawu funkcji, które mają zastosowanie do wdrożenia aplikacji i zarządzania. Ten temat zawiera omówienie funkcji w <xref:System.Windows.Application> klasa do tworzenia aplikacji i zarządzaniem nimi.  
   
  
## <a name="the-application-class"></a>Klasa aplikacji  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], typowych funkcji o zakresie aplikacji jest hermetyzowany w <xref:System.Windows.Application> klasy. <xref:System.Windows.Application> Klasa zawiera następujące funkcje:  
  
-   Śledzenie i interakcji z okresem istnienia aplikacji.  
  
-   Trwa pobieranie i przetwarzanie parametry wiersza polecenia.  
  
-   Wykrywanie i reagowanie na nieobsługiwanych wyjątków.  
  
-   Udostępnianie właściwości zakresu aplikacji i zasobów.  
  
-   Zarządzanie systemem windows w aplikacje autonomiczne.  
  
-   Śledzenie i zarządzanie nimi nawigacji.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Jak wykonywać typowe zadania za pomocą klasy aplikacji  
 Jeśli interesuje Cię nie wszystkie szczegóły <xref:System.Windows.Application> klasy, w poniższej tabeli wymieniono niektóre typowe zadania <xref:System.Windows.Application> i sposobu ich wykonania. Wyświetlając interfejsu API i Tematy pokrewne można znaleźć więcej informacji i przykładowy kod.  
  
|Zadanie|Podejście|  
|----------|--------------|  
|Pobierz obiekt, który reprezentuje bieżącej aplikacji|Użyj <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> właściwości.|  
|Dodaj ekran startowy aplikacji|Zobacz [dodać ekran powitalny do aplikacji WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Uruchamianie aplikacji|Użyj <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> metody.|  
|Zatrzymaj aplikację|Użyj <xref:System.Windows.Application.Shutdown%2A> metody <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> obiektu.|  
|Pobierz argumenty z wiersza polecenia|Obsługa <xref:System.Windows.Application.Startup?displayProperty=nameWithType> zdarzeń i używania <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> właściwości. Aby uzyskać przykład, zobacz <xref:System.Windows.Application.Startup?displayProperty=nameWithType> zdarzeń.|  
|Pobieranie i ustawianie kod zakończenia aplikacji|Ustaw <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Application.Exit?displayProperty=nameWithType> program obsługi zdarzeń lub wywołanie <xref:System.Windows.Application.Shutdown%2A> metody i przekaż liczbą całkowitą.|  
|Wykrywanie oraz reagowanie na nieobsłużonych wyjątków|Obsługa <xref:System.Windows.Application.DispatcherUnhandledException> zdarzeń.|  
|Pobieranie i ustawianie zasobów zakresu aplikacji|Użyj <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> właściwości.|  
|Użyj słownika zasobów zakresu aplikacji|Zobacz [użyć słownika zasobów zakresu aplikacji](../../../../docs/framework/wpf/app-development/how-to-use-an-application-scope-resource-dictionary.md).|  
|Pobieranie i ustawianie właściwości z zakresu aplikacji|Użyj <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> właściwości.|  
|Pobierz i Zapisz stan aplikacji|Zobacz [Utrwalaj i przywracaj właściwości zakresu aplikacji między sesjami aplikacji](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).|  
|Zarządzaj pliki danych bez kodu, w tym pliki zasobów, pliki zawartości i pliki do witryny pochodzenia.|Zobacz [zasoby aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).|  
|Zarządzanie systemem windows w aplikacje autonomiczne|Zobacz [Przegląd Windows WPF](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).|  
|Śledzenie i zarządzanie nawigacji|Zobacz [Nawigacja — omówienie](../../../../docs/framework/wpf/app-development/navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Definicja aplikacji  
 Do korzystania z funkcji <xref:System.Windows.Application> klasy należy zaimplementować definicji aplikacji. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definicji aplikacji jest klasa, która pochodzi od klasy <xref:System.Windows.Application> i jest skonfigurowany przy użyciu specjalnego [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] ustawienie.  
  
### <a name="implementing-an-application-definition"></a>Implementowanie definicji aplikacji  
 Typowa [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definicji aplikacji jest implementowany przy użyciu znaczników i związane z kodem. Dzięki temu można za pomocą znaczników deklaratywne Ustawianie właściwości aplikacji, zasobów i rejestrowanie zdarzeń, obsługa zdarzeń i implementowanie zachowania specyficzne dla aplikacji w związanym z kodem.  
  
 Poniższy przykład pokazuje, jak zaimplementować definicję aplikacji przy użyciu znaczników i związane z kodem:  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Aby umożliwić pliku znaczników i pliku związanego z kodem pracy zespołowej, następujące ma miejsce:  
  
-   W znaczniku `Application` element musi zawierać `x:Class` atrybutu. Podczas kompilowania aplikacji, istnienie `x:Class` w znaczniku pliku powoduje, że [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] utworzyć `partial` klasę pochodzącą od <xref:System.Windows.Application> i ma nazwę, która jest określona przez `x:Class` atrybutu. Wymaga to dodania [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklarację przestrzeni nazw dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schematu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).  
  
-   Związane z kodem, klasy musi być `partial` klasy o takiej samej nazwie, który jest określony przez `x:Class` atrybutu w znacznikach i musi pochodzić od klasy <xref:System.Windows.Application>. Dzięki temu pliku związanego z kodem, który ma zostać skojarzony z `partial` klasy, który jest generowany dla pliku znaczników Po skompilowaniu aplikację (zobacz [Kompilowanie aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Podczas tworzenia nowego projektu aplikacji WPF lub aplikacja przeglądarki środowiska WPF projekt za pomocą [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], definicji aplikacji jest domyślnie włączone i jest definiowana za pomocą znaczników i związane z kodem.  
  
 Ten kod jest minimalna, który jest wymagany do zaimplementowania definicji aplikacji. Jednak dodatkowe [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] konfiguracji musi zapewnić definicji aplikacji przed kompilowania i uruchamiania aplikacji.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Konfigurowanie definicji aplikacji dla programu MSBuild  
 Aplikacje autonomiczne i [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] wymagają wykonania pewien poziom infrastrukturą, przed uruchomieniem przez nich. Najważniejsza część tej infrastruktury jest punktem wejścia. Gdy aplikacja zostanie uruchomiona przez użytkownika, system operacyjny wywołuje punkt wejścia, który jest dobrze znanych funkcji uruchamiania aplikacji.  
  
 Tradycyjnie deweloperzy musieli zapisać niektórych lub wszystkich ten kod samodzielnie, w zależności od technologii. Jednak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] generuje kod dla Ciebie, gdy pliku znaczników definicji aplikacji jest skonfigurowany jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` elementu, jak pokazano w następującym [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] pliku projektu:  
  
```xml  
<Project   
  DefaultTargets="Build"  
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 Ponieważ plik CodeBehind zawiera kod, jest ona oznaczona jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` elementu, jest to normalne.  
  
 Zastosowanie tych [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] konfiguracji do plików znaczników i związane z kodem definicji aplikacji powoduje, że [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] do generowania kodu, podobnie do poniższego:  
  
 [!code-csharp[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode1)]
 [!code-vb[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode1)]  
[!code-csharp[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode2)]
[!code-vb[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode2)]  
  
 Następnie kod wynikowy rozszerzają definicji aplikacji kodem dodatkowej infrastruktury, który zawiera metodę punktu wejścia `Main`. <xref:System.STAThreadAttribute> Atrybut jest stosowany do `Main` metodę, aby wskazać, że głównym [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacja jest wątkiem STA., który jest wymagany do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji. Po wywołaniu `Main` tworzy nowe wystąpienie klasy `App` przed wywołaniem `InitializeComponent` metodę, aby rejestrować zdarzenia i ustawić właściwości, które są implementowane w znacznikach. Ponieważ `InitializeComponent` jest generowany, nie trzeba jawnie wywołać `InitializeComponent` z definicji aplikacji, tak jak w przypadku <xref:System.Windows.Controls.Page> i <xref:System.Windows.Window> implementacji. Na koniec <xref:System.Windows.Application.Run%2A> metoda jest wywoływana, aby uruchomić aplikację.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Pobieranie bieżącej aplikacji  
 Ponieważ funkcje <xref:System.Windows.Application> klasy są współdzielone przez aplikację, może istnieć tylko jedno wystąpienie <xref:System.Windows.Application> klasy na <xref:System.AppDomain>. Do wyegzekwowania tego, <xref:System.Windows.Application> klasy jest implementowany jako klasa pojedyncza (zobacz [wdrażanie pojedynczego wystąpienia w języku C#](https://go.microsoft.com/fwlink/?LinkId=100567)), który tworzy pojedyncze wystąpienie sam i zapewnia udostępniony dostęp do niego za pomocą `static` <xref:System.Windows.Application.Current%2A> Właściwość.  
  
 Poniższy kod pokazuje, jak można uzyskać odwołanie do <xref:System.Windows.Application> obiektu dla bieżącego <xref:System.AppDomain>.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A> Zwraca odwołanie do wystąpienia <xref:System.Windows.Application> klasy. Jeśli chcesz, aby odwołanie do usługi <xref:System.Windows.Application> klasy, należy rzutować wartość <xref:System.Windows.Application.Current%2A> właściwości, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Możesz badać wartości <xref:System.Windows.Application.Current%2A> w dowolnym momencie w trakcie trwania <xref:System.Windows.Application> obiektu. Jednakże należy zachować ostrożność. Po <xref:System.Windows.Application> tworzenia wystąpienia klasy, ma okres, przez który stan <xref:System.Windows.Application> obiektu jest niespójny. W tym okresie <xref:System.Windows.Application> wykonuje różnych zadań inicjowania, które są wymagane przez kod, aby uruchomić, w tym ustanawiania infrastruktury aplikacji, ustawianie właściwości i rejestrowanie zdarzeń. Jeśli spróbujesz użyć <xref:System.Windows.Application> obiekt w tym okresie, Twój kod może mieć nieoczekiwane wyniki, szczególnie w przypadku, gdy jest to uzależnione od różnych <xref:System.Windows.Application> właściwości są ustawione.  
  
 Gdy <xref:System.Windows.Application> ukończy pracę inicjowania, naprawdę rozpoczyna się jego okres istnienia.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Okres istnienia aplikacji  
 Okres istnienia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacja będzie posiadała przez kilka zdarzeń, które są wywoływane przez <xref:System.Windows.Application> informacją o tym, kiedy aplikacja została uruchomiona, zostało aktywowane i dezaktywowane i została zamknięta.  
  
  
<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Ekran powitalny  
 Począwszy od [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], można określić obrazu do użycia w oknie uruchamiania lub *ekran powitalny*. <xref:System.Windows.SplashScreen> Klasy można łatwo wyświetlać okno uruchamiania podczas ładowania aplikacji. <xref:System.Windows.SplashScreen> Okna jest tworzony i wyświetlany przed <xref:System.Windows.Application.Run%2A> jest wywoływana. Aby uzyskać więcej informacji, zobacz [czas uruchamiania aplikacji](../../../../docs/framework/wpf/advanced/application-startup-time.md) i [dodać ekran powitalny do aplikacji WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Uruchamianie aplikacji  
 Po <xref:System.Windows.Application.Run%2A> nosi nazwę i aplikacja została zainicjowany, czy aplikacja jest gotowa do uruchomienia. Tej chwili jest oznaczony po <xref:System.Windows.Application.Startup> zdarzenie jest zgłaszane:  
  
 [!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind1)]
 [!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind1)]  
[!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind2)]
[!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind2)]  
  
 W tym momencie w okresie istnienia aplikacji, pierwsze najbardziej typowych, należy jest pokazanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Showing_a_User_Interface"></a>   
### <a name="showing-a-user-interface"></a>Wyświetlanie interfejsu użytkownika  
 Większość aplikacji Windows autonomiczny Otwórz <xref:System.Windows.Window> gdy zaczyna uruchomiona. <xref:System.Windows.Application.Startup> Procedura obsługi zdarzeń jest jedną lokalizację, z którego można to zrobić, jak pokazano w następującym kodem.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  Pierwszy <xref:System.Windows.Window> z myślą o uruchamianiu w samodzielnej aplikacji staje się okna głównego aplikacji domyślnie. To <xref:System.Windows.Window> odwołuje się obiekt <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> właściwości. Wartość <xref:System.Windows.Application.MainWindow%2A> właściwość można zmienić programowo Jeśli innego okna niż pierwszy uruchomiony <xref:System.Windows.Window> powinny być głównego okna.  
  
 Gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pierwszym uruchomieniem, najprawdopodobniej przechodzi do <xref:System.Windows.Controls.Page>. Jest to pokazane w poniższym kodzie.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Jeśli możesz obsługiwać <xref:System.Windows.Application.Startup> można otwierać tylko <xref:System.Windows.Window> ścieżkę fizyczną lub przejdź do <xref:System.Windows.Controls.Page>, można ustawić `StartupUri` zamiast tego atrybutu w znacznikach.  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Application.StartupUri%2A> z samodzielnej aplikacji, aby otworzyć <xref:System.Windows.Window>.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Application.StartupUri%2A> z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] można przejść do <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Ten kod znaczników ma taki sam skutek jak poprzedni kod do otwierania okna.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na pasku nawigacyjnym, zobacz [Nawigacja — omówienie](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 Wymagana jest obsługa <xref:System.Windows.Application.Startup> zdarzenie, aby otworzyć <xref:System.Windows.Window> Jeśli musisz utworzyć go za pomocą konstruktora innych niż domyślne wystąpienie, musisz ustawić jej właściwości lub subskrybować ze zdarzeniami, przed wyświetleniem lub trzeba przetworzyć żadnych argumentów wiersza polecenia, podano, gdy aplikacja została uruchomiona.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Przetwarzanie argumentów wiersza polecenia.  
 W Windows aplikacje autonomiczne można uruchamiać z wiersza polecenia lub pulpitu. W obu przypadkach argumenty wiersza polecenia mogą być przekazywane do aplikacji. W poniższym przykładzie przedstawiono aplikację, która jest uruchamiana z jednym argumentem wiersza polecenia "/ StartMinimized":  
  
 `wpfapplication.exe /StartMinimized`  
  
 Podczas inicjowania aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pobiera argumenty wiersza polecenia systemu operacyjnego i przekazuje je do <xref:System.Windows.Application.Startup> programu obsługi zdarzeń za pośrednictwem <xref:System.Windows.StartupEventArgs.Args%2A> właściwość <xref:System.Windows.StartupEventArgs> parametru. Można pobrać i zapisać argumentów wiersza polecenia przy użyciu kodu, jak pokazano poniżej.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Obsługuje kod <xref:System.Windows.Application.Startup> Aby sprawdzić, czy **/StartMinimized** podano argument wiersza polecenia — Jeśli tak, zostanie otwarte okno główne z <xref:System.Windows.WindowState> z <xref:System.Windows.WindowState.Minimized>. Należy pamiętać, że ponieważ <xref:System.Windows.Window.WindowState%2A> musi być ustawiona właściwość programowo, głównym <xref:System.Windows.Window> muszą być otwarte jawnie w kodzie.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] Nie można pobrać i przetworzyć argumenty wiersza polecenia, ponieważ będą uruchamiane przy użyciu [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] wdrożenia (zobacz [wdrażanie aplikacji WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)). Jednakże można pobrać i przetworzyć parametry ciągu zapytania z adresów URL, które są używane do ich uruchamiania.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Aktywacja aplikacji i dezaktywacji  
 Windows umożliwia użytkownikom przełączania się między aplikacjami. Najczęstszym sposobem jest użyj kombinacji klawiszy ALT + TAB. Aplikacji mogą być przełączane do, tylko jeśli ma on widoczny <xref:System.Windows.Window> , użytkownik może wybrać. Obecnie wybranym parametrem <xref:System.Windows.Window> jest *aktywne okno* (znany także jako *okna pierwszoplanowego*) i jest <xref:System.Windows.Window> odbierająca dane wejściowe użytkownika. Aplikacja w aktywnym oknie *aktywnej aplikacji* (lub *pierwszoplanowych*). Aplikacja staje się aktywnej aplikacji w następujących okolicznościach:  
  
-   Zostanie uruchomiony i pokazuje <xref:System.Windows.Window>.  
  
-   Użytkownik przełączy się z innej aplikacji, wybierając <xref:System.Windows.Window> w aplikacji.  
  
 Wykryć, kiedy aplikacja stanie się aktywny obsługi <xref:System.Windows.Application.Activated?displayProperty=nameWithType> zdarzeń.  
  
 Podobnie aplikacja może stać się nieaktywny w następujących okolicznościach:  
  
-   Użytkownik przełączy się do innej aplikacji z obecnym.  
  
-   Kiedy aplikacja kończy pracę.  
  
 Wykryć, kiedy aplikacja stanie się nieaktywny, obsługując <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> zdarzeń.  
  
 Poniższy kod przedstawia sposób obsługi <xref:System.Windows.Application.Activated> i <xref:System.Windows.Application.Deactivated> zdarzenia w celu określenia, czy aplikacja jest aktywna.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 A <xref:System.Windows.Window> również może być aktywowane i dezaktywowane. Zobacz <xref:System.Windows.Window.Activated?displayProperty=nameWithType> i <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> Aby uzyskać więcej informacji.  
  
> [!NOTE]
>  Ani <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ani <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> jest wywoływane dla [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Zamykanie aplikacji  
 Cyklu życia aplikacji kończy się, gdy jest wyłączony, co może nastąpić z następujących powodów:  
  
-   Użytkownik zamknie co <xref:System.Windows.Window>.  
  
-   Użytkownik zamknie głównym <xref:System.Windows.Window>.  
  
-   Użytkownik kończy sesję Windows, wylogowania lub zamykania.  
  
-   Spełniono warunek specyficzne dla aplikacji.  
  
 Aby ułatwić zarządzanie zamknięcia aplikacji <xref:System.Windows.Application> zapewnia <xref:System.Windows.Application.Shutdown%2A> metody, <xref:System.Windows.Application.ShutdownMode%2A> właściwości i <xref:System.Windows.Application.SessionEnding> i <xref:System.Windows.Application.Exit> zdarzenia.  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A> lze volat pouze z aplikacji, które mają <xref:System.Security.Permissions.UIPermission>. Autonomiczny [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje zawsze mają to uprawnienie. Jednak [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nie jest uruchomiona w piaskownicy częściowego zaufania zabezpieczeń strefy Internet.  
  
#### <a name="shutdown-mode"></a>Tryb zamykania  
 Większość aplikacji Zakończ pracę po zamknięciu wszystkich okien albo po zamknięciu okna głównego. Czasami jednak inne warunki specyficzne dla aplikacji może ustalić zamknięcia aplikacji. Można określić warunki, w których aplikacja zostanie zamknięty, ustawiając <xref:System.Windows.Application.ShutdownMode%2A> przy użyciu jednego z następujących <xref:System.Windows.ShutdownMode> wartości wyliczenia:  
  
-   <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 Wartość domyślna <xref:System.Windows.Application.ShutdownMode%2A> jest <xref:System.Windows.ShutdownMode.OnLastWindowClose>, co oznacza, że aplikacja zostaje automatycznie zamknięty po zamknięciu ostatniego okna w aplikacji przez użytkownika. Jednak jeśli należy zamknąć aplikację po okno główne jest zamknięte, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automatycznie robi to, jeśli ustawisz <xref:System.Windows.Application.ShutdownMode%2A> do <xref:System.Windows.ShutdownMode.OnMainWindowClose>. Jest to pokazane w poniższym przykładzie.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Jeśli masz warunki zamykania specyficzne dla aplikacji, można skonfigurować ustawienie <xref:System.Windows.Application.ShutdownMode%2A> do <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. W tym przypadku jest odpowiedzialny za zamknięcia aplikacji przez jawne wywołanie <xref:System.Windows.Application.Shutdown%2A> metody; w przeciwnym razie aplikacja nadal będzie działać, nawet jeśli wszystkie okna są zamknięte. Należy pamiętać, że <xref:System.Windows.Application.Shutdown%2A> jest wywoływana niejawnie po <xref:System.Windows.Application.ShutdownMode%2A> jest <xref:System.Windows.ShutdownMode.OnLastWindowClose> lub <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A> można ustawić [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], ale jest on ignorowany; [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest zawsze zamknięcie jest przejście od w przeglądarce lub przeglądarki, która hostuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest zamknięty. Aby uzyskać więcej informacji, zobacz [Nawigacja — omówienie](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
#### <a name="session-ending"></a>Trwa kończenie sesji  
 Warunki zamykania, które są opisane przez <xref:System.Windows.Application.ShutdownMode%2A> właściwości są specyficzne dla aplikacji. W niektórych przypadkach jednak aplikacji może zostać wyłączony w wyniku warunek zewnętrznych. Najbardziej typowe zewnętrznych warunek występuje, gdy użytkownik kończy sesję Windows przez następujące akcje:  
  
-   Trwa wylogowywanie  
  
-   Zamykanie  
  
-   Ponowne uruchamianie  
  
-   Hibernacji  
  
 Aby wykryć, po zakończeniu sesji programu Windows, można obsługiwać <xref:System.Windows.Application.SessionEnding> zdarzeń, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 W tym przykładzie, sprawdza kod <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> właściwości w celu określenia, jak kończy się sesja Windows. Aby wyświetlić komunikat potwierdzenia dla użytkownika używa tej wartości. Jeśli użytkownik nie chce, aby zakończyć sesję, kod ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> do `true` zapobiegające kończenie sesji Windows.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding> nie jest inicjowane dla [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
#### <a name="exit"></a>Zakończ  
 Podczas zamykania aplikacji, trzeba wykonać jakieś operacje przetwarzania końcowego, takich jak przechowywanie stanu aplikacji. W takich sytuacjach można obsługiwać <xref:System.Windows.Application.Exit> zdarzeń.  
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml1)]  
[!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml2)]  
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind1)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind1)]  
[!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind2)]
[!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind2)]  
  
 Aby uzyskać kompletny przykład, zobacz [utrwalanie i przywracanie właściwości zakresu aplikacji między sesjami aplikacji](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit> może zostać obsłużony przez obie aplikacje autonomiczne i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Aby uzyskać [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], <xref:System.Windows.Application.Exit> jest wywoływane, gdy komputer znajduje się w następujących okolicznościach:  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Jest opuszczeniu.  
  
-   W [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)], gdy karta, która jest hostem [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest zamknięty.  
  
-   Po zamknięciu przeglądarki.  
  
#### <a name="exit-code"></a>Kod zakończenia  
 Przede wszystkim na rynek aplikacji przez system operacyjny w odpowiedzi na żądanie użytkownika. Jednak można uruchamiać aplikacji przez inną aplikację do wykonywania określonych zadań. Podczas zamykania uruchomionej aplikacji, uruchamiania aplikacji może być ustalenie warunek określający zamknięcia uruchomionej aplikacji. W takich sytuacjach Windows umożliwia aplikacji zwróci kod zakończenia aplikacji podczas zamykania. Domyślnie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji zwraca wartość kodu zakończenia 0.  
  
> [!NOTE]
>  Podczas debugowania z [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], kod zakończenia aplikacji jest wyświetlany w **dane wyjściowe** okna wyłączaniu aplikacji, w wiadomości, wygląda następująco:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Możesz otworzyć **dane wyjściowe** okien przez kliknięcie przycisku **dane wyjściowe** na **widoku** menu.  
  
 Aby zmienić kod zakończenia, można wywołać <xref:System.Windows.Application.Shutdown%28System.Int32%29> przeciążenia, które przyjmuje argument liczby całkowitej jako kod zakończenia:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Wykrywa wartość kodu zakończenia i zmień je, obsługując <xref:System.Windows.Application.Exit> zdarzeń. <xref:System.Windows.Application.Exit> Programu obsługi zdarzeń jest przekazywany <xref:System.Windows.ExitEventArgs> zapewniającą dostęp do kodu zakończenia z <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> właściwości. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  W obu aplikacje autonomiczne można ustawić kod zakończenia i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Jednak wartość kodu zakończenia jest ignorowany dla [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Nieobsługiwane wyjątki  
 Czasami aplikacja może nastąpić w nietypowych warunków, takich jak kiedy występuje nieoczekiwany wyjątek. W takim przypadku aplikacja nie może mieć kod w celu wykrywania i przetwarzania wyjątku. Ten typ wyjątku jest nieobsługiwany wyjątek; zostanie wyświetlone powiadomienie podobne do przedstawionego na poniższym rysunku, przed zamknięciem aplikacji.  
  
 ![Nieobsługiwany wyjątek powiadomień](../../../../docs/framework/wpf/app-development/media/applicationmanagementoverviewfigure2.png "ApplicationManagementOverviewFigure2")  
  
 Z punktu widzenia środowisko użytkownika jest lepszym rozwiązaniem dla aplikacji uniknąć tego zachowania domyślnego, wykonując niektóre lub wszystkie z następujących czynności:  
  
-   Wyświetlanie informacji przyjazny dla użytkownika.  
  
-   Podjęto próbę utrzymują działanie aplikacji.  
  
-   Rejestrowanie szczegółowe, przyjazne dla deweloperów, informacje o wyjątku w dzienniku zdarzeń Windows.  
  
 Implementacja tej obsługi zależy możliwość wykrywania nieobsłużone wyjątki, to znaczy elementy <xref:System.Windows.Application.DispatcherUnhandledException> zdarzenie jest wywoływane dla.  
  
 [!code-xaml[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
 [!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind1)]
 [!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind1)]  
[!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind2)]
[!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind2)]  
  
 <xref:System.Windows.Application.DispatcherUnhandledException> Programu obsługi zdarzeń jest przekazywany <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> parametr zawierający informacje kontekstowe dotyczące nieobsłużony wyjątek, w tym wyjątków, sama (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Aby określić sposób obsługi wyjątku, można użyć tych informacji.  
  
 Podczas obsługi <xref:System.Windows.Application.DispatcherUnhandledException>, należy ustawić <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> właściwości `true`; w przeciwnym razie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nadal uważa wyjątek obsługiwane i przywraca domyślne zachowanie wcześniejszym opisem. Jeśli jest nieobsługiwany wyjątek i <xref:System.Windows.Application.DispatcherUnhandledException> zdarzenie nie jest obsługiwane. w przeciwnym razie zdarzenie jest obsługiwane i <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> jest równa `false`, natychmiast zamyka aplikację. Ponadto żadne inne <xref:System.Windows.Application> zdarzenia są wywoływane. W związku z tym, będzie konieczna Obsługa <xref:System.Windows.Application.DispatcherUnhandledException> Jeśli aplikacja ma kod, który należy uruchomić przed zamknięciem aplikacji.  
  
 Mimo że aplikacja może zostać wyłączony w wyniku nieobsługiwany wyjątek, zwykle zamknięcie w odpowiedzi na żądanie użytkownika zgodnie z opisem w następnej sekcji.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Zdarzenia okresu istnienia aplikacji  
 Aplikacje autonomiczne i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nie mają dokładnie tych samych okresy istnienia. Poniższa ilustracja przedstawia kluczowych zdarzeń w cyklu życia aplikacji autonomicznej i przedstawiono sekwencję, w którym są one inicjowane.  
  
 ![Aplikacja autonomiczna &#45; zdarzenia obiektu aplikacji](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 Podobnie na poniższym rysunku przedstawiono kluczowych zdarzeń w trakcie trwania [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]i przedstawiono sekwencję, w którym są one inicjowane.  
  
 ![XBAP &#45; zdarzenia obiektu aplikacji](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Application>  
 [Okna WPF — omówienie](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)  
 [Nawigacja — omówienie](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [Zasoby aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)  
 [Pakowanie URI w WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Model aplikacji: Tematy porad](https://msdn.microsoft.com/library/76771b09-3688-4d1c-8818-9b3f4cf39a30)  
 [Projektowanie aplikacji](../../../../docs/framework/wpf/app-development/index.md)
