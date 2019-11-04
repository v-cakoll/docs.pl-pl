---
title: Projektowanie aplikacji
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: ce37eecf7edf2adcc4f56af27a5c658400f7abba
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420638"
---
# <a name="application-development"></a>Projektowanie aplikacji
<a name="introduction"></a>Windows Presentation Foundation (WPF) to struktura prezentacji, za pomocą której można opracowywać następujące typy aplikacji:  
  
- Aplikacje autonomiczne (tradycyjne style systemu Windows skompilowane jako zestawy wykonywalne, które są instalowane i uruchamiane z komputera klienckiego).  
  
- Aplikacje przeglądarki XAML (XBAP) (aplikacje złożone z stron nawigacyjnych, które są wbudowane jako zestawy wykonywalne i obsługiwane przez przeglądarki sieci Web, takie jak Microsoft Internet Explorer lub Mozilla Firefox).  
  
- Niestandardowe biblioteki formantów (zestawy niewykonywalne zawierające kontrolki wielokrotnego użytku).  
  
- Biblioteki klas (zestawy niewykonywalne, które zawierają klasy wielokrotnego użytku).  
  
> [!NOTE]
> Korzystanie z typów WPF w usłudze systemu Windows jest zdecydowanie odradzane. Jeśli spróbujesz użyć tych funkcji w usłudze systemu Windows, mogą one nie zadziałały zgodnie z oczekiwaniami.  
  
 Aby skompilować ten zestaw aplikacji, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementuje hosta usług. Ten temat zawiera omówienie tych usług i miejsca, w których można znaleźć więcej informacji.  

