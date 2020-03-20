---
title: Projektowanie aplikacji
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 5ff9f58b72982f79e70b80f60c10828c3b54e5bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186004"
---
# <a name="application-development"></a>Projektowanie aplikacji
<a name="introduction"></a>Windows Presentation Foundation (WPF) to struktura prezentacji, która może służyć do tworzenia następujących typów aplikacji:  
  
- Aplikacje autonomiczne (aplikacje systemu Windows w tradycyjnym stylu utworzone jako zestawy wykonywalne, które są instalowane i uruchamiane z komputera klienckiego).  
  
- Aplikacje przeglądarki XAML (XBAPs) (aplikacje składające się ze stron nawigacyjnych, które są zbudowane jako zestawy wykonywalne i hostowane przez przeglądarki internetowe, takie jak Microsoft Internet Explorer lub Mozilla Firefox).  
  
- Niestandardowe biblioteki sterowania (zestawy niewykonalne zawierające kontrolki wielokrotnegoużynia).  
  
- Biblioteki klas (zestawy niewykonalne zawierające klasy wielokrotnegoużynia).  
  
> [!NOTE]
> Za pomocą WPF typów w usłudze systemu Windows jest zdecydowanie odradzane. Jeśli spróbujesz użyć tych funkcji w usłudze systemu Windows, mogą one nie działać zgodnie z oczekiwaniami.  
  
 Aby utworzyć ten zestaw aplikacji, WPF implementuje wiele usług. Ten temat zawiera omówienie tych usług i gdzie znaleźć więcej informacji.  

<a name="Application_Management"></a>
## <a name="application-management"></a>Zarządzanie aplikacjami  
 Aplikacje WPF wykonywalne często wymagają podstawowego zestawu funkcji, który zawiera następujące elementy:  
  
- Tworzenie wspólnej infrastruktury aplikacji i zarządzanie nimi (w tym tworzenie metody punktu wejścia i pętli komunikatów systemu Windows w celu odbierania komunikatów systemowych i wejściowych).  
  
- Śledzenie i interakcja z okresem istnienia aplikacji.  
  
- Pobieranie i przetwarzanie parametrów wiersza polecenia.  
  
- Udostępnianie właściwości i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zasobów zakresu aplikacji.  
  
- Wykrywanie i przetwarzanie nieobsługiwał wyjątków.  
  
- Zwracanie kodów wyjścia.  
  
- Zarządzanie oknami w aplikacjach autonomicznych.  
  
