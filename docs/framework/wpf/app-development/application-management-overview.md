---
title: "Przegląd Zarządzanie aplikacjami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09129f2dc2bac2bb17ebacd6d6db020288b6f616
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="application-management-overview"></a>Przegląd Zarządzanie aplikacjami
Wszystkie aplikacje zazwyczaj korzystają ze wspólnego zestawu funkcji, które stosuje się do zarządzania i wdrażania aplikacji. Ten temat zawiera omówienie funkcji w <xref:System.Windows.Application> klasa do tworzenia aplikacji i zarządzanie nimi.  
   
  
## <a name="the-application-class"></a>Klasa aplikacji  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], często używane funkcje z zakresu aplikacji jest hermetyzowany w <xref:System.Windows.Application> klasy. <xref:System.Windows.Application> Klasa zawiera następujące funkcje:  
  
-   Śledzenie i interakcji z okresu istnienia aplikacji.  
  
-   Trwa pobieranie i przetwarzanie parametry wiersza polecenia.  
  
-   Wykrywanie i reagowanie na nieobsługiwanych wyjątków.  
  
-   Udostępnianie właściwości zakresu aplikacji i zasobów.  
  
-   Zarządzanie oknami w autonomicznej aplikacji.  
  
-   Śledzenie i zarządzanie nawigacji.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Jak wykonać typowe zadania za pomocą klasy aplikacji  
 Jeśli nie jest konieczne we wszystkich szczegółów <xref:System.Windows.Application> klasy, w poniższej tabeli przedstawiono niektóre typowe zadania <xref:System.Windows.Application> i sposobie ich. Wyświetlając powiązane interfejsu API i tematy, można znaleźć więcej informacji oraz przykładowy kod.  
  
