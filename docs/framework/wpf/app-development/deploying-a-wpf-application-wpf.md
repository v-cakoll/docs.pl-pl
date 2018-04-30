---
title: Wdrażanie aplikacji WPF (WPF)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bf38c4b15f59ca90d00f8f6b365a3233ee3516bb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="deploying-a-wpf-application-wpf"></a>Wdrażanie aplikacji WPF (WPF)
Po aplikacji Windows Presentation Foundation (WPF) są wbudowane, muszą zostać wdrożone. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i .NET Framework obejmuje kilka technologii wdrażania. Technologia wdrożenia, która służy do wdrażania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji zależy od typu aplikacji. Ten temat zawiera krótkie omówienie tych technologii wdrażania oraz sposób ich użycia w połączeniu z wymaganiami wdrożenia każdego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] typu aplikacji.  
  
   
<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Technologie wdrażania  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i .NET Framework obejmują kilka technologii wdrażania, w tym:  
  
-   XCopy wdrożenia.  
  
-   [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] wdrożenia.  
  
-   [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] wdrożenia.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>XCopy wdrożenia  
 Wdrożenie XCopy odwołuje się do użycia programu wiersza polecenia XCopy do kopiowania plików z jednej lokalizacji do innej. XCopy wdrożenia jest odpowiednia w następujących okolicznościach:  
  
-   Aplikacja jest niezależna. Nie jest konieczne, zaktualizuj klienta do uruchomienia.  
  
-   Pliki aplikacji wymagającego przeniesienia z jednej lokalizacji do innej, takich jak z lokalizacji kompilacji (dysk lokalny [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] udziału plików i tak dalej) do lokalizacji publikowania (witryny sieci Web [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] udziału plików i tak dalej).  
  
