---
title: Projektowanie aplikacji
ms.date: 01/26/2018
helpviewer_keywords:
  - 'WPF [WPF], about application development'
  - 'application development [WPF], about'
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
---
# <a name="application-development"></a>Projektowanie aplikacji
<a name="introduction"></a> Windows Presentation Foundation (WPF) to struktura prezentacji, która może służyć do tworzenia następujących typów aplikacji:  
  
-   Aplikacje autonomiczne (tradycyjny styl [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] aplikacje tworzone w zestawach wykonywalnych, które są zainstalowane i uruchomienie z komputera klienta).  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] (aplikacje składające się z nawigacji strony, które są tworzone w zestawach wykonywalnych i hostowanych przez przeglądarki sieci Web, takich jak [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] lub Mozilla Firefox).  
  
-   Biblioteki Kontrolki niestandardowe (niewykonywalnej zestawów zawierających formanty wielokrotnego użytku).  
  
-   Biblioteki klas (niewykonywalnej zestawów zawierających klasy wielokrotnego użytku).  
  
> [!NOTE]
>  Używanie typów WPF w usłudze Windows jest zdecydowanie odradzane. Jeśli spróbujesz użyć tych funkcji w usłudze Windows może nie działają zgodnie z oczekiwaniami.  
  
 Do tworzenia tego zestawu aplikacji, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementuje hosta usługi. Ten temat zawiera omówienie tych usług i gdzie można znaleźć więcej informacji.  
  

  
