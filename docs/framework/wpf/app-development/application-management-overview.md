---
title: Przegląd Zarządzanie aplikacjami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: d8e26ff197e22ffa18b4acdd020b80879023c0f7
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364089"
---
# <a name="application-management-overview"></a>Przegląd Zarządzanie aplikacjami
Wszystkie aplikacje korzystają ze wspólnego zestawu funkcji, które dotyczą implementacji i zarządzania aplikacjami. Ten temat zawiera omówienie funkcji w <xref:System.Windows.Application> klasie służącej do tworzenia aplikacji i zarządzania nimi.  

## <a name="the-application-class"></a>Klasa aplikacji  
 W programie WPF wspólne funkcje w zakresie aplikacji są hermetyzowane w <xref:System.Windows.Application> klasie. <xref:System.Windows.Application> Klasa obejmuje następujące funkcje:  
  
- Śledzenie i posługiwanie się okresem istnienia aplikacji.  
  
- Pobieranie i przetwarzanie parametrów wiersza polecenia.  
  
- Wykrywanie nieobsłużonych wyjątków i odpowiadanie na nie.  
  
- Udostępnianie właściwości i zasobów zakresu aplikacji.  
  
- Zarządzanie oknami w aplikacjach autonomicznych.  
  
- Śledzenie i zarządzanie nawigacją.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Wykonywanie typowych zadań przy użyciu klasy aplikacji  
 Jeśli nie interesują Cię wszystkie szczegóły <xref:System.Windows.Application> dotyczące klasy, w poniższej tabeli wymieniono niektóre typowe <xref:System.Windows.Application> zadania i sposoby ich wykonania. Wyświetlając pokrewne interfejsy API i tematy, możesz znaleźć więcej informacji i przykładowy kod.  
  