-   Aplikacja nie wymaga integracji powłoki (skrótu w menu Start, ikony pulpitu i tak dalej).  
  
 Chociaż XCopy jest odpowiedni dla scenariuszy wdrażania prostego, jest ograniczona gdy wymagane są bardziej złożone możliwości wdrażania. W szczególności przy użyciu polecenia XCopy często wiąże się obciążenie za tworzenie, wykonywanie i obsługę skryptów do zarządzania w niezawodny sposób wdrażania. Ponadto XCopy nie obsługuje wersji, Odinstalowywanie lub wycofywania.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Instalator Windows  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] Umożliwia aplikacjom umieszczone jako niezależne plików wykonywalnych, które mogą być łatwo dystrybuowane do klientów i uruchamiać. Ponadto [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] jest instalowany z [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i umożliwia integrację z pulpitu, Start menu i programy w Panelu sterowania.  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] upraszcza instalowanie i odinstalowywanie aplikacji, ale nie zapewnia urządzenia do zapewnienia zainstalowanych aplikacji są aktualizowane z punktu widzenia przechowywania wersji.  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)], zobacz [wdrożenia Instalatora Windows](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Wdrożenie ClickOnce  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] Umożliwia wdrażanie aplikacji w stylu sieci Web dla aplikacji sieci Web. Aplikacje są publikowane w i wdrożone z serwerów sieci Web lub pliku. Mimo że [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nie obsługuje pełny zakres klienta funkcji [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]— czy zainstalowane aplikacje, obsługuje podzbiór obejmuje następujące elementy:  
  
-   Integracja z Start menu i programy w Panelu sterowania.  
  
-   Przechowywanie wersji, wycofywania i odinstalowywania.  
  
-   Tryb online instalacji zawsze uruchamia aplikacji z lokalizacji wdrożenia.  
  
-   Automatyczne aktualizowanie po udostępnieniu nowej wersji.  
  
-   Rejestracja rozszerzenia pliku.  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], zobacz [zabezpieczenia ClickOnce i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>Wdrażanie aplikacji WPF  
 Opcje wdrożenia dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji są zależne od typu aplikacji. Z perspektywy wdrożenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera trzy znaczących aplikacji:  
  
-   Aplikacje autonomiczne.  
  
-   Tylko do znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacji.  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Wdrażanie aplikacji autonomicznych  
 Aplikacje autonomiczne są wdrażane za pomocą [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] lub [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. W obu przypadkach aplikacje autonomiczne wymagają pełnego zaufania do uruchomienia. Pełne zaufanie jest automatycznie przyznawane do aplikacji autonomicznej, które są wdrażane za pomocą [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Aplikacje autonomiczne, które są wdrażane za pomocą [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nie otrzymują automatycznie pełnego zaufania. Zamiast tego [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] wyświetla ostrzeżenie okna dialogowego, które użytkownicy muszą zaakceptować przed zainstalowaniem aplikacji autonomicznej zabezpieczeń. Czy przyjęty, aplikacja autonomiczna jest zainstalowany i udzielane pełne zaufanie. Jeśli nie, nie zainstalowano aplikacji autonomicznych.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Wdrażanie aplikacji tylko do znaczników XAML  
 Tylko do znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony są zazwyczaj publikowane na serwerach sieci Web, tak samo, jak [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] stron i można je wyświetlać za pomocą [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]. Tylko do znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony uruchomione w częściowo zaufanym izolowanym z ograniczeniami, zdefiniowane przez zestaw uprawnień w strefie Internet. Zapewnia to odpowiednik izolowanym do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]— aplikacje sieci Web.  
  
 Aby uzyskać więcej informacji o zabezpieczeniach dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, zobacz [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md).  
  
 Tylko do znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony mogą być zainstalowane w lokalnym systemie plików przy użyciu albo XCopy lub [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Te strony można wyświetlić przy użyciu [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] lub w Eksploratorze Windows.  
  
 Aby uzyskać więcej informacji na temat języka XAML, zobacz [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>Wdrażanie aplikacji przeglądarki XAML  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] są skompilowane aplikacji, które wymagają następujących trzech plików do wdrożenia:  
  
-   *ApplicationName*.exe: plik wykonywalny zestawu aplikacji.  
  
-   *ApplicationName*.xbap: manifest wdrażania.  
  
-   *ApplicationName*. exe.manifest: manifest aplikacji.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat manifesty wdrażania i aplikacji, zobacz [kompilowania aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 Te pliki są tworzone po [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest wbudowana. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji przeglądarki WPF](http://msdn.microsoft.com/library/72ef4d90-e163-42a1-8df0-ea7ccfd1901f). Tylko do znaczników, takich jak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] zwykle są publikowane na serwerze sieci Web i wyświetlać za pomocą [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)].  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] można wdrożyć dla klientów korzystających z dowolną z metod wdrażania. Jednak [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] jest zalecane, ponieważ zapewnia następujące możliwości:  
  
1.  Aktualizacje automatyczne po opublikowaniu nowej wersji.  
  
2.  Podniesienie uprawnień dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uruchamiania przy pełnym zaufaniu.  
  
 Domyślnie ClickOnce publikowanie aplikacji pliki z rozszerzeniem .deploy. Może być problemem, ale można go wyłączyć. Aby uzyskać więcej informacji, zobacz [serwera i klienta problemów z konfiguracją we wdrożeniach ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Aby uzyskać więcej informacji o wdrażaniu [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], zobacz [przeglądu aplikacje przeglądarki XAML w WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>Instalowanie programu .NET Framework  
 Aby uruchomić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji Microsoft .NET Framework należy zainstalować na kliencie. [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] automatycznie wykrywa, czy klienci zostali zainstalowani platformy .NET Framework podczas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje obsługiwane w przeglądarce są wyświetlane. Jeśli nie zainstalowano programu .NET Framework, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] monituje użytkowników, aby go zainstalować.  
  
 Aby wykryć, czy programu .NET Framework są zainstalowane, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] obejmuje aplikacji programu inicjującego, który jest zarejestrowany jako metody rezerwowej [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] obsługi plików zawartości z następującymi rozszerzeniami: .xaml, XPS .xbap i .application. Jeśli przejdziesz do tych typów plików i .NET Framework nie jest zainstalowany na komputerze klienckim, aplikacji programu inicjującego żąda uprawnienia do jej zainstalowania. Jeśli uprawnienia nie zostanie podany, aplikacji ani programu .NET Framework jest zainstalowana.  
  
 Jeśli uprawnienie zostanie udzielone, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] pobierana i instalowana za pomocą .NET Framework [!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)]. Po pomyślnej instalacji programu .NET Framework pierwotnie żądany plik jest otwarty w nowym oknie przeglądarki.  
  
 Automatyczne wykrywanie .NET framework jest dostępna w [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)], i [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] klientów, którzy mają [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] lub nowszy.  
  
 Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji i .NET Framework](../../../../docs/framework/deployment/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Zabezpieczenia](../../../../docs/framework/wpf/security-wpf.md)
