---
title: Wdrażanie aplikacji WPF (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 4679a114f4b6d0bc2b3773d46a4dffa774d38918
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401673"
---
# <a name="deploying-a-wpf-application-wpf"></a>Wdrażanie aplikacji WPF (WPF)
Po skompilowaniu aplikacji Windows Presentation Foundation (WPF) muszą one zostać wdrożone. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]a .NET Framework zawierają kilka technologii wdrażania. Technologia wdrażania, która jest używana do wdrażania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, zależy od typu aplikacji. Ten temat zawiera krótkie omówienie poszczególnych technologii wdrażania oraz sposób ich użycia w połączeniu z wymaganiami dotyczącymi wdrożenia poszczególnych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] typów aplikacji.  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Technologie wdrażania  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].NET Framework obejmuje kilka technologii wdrażania, w tym:  
  
- Wdrażanie polecenia XCopy.  
  
- [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]mieszczeniu.  
  
- Wdrożenie ClickOnce.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>Wdrażanie polecenia XCopy  
 Polecenie XCopy Deployment odnosi się do kopiowania plików z jednej lokalizacji do drugiej przy użyciu narzędzia wiersza polecenia XCopy. Wdrożenie polecenia XCopy jest odpowiednie w następujących okolicznościach:  
  
- Aplikacja jest samodzielna. Nie trzeba aktualizować klienta programu, aby uruchomić program.  
  
- Pliki aplikacji muszą zostać przeniesione z jednej lokalizacji do innej, na przykład z lokalizacji kompilacji (dysk lokalny, [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] udział plików itd.), do lokalizacji publikowania (witryna sieci Web, [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] udział plików itd.).  
  
