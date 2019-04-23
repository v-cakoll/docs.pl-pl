---
title: Wdrażanie aplikacji WPF (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 0ffd4fb05a5a409d74f8a9401a5fb021db0cd99b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320655"
---
# <a name="deploying-a-wpf-application-wpf"></a>Wdrażanie aplikacji WPF (WPF)
Po są wbudowane aplikacje Windows Presentation Foundation (WPF), muszą zostać wdrożone. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a .NET Framework zawierają kilka technologie wdrażania. Technologie wdrażania, które jest używane do wdrażania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacja jest zależna od typu aplikacji. Ten temat zawiera krótkie omówienie poszczególnych technologii wdrożenia i jak są używane w połączeniu z wymagań związanych z wdrażaniem każdego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] typu aplikacji.  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Technologie wdrażania  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i .NET Framework zawiera kilka technologii wdrożenia, w tym:  
  
-   Umożliwia wdrażanie XCopy.  
  
-   [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] wdrożenie.  
  
-   [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] wdrożenie.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>Umożliwia wdrażanie XCopy  
 Umożliwia wdrażanie XCopy odnosi się do korzystania z programu wiersza polecenia XCopy, aby skopiować pliki z jednej lokalizacji do innej. Umożliwia wdrażanie XCopy jest odpowiednie w następujących okolicznościach:  
  
-   Aplikacja jest niezależna. Nie trzeba ją zaktualizować klienta do uruchomienia.  
  
-   Pliki aplikacji należy przenieść z jednej lokalizacji do innej, takich jak z lokalizacji kompilacji (dysk lokalny, [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] udziału plików i tak dalej) do lokalizacji publikowania (witryny sieci Web [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] udziału plików i tak dalej).  
  
