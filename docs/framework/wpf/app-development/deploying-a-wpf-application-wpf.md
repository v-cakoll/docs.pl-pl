---
title: Wdrażanie aplikacji WPF (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: a1441f0cc3a7ac715a173be12e68c055ce36ff00
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460135"
---
# <a name="deploying-a-wpf-application-wpf"></a>Wdrażanie aplikacji WPF (WPF)
Po skompilowaniu aplikacji Windows Presentation Foundation (WPF) muszą one zostać wdrożone. Systemy Windows i .NET Framework zawierają kilka technologii wdrażania. Technologia wdrażania, która jest używana do wdrażania aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zależy od typu aplikacji. Ten temat zawiera krótkie omówienie poszczególnych technologii wdrażania oraz sposób ich użycia w połączeniu z wymaganiami dotyczącymi wdrożenia poszczególnych typów aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Technologie wdrażania  
 Systemy Windows i .NET Framework zawierają kilka technologii wdrażania, w tym:  
  
- Wdrażanie polecenia XCopy.  
  
- Wdrożenie Instalator Windows.  
  
- Wdrożenie ClickOnce.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>Wdrażanie polecenia XCopy  
 Polecenie XCopy Deployment odnosi się do kopiowania plików z jednej lokalizacji do drugiej przy użyciu narzędzia wiersza polecenia XCopy. Wdrożenie polecenia XCopy jest odpowiednie w następujących okolicznościach:  
  
- Aplikacja jest samodzielna. Nie trzeba aktualizować klienta programu, aby uruchomić program.  
  
- Pliki aplikacji muszą zostać przeniesione z jednej lokalizacji do innej, na przykład z lokalizacji kompilacji (dysk lokalny, udział plików UNC itd.), do lokalizacji publikowania (witryna sieci Web, udział plików UNC itd.).  
  
- Aplikacja nie wymaga integracji powłoki (skrót menu Start, ikona pulpitu itp.).  
  
 Chociaż XCopy jest odpowiednie dla prostych scenariuszy wdrażania, jest ograniczone, gdy wymagane są bardziej złożone możliwości wdrażania. W szczególności użycie XCopy często polega na tworzeniu i wykonywaniu skryptów służących do zarządzania wdrażaniem w niezawodny sposób. Ponadto XCopy nie obsługuje przechowywania wersji, odinstalowywania lub wycofywania.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Instalator Windows  
 Instalator Windows umożliwia spakowanie aplikacji jako samodzielnych plików wykonywalnych, które mogą być łatwo dystrybuowane do klientów i uruchamiane. Ponadto program Instalator Windows jest instalowany z systemem Windows i umożliwia integrację z pulpitem, menu Start i apletem programy w panelu sterowania.  
  
 Instalator Windows upraszcza instalację i odinstalowywanie aplikacji, ale nie zapewnia możliwości zapewniania aktualności zainstalowanych aplikacji z punktu widzenia wersji programu.  
  
 Aby uzyskać więcej informacji na temat Instalator Windows, zobacz [Instalator Windows Deployment](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Wdrożenie ClickOnce  
 Technologia ClickOnce umożliwia wdrażanie aplikacji w stylu sieci Web dla aplikacji innych niż sieci Web. Aplikacje są publikowane w sieci Web lub na serwerach plików i wdrażane z nich. Chociaż technologia ClickOnce nie obsługuje pełnego zakresu funkcji klienta, które Instalator Windows zainstalowanych aplikacji, obsługuje podzestaw, który obejmuje następujące elementy:  
  
- Integracja z menu Start i apletem Panel sterowania programy.  
  
- Przechowywanie wersji, wycofywanie i odinstalowywanie.  
  
- Tryb instalacji online, który zawsze uruchamia aplikację z lokalizacji wdrożenia.  
  
- Automatyczne aktualizowanie po wydaniu nowych wersji.  
  
- Rejestracja rozszerzeń plików.  
  
 Aby uzyskać więcej informacji na temat technologii ClickOnce, zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>Wdrażanie aplikacji WPF  
 Opcje wdrażania dla aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zależą od typu aplikacji. W perspektywie wdrożenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ma trzy znaczące typy aplikacji:  
  
- Aplikacje autonomiczne.  
  
- Tylko znaczniki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacji.  
  
- Aplikacje przeglądarki XAML (XBAP).  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Wdrażanie aplikacji autonomicznych  
 Aplikacje autonomiczne są wdrażane przy użyciu technologii ClickOnce lub Instalator Windows. W obu przypadkach aplikacje autonomiczne wymagają pełnego zaufania do uruchomienia. Pełne zaufanie jest automatycznie przydzielane do aplikacji autonomicznych wdrożonych przy użyciu Instalator Windows. Aplikacje autonomiczne wdrożone przy użyciu technologii ClickOnce nie mają automatycznie pełnego zaufania. Zamiast tego, ClickOnce Wyświetla okno dialogowe ostrzeżenia o zabezpieczeniach, które użytkownicy muszą zaakceptować przed zainstalowaniem aplikacji autonomicznej. W przypadku zaakceptowania aplikacja autonomiczna jest zainstalowana i ma przyznane pełne zaufanie. W przeciwnym razie aplikacja autonomiczna nie jest zainstalowana.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Wdrażanie aplikacji XAML tylko do znaczników  
 Tylko znaczniki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony są zwykle publikowane na serwerach sieci Web, takich jak strony HTML, i można je przeglądać za pomocą programu Internet Explorer. Tylko znaczniki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony są uruchamiane w obszarze piaskownicy zabezpieczeń częściowej relacji zaufania z ograniczeniami, które są zdefiniowane przez zestaw uprawnień strefy internetowej. Zapewnia to równorzędną piaskownicę zabezpieczeń dla aplikacji sieci Web opartych na języku HTML.  
  
 Aby uzyskać więcej informacji na temat zabezpieczeń aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [zabezpieczenia](../security-wpf.md).  
  
 Tylko znaczniki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony można zainstalować w lokalnym systemie plików przy użyciu polecenia XCopy lub Instalator Windows. Te strony można wyświetlać przy użyciu programu Internet Explorer lub Eksploratora Windows.  
  
 Aby uzyskać więcej informacji na temat języka XAML, zobacz [Omówienie języka XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>Wdrażanie aplikacji przeglądarki XAML  
 Aplikacje XBAP są skompilowanymi aplikacjami, które wymagają wdrożenia następujących trzech plików:  
  
- *ApplicationName*. exe: plik wykonywalny aplikacji zestawu.  
  
- *ApplicationName*. XBAP: manifest wdrożenia.  
  
- *ApplicationName*. exe. manifest: manifest aplikacji.  
  
> [!NOTE]
> Aby uzyskać więcej informacji na temat wdrażania i manifestów aplikacji, zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
 Te pliki są tworzone po skompilowaniu aplikacji XBAP. Aby uzyskać więcej informacji, zobacz [How to: Create a New WPF Browser Application](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Podobnie jak w przypadku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron, aplikacje XBAP są zwykle publikowane na serwerze sieci Web i wyświetlane przy użyciu przeglądarki Internet Explorer.  
  
 Aplikacje XBAP można wdrożyć na klientach przy użyciu dowolnych metod wdrażania. Jednak funkcja ClickOnce jest zalecana, ponieważ zapewnia następujące możliwości:  
  
1. Aktualizacje automatyczne po opublikowaniu nowej wersji.  
  
2. Podniesienie uprawnień dla aplikacji XBAP działającego z pełnym zaufaniem.  
  
 Domyślnie ClickOnce publikuje pliki aplikacji przy użyciu rozszerzenia. deploy. Może to być przyczyną problemów, ale można ją wyłączyć. Aby uzyskać więcej informacji, zobacz [problemy z konfiguracją serwera i klienta we wdrożeniach ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Aby uzyskać więcej informacji na temat wdrażania aplikacji przeglądarki XAML (XBAP), zobacz [Omówienie aplikacji przeglądarki XAML w języku WPF](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>Instalowanie programu .NET Framework  
 Aby uruchomić aplikację [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], na kliencie musi być zainstalowana platforma Microsoft .NET. Program Internet Explorer automatycznie wykrywa, czy klienci są instalowani z .NET Framework podczas wyświetlania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji hostowanych w przeglądarce. Jeśli .NET Framework nie jest zainstalowana, program Internet Explorer poprosi użytkowników o ich zainstalowanie.  
  
 Aby wykryć, czy .NET Framework jest zainstalowana, program Internet Explorer zawiera aplikację programu inicjującego, która jest zarejestrowana jako rezerwowa procedura obsługi rozszerzeń MIME (Multipurpose Internet Mail Extensions) dla plików zawartości z następującymi rozszerzeniami: XAML, XPS,. XBAP i. Application. Jeśli przejdziesz do tych typów plików, a .NET Framework nie jest zainstalowana na kliencie, aplikacja inicjująca zażąda uprawnień do jej zainstalowania. Jeśli nie zostanie podane uprawnienie, ani .NET Framework ani aplikacja nie zostanie zainstalowana.  
  
 W przypadku udzielenia uprawnienia program Internet Explorer pobiera i instaluje .NET Framework przy użyciu Usługa inteligentnego transferu w tle Microsoft (BITS). Po pomyślnej instalacji .NET Framework pierwotnie żądany plik zostanie otwarty w nowym oknie przeglądarki.  
  
 Aby uzyskać więcej informacji, zobacz [wdrażanie .NET Framework i aplikacji](../../deployment/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)
- [Security](../security-wpf.md)