<a name="Application_Management"></a>   
## <a name="application-management"></a>Zarządzanie aplikacjami  
 Plik wykonywalny [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje często wymagają podstawowego zestawu funkcji, który obejmuje następujące elementy:  
  
- Tworzenie wspólnej infrastruktury aplikacji (w tym tworzenie metody punktu wejścia i pętla komunikatów systemu Windows w celu odbierania komunikatów systemowych i wejściowych) oraz zarządzanie nimi.  
  
- Śledzenie i posługiwanie się okresem istnienia aplikacji.  
  
- Pobieranie i przetwarzanie parametrów wiersza polecenia.  
  
- Udostępnianie właściwości zakresu aplikacji i zasobów [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
- Wykrywanie i przetwarzanie nieobsługiwanych wyjątków.  
  
- Zwracanie kodów zakończenia.  
  
- Zarządzanie oknami w aplikacjach autonomicznych.  
  
- Śledzenie nawigacji w aplikacjach przeglądarki XAML (XBAP) i autonomicznych aplikacjach z oknami nawigacji i ramkami.  
  
 Te możliwości są implementowane przez klasę <xref:System.Windows.Application>, która jest dodawana do aplikacji przy użyciu *definicji aplikacji*.  
  
 Aby uzyskać więcej informacji, zobacz [Omówienie zarządzania aplikacjami](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a>Zasoby aplikacji WPF, zawartość, pliki danych  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerza podstawowe wsparcie w strukturze Microsoft .NET dla zasobów osadzonych z obsługą trzech rodzajów niewykonywalnych plików danych: zasobu, zawartości i danych. Aby uzyskać więcej informacji, zapoznaj się z tematem [zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md).  
  
 Kluczowym elementem obsługi plików danych niewykonywalnych WPF jest możliwość identyfikowania i ładowania ich przy użyciu unikatowego identyfikatora URI. Aby uzyskać więcej informacji, zobacz [identyfikatory URI pakietów w WPF](pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a>Okna i okna dialogowe  
 Użytkownicy współpracują z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] autonomicznymi aplikacjami za pomocą systemu Windows. Przeznaczeniem okna jest hostowanie zawartości aplikacji i Uwidacznianie funkcjonalności aplikacji, która zwykle umożliwia użytkownikom współdziałanie z zawartością. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]systemu Windows są hermetyzowane przez klasę <xref:System.Windows.Window>, która obsługuje:  
  
- Tworzenie i wyświetlanie okien.  
  
- Ustanawianie relacji okna właściciela/własności.  
  
- Konfigurowanie wyglądu okna (na przykład rozmiaru, lokalizacji, ikon, tekstu paska tytułu, obramowania).  
  
- Śledzenie i posługiwanie się okresem istnienia okna.  
  
 Aby uzyskać więcej informacji, zobacz [WPF Windows — omówienie](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window> obsługuje możliwość tworzenia specjalnego typu okna znanego jako okno dialogowe. Można utworzyć zarówno modalne, jak i niemodalne typy okien dialogowych.  
  
 Dla wygody i korzyści ze stosowania i spójnego środowiska użytkownika w aplikacjach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uwidacznia trzy podstawowe okna dialogowe systemu Windows: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>i <xref:System.Windows.Controls.PrintDialog>.  
  
 Okno komunikatu jest specjalnym typem okna dialogowego służącym do wyświetlania ważnych informacji tekstowych dla użytkowników, a w przypadku pytania proste tak/nie/OK/Anuluj. Za pomocą klasy <xref:System.Windows.MessageBox> można tworzyć i wyświetlać okna komunikatów.  
  
 Aby uzyskać więcej informacji, zobacz [okna dialogowe przegląd](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Nawigacja  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługuje nawigowanie w stylu sieci Web za pomocą stron (<xref:System.Windows.Controls.Page>) i hiperlinków (<xref:System.Windows.Documents.Hyperlink>). Nawigację można zaimplementować na różne sposoby:  
  
- Autonomiczne strony hostowane w przeglądarce internetowej.  
  
- Strony skompilowane w aplikacji XBAP, która jest hostowana w przeglądarce sieci Web.  
  
- Strony skompilowane w aplikacji autonomicznej i hostowane w oknie nawigacji (<xref:System.Windows.Navigation.NavigationWindow>).  
  
- Strony hostowane przez ramkę (<xref:System.Windows.Controls.Frame>), które mogą być hostowane na stronie autonomicznej lub strony skompilowane w aplikacji XBAP lub autonomicznej.  
  
 Aby ułatwić nawigację, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementuje następujące elementy:  
  
- <xref:System.Windows.Navigation.NavigationService>udostępniony aparat nawigacyjny do przetwarzania żądań nawigacji, które są używane przez <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>i XBAP do obsługi nawigacji wewnątrz aplikacji.  
  
- Metody nawigacji umożliwiające zainicjowanie nawigacji.  
  
- Zdarzenia nawigacji do śledzenia i współpracy z okresem istnienia nawigacji.  
  
- Zapamiętywanie nawigacji z tyłu i do przodu przy użyciu dziennika, który można także sprawdzić i manipulować.  
  
 Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](navigation-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługuje również specjalny typ nawigacji znany jako Nawigacja strukturalna. Strukturalna Nawigacja może służyć do wywoływania co najmniej jednej strony, która zwraca dane w sposób strukturalny i przewidywalny, który jest zgodny z funkcjami wywołującymi. Ta funkcja zależy od klasy <xref:System.Windows.Navigation.PageFunction%601>, która jest opisana dokładniej w temacie [Omówienie nawigacji strukturalnej](structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601> służy również do uproszczenia tworzenia złożonych topologii nawigacyjnej, które są opisane w [Omówienie topologii nawigacji](navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## <a name="hosting"></a>Hosting  
 Aplikacje XBAP mogą być hostowane w programie Microsoft Internet Explorer lub Firefox. Każdy model hostingu ma swój własny zestaw zagadnień i ograniczeń, które są omówione w [hostingu](hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a>Wdróż i konfiguruj  
 Chociaż proste aplikacje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mogą być kompilowane z wiersza polecenia przy użyciu kompilatorów wiersza polecenia, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integruje się z programem Visual Studio, aby zapewnić dodatkową pomoc techniczną, która uprości proces tworzenia i kompilowania. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
 W zależności od typu skompilowanej aplikacji istnieje co najmniej jedna opcja wdrażania do wyboru. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Zarządzanie aplikacjami — omówienie](application-management-overview.md)|Zawiera przegląd klasy <xref:System.Windows.Application>, w tym zarządzanie okresem istnienia aplikacji, systemem Windows, zasobami aplikacji i nawigacją.|  
|[Okna w programie WPF](windows-in-wpf-applications.md)|Zawiera szczegółowe informacje dotyczące zarządzania oknami w aplikacji, w tym sposób używania <xref:System.Windows.Window> klasy i okien dialogowych.|  
|[Nawigacja — omówienie](navigation-overview.md)|Zawiera omówienie zarządzania nawigacją między stronami aplikacji.|  
|[Hosting](hosting-wpf-applications.md)|Zawiera omówienie aplikacji przeglądarki XAML (XBAP).|  
|[Tworzenie i wdrażanie](building-and-deploying-wpf-applications.md)|Opisuje sposób kompilowania i wdrażania aplikacji WPF.|  
|[Wprowadzenie do platformy WPF w programie Visual Studio](../getting-started/introduction-to-wpf-in-vs.md)|Opisuje główne funkcje platformy WPF.|  
|[Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Przewodnik, który pokazuje, jak utworzyć aplikację WPF za pomocą nawigacji, układu, kontrolek, obrazów, stylów i powiązania.|