<a name="Application_Management"></a>   
## <a name="application-management"></a>Zarządzanie aplikacjami  
 Plik wykonywalny [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje często wymagają podstawowy zestaw funkcji, który obejmuje następujące elementy:  
  
-   Tworzenie i zarządzanie nimi wspólnej infrastruktury aplikacji (w tym tworzenia metody punktu wejścia i pętlę komunikatów Windows, aby otrzymać systemu i komunikaty wejściowe).  
  
-   Śledzenie i interakcji z cyklu życia aplikacji.  
  
-   Trwa pobieranie i przetwarzanie parametry wiersza polecenia.  
  
-   Udostępnianie właściwości zakresu aplikacji i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zasobów.  
  
-   Wykrywanie i przetwarzanie nieobsługiwanych wyjątków.  
  
-   Zwracanie kodów zakończenia.  
  
-   Zarządzanie systemem windows w aplikacje autonomiczne.  
  
-   Śledzenie nawigacji w [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]i aplikacji autonomicznych przy użyciu systemu windows nawigacji i ramki.  
  
 Te możliwości są implementowane przez <xref:System.Windows.Application> klasy, która dodawanie do aplikacji przy użyciu *definicji aplikacji*.  
  
 Aby uzyskać więcej informacji, zobacz [Zarządzanie aplikacjami — omówienie](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a>Zasoby aplikacji WPF, zawartość, pliki danych  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Rozszerzone wsparcie podstawowe programu Microsoft .NET Framework dla osadzonych zasobów dzięki obsłudze trzy rodzaje plików danych innego niż plik wykonywalny: zasób, zawartość i danych. Aby uzyskać więcej informacji, zobacz [zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md).  
  
 Kluczowym elementem obsługę plików danych niewykonywalnej WPF jest możliwość identyfikowania i załadować je przy użyciu unikatowej [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Aby uzyskać więcej informacji, zobacz [pakiet URI w WPF](pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a>Windows i oknach dialogowych  
 Posługują się użytkownicy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji autonomicznych przy użyciu systemu windows. Okno ma na celu hostowanie zawartości aplikacji i ujawniać funkcjonalność aplikacji, umożliwiający użytkownikom na interakcję z zawartością. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], systemu windows są hermetyzowane przez <xref:System.Windows.Window> klasy, który obsługuje:  
  
-   Tworzenie i wyświetlanie systemu windows.  
  
-   Ustanawianie relacji okno właściciela/właścicielem.  
  
-   Konfigurowanie wygląd okna (na przykład, rozmiar, lokalizację, ikony, tekst paska tytułu, obramowania).  
  
-   Śledzenie i interakcji z okresem istnienia okna.  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd Windows WPF](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window> obsługuje możliwość tworzenia specjalny rodzaj okna, znane jako okno dialogowe. Można utworzyć typy modalne i Niemodalne okna dialogowe.  
  
 Dla wygody i zalet możliwość ponownego wykorzystania i spójne środowisko użytkownika w aplikacjach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] udostępnia trzy typowych okien dialogowych Windows: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, i <xref:System.Windows.Controls.PrintDialog>.  
  
 Okno komunikatu to specjalny typ okna dialogowego do wyświetlania ważnych informacji tekstowych dla użytkowników, a także dotyczące zadawania pytań tak/nie/OK/Anuluj. Możesz użyć <xref:System.Windows.MessageBox> klasa do tworzenia i wyświetlanie okien komunikatów.  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd okien dialogowych](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Nawigacja  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługuje nawigacji w stylu dla sieci Web za pomocą stron (<xref:System.Windows.Controls.Page>) i hiperłączy (<xref:System.Windows.Documents.Hyperlink>). Nawigacja mogą być implementowane w na różne sposoby, które obejmują następujące czynności:  
  
-   Strony autonomicznych, które znajdują się w przeglądarce sieci Web.  
  
-   Strony są kompilowane do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest hostowana w przeglądarce sieci Web.  
  
-   Strony kompilowane do aplikacji autonomicznej i pracujących na oknie nawigacji (<xref:System.Windows.Navigation.NavigationWindow>).  
  
-   Stron, które są hostowane przez ramki (<xref:System.Windows.Controls.Frame>), może być hostowana na stronie autonomicznego lub strona skompilowane w ramach jednej [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] lub aplikacją.  
  
 Aby ułatwić nawigację, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wykonuje następujące czynności:  
  
-   <xref:System.Windows.Navigation.NavigationService>, aparat nawigacji udostępnione do przetwarzania żądań nawigacji, które jest używane przez <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] do obsługi nawigacji w obrębie aplikacji.  
  
-   Metody nawigacji do zainicjowania nawigacji.  
  
-   Nawigacja zdarzenia do śledzenia i wchodzić w interakcje z okresem istnienia nawigacji.  
  
-   Zapamiętywanie przy użyciu arkusza przeglądania do przodu i Wstecz, którego można się sprawdził i manipulować.  
  
 Aby uzyskać informacje, zobacz [Nawigacja — omówienie](navigation-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługuje również specjalny rodzaj nawigacji, znane jako strukturyzowana Nawigacja. Strukturyzowana Nawigacja może służyć do wywołania jednej lub więcej stron, które zwracają dane w sposób ze strukturą i przewidywalne, który jest zgodny z wywołaniem funkcji. Ta funkcja jest zależna od <xref:System.Windows.Navigation.PageFunction%601> klasy, która jest dokładniejszym opisem zawartym w [ze strukturą Przegląd Nawigacja](structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601> Służy również można uproszczenie tworzenia topologie nawigacji złożonych, które są opisane w [Przegląd topologia nawigacji](navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## <a name="hosting"></a>Hosting  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] może być hostowana w [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] lub Firefox. Każdy model hostingu ma swój własny zestaw zagadnienia i ograniczenia, które zostały omówione w [hostingu](hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a>Wdróż i konfiguruj  
 Mimo że jest to prosty [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje można tworzyć przy użyciu kompilatorów wiersza polecenia w wierszu polecenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integruje się z usługą [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] zapewnienie dodatkowego wsparcia, który uproszczony proces projektowania i kompilowania. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
 W zależności od typu aplikacji, które tworzysz istnieje co najmniej jedna opcja wdrażania do wyboru. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Zarządzanie aplikacjami — omówienie](application-management-overview.md)|Zawiera omówienie <xref:System.Windows.Application> klasy, w tym zarządzanie okresem istnienia aplikacji, systemu windows, zasobów aplikacji i nawigacji.|  
|[Okna w programie WPF](windows-in-wpf-applications.md)|Zawiera szczegółowe informacje o zarządzanie systemem windows w Twojej aplikacji, takich jak używać <xref:System.Windows.Window> klasy i w oknach dialogowych.|  
|[Nawigacja — omówienie](navigation-overview.md)|Omówienie zarządzania Nawigacja między stronami aplikacji.|  
|[Hosting](hosting-wpf-applications.md)|Zawiera omówienie [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].|  
|[Tworzenie i wdrażanie](building-and-deploying-wpf-applications.md)|W tym artykule opisano sposób tworzenia i wdrażania aplikacji WPF.|  
|[Wprowadzenie do platformy WPF w programie Visual Studio](../getting-started/introduction-to-wpf-in-vs.md)|W tym artykule opisano główne funkcje WPF.|  
|[Przewodnik: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Przewodnik, który pokazuje, jak utworzyć WPF aplikacji za pomocą strony nawigacji, układ, formanty, obrazy, style i powiązania.|
