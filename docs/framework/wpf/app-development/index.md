---
title: Projektowanie aplikacji
ms.custom: ''
ms.date: 01/26/2018
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1d2a79a05f18fecf4e008aa6a95d359c719e854b
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="application-development"></a>Projektowanie aplikacji
<a name="introduction"></a>
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]to platforma prezentacji, która umożliwia tworzenie następujących typów aplikacji:  
  
-   Aplikacje autonomiczne (styl tradycyjnych [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] aplikacje utworzone jako pliku wykonywalnego zestawy, które są zainstalowane na i uruchamiane na komputerze klienta).  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)](aplikacji składający się z nawigacji strony, które są tworzone w postaci pliku wykonywalnego zestawów i hostowany przez przeglądarki sieci Web, takiej jak [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] lub Mozilla Firefox).  
  
-   Biblioteki formantów niestandardowych (z systemem innym niż plik wykonywalny zestawów zawierających formantów wielokrotnych).  
  
-   Biblioteki klas (inne niż wykonywalne zestawy zawierające klasy wielokrotnego użytku).  
  
> [!NOTE]
>  Używanie typów WPF w usłudze systemu Windows jest zalecane. Próba użycia tych funkcji w usłudze systemu Windows, mogą one nie działać zgodnie z oczekiwaniami.  
  
 Do tworzenia aplikacji, ten zestaw [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementuje hosta usługi. Ten temat zawiera omówienie tych usług i gdzie można znaleźć więcej informacji.  
  

  
<a name="Application_Management"></a>   
## <a name="application-management"></a>Zarządzanie aplikacjami  
 Plik wykonywalny [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje często wymagają podstawowy zestaw funkcji, który obejmuje następujące elementy:  
  
-   Tworzenie i zarządzanie nimi wspólną infrastrukturę aplikacji (w tym tworzenie metoda punktu wejścia i Pętla wiadomości Windows odbierać systemu i komunikaty wejściowe).  
  
-   Śledzenie i interakcji z użytkowania aplikacji.  
  
-   Trwa pobieranie i przetwarzanie parametry wiersza polecenia.  
  
-   Właściwości zakresu aplikacji do udostępniania i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zasobów.  
  
-   Wykrywanie i przetwarzania nieobsługiwanych wyjątków.  
  
-   Zwraca kod zakończenia.  
  
-   Zarządzanie oknami w autonomicznej aplikacji.  
  
-   Śledzenie nawigacji w [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]i aplikacje autonomiczne z systemem windows nawigacji i ramki.  
  
 Te możliwości są implementowane przez <xref:System.Windows.Application> klasy, który można dodać do aplikacji przy użyciu *definicji aplikacji*.  
  
 Aby uzyskać więcej informacji, zobacz [omówienie zarządzania aplikacji](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a>Zasoby aplikacji WPF, zawartość, pliki danych  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]oferuje rozszerzone wsparcie podstawowe w [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] dla zasobów osadzonych o obsługę trzy rodzaje pliki danych z systemem innym niż plik wykonywalny: zasobów, zawartość i danych. Aby uzyskać więcej informacji, zobacz [zasób w aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Najważniejszym aspektem obsługę plików danych inne niż wykonywalne WPF jest możliwość identyfikowania i załadować je za pomocą unikatowego [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Aby uzyskać więcej informacji, zobacz [identyfikatorów URI pakietu na platformie WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a>I okna dialogowe  
 Użytkownicy korzystają z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji autonomicznych przy użyciu systemu windows. Okno ma na celu udostępnić zawartość aplikacji i ujawniać funkcjonalność aplikacji, umożliwiający użytkownikom na interakcję z zawartością. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], systemu windows są hermetyzowane przez <xref:System.Windows.Window> klasy, który obsługuje:  
  
-   Tworzenie i wyświetlanie systemu windows.  
  
-   Ustanowienie relacji okno właściciela/własnością.  
  
-   Konfigurowanie wyglądu okna (na przykład, rozmiar, lokalizację, ikony, tekst paska tytułu, obramowania).  
  
-   Śledzenie i interakcji z okresu istnienia okna.  
  
 Aby uzyskać więcej informacji, zobacz [WPF systemu Windows — omówienie](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
 <xref:System.Windows.Window>obsługuje możliwość tworzenia specjalny typ oknem znanym jako okno dialogowe. Można tworzyć typy zarówno modalne i Niemodalne okna dialogowe.  
  
 Dla wygody i zalet możliwość ponownego wykorzystania i spójny interfejs użytkownika w aplikacjach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] udostępnia trzy typowe [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] okien dialogowych: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, i <xref:System.Windows.Controls.PrintDialog>.  
  
 Okno komunikatu jest specjalnym rodzajem okno dialogowe pokazujące ważnych informacji tekstowych dla użytkowników i do zadawania pytań Yes/No/OK/Anuluj. Możesz użyć <xref:System.Windows.MessageBox> klasa do tworzenia i wyświetlanie pola komunikatu.  
  
 Aby uzyskać więcej informacji, zobacz [omówienie pola dialogowe](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Nawigacji  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]obsługuje nawigacji stylu sieci Web za pomocą stron (<xref:System.Windows.Controls.Page>) i hiperłącza (<xref:System.Windows.Documents.Hyperlink>). Nawigacji może być wdrożonych w różnych sposobów są następujące:  
  
-   Autonomiczny stron, które są obsługiwane w przeglądarce sieci Web.  
  
-   Skompilowane stron w [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest hostowana w przeglądarce sieci Web.  
  
-   Strony skompilowany do aplikacji autonomicznej i hostowanych przez okno nawigacji (<xref:System.Windows.Navigation.NavigationWindow>).  
  
-   Stron, które są obsługiwane przez ramki (<xref:System.Windows.Controls.Frame>), może być hostowana na stronie autonomicznej lub strona skompilowany w albo [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] lub aplikacja autonomiczna.  
  
 Aby ułatwić nawigacji, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wykonuje następujące czynności:  
  
-   <xref:System.Windows.Navigation.NavigationService>, aparat nawigacji udostępnione do przetwarzania żądań nawigacji, które jest używane przez <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] do obsługi nawigacji wewnątrz aplikacji.  
  
-   Metody nawigacji do zainicjowania nawigacji.  
  
-   Zdarzenia nawigacji do śledzenia i interakcję z okresu istnienia nawigacji.  
  
-   Zapamiętywanie Wstecz i przeglądania do przodu przy użyciu dziennika, który również można inspekcji i manipulowanie.  
  
 Aby uzyskać informacje, zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]obsługuje również specjalny typ nawigacji znany jako strukturze nawigacji. Strukturalne nawigacji może służyć do wywołania jedną lub więcej stron, które zwracają dane w sposób strukturalnych i przewidywalne, który jest zgodny z wywołaniem funkcji. Ta funkcja jest zależna od <xref:System.Windows.Navigation.PageFunction%601> klasy, która jest opisane dalej w [strukturalnych omówienie nawigacji](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601>Służy również do uproszczenia procesu tworzenia topologii złożonych nawigacji, które zostały opisane w [— omówienie topologii nawigacji](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## <a name="hosting"></a>Hosting  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]może być hostowana w [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] lub Firefox. Każdy model hostingu ma swój własny zestaw zagadnień i ograniczenia, które zostały omówione w [hostingu](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a>Wdróż i konfiguruj  
 Mimo że jest to prosty [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje mogą być wbudowane w wierszu polecenia przy użyciu kompilatory w wierszu polecenia, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integruje się z [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] zapewnienie dodatkowego wsparcia, który uproszczony proces projektowania i kompilacji. Aby uzyskać więcej informacji, zobacz [kompilowania aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 W zależności od typu aplikacji, które tworzysz istnieje co najmniej jedna opcja wdrażania do wyboru. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Zarządzanie aplikacjami — omówienie](../../../../docs/framework/wpf/app-development/application-management-overview.md)|Zawiera omówienie <xref:System.Windows.Application> klasy w tym zarządzanie okresem istnienia aplikacji, systemu windows, zasobów aplikacji i nawigacji.|  
|[Okna w programie WPF](../../../../docs/framework/wpf/app-development/windows-in-wpf-applications.md)|Zawiera szczegółowe informacje dotyczące zarządzania systemu windows, w tym dotyczące używania aplikacji <xref:System.Windows.Window> pola klasy i okna dialogowego.|  
|[Nawigacja — omówienie](../../../../docs/framework/wpf/app-development/navigation-overview.md)|Omówienie zarządzania nawigacji między stronami aplikacji.|  
|[Hosting](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)|Zawiera omówienie [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].|  
|[Tworzenie i wdrażanie](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md)|Opisuje sposób tworzenia i wdrażania aplikacji WPF.|  
|[Wprowadzenie do platformy WPF w programie Visual Studio](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)|Zawiera opis głównych funkcji WPF.|  
|[Przewodnik: moja pierwsza aplikacja klasyczna WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|Wskazówki, które pokazuje, jak utworzyć WPF aplikacji przy użyciu strony nawigacji, układ, kontrolek, obrazy, style i powiązania.|