- Śledzenie nawigacji w aplikacjach przeglądarki XAML (XBAPs) i autonomicznych aplikacjach z oknami nawigacyjnymi i ramkami.  
  
 Te możliwości są implementowane <xref:System.Windows.Application> przez klasę, która jest dodawany do aplikacji przy użyciu *definicji aplikacji*.  
  
 Aby uzyskać więcej informacji, zobacz [Omówienie zarządzania aplikacjami](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a>Zasoby aplikacji WPF, zawartość, pliki danych  
 WPF WPF rozszerza podstawową obsługę w programie Microsoft .NET Framework dla osadzonych zasobów z obsługą trzech rodzajów plików danych niekonywalnych: zasobów, zawartości i danych. Aby uzyskać więcej informacji, zobacz [Zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md).  
  
 Kluczowym składnikiem obsługi plików danych niewykonalnych WPF WPF jest możliwość identyfikowania i ładowania ich przy użyciu unikatowego identyfikatora URI. Aby uzyskać więcej informacji, zobacz [Pack URI w WPF](pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a>Okna i okna dialogowe  
 Użytkownicy wchodzą w interakcje z aplikacjami autonomicznymi WPF za pośrednictwem systemu Windows. Celem okna jest hostować zawartość aplikacji i udostępniać funkcje aplikacji, które zwykle umożliwia użytkownikom interakcję z zawartością. W WPF WPF okna są <xref:System.Windows.Window> hermetyzowane przez klasę, która obsługuje:  
  
- Tworzenie i pokazywanie okien.  
  
- Ustanawianie relacji właściciel/okno należące do właściciela.  
  
- Konfigurowanie wyglądu okna (na przykład rozmiar, lokalizacja, ikony, tekst paska tytułu, obramowanie).  
  
- Śledzenie i interakcja z okresem istnienia okna.  
  
 Aby uzyskać więcej informacji, zobacz [Omówienie systemu Windows WPF](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window>obsługuje możliwość tworzenia specjalnego typu okna znanego jako okno dialogowe. Można tworzyć zarówno modalne, jak i niemodalne typy okien dialogowych.  
  
 Dla wygody i korzyści z ponownego użycia i spójnego środowiska użytkownika w różnych aplikacjach, WPF udostępnia trzy typowe okna dialogowe systemu Windows: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, i <xref:System.Windows.Controls.PrintDialog>.  
  
 Okno komunikatu to specjalny typ okna dialogowego do wyświetlania ważnych informacji tekstowych użytkownikom oraz do zadawania prostych pytań Tak/Nie/OK/Anuluj. <xref:System.Windows.MessageBox> Klasy służy do tworzenia i pokazywalek komunikatów.  
  
 Aby uzyskać więcej informacji, zobacz [Omówienie okien dialogowych](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Nawigacja  
 WPF WPF obsługuje nawigację<xref:System.Windows.Controls.Page>w stylu sieci<xref:System.Windows.Documents.Hyperlink>Web przy użyciu stron ( ) i hiperłączy ( ). Nawigacja może być zaimplementowana na wiele sposobów, które obejmują następujące elementy:  
  
- Strony autonomiczne hostowane w przeglądarce sieci Web.  
  
- Strony skompilowane w XBAP, który jest obsługiwany w przeglądarce sieci Web.  
  
- Strony skompilowane w samodzielną aplikację i hostowane przez okno nawigacji (<xref:System.Windows.Navigation.NavigationWindow>).  
  
- Strony hostowane przez ramkę<xref:System.Windows.Controls.Frame>( ), które mogą być hostowane na stronie autonomicznej lub strony skompilowane do XBAP lub aplikacji autonomicznej.  
  
 Aby ułatwić nawigację, WPF implementuje następujące elementy:  
  
- <xref:System.Windows.Navigation.NavigationService>, udostępniony aparat nawigacyjny do przetwarzania żądań nawigacji używanych przez <xref:System.Windows.Controls.Frame>program <xref:System.Windows.Navigation.NavigationWindow>, oraz XBAPs do obsługi nawigacji wewnątrz aplikacji.  
  
- Metody nawigacji do inicjowania nawigacji.  
  
- Zdarzenia nawigacji do śledzenia i interakcji z okresem istnienia nawigacji.  
  
- Zapamiętywanie nawigacji do tyłu i do przodu za pomocą dziennika, który można również sprawdzić i manipulować.  
  
 Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](navigation-overview.md).  
  
 WPF WPF obsługuje również specjalny typ nawigacji znany jako nawigacji strukturalnej. Nawigacja strukturalna może służyć do wywołania jednej lub więcej stron, które zwracają dane w sposób strukturalny i przewidywalny, który jest zgodny z funkcjami wywołującymi. Ta funkcja zależy <xref:System.Windows.Navigation.PageFunction%601> od klasy, która jest opisana dalej w [ustrukturyzowanym przeglądzie nawigacji.](structured-navigation-overview.md) <xref:System.Windows.Navigation.PageFunction%601>służy również uproszczeniu tworzenia złożonych topologii nawigacji, które są opisane w [Przeglądzie Topologii Nawigacji](navigation-topologies-overview.md).  
  
<a name="Hosting"></a>
## <a name="hosting"></a>Hosting  
 XBAPs mogą być hostowane w programie Microsoft Internet Explorer lub Firefox. Każdy model hostingu ma swój własny zestaw zagadnień i ograniczeń, które są objęte [hostingiem](hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a>Wdróż i konfiguruj  
 Mimo że proste aplikacje WPF można utworzyć z wiersza polecenia przy użyciu kompilatorów wiersza polecenia, WPF integruje się z programem Visual Studio, aby zapewnić dodatkową obsługę, która uprościła proces tworzenia i kompilacji. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
 W zależności od typu aplikacji, które tworzysz, istnieje jedna lub więcej opcji wdrażania do wyboru. Aby uzyskać więcej informacji, zobacz [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przegląd Zarządzanie aplikacjami](application-management-overview.md)|Zawiera omówienie <xref:System.Windows.Application> klasy, w tym zarządzanie okresem istnienia aplikacji, oknami, zasobami aplikacji i nawigacją.|  
|[Okna w WPF](windows-in-wpf-applications.md)|Zawiera szczegółowe informacje na temat zarządzania <xref:System.Windows.Window> oknami w aplikacji, w tym jak używać klasy i okien dialogowych.|  
|[Przegląd Nawigacja](navigation-overview.md)|Zawiera omówienie zarządzania nawigacją między stronami aplikacji.|  
|[Hosting](hosting-wpf-applications.md)|Zawiera przegląd aplikacji przeglądarki XAML (XBAPs).|  
|[Buduj i wdrażaj](building-and-deploying-wpf-applications.md)|W tym artykule opisano, jak skompilować i wdrożyć aplikację WPF.|  
|[Wprowadzenie do platformy WPF w programie Visual Studio](../getting-started/introduction-to-wpf-in-vs.md)|Opisuje główne funkcje WPF.|  
|[Instruktaż: Moja pierwsza aplikacja komputerowa WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Przewodnik, który pokazuje, jak utworzyć aplikację WPF przy użyciu nawigacji strony, układ, formanty, obrazy, style i powiązania.|