|Zadanie|Podejście|  
|----------|--------------|  
|Pobierz obiekt, który reprezentuje bieżącej aplikacji|Użyj <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> właściwości.|  
|Dodawanie do aplikacji ekranu startowego|Zobacz [dodać ekranu powitalnego aplikacji WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Uruchamianie aplikacji|Użyj <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> metody.|  
|Zatrzymaj aplikację|Użyj <xref:System.Windows.Application.Shutdown%2A> metody <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> obiektu.|  
|Pobierz argumenty z wiersza polecenia|Obsługa <xref:System.Windows.Application.Startup?displayProperty=nameWithType> zdarzeń i użyj <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> właściwości. Na przykład zobacz <xref:System.Windows.Application.Startup?displayProperty=nameWithType> zdarzeń.|  
|Pobieranie i ustawianie kod zakończenia aplikacji|Ustaw <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> właściwości w <xref:System.Windows.Application.Exit?displayProperty=nameWithType> program obsługi zdarzeń lub wywołanie <xref:System.Windows.Application.Shutdown%2A> — metoda i przekaż liczbą całkowitą.|  
|Wykrywanie i reagowanie na nieobsługiwanych wyjątków|Obsługa <xref:System.Windows.Application.DispatcherUnhandledException> zdarzeń.|  
|Pobieranie i Ustawianie zakresu aplikacji zasobów|Użyj <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> właściwości.|  
|Użyj słownika zasobów zakresu aplikacji|Zobacz [użyć słownika zasobów zakresu aplikacji](../../../../docs/framework/wpf/app-development/how-to-use-an-application-scope-resource-dictionary.md).|  
|Pobieranie i ustawianie właściwości z zakresu aplikacji|Użyj <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> właściwości.|  
|Pobierz i Zapisz stan aplikacji|Zobacz [utrwalić i przywrócić właściwości zakresu aplikacji między sesjami aplikacji](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).|  
|Zarządzanie pliki danych z systemem innym niż kodu, w tym pliki zasobów, pliki zawartości i pliki witryny pochodzenia.|Zobacz [zasób w aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).|  
|Zarządzanie systemem windows w autonomicznej aplikacji|Zobacz [WPF systemu Windows — omówienie](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).|  
|Śledzenie i zarządzanie nimi nawigacji|Zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Definicja aplikacji  
 Do korzystania z funkcji <xref:System.Windows.Application> klasy, musisz zaimplementować definicji aplikacji. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definicji aplikacji jest klasą pochodzącą z <xref:System.Windows.Application> i skonfigurowano specjalnego [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] ustawienie.  
  
### <a name="implementing-an-application-definition"></a>Implementowanie definicji aplikacji  
 Typowe [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definicji aplikacji jest implementowane za pomocą zarówno znaczników i związane z kodem. Dzięki temu można deklaratywnie ustawić właściwości aplikacji i zasobów i rejestrować zdarzenia, podczas obsługi zdarzenia i wdrażanie zachowanie specyficzne dla aplikacji w CodeBehind za pomocą znacznika.  
  
 Poniższy przykład przedstawia sposób wykonania definicji aplikacji przy użyciu zarówno znaczników i kodu powiązanego:  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Aby umożliwić pliku znaczników i plik CodeBehind współdziałają ze sobą, następujące musi zostać przeprowadzona:  
  
-   W znaczniku `Application` musi zawierać element `x:Class` atrybutu. Gdy aplikacja utworzeniu istnienie `x:Class` w znaczniku pliku powoduje, że [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] do utworzenia `partial` klasą pochodzącą z <xref:System.Windows.Application> i ma przypisaną nazwę określonego przez `x:Class` atrybutu. Wymaga to dodanie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklaracji przestrzeni nazw dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schematu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).  
  
-   W kodem, musi być klasa `partial` klasa o takiej samej nazwie, która jest określona przez `x:Class` atrybutów w znaczniku i musi pochodzić od <xref:System.Windows.Application>. Dzięki temu plik CodeBehind ma być skojarzone z `partial` klasy, która jest generowane dla pliku znaczników, podczas tworzenia aplikacji (zobacz [kompilowania aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Podczas tworzenia nowego projektu aplikacji WPF lub za pomocą projektu aplikacji w przeglądarce WPF [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], definicji aplikacji jest włączone domyślnie i jest definiowana za pomocą zarówno znaczników i związane z kodem.  
  
 Ten kod jest minimum wymagane do zaimplementowania definicji aplikacji. Jednak dodatkowe [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] należy do definicji aplikacji przed tworzenia i uruchamiania aplikacji.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Konfigurowanie definicji aplikacji dla programu MSBuild  
 Aplikacje autonomiczne i [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] wymagają wykonania określonego poziomu infrastruktury przed uruchomieniem. Najważniejszy element tej infrastruktury jest punkt wejścia. Gdy aplikacja jest uruchamiana przez użytkownika, system operacyjny wywołuje punktu wejścia jest funkcją dobrze znanego uruchamiania aplikacji.  
  
 Tradycyjnie deweloperzy musieli napisać niektórych lub wszystkich ten kod samodzielnie, w zależności od technologii. Jednak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] generuje kod dla Ciebie, gdy pliku znaczników definicji aplikacji jest skonfigurowana jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` elementów, jak pokazano w następującym [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] pliku projektu:  
  
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
  
 Ponieważ plik CodeBehind zawiera kod, nie jest oznaczona jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` elementu, jest to normalne.  
  
 Zastosowania [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] konfiguracji do plików znaczników i kodu powiązanego definicji aplikacji powoduje, że [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] do generowania kodu, takie jak następujące:  
  
 [!code-csharp[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode1)]
 [!code-vb[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode1)]  
[!code-csharp[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode2)]
[!code-vb[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode2)]  
  
 Wynikowy kod wspomaga definicji aplikacji z kodem dodatkowej infrastruktury, który zawiera metodę punktu wejścia `Main`. <xref:System.STAThreadAttribute> Atrybut jest stosowany do `Main` metody w celu wskazania, że głównym [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji jest wątku STA, który jest wymagany dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji. Po wywołaniu `Main` tworzy nowe wystąpienie klasy `App` przed wywołaniem `InitializeComponent` metody do rejestrowania zdarzeń i ustaw właściwości, które są wdrożone w znaczniku. Ponieważ `InitializeComponent` jest generowany, nie trzeba jawnie wywołać `InitializeComponent` z definicji aplikacji, tak jak w przypadku <xref:System.Windows.Controls.Page> i <xref:System.Windows.Window> implementacji. Na koniec <xref:System.Windows.Application.Run%2A> metoda jest wywoływana, aby uruchomić aplikację.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Pobieranie bieżącej aplikacji  
 Ponieważ funkcje <xref:System.Windows.Application> klasy są współużytkowane przez aplikację, może istnieć tylko jedno wystąpienie <xref:System.Windows.Application> klasy na <xref:System.AppDomain>. Aby wymusić, <xref:System.Windows.Application> klasy jest zaimplementowany jako klasa pojedyncza (zobacz [implementacja Singleton w języku C#](http://go.microsoft.com/fwlink/?LinkId=100567)), co powoduje utworzenie pojedynczego wystąpienia samej siebie i zapewnia dostęp do niego z udostępnionych `static` <xref:System.Windows.Application.Current%2A> Właściwość.  
  
 Poniższy kod przedstawia sposób uzyskać odwołania do <xref:System.Windows.Application> obiektu dla bieżącej <xref:System.AppDomain>.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A>Zwraca odwołanie do wystąpienia <xref:System.Windows.Application> klasy. Jeśli chcesz, aby odwołanie do użytkownika <xref:System.Windows.Application> klasy, należy rzutować wartości <xref:System.Windows.Application.Current%2A> właściwości, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Możesz sprawdzić wartość <xref:System.Windows.Application.Current%2A> w dowolnym momencie w okresie istnienia <xref:System.Windows.Application> obiektu. Jednak należy zachować ostrożność. Po <xref:System.Windows.Application> tworzenia wystąpienia klasy, jest okres, przez który stan <xref:System.Windows.Application> obiektu jest niezgodny. W tym okresie <xref:System.Windows.Application> wykonuje różne zadania inicjowania, które są wymagane przez kod do uruchomienia, w tym ustanawiania infrastruktury aplikacji, ustawianie właściwości i rejestrowanie zdarzeń. Jeśli spróbujesz użyć <xref:System.Windows.Application> obiektów w tym okresie kodu może mieć nieoczekiwane wyniki, zwłaszcza w wypadku zależy od różnych <xref:System.Windows.Application> ustawiania właściwości.  
  
 Gdy <xref:System.Windows.Application> ukończy pracy inicjowania, naprawdę rozpoczyna się jego okres istnienia.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Cykl życia aplikacji  
 Okres istnienia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji zostało oznaczone przez kilka zdarzeń, które zostały zgłoszone przez <xref:System.Windows.Application> z informacją, jeśli aplikacja została uruchomiona, została aktywowana i dezaktywowane i został zamknięty.  
  
  
<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Ekran powitalny  
 Począwszy od [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], można określić obraz ma być używany w oknie uruchamiania lub *ekranu powitalnego*. <xref:System.Windows.SplashScreen> Klasy ułatwia wyświetlanie okna uruchomienia podczas ładowania aplikacji. <xref:System.Windows.SplashScreen> Okno jest tworzone i wyświetlane przed <xref:System.Windows.Application.Run%2A> jest wywoływana. Aby uzyskać więcej informacji, zobacz [czas uruchamiania aplikacji](../../../../docs/framework/wpf/advanced/application-startup-time.md) i [dodać ekranu powitalnego aplikacji WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Uruchamianie aplikacji  
 Po <xref:System.Windows.Application.Run%2A> nosi nazwę i aplikacja została zainicjowana, aplikacja jest gotowa do uruchomienia. Tej chwili jest oznaczony po <xref:System.Windows.Application.Startup> zdarzenia:  
  
 [!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind1)]
 [!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind1)]  
[!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind2)]
[!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind2)]  
  
 W tym momencie w okresie istnienia aplikacji, najczęściej etapem jest pokazanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Showing_a_User_Interface"></a>   
### <a name="showing-a-user-interface"></a>Wyświetlanie interfejsu użytkownika  
 Większość autonomiczny [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] Otwórz aplikacji <xref:System.Windows.Window> one rozpoczęcia uruchomiona. <xref:System.Windows.Application.Startup> Procedura obsługi zdarzeń jest jedną lokalizację, z którego można to zrobić, jak pokazano w następującym kodem.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  Pierwszy <xref:System.Windows.Window> zostać utworzone w autonomicznej aplikacji staje się w głównym oknie aplikacji domyślnie. To <xref:System.Windows.Window> odwołuje się obiekt <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> właściwości. Wartość <xref:System.Windows.Application.MainWindow%2A> właściwość można zmienić programowo, gdy okno innego niż pierwszy wystąpienia <xref:System.Windows.Window> powinna być głównego okna.  
  
 Gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pierwszym uruchomieniem, najprawdopodobniej przechodzi do <xref:System.Windows.Controls.Page>. Przedstawiono to w poniższym kodzie.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Jeśli można obsługiwać <xref:System.Windows.Application.Startup> tylko otworzyć <xref:System.Windows.Window> lub przejdź do <xref:System.Windows.Controls.Page>, można ustawić `StartupUri` zamiast tego atrybutu w znaczniku.  
  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Application.StartupUri%2A> z aplikacji autonomicznej, aby otworzyć <xref:System.Windows.Window>.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Application.StartupUri%2A> z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] można przejść do <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Ten kod znaczników ma ten sam efekt co poprzedni kod do otwierania okna.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji dotyczących nawigacji, zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 Wymagana jest obsługa <xref:System.Windows.Application.Startup> zdarzeń, aby otworzyć <xref:System.Windows.Window> należy utworzyć przy użyciu konstruktora z systemem innym niż domyślny, lub należy ustawić jej właściwości lub subskrybować jego zdarzeń przed wyświetleniem, czy należy przetworzyć żadnych argumentów wiersza polecenia który zostały podane, kiedy aplikacja została uruchomiona.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Przetwarzanie argumentów wiersza polecenia  
 W [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)], aplikacje autonomiczne można uruchomić z wiersza polecenia lub pulpitu. W obu przypadkach argumenty wiersza polecenia mogą zostać przekazane do aplikacji. W poniższym przykładzie przedstawiono aplikację, która jest uruchamiana z pojedynczym argumentem wiersza polecenia "/ StartMinimized":  
  
 `wpfapplication.exe /StartMinimized`  
  
 Podczas inicjowania aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pobiera argumenty wiersza polecenia systemu operacyjnego i przekazuje je do <xref:System.Windows.Application.Startup> obsługi zdarzeń za pomocą <xref:System.Windows.StartupEventArgs.Args%2A> właściwość <xref:System.Windows.StartupEventArgs> parametru. Można pobrać i przechowywać argumenty wiersza polecenia przy użyciu kodu podobne do następujących.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Uchwyty kodu <xref:System.Windows.Application.Startup> Aby sprawdzić, czy **/StartMinimized** argumentu wiersza polecenia podano; jeśli tak, zostanie otwarte okno główne z <xref:System.Windows.WindowState> z <xref:System.Windows.WindowState.Minimized>. Należy pamiętać, że ponieważ <xref:System.Windows.Window.WindowState%2A> musi być ustawiona właściwość programowo, głównym <xref:System.Windows.Window> musi zostać jawnie otwarty w kodzie.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]Nie można pobrać i przetworzyć argumenty wiersza polecenia, ponieważ są one uruchomiony przy użyciu [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] wdrożenia (zobacz [wdrażanie aplikacji WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)). Jednak można pobrać i przetworzyć parametrów ciągu zapytania z adresów URL, które są używane do uruchamiania ich.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Aktywacja aplikacji i dezaktywację.  
 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)]Umożliwia użytkownikom przełączania się między aplikacjami. Najczęściej jest użyj kombinacji klawiszy ALT + TAB. Aplikacji mogą być przełączane do, tylko jeśli ma ona widoczna <xref:System.Windows.Window> wybranego użytkownika. Aktualnie zaznaczonego <xref:System.Windows.Window> jest *aktywne okno* (znanej także jako *okna pierwszoplanowego*) i jest <xref:System.Windows.Window> odbierająca dane wejściowe użytkownika. Aplikacja w aktywnym oknie *aktywnej aplikacji* (lub *pierwszoplanowych*). Aplikacja, staje się aktywnej aplikacji w następujących okolicznościach:  
  