-   Aplikacja nie wymaga integracji powłoki (skrótu w menu Start, ikony pulpitu i tak dalej).  
  
 Chociaż XCopy nadaje się do prostych wdrożeń, jest ograniczona w przypadku bardziej złożonych możliwości wdrażania wymagane. W szczególności za pomocą polecenia XCopy często wiąże się obciążenie do tworzenia, wykonywania i utrzymywania skrypty do zarządzania wdrożeniem w niezawodny sposób. Ponadto polecenia XCopy nie obsługuje przechowywania wersji, Odinstalowywanie lub wycofywania.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Instalator Windows  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] Umożliwia aplikacjom spakowanych jako autonomiczne pliki wykonywalne, które można łatwo dystrybuowane do klientów i uruchamiać. Ponadto [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] został zainstalowany przy użyciu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i umożliwia integrację z pulpitu, Start menu i programy w Panelu sterowania.  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] upraszcza instalowania i odinstalowywania aplikacji, ale nie zapewnia funkcje służące do zapewnienia zainstalowane aplikacje są aktualizowane z punktu widzenia obsługi wersji.  
  
 Aby uzyskać więcej informacji na temat Instalatora Windows, zobacz [wdrożenia Instalatora Windows](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Wdrożenie ClickOnce  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] Umożliwia wdrażanie aplikacji internetowych dla innych aplikacji. Aplikacje są publikowane i wdrażane z serwerów sieci Web lub pliku. Mimo że [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nie obsługuje pełnej gamy klienta funkcji [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]— czy zainstalowane aplikacje, obsługuje ona podzestaw, który obejmuje następujące elementy:  
  
-   Integracja z Start menu i programy w Panelu sterowania.  
  
-   Przechowywanie wersji, wycofywania i odinstalowywania.  
  
-   Tryb instalacji w trybie online, który zawsze uruchamia aplikację w lokalizacji wdrożenia.  
  
-   Automatyczne aktualizowanie, gdy wydawane są nowe wersje.  
  
-   Rejestrowanie rozszerzeń nazw plików.  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], zobacz [wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>Wdrażanie aplikacji WPF  
 Opcji wdrażania dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji są zależne od typu aplikacji. Z punktu widzenia wdrażania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dostępne są trzy typy znaczące aplikacji:  
  
-   Aplikacje autonomiczne.  
  
-   Tylko znaczniki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacji.  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Wdrażanie aplikacji autonomicznych  
 Aplikacje autonomiczne są wdrażane przy użyciu [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] lub [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. W obu przypadkach aplikacje autonomiczne wymaga pełnego zaufania do uruchomienia. Pełne zaufanie jest automatycznie przyznane dla aplikacji autonomicznych, które są wdrażane przy użyciu [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Aplikacje autonomiczne, które są wdrażane przy użyciu [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nie są automatycznie przyznawane pełnego zaufania. Zamiast tego [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] Wyświetla zabezpieczeń, okno dialogowe Ostrzeżenie, które użytkownicy muszą zaakceptować przed zainstalowaniem aplikacji autonomicznej. Jeśli zaakceptowane, autonomiczną aplikacją jest zainstalowany i udzielone pełne zaufanie. Jeśli nie, nie zainstalowano aplikacji autonomicznej.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Wdrażanie aplikacji tylko do znaczników XAML  
 Tylko znaczniki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony są zazwyczaj publikowane na serwerach sieci Web, takie jak [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] strony i mogą być wyświetlane przy użyciu [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]. Tylko znaczniki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron uruchomić w piaskownicy częściowego zaufania zabezpieczeń bez ograniczeń, które są definiowane przez zestaw uprawnień strefy Internet. Dzięki temu równoważne izolowanym do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]— na podstawie aplikacji sieci Web.  
  
 Aby uzyskać więcej informacji o zabezpieczeniach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , zobacz [zabezpieczeń](../security-wpf.md).  
  
 Tylko znaczniki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony mogą być zainstalowane do lokalnego systemu plików przy użyciu dowolnego polecenia XCopy lub [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Te strony można wyświetlić przy użyciu [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] lub w Eksploratorze Windows.  
  
 Aby uzyskać więcej informacji na temat XAML, zobacz [Przegląd XAML (WPF)](../advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>Deploying XAML Browser Applications  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] są skompilowanymi aplikacji, które wymagają następujących trzech plików do wdrożenia:  
  
-   *ApplicationName*.exe: Plik zestawu pliku wykonywalnego aplikacji.  
  
-   *ApplicationName*XBAP: Manifest wdrożenia.  
  
-   *ApplicationName*. exe.manifest: Manifest aplikacji.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat manifesty wdrażania i aplikacji, zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
 Te pliki są tworzone podczas [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest wbudowana. Aby uzyskać więcej informacji, zobacz [jak: Utwórz nowy projekt aplikacji przeglądarki WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Tylko znaczniki, takich jak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] najczęściej są publikowane na serwerze sieci Web oraz wyświetlać za pomocą [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)].  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] można wdrożyć na klientach przy użyciu dowolnej techniki wdrażania. Jednak [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] jest zalecane, ponieważ zapewnia następujące możliwości:  
  
1. Aktualizacje automatyczne po opublikowaniu nowej wersji.  
  
2. Podniesienie uprawnień dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uruchomiona z pełnym zaufaniem.  
  
 Domyślnie ClickOnce publikowanie aplikacji pliki z rozszerzeniem .deploy. Może być problematyczne, ale można go wyłączyć. Aby uzyskać więcej informacji, zobacz [serwera i problemy z konfiguracją klienta we wdrożeniach ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Aby uzyskać więcej informacji o wdrażaniu [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], zobacz [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>Instalowanie programu .NET Framework  
 Aby uruchomić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji Microsoft .NET Framework, należy można zainstalować na komputerze klienckim. [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] automatycznie wykrywa, czy klienci zostali zainstalowani za pomocą .NET Framework podczas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] są wyświetlane aplikacje hostowane w przeglądarce. Jeśli nie zainstalowano programu .NET Framework, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] monituje użytkowników o jego zainstalowanie.  
  
 Aby wykryć, czy są zainstalowane .NET Framework, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] obejmuje aplikację program inicjujący, który jest zarejestrowany jako plan awaryjny [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] obsługi zawartości plików z następującymi rozszerzeniami: .xaml, XPS, XBAP i .application. Jeśli przejdziesz do tych typów plików i .NET Framework nie jest zainstalowany na komputerze klienckim, aplikacja inicjująca żąda uprawnienia do jej zainstalowania. Jeśli uprawnienie nie zostanie podany, .NET Framework ani aplikacji nie jest zainstalowany.  
  
 W przypadku przyznania uprawnienia [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] pobiorą i zainstalują przy użyciu .NET Framework [!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)]. Po pomyślnej instalacji programu .NET Framework pierwotnie żądany plik jest otwarty w nowym oknie przeglądarki.  
  
 Automatyczne wykrywanie .NET framework jest dostępna w [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)], i [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] klienci, którzy mają [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] lub nowszej.  
  
 Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji .NET Framework i](../../deployment/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)
- [Zabezpieczenia](../security-wpf.md)