|Zadanie|Podejście|  
|----------|--------------|  
|Pobierz obiekt reprezentujący bieżącą aplikację|<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> Użyj właściwości.|  
|Dodawanie ekranu startowego do aplikacji|Zobacz [Dodaj ekran powitalny do aplikacji WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Uruchom aplikację|<xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> Użyj metody.|  
|Zatrzymaj aplikację|<xref:System.Windows.Application.Shutdown%2A> Użyj metody<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> obiektu.|  
|Pobieranie argumentów z wiersza polecenia|Obsłuż <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> zdarzenie i Użyj właściwości. <xref:System.Windows.Application.Startup?displayProperty=nameWithType> Aby zapoznać się z przykładem <xref:System.Windows.Application.Startup?displayProperty=nameWithType> , zobacz zdarzenie.|  
|Pobieranie i Ustawianie kodu zakończenia aplikacji|Ustaw właściwość w programie <xref:System.Windows.Application.Shutdown%2A> obsługi zdarzeńlubwywołajmetodęiprzekażliczbęcałkowitą.<xref:System.Windows.Application.Exit?displayProperty=nameWithType> <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType>|  
|Wykrywanie nieobsłużonych wyjątków i odpowiadanie na nie|Obsłuż <xref:System.Windows.Application.DispatcherUnhandledException> zdarzenie.|  
|Pobieranie i Ustawianie zasobów należących do zakresu aplikacji|<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> Użyj właściwości.|  
|Korzystanie z słownika zasobów zakresu aplikacji|Zobacz [używanie słownika zasobów zakresu aplikacji](how-to-use-an-application-scope-resource-dictionary.md).|  
|Pobieranie i Ustawianie właściwości w zakresie aplikacji|<xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> Użyj właściwości.|  
|Pobierz i Zapisz stan aplikacji|Zobacz [utrwalanie i przywracanie właściwości zakresu aplikacji między sesjami aplikacji](persist-and-restore-application-scope-properties.md).|  
|Zarządzaj plikami danych nienależącymi do kodu, takimi jak pliki zasobów, pliki zawartości i pliki pochodzenia lokacja.|Zobacz temat [zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md).|  
|Zarządzanie systemem Windows w aplikacjach autonomicznych|Zobacz [WPF Windows — omówienie](wpf-windows-overview.md).|  
|Śledź nawigację i zarządzaj nią|Zobacz [Omówienie nawigacji](navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Definicja aplikacji  
 Aby skorzystać z funkcjonalności <xref:System.Windows.Application> klasy, należy zaimplementować definicję aplikacji. Definicja aplikacji WPF jest klasą, która pochodzi od <xref:System.Windows.Application> i jest skonfigurowana przy użyciu specjalnego ustawienia MSBuild.  

### <a name="implementing-an-application-definition"></a>Implementowanie definicji aplikacji  
 Typowa definicja aplikacji WPF jest implementowana przy użyciu znaczników i kodu. Pozwala to na użycie znaczników w celu deklaratywnego ustawiania właściwości aplikacji, zasobów i zdarzeń rejestrowania, a jednocześnie obsługę zdarzeń i wdrażanie zachowań specyficznych dla aplikacji w kodzie.  
  
 Poniższy przykład pokazuje, jak zaimplementować definicję aplikacji przy użyciu znaczników i kodu:  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Aby umożliwić współdziałanie pliku znaczników i pliku związanego z kodem, należy wykonać następujące czynności:  
  
- W znaczniku `Application` element musi `x:Class` zawierać atrybut. Gdy aplikacja jest `x:Class` skompilowana, istnienie w pliku znaczników powoduje, że MSBuild `partial` tworzy klasę, która dziedziczy z <xref:System.Windows.Application> i `x:Class` ma nazwę, która jest określona przez atrybut. Wymaga to dodania deklaracji przestrzeni nazw XML dla schematu XAML (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`).
  
- W kodzie, Klasa musi być `partial` klasą o tej samej nazwie, która jest określona `x:Class` przez atrybut w znaczniku i musi pochodzić od <xref:System.Windows.Application>. Pozwala to skojarzyć plik związany z kodem z `partial` klasą wygenerowaną dla pliku znaczników podczas kompilowania aplikacji (zobacz Kompilowanie [aplikacji WPF](building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Gdy tworzysz nowy projekt aplikacji WPF lub projekt aplikacji przeglądarki WPF przy użyciu programu Visual Studio, definicja aplikacji jest domyślnie uwzględniana i jest definiowana przy użyciu znaczników i kodu.  
  
 Ten kod jest minimalnym wymaganym do zaimplementowania definicji aplikacji. Jednak przed rozpoczęciem kompilowania i uruchamiania aplikacji należy wprowadzić dodatkową konfigurację programu MSBuild do definicji aplikacji.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Konfigurowanie definicji aplikacji dla programu MSBuild  
 Aplikacje autonomiczne i aplikacje przeglądarki XAML (XBAP) wymagają implementacji określonego poziomu infrastruktury, zanim będą mogły zostać uruchomione. Najważniejszym elementem tej infrastruktury jest punkt wejścia. Gdy aplikacja jest uruchamiana przez użytkownika, system operacyjny wywołuje punkt wejścia, który jest dobrze znana funkcja uruchamiania aplikacji.  
  
 Tradycyjnie deweloperzy muszą napisać część lub cały kod, w zależności od technologii. Jednak program WPF generuje ten kod, gdy plik znaczników definicji aplikacji jest skonfigurowany jako element MSBuild `ApplicationDefinition` , jak pokazano w następującym pliku projektu MSBuild:  
  
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
  
 Ponieważ plik związany z kodem zawiera kod, jest oznaczony jako element MSBuild `Compile` , jak jest to normalne.  
  
 Zastosowanie tych konfiguracji programu MSBuild do znaczników i plików powiązanych z kodem w definicji aplikacji powoduje, że program MSBuild generuje kod podobny do następującego:  
  
 [!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
 [!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]  
  
 Otrzymany kod rozszerza definicję aplikacji o dodatkowy kod infrastruktury, który obejmuje metodę `Main`punktu wejścia. Ten <xref:System.STAThreadAttribute> atrybut jest stosowany `Main` do metody, aby wskazać, że głównym wątkiem interfejsu użytkownika aplikacji WPF jest wątek sta, który jest wymagany dla aplikacji WPF. Gdy jest wywoływana `Main` , tworzy nowe `App` wystąpienie przed wywołaniem `InitializeComponent` metody w celu zarejestrowania zdarzeń i ustawienia właściwości, które są zaimplementowane w znaczniku. Ponieważ `InitializeComponent` jest generowany dla Ciebie, nie trzeba jawnie wywoływać `InitializeComponent` z definicji aplikacji, takiej jak dla <xref:System.Windows.Controls.Page> implementacji i <xref:System.Windows.Window> . Na koniec Metoda jest wywoływana w celu uruchomienia aplikacji. <xref:System.Windows.Application.Run%2A>  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Pobieranie bieżącej aplikacji  
 Ponieważ funkcje <xref:System.Windows.Application> klasy są współużytkowane przez aplikację, może istnieć tylko jedno wystąpienie <xref:System.Windows.Application> klasy na <xref:System.AppDomain>. Aby wymusić to <xref:System.Windows.Application> , Klasa jest zaimplementowana jako Klasa pojedyncza (zobacz [implementowanie pojedynczych w C# ](https://go.microsoft.com/fwlink/?LinkId=100567)), która tworzy pojedyncze wystąpienie samego siebie i zapewnia `static` <xref:System.Windows.Application.Current%2A> współdzielony dostęp do niego z właściwością.  
  
 Poniższy kod pokazuje, jak uzyskać odwołanie do <xref:System.Windows.Application> obiektu dla bieżącego. <xref:System.AppDomain>  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A>Zwraca odwołanie do wystąpienia <xref:System.Windows.Application> klasy. Jeśli chcesz odwołać się do <xref:System.Windows.Application> klasy pochodnej, musisz rzutować wartość <xref:System.Windows.Application.Current%2A> właściwości, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Możesz sprawdzić wartość <xref:System.Windows.Application.Current%2A> w dowolnym momencie okresu istnienia <xref:System.Windows.Application> obiektu. Należy jednak zachować ostrożność. Po utworzeniu wystąpienia <xref:System.Windows.Application> klasyistniejeokres,wktórymstanobiektujest<xref:System.Windows.Application> niespójny. W tym okresie program <xref:System.Windows.Application> wykonuje różne zadania inicjowania, które są wymagane przez kod do uruchomienia, w tym ustanawianie infrastruktury aplikacji, Ustawianie właściwości i rejestrowanie zdarzeń. Jeśli spróbujesz użyć <xref:System.Windows.Application> obiektu w tym okresie, kod może mieć nieoczekiwane wyniki, szczególnie jeśli zależy od różnych <xref:System.Windows.Application> ustawionych właściwości.  
  
 Po <xref:System.Windows.Application> zakończeniu jego działania inicjowania jego okres istnienia rzeczywiście rozpoczyna się.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Okres istnienia aplikacji  
 Okres istnienia aplikacji WPF jest oznaczony przez kilka zdarzeń, które są wywoływane przez <xref:System.Windows.Application> , aby poinformować użytkownika o tym, że aplikacja została uruchomiona, została aktywowana i zdezaktywowana i wyłączona.  

<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Ekran powitalny  
 Począwszy od .NET Framework 3,5 z dodatkiem SP1, można określić obraz do użycia w oknie uruchamiania lub na *ekranie powitalnym*. <xref:System.Windows.SplashScreen> Klasa ułatwia wyświetlanie okna uruchamiania podczas ładowania aplikacji. Okno jest tworzone i wyświetlane przed <xref:System.Windows.Application.Run%2A> wywołaniem. <xref:System.Windows.SplashScreen> Aby uzyskać więcej informacji, zobacz [czas uruchamiania aplikacji](../advanced/application-startup-time.md) i [Dodaj ekran powitalny do aplikacji WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Uruchamianie aplikacji  
 Po <xref:System.Windows.Application.Run%2A> wywołaniu i zainicjowaniu aplikacji aplikacja jest gotowa do uruchomienia. To chwilę oznacza, że <xref:System.Windows.Application.Startup> zdarzenie jest zgłaszane:  
  
[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]
  
 W tym momencie w okresie istnienia aplikacji najbardziej powszechną kwestią jest wyświetlenie interfejsu użytkownika.  
  
<a name="Showing_a_User_Interface"></a>
### <a name="showing-a-user-interface"></a>Wyświetlanie interfejsu użytkownika  
 Większość autonomicznych aplikacji systemu Windows <xref:System.Windows.Window> otwiera a po rozpoczęciu pracy. Program <xref:System.Windows.Application.Startup> obsługi zdarzeń jest jedną lokalizacją, z której można to zrobić, jak pokazano w poniższym kodzie.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  Pierwszy <xref:System.Windows.Window> do utworzenia wystąpienia w aplikacji autonomicznej jest domyślnie głównym oknem aplikacji. Ten <xref:System.Windows.Window> obiekt jest przywoływany <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> przez właściwość. Wartość <xref:System.Windows.Application.MainWindow%2A> właściwości można zmienić programowo, jeśli inne okno niż pierwsze <xref:System.Windows.Window> wystąpienie jest oknem głównym.  
  
 Po pierwszym uruchomieniu programu XBAP najprawdopodobniej przejdziesz do <xref:System.Windows.Controls.Page>. Jest to pokazane w poniższym kodzie.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Jeśli jest obsługiwany <xref:System.Windows.Application.Startup> tylko w celu <xref:System.Windows.Window> otwarcia lub przejścia do <xref:System.Windows.Controls.Page>, można zamiast tego ustawić `StartupUri` atrybut w znaczniku.  
  
 Poniższy przykład pokazuje, jak użyć z aplikacji <xref:System.Windows.Application.StartupUri%2A> autonomicznej, aby <xref:System.Windows.Window>otworzyć.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 Poniższy przykład pokazuje, jak użyć <xref:System.Windows.Application.StartupUri%2A> z aplikacji XBAP, aby przejść <xref:System.Windows.Controls.Page>do.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Ten znacznik ma ten sam skutek jak poprzedni kod otwierania okna.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat nawigacji, zobacz [Omówienie nawigacji](navigation-overview.md).  
  
 Musisz obsłużyć zdarzenie <xref:System.Windows.Application.Startup> , aby otworzyć plik <xref:System.Windows.Window> , jeśli trzeba utworzyć wystąpienie go przy użyciu konstruktora bez parametrów lub należy ustawić jego właściwości lub zasubskrybować jego zdarzenia przed wyświetleniem go lub trzeba przetworzyć dowolne argumenty wiersza polecenia dostarczone, gdy aplikacja została uruchomiona.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Przetwarzanie argumentów wiersza polecenia  
 W systemie Windows aplikacje autonomiczne można uruchomić z poziomu wiersza polecenia lub pulpitu. W obu przypadkach argumenty wiersza polecenia mogą być przekazane do aplikacji. W poniższym przykładzie przedstawiono aplikację, która jest uruchamiana z pojedynczym argumentem wiersza polecenia "/StartMinimized":  
  
 `wpfapplication.exe /StartMinimized`  
  
 Podczas inicjowania aplikacji WPF Pobiera argumenty wiersza polecenia z systemu operacyjnego i przekazuje je do <xref:System.Windows.Application.Startup> programu obsługi zdarzeń <xref:System.Windows.StartupEventArgs.Args%2A> za pośrednictwem właściwości <xref:System.Windows.StartupEventArgs> parametru. Argumenty wiersza polecenia można pobrać i zapisać przy użyciu kodu, takiego jak poniższy.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Kod obsługuje <xref:System.Windows.Application.Startup> sprawdzanie, czy argument wiersza polecenia **/StartMinimized** został podany. Jeśli tak, otwiera <xref:System.Windows.WindowState> <xref:System.Windows.WindowState.Minimized>okno główne z. Należy pamiętać, że <xref:System.Windows.Window.WindowState%2A> ponieważ właściwość musi być ustawiona programowo, główny <xref:System.Windows.Window> musi być otwarty jawnie w kodzie.  
  
 Aplikacje XBAP nie mogą pobrać i przetworzyć argumentów wiersza polecenia, ponieważ są uruchamiane przy użyciu wdrażania ClickOnce (zobacz [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)). Mogą jednak pobierać i przetwarzać parametry ciągu zapytania z adresów URL, które są używane do ich uruchamiania.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Aktywacja i dezaktywacja aplikacji  
 System Windows umożliwia użytkownikom przełączanie się między aplikacjami. Najbardziej typowym sposobem jest użycie kombinacji klawiszy ALT + TAB. Aplikacja może zostać przełączona tylko w przypadku, gdy ma widoczną <xref:System.Windows.Window> , którą użytkownik może wybrać. Aktualnie wybrane <xref:System.Windows.Window> jest *aktywne okno* (nazywane również <xref:System.Windows.Window> *oknem pierwszego planu*) i jest odbierane przez użytkownika. Aplikacja z aktywnym oknem jest aktywną *aplikacją* (lub *aplikacją na pierwszym planie*). Aplikacja przechodzi do aktywnej aplikacji w następujących okolicznościach:  
  
- Jest on uruchamiany i zawiera <xref:System.Windows.Window>.  
  
- Użytkownik przełącza się z innej aplikacji, wybierając <xref:System.Windows.Window> w aplikacji.  
  
 Możesz wykryć, kiedy aplikacja stanie się aktywna przez obsługę <xref:System.Windows.Application.Activated?displayProperty=nameWithType> zdarzenia.  
  
 Podobnie aplikacja może stać się nieaktywna w następujących okolicznościach:  
  
- Użytkownik przełącza się do innej aplikacji z bieżącej.  
  
- Gdy aplikacja zostanie zamknięta.  
  
 Możesz wykryć, kiedy aplikacja stanie się nieaktywna przez obsługę <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> zdarzenia.  
  
 Poniższy kod pokazuje, <xref:System.Windows.Application.Activated> jak obsłużyć zdarzenia i <xref:System.Windows.Application.Deactivated> określić, czy aplikacja jest aktywna.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 <xref:System.Windows.Window> Można również aktywować i dezaktywować. Zobacz <xref:System.Windows.Window.Activated?displayProperty=nameWithType> i <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> , aby uzyskać więcej informacji.  
  
> [!NOTE]
>  Nie <xref:System.Windows.Application.Activated?displayProperty=nameWithType> są <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> one ani wywoływane dla aplikacji XBAP.  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Zamykanie aplikacji  
 Cykl życia aplikacji kończy się, gdy zostanie zamknięty, co może wystąpić z następujących powodów:  
  
- Użytkownik zamyka co <xref:System.Windows.Window>.  
  
- Użytkownik zamyka główny <xref:System.Windows.Window>.  
  
- Użytkownik kończy sesję systemu Windows, logując się lub wyłączając.  
  
- Warunek specyficzny dla aplikacji został spełniony.  
  
 Aby ułatwić zarządzanie zamknięciem aplikacji, <xref:System.Windows.Application> program <xref:System.Windows.Application.Shutdown%2A> udostępnia metodę, <xref:System.Windows.Application.ShutdownMode%2A> Właściwość oraz <xref:System.Windows.Application.SessionEnding> zdarzenia i <xref:System.Windows.Application.Exit> .  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A>można wywołać tylko z aplikacji, które mają <xref:System.Security.Permissions.UIPermission>. Autonomiczne aplikacje WPF zawsze mają to uprawnienie. Jednak aplikacje XBAP działające w obszarze izolowanie zabezpieczeń strefa Internet częściowo ufają nie.  
  
#### <a name="shutdown-mode"></a>Tryb zamykania  
 Większość aplikacji jest zamykana po zamknięciu wszystkich okien lub zamknięciu okna głównego. Czasami jednak inne warunki specyficzne dla aplikacji mogą określić, kiedy aplikacja jest zamykana. Możesz określić warunki, w których aplikacja zostanie ZAMKNIĘTA, ustawiając <xref:System.Windows.Application.ShutdownMode%2A> jedną z następujących <xref:System.Windows.ShutdownMode> wartości wyliczenia:  
  
- <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 Wartość <xref:System.Windows.Application.ShutdownMode%2A> domyślna to <xref:System.Windows.ShutdownMode.OnLastWindowClose>, co oznacza, że aplikacja automatycznie zamyka się, gdy ostatnie okno aplikacji zostanie zamknięte przez użytkownika. Jeśli jednak aplikacja powinna zostać ZAMKNIĘTA po zamknięciu okna głównego, w przypadku ustawienia <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>opcji WPF automatycznie robi to. Pokazano to w poniższym przykładzie.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Jeśli istnieją warunki zamknięcia specyficzne dla aplikacji, należy ustawić na <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnExplicitShutdown>wartość. W takim przypadku jest odpowiedzialny za zamknięcie aplikacji przez jawne wywołanie <xref:System.Windows.Application.Shutdown%2A> metody. w przeciwnym razie aplikacja będzie działać nawet wtedy, gdy wszystkie okna są zamknięte. Należy zauważyć <xref:System.Windows.Application.Shutdown%2A> , że jest wywoływana niejawnie, <xref:System.Windows.ShutdownMode.OnLastWindowClose> <xref:System.Windows.Application.ShutdownMode%2A> gdy <xref:System.Windows.ShutdownMode.OnMainWindowClose>jest albo lub.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A>można ustawić z elementu XBAP, ale jest on ignorowany; Program XBAP jest zawsze zamykany, gdy zostanie odsunięty z przeglądarki lub w przypadku zamknięcia przeglądarki obsługującej aplikację XBAP. Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](navigation-overview.md).  
  
#### <a name="session-ending"></a>Zakończenie sesji  
 Warunki zamknięcia, które są opisane przez <xref:System.Windows.Application.ShutdownMode%2A> właściwość, są specyficzne dla aplikacji. W niektórych przypadkach aplikacja może zostać zamknięta w wyniku zewnętrznego stanu. Najbardziej typowym warunkiem zewnętrznym jest sytuacja, w której użytkownik skończy sesję systemu Windows przez wykonanie następujących czynności:  
  
- Wylogowywanie  
  
- Zamykanie  
  
- Ponowne uruchomienie  
  
- Hibernacji  
  
 Aby wykryć czas zakończenia sesji systemu Windows, można obsłużyć <xref:System.Windows.Application.SessionEnding> zdarzenie, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 W tym przykładzie kod sprawdza <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> właściwość, aby określić, jak kończy się sesja systemu Windows. Używa tej wartości, aby wyświetlić komunikat z potwierdzeniem dla użytkownika. Jeśli użytkownik nie chce, aby sesja była zakończona, kod ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> , aby `true` uniemożliwić zakończenie sesji systemu Windows.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding>nie jest wywoływany dla aplikacji XBAP.

#### <a name="exit"></a>Zakończ  
 Gdy aplikacja zostanie ZAMKNIĘTA, może być konieczne przeprowadzenie ostatecznego przetwarzania, takiego jak utrwalanie stanu aplikacji. W takich sytuacjach można obsłużyć <xref:System.Windows.Application.Exit> zdarzenie, `App_Exit` ponieważ procedura obsługi zdarzeń w poniższym przykładzie. Jest on zdefiniowany jako program obsługi zdarzeń w pliku *App. XAML* . Jego implementacja została wyróżniona w plikach *App.XAML.cs* i *Application. XAML. vb* .
  
[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]  
  
 [!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
 [!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [utrwalanie i przywracanie właściwości zakresu aplikacji między sesjami aplikacji](persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit>może być obsługiwany przez aplikacje autonomiczne i XBAP. W przypadku aplikacji XBAP <xref:System.Windows.Application.Exit> jest zgłaszane w następujących okolicznościach:  
  
- Element XBAP jest przesunięty od firmy.  
  
- W [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)]programie, gdy zostanie ZAMKNIĘTA karta obsługująca aplikacje XBAP.  
  
- Gdy przeglądarka zostanie zamknięta.  
  
#### <a name="exit-code"></a>Kod zakończenia  
 Aplikacje są najczęściej uruchamiane przez system operacyjny w odpowiedzi na żądanie użytkownika. Jednak aplikacja może być uruchamiana przez inną aplikację w celu wykonania określonego zadania. Gdy uruchomiona aplikacja zostanie ZAMKNIĘTA, uruchamianie aplikacji może chcieć znać warunek, pod którym uruchomiona aplikacja została zamknięta. W takich sytuacjach system Windows umożliwia aplikacjom zwracanie kodu zakończenia aplikacji przy zamykaniu. Domyślnie aplikacje WPF zwracają wartość kodu zakończenia 0.  
  
> [!NOTE]
>  Podczas debugowania z programu Visual Studio kod wyjścia aplikacji jest wyświetlany w oknie **danych wyjściowych** , gdy aplikacja zostanie ZAMKNIĘTA, w komunikacie podobnym do poniższego:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Aby otworzyć okno **dane wyjściowe** , kliknij pozycję **dane wyjściowe** w menu **Widok** .  
  
 Aby zmienić kod zakończenia, można wywołać <xref:System.Windows.Application.Shutdown%28System.Int32%29> Przeciążenie, które akceptuje argument liczby całkowitej jako kod zakończenia:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Możesz wykryć wartość kodu zakończenia i zmienić ją, obsługując <xref:System.Windows.Application.Exit> zdarzenie. Przeszedł procedurę <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> obsługi <xref:System.Windows.Application.Exit> zdarzeń, którazapewniadostępdokoduzakończenia<xref:System.Windows.ExitEventArgs> z właściwością. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  Możesz ustawić kod zakończenia zarówno w aplikacji autonomicznej, jak i w aplikacjach XBAP. Jednak wartość kodu zakończenia jest ignorowana dla aplikacji XBAP.  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Nieobsłużone wyjątki  
 Czasami aplikacja może zostać zamknięta w nieprawidłowych warunkach, na przykład w przypadku wykrycia nieoczekiwanego wyjątku. W takim przypadku aplikacja może nie mieć kodu do wykrywania i przetwarzania wyjątku. Ten typ wyjątku jest nieobsługiwanym wyjątkiem; powiadomienie podobne do pokazane na poniższym rysunku jest wyświetlane przed zamknięciem aplikacji.  
  
 ![Zrzut ekranu pokazujący powiadomienie o nieobsługiwanym wyjątku.](./media/application-management-overview/unhandled-exception-notification.png)  
  
 W perspektywie środowiska użytkownika lepiej jest w aplikacji uniknąć tego zachowania domyślnego, wykonując niektóre lub wszystkie z następujących czynności:  
  
- Wyświetlanie informacji przyjaznych dla użytkownika.  
  
- Podjęto próbę zachowania aplikacji.  
  
- Rejestrowanie szczegółowych informacji o wyjątku przyjaznych dla deweloperów w dzienniku zdarzeń systemu Windows.  
  
 Zaimplementowanie tej obsługi zależy od możliwości wykrywania nieobsłużonych wyjątków, które to <xref:System.Windows.Application.DispatcherUnhandledException> zdarzenie jest zgłaszane.  
  
[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]  
  
 <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>Program <xref:System.Windows.Application.DispatcherUnhandledException> obsługi<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> zdarzeń przekazuje parametr, który zawiera informacje kontekstowe dotyczące nieobsłużonego wyjątku, w tym wyjątek (). Korzystając z tych informacji, można określić, jak obsłużyć wyjątek.  
  
 Podczas obsługi <xref:System.Windows.Application.DispatcherUnhandledException>należy <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> ustawić właściwość na `true`; w przeciwnym razie, WPF nadal uznaje wyjątek, który ma być nieobsługiwany i przywraca domyślne zachowanie opisane wcześniej. Jeśli wystąpił nieobsługiwany wyjątek, a <xref:System.Windows.Application.DispatcherUnhandledException> zdarzenie nie jest obsłużone lub zdarzenie jest obsługiwane i <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> jest ustawione na `false`, aplikacja zostanie natychmiast ZAMKNIĘTA. Ponadto nie są zgłaszane <xref:System.Windows.Application> żadne inne zdarzenia. W związku z tym należy obsłużyć <xref:System.Windows.Application.DispatcherUnhandledException> , jeśli aplikacja ma kod, który musi zostać uruchomiony przed zamknięciem aplikacji.  
  
 Mimo że aplikacja może zostać zamknięta w wyniku nieobsłużonego wyjątku, aplikacja zwykle zamyka się w odpowiedzi na żądanie użytkownika, zgodnie z opisem w następnej sekcji.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Zdarzenia okresu istnienia aplikacji  
 Aplikacje autonomiczne i XBAP nie mają dokładnie tych samych okresów istnienia. Na poniższej ilustracji przedstawiono kluczowe zdarzenia w okresie istnienia aplikacji autonomicznej i przedstawiono sekwencję, w której zostały zgłoszone.  
  
 ![Zdarzenia obiektu &#45; aplikacji autonomicznej] aplikacji (./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 Podobnie na poniższej ilustracji przedstawiono kluczowe zdarzenia w okresie istnienia aplikacji XBAP i przedstawiono sekwencję, w której zostały zgłoszone.  
  
 ![Zdarzenia &#45; obiektu aplikacji XBAP](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Application>
- [Okna WPF — omówienie](wpf-windows-overview.md)
- [Nawigacja — omówienie](navigation-overview.md)
- [Zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md)
- [Pakowanie URI w WPF](pack-uris-in-wpf.md)
- [Model aplikacji: Tematy porad](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [Projektowanie aplikacji](index.md)