- Aplikacja nie wymaga integracji powłoki (skrót menu Start, ikona pulpitu itp.).  
  
 Chociaż XCopy jest odpowiednie dla prostych scenariuszy wdrażania, jest ograniczone, gdy wymagane są bardziej złożone możliwości wdrażania. W szczególności użycie XCopy często polega na tworzeniu i wykonywaniu skryptów służących do zarządzania wdrażaniem w niezawodny sposób. Ponadto XCopy nie obsługuje przechowywania wersji, odinstalowywania lub wycofywania.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Instalator Windows  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]umożliwia pakowanie aplikacji jako samodzielnych plików wykonywalnych, które mogą być łatwo dystrybuowane do klientów i uruchamiane. Ponadto program [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] jest instalowany z [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] programem i umożliwia integrację z pulpitem, menu Start i panelami sterowania programy.  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]upraszcza instalację i odinstalowywanie aplikacji, ale nie udostępnia obiektów do zapewnienia aktualności zainstalowanych aplikacji z punktu widzenia wersji systemu.  
  
 Aby uzyskać więcej informacji na temat Instalator Windows, zobacz [Instalator Windows Deployment](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Wdrożenie ClickOnce  
 Technologia ClickOnce umożliwia wdrażanie aplikacji w stylu sieci Web dla aplikacji innych niż sieci Web. Aplikacje są publikowane w sieci Web lub na serwerach plików i wdrażane z nich. Chociaż technologia ClickOnce nie obsługuje pełnego zakresu funkcji [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]klienta zainstalowanych aplikacji, to obsługuje podzestaw, który obejmuje następujące elementy:  
  
- Integracja z menu Start i apletem Panel sterowania programy.  
  
- Przechowywanie wersji, wycofywanie i odinstalowywanie.  
  
- Tryb instalacji online, który zawsze uruchamia aplikację z lokalizacji wdrożenia.  
  
- Automatyczne aktualizowanie po wydaniu nowych wersji.  
  
- Rejestracja rozszerzeń plików.  
  
 Aby uzyskać więcej informacji na temat technologii ClickOnce, zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>Wdrażanie aplikacji WPF  
 Opcje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wdrażania aplikacji zależą od typu aplikacji. Z perspektywy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wdrożenia mają trzy znaczące typy aplikacji:  
  
- Aplikacje autonomiczne.  
  
- Aplikacje tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do znaczników.  
  
- [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Wdrażanie aplikacji autonomicznych  
 Aplikacje autonomiczne są wdrażane przy użyciu [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]technologii ClickOnce lub. W obu przypadkach aplikacje autonomiczne wymagają pełnego zaufania do uruchomienia. Pełne zaufanie jest automatycznie przydzielane do aplikacji autonomicznych wdrożonych [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]przy użyciu programu. Aplikacje autonomiczne wdrożone przy użyciu technologii ClickOnce nie mają automatycznie pełnego zaufania. Zamiast tego, ClickOnce Wyświetla okno dialogowe ostrzeżenia o zabezpieczeniach, które użytkownicy muszą zaakceptować przed zainstalowaniem aplikacji autonomicznej. W przypadku zaakceptowania aplikacja autonomiczna jest zainstalowana i ma przyznane pełne zaufanie. W przeciwnym razie aplikacja autonomiczna nie jest zainstalowana.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Wdrażanie aplikacji XAML tylko do znaczników  
 Strony ze znacznikami są zwykle publikowane na serwerach sieci Web, [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] takich jak strony i mogą być wyświetlane [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]przyużyciu. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Strony zawierające tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczniki są uruchamiane w obszarze piaskownicy zabezpieczeń częściowej relacji zaufania z ograniczeniami, które są zdefiniowane przez zestaw uprawnień strefy internetowej. Zapewnia to równoważną ochronę aplikacji sieci [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]Web opartych na zabezpieczeniach.  
  
 Aby uzyskać więcej informacji o zabezpieczeniach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, zobacz [zabezpieczenia](../security-wpf.md).  
  
 Strony tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do znaczników można zainstalować w lokalnym systemie plików przy użyciu polecenia XCOPY lub [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Te strony można wyświetlać przy użyciu [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] programu lub Eksploratora Windows.  
  
 Aby uzyskać więcej informacji na temat języka XAML, zobacz [Omówienie języka XAML (WPF)](../advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>Wdrażanie aplikacji przeglądarki XAML  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]są skompilowanymi aplikacjami, które wymagają wdrożenia następujących trzech plików:  
  
- *ApplicationName*. exe: Plik wykonywalny aplikacji zestawu.  
  
- *ApplicationName*. XBAP: Manifest wdrożenia.  
  
- *ApplicationName*. exe. manifest: Manifest aplikacji.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat wdrażania i manifestów aplikacji, zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
 Te pliki są tworzone podczas [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kompilowania. Aby uzyskać więcej informacji, zobacz [jak: Utwórz nowy projekt](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))aplikacji w przeglądarce WPF. Podobnie jak w przypadku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron ze [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] znakiem, są zwykle publikowane na serwerze sieci Web [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]i wyświetlane przy użyciu.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]Program można wdrożyć na klientach przy użyciu dowolnych metod wdrażania. Jednak funkcja ClickOnce jest zalecana, ponieważ zapewnia następujące możliwości:  
  
1. Aktualizacje automatyczne po opublikowaniu nowej wersji.  
  
2. Podniesienie uprawnień dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uruchomionego z pełnym zaufaniem.  
  
 Domyślnie ClickOnce publikuje pliki aplikacji przy użyciu rozszerzenia. deploy. Może to być przyczyną problemów, ale można ją wyłączyć. Aby uzyskać więcej informacji, zobacz [problemy z konfiguracją serwera i klienta we wdrożeniach ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Aby uzyskać więcej informacji na [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]temat wdrażania, zobacz [WPF XAML przeglądarki aplikacje przegląd](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>Instalowanie programu .NET Framework  
 Aby można było [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uruchomić aplikację, na kliencie musi być zainstalowana platforma Microsoft .NET. [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]Program automatycznie wykrywa, czy klienci zostali zainstalowani przy użyciu .NET Framework, gdy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] są wyświetlane aplikacje hostowane w przeglądarce. Jeśli .NET Framework nie jest zainstalowana, program [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] poprosi użytkowników o ich zainstalowanie.  
  
 Aby wykryć, czy .NET Framework jest zainstalowana, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] zawiera aplikację programu inicjującego, która jest zarejestrowana jako [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] procedura obsługi rezerwowej dla plików zawartości z następującymi rozszerzeniami:. XAML,. XPS,. XBAP i. Application. Jeśli przejdziesz do tych typów plików, a .NET Framework nie jest zainstalowana na kliencie, aplikacja inicjująca zażąda uprawnień do jej zainstalowania. Jeśli nie zostanie podane uprawnienie, ani .NET Framework ani aplikacja nie zostanie zainstalowana.  
  
 W przypadku udzielenia uprawnień program [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] pobiera i instaluje .NET Framework przy użyciu usługa inteligentnego transferu w tle Microsoft (BITS). Po pomyślnej instalacji .NET Framework pierwotnie żądany plik zostanie otwarty w nowym oknie przeglądarki.  
  
 Funkcja automatycznego wykrywania .NET Framework jest dostępna w [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]systemach [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)], i [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] klientach z [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] zainstalowanym systemem lub nowszym.  
  
 Aby uzyskać więcej informacji, zobacz [wdrażanie .NET Framework i aplikacji](../../deployment/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)
- [Zabezpieczenia](../security-wpf.md)