-   Zostanie uruchomiony i pokazuje <xref:System.Windows.Window>.  
  
-   Użytkownik przełącza z innej aplikacji, wybierając <xref:System.Windows.Window> w aplikacji.  
  
 Może wykryć, gdy aplikacja stanie się aktywny Obsługa <xref:System.Windows.Application.Activated?displayProperty=nameWithType> zdarzeń.  
  
 Podobnie aplikacja może stać się nieaktywne w następujących okolicznościach:  
  
-   Użytkownik zmienia się na inną aplikację z bieżącej.  
  
-   Gdy aplikacja będzie zamykany.  
  
 Może wykryć, gdy aplikacja stanie się nieaktywny Obsługa <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> zdarzeń.  
  
 Poniższy kod przedstawia sposób obsługi <xref:System.Windows.Application.Activated> i <xref:System.Windows.Application.Deactivated> zdarzeń w celu określenia, czy aplikacja jest aktywna.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 A <xref:System.Windows.Window> mogą także aktywować i dezaktywowane. Zobacz <xref:System.Windows.Window.Activated?displayProperty=nameWithType> i <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> Aby uzyskać więcej informacji.  
  
> [!NOTE]
>  Ani <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ani <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> jest wywoływane dla [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Zamykania aplikacji  
 Użytkowania aplikacji kończy się po jego zamknięciem, co może nastąpić z następujących powodów:  
  
-   Użytkownik zamyka każdego <xref:System.Windows.Window>.  
  
-   Użytkownik zamyka głównym <xref:System.Windows.Window>.  
  
-   Użytkownik kończy się [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] sesję przez wylogowanie lub zamykania.  
  
-   Spełniono warunek specyficzne dla aplikacji.  
  
 W celu zarządzania zamykania aplikacji <xref:System.Windows.Application> zapewnia <xref:System.Windows.Application.Shutdown%2A> metody, <xref:System.Windows.Application.ShutdownMode%2A> właściwości oraz <xref:System.Windows.Application.SessionEnding> i <xref:System.Windows.Application.Exit> zdarzenia.  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A>można wywołać tylko z aplikacji, które mają <xref:System.Security.Permissions.UIPermission>. Autonomiczny [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje zawsze ma tych uprawnień. Jednak [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] działający w izolowanym częściowego zaufania zabezpieczeń strefy Internet nie.  
  
#### <a name="shutdown-mode"></a>Tryb zamykania  
 Większość aplikacji Zamknij po zamknięciu wszystkich okien albo po zamknięciu głównego okna. Czasami jednak inne warunki specyficzne dla aplikacji mogą określić zamknięcia aplikacji. Można określić warunki, w których aplikacja zostanie zamknięty przez ustawienie <xref:System.Windows.Application.ShutdownMode%2A> z jedną z następujących <xref:System.Windows.ShutdownMode> wartości wyliczenia:  
  
-   <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 Wartość domyślna <xref:System.Windows.Application.ShutdownMode%2A> jest <xref:System.Windows.ShutdownMode.OnLastWindowClose>, co oznacza, że aplikacja zostaje automatycznie zamknięty podczas zamykania okna ostatniego w aplikacji przez użytkownika. Jednak jeśli można zamknąć aplikacji gdy główne okno jest zamknięty, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automatycznie robi to w przypadku ustawienia <xref:System.Windows.Application.ShutdownMode%2A> do <xref:System.Windows.ShutdownMode.OnMainWindowClose>. Przedstawiono to w poniższym przykładzie.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Jeśli masz warunki zamykania specyficzne dla aplikacji, można skonfigurować ustawienie <xref:System.Windows.Application.ShutdownMode%2A> do <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. W takim przypadku jest obowiązek Zamknij aplikację jawnie wywołując <xref:System.Windows.Application.Shutdown%2A> metody; w przeciwnym razie aplikacja nadal będzie działać nawet wtedy, gdy zamknięciu wszystkich okien. Należy pamiętać, że <xref:System.Windows.Application.Shutdown%2A> jest nazywany niejawnie po <xref:System.Windows.Application.ShutdownMode%2A> jest <xref:System.Windows.ShutdownMode.OnLastWindowClose> lub <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A>można ustawić [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], ale jest on ignorowany; [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest zawsze zamknięcie jest przejście od w przeglądarce lub przeglądarki, która obsługuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest zamknięty. Aby uzyskać więcej informacji, zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
#### <a name="session-ending"></a>Kończenie sesji  
 Warunki zamykania, które są opisane przez <xref:System.Windows.Application.ShutdownMode%2A> właściwości są specyficzne dla aplikacji. W niektórych przypadkach, aplikacja może zostać wyłączony wyniku warunek zewnętrznych. Najbardziej typowe zewnętrznych stan występuje, gdy użytkownik kończy się [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] sesji przez następujące akcje:  
  
-   Wylogowanie  
  
-   Wyłączanie  
  
-   Ponowne uruchamianie  
  
-   Hibernacji  
  
 Aby wykryć, kiedy [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] zakończenia sesji może obsłużyć <xref:System.Windows.Application.SessionEnding> zdarzeń, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 W tym przykładzie kodu sprawdza <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> właściwości w celu określenia sposobu [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] kończy się sesja. Ta wartość używa do wyświetlania potwierdzenia dla użytkownika. Jeśli użytkownik nie chce, aby zakończyć sesję, ustawia kod <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> do `true` zapobiegające [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] sesji od zakończenia.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding>nie jest wywoływane dla [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
#### <a name="exit"></a>Zakończ  
 Podczas zamykania aplikacji, trzeba wykonać niektóre końcowego przetwarzania, takich jak utrwalanie stanu aplikacji. W takich sytuacjach może obsłużyć <xref:System.Windows.Application.Exit> zdarzeń.  
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml1)]  
[!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml2)]  
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind1)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind1)]  
[!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind2)]
[!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind2)]  
  
 Aby uzyskać pełny przykład, zobacz [utrwalanie i przywrócić właściwości zakresu aplikacji między sesjami aplikacji](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit>są obsługiwane przez obie aplikacje autonomiczne i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Aby uzyskać [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], <xref:System.Windows.Application.Exit> jest wywoływane, gdy w następujących okolicznościach:  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Jest opuszczeniu.  
  
-   W [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)], gdy karta, który jest hostem [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest zamknięty.  
  
-   Gdy przeglądarka jest zamknięty.  
  
#### <a name="exit-code"></a>Kod zakończenia  
 Przede wszystkim uruchamiania aplikacji przez system operacyjny w odpowiedzi na żądanie użytkownika. Aplikacja może jednak uruchomić przez inną aplikację do wykonywania określonych zadań. Po zamknięciu uruchomionej aplikacji uruchamiania aplikacji może być ustalenie warunku, pod którym zamknąć uruchomionej aplikacji. W takich sytuacjach [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] umożliwia aplikacjom zwraca kod zakończenia aplikacji na zamknięcie. Domyślnie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji zwraca wartość kodu zakończenia 0.  
  
> [!NOTE]
>  Podczas debugowania z [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], kod zakończenia aplikacji jest wyświetlany w **dane wyjściowe** okna wyłączaniu aplikacji, w wiadomości, że wygląda podobnie do następującego:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Możesz otworzyć **dane wyjściowe** okna, klikając **dane wyjściowe** na **widoku** menu.  
  
 Aby zmienić kod zakończenia, można wywołać <xref:System.Windows.Application.Shutdown%28System.Int32%29> przeciążenia, która akceptuje argument liczby całkowitej jako kod zakończenia:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Wykryj wartość kodu zakończenia i zmień ją, obsługa <xref:System.Windows.Application.Exit> zdarzeń. <xref:System.Windows.Application.Exit> Program obsługi zdarzeń jest przekazywany <xref:System.Windows.ExitEventArgs> zapewniające dostęp do kodu zakończenia z <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> właściwości. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  Można ustawić kodu zakończenia w obydwu aplikacji autonomicznej i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Jednak wartość kodu zakończenia jest ignorowany dla [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Nieobsługiwane wyjątki  
 Czasami aplikacji może wyłączyć w anomalii, takie jak kiedy nieprzewidziane jest zwracany wyjątek. W takim przypadku aplikacja może nie mieć kodu w celu wykrywania i przetwarzania wyjątek. Ten typ wyjątku jest nieobsługiwany wyjątek; zostanie wyświetlone powiadomienie podobnie jak pokazano na poniższej ilustracji, przed zamknięciem aplikacji.  
  
 ![Wystąpił nieobsługiwany wyjątek powiadomień](../../../../docs/framework/wpf/app-development/media/applicationmanagementoverviewfigure2.png "ApplicationManagementOverviewFigure2")  
  
 Z punktu widzenia środowiska użytkownika lepiej jest dla aplikacji, aby uniknąć to zachowanie domyślne, wykonując niektóre lub wszystkie z następujących czynności:  
  
-   Wyświetlanie informacji przyjazną dla użytkownika.  
  
-   Próba zachować uruchomioną aplikację.  
  
-   Rejestrowanie informacji szczegółowych, przyjazny dla dewelopera, wyjątek w [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] dziennika zdarzeń.  
  
 Implementacja tej pomocy technicznej zależy od możliwość wykrywania nieobsługiwanych wyjątków, to znaczy elementy <xref:System.Windows.Application.DispatcherUnhandledException> zdarzenie jest zgłaszane w przypadku.  
  
 [!code-xaml[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
 [!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind1)]
 [!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind1)]  
[!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind2)]
[!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind2)]  
  
 <xref:System.Windows.Application.DispatcherUnhandledException> Program obsługi zdarzeń jest przekazywany <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> parametr, który zawiera informacje kontekstowe dotyczące nieobsłużony wyjątek, łącznie z wyjątkiem samej (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Można użyć tych informacji do określenia sposobu obsługi wyjątku.  
  
 Podczas obsługi <xref:System.Windows.Application.DispatcherUnhandledException>, należy ustawić <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> właściwości `true`; w przeciwnym razie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nadal uważa za nieobsługiwany wyjątek i powraca do domyślne zachowanie opisany wcześniej. Jeśli jest nieobsługiwany wyjątek i <xref:System.Windows.Application.DispatcherUnhandledException> zdarzenie nie jest obsługiwane lub zdarzenie jest obsługiwane i <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> ma ustawioną wartość `false`, aplikacja zostanie natychmiast. Ponadto żadnych innych <xref:System.Windows.Application> pojawienia się zdarzenia. W rezultacie musi obsłużyć <xref:System.Windows.Application.DispatcherUnhandledException> Jeśli aplikacja ma kod, który musi zostać uruchomiony przed zamknięciem aplikacji.  
  
 Mimo że aplikacja może zostać wyłączony w wyniku nieobsługiwany wyjątek, zwykle zamknięcie w odpowiedzi na żądanie użytkownika zgodnie z opisem w następnej sekcji.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Zdarzenia cykl życia aplikacji  
 Aplikacje autonomiczne i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nie mają tej samej okresy. Poniższa ilustracja przedstawia klucza zdarzenia w okresie istnienia aplikacji autonomicznej i przedstawiono sekwencję, w której zostaną podniesione.  
  
 ![Aplikacja autonomiczna &#45; Zdarzenia obiektów aplikacji](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 Ponadto na poniższym rysunku przedstawiono klucza zdarzenia w okresie istnienia [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]oraz przedstawiono sekwencję, w której zostaną podniesione.  
  
 ![XBAP &#45; Zdarzenia obiektów aplikacji](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Application>  
 [WPF systemu Windows — omówienie](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)  
 [Omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [Zasób w aplikacji WPF, zawartość i plików danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)  
 [Identyfikatory URI pakietu na platformie WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Modelu aplikacji: Tematy porad](http://msdn.microsoft.com/en-us/76771b09-3688-4d1c-8818-9b3f4cf39a30)  
 [Projektowanie aplikacji](../../../../docs/framework/wpf/app-development/index.md)
